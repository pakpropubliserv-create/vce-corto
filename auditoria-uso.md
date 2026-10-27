# Ade — auditoría de uso

Sobre `plataforma-ade.html`, estado del 27/10/2026. Todo lo que sigue se midió en el
navegador con el guion real del proyecto cargado. No hay nada supuesto: cada hallazgo
tiene abajo el número que lo prueba y el número después de arreglarlo.

El criterio de la auditoría es el eje del proyecto: **de un audio a un rodaje.** Un
fallo se considera grave cuando corta esa cadena en silencio — porque lo que mata un
proyecto no es el error que se ve, es el que no avisa.

---

## Resumen

| | Antes | Ahora |
|---|---|---|
| Fallos que dejaban la aplicación muerta sin mensaje | 6 | 0 |
| Declaraciones CSS que no pintaban nada | 22 | 0 |
| Idiomas que el parser entendía | 1 (portugués con acentos) | 3, con o sin acentos |
| Viñetas de storyboard para un guion de 11 secuencias | 10 | 11 |
| Viñetas de storyboard a nivel de plano | 0 | 49 |
| Forma de sacar un proyecto del navegador | ninguna | `.json` y `.fountain` |

---

## 1 · La aplicación se moría entera, en silencio

**Lo que pasaba.** Todo el estado vive en `localStorage`. `localStorage` lanza
excepción en modo privado, con las cookies bloqueadas, dentro de un iframe aislado y
—esto es lo importante— **al abrir el archivo con doble clic**, porque `file://` y
`data:` no tienen origen. No había un solo `try` en el camino de arranque:
`initProyectos()` moría en su primera línea, el `load` entero se abortaba y quedaba una
página en blanco. Sin mensaje, sin consola, sin nada.

**La medición.** Cargando la plataforma en un iframe de origen opaco, que es
exactamente lo que ve alguien a quien le pasás el archivo por correo:

| | Antes | Ahora |
|---|---|---|
| Secuencias leídas | 0 | 10 |
| Viñetas de storyboard | 0 | 10 |
| Grupos de desglose | 0 | 8 |
| Guion cargado | 0 caracteres | 9.351 |
| Aviso al usuario | ninguno | banda explicando que no se está guardando |

**Lo que se hizo.** Una capa `lsGet` / `lsSet` / `lsDel` con respaldo en memoria: si el
navegador no deja guardar, el trabajo sigue vivo en la pestaña y aparece una banda —no
un `alert`, que interrumpe a quien está escribiendo— que dice qué pasa y ofrece
descargar la copia. Los cinco `JSON.parse` sin red pasaron a `jsonSeguro`: un dato
corrupto ya no puede impedir que la aplicación abra. Y el arranque completo va dentro
de un `try/catch` que, si algo falla, lo dice en vez de quedarse mudo.

---

## 2 · Veintidós declaraciones de estilo que no pintaban nada

El rediseño cambió la hoja de estilos entera pero nadie migró los estilos en línea de
las plantillas JS. Seis tokens quedaron huérfanos: `--primary`, `--secondary`,
`--border`, `--gray-dark`, `--gray-mid`, `--gray-light`.

Una propiedad personalizada que no existe **invalida la declaración completa**. Medido
en el navegador:

- `color: var(--primary)` → resolvía al color del cuerpo. Sin jerarquía ninguna.
- `border: 1px solid var(--border)` → `border-style: none`, `border-width: 0px`. **El
  borde literalmente no existía.**

Dónde dolía más: los **cinco títulos del asistente técnico** («¿Qué tipo de plano?»,
«¿Ángulo de cámara?», «¿Movimiento de cámara?», «Desglose de arte», «Notas técnicas»)
no tenían color, y los campos donde se escribe el desglose de arte **no tenían borde
visible**. El asistente técnico es la herramienta que convierte un guion en una lista
de planos: es justo la pieza que no se podía ver.

También: el separador de cabecera de cada tarjeta de storyboard y los cinco rótulos del
plan de rodaje (Secuencias a rodar, Elenco, Arte, Post, Sonido).

---

## 3 · El storyboard se desincronizaba sin avisar

**Lo que pasaba.** El storyboard se dibujaba recorriendo las **líneas del guion
técnico**, no las secuencias del guion literario. Si el guion crecía y el técnico no,
las secuencias nuevas simplemente no existían para el storyboard.

**La medición.** Guion de 11 secuencias, guion técnico de 10 líneas:

| | Antes | Ahora |
|---|---|---|
| Secuencias leídas | 11 | 11 |
| Viñetas de storyboard | **10** | 11 |
| Aparece en el plan de rodaje | sí | sí |

La secuencia 11 salía en el desglose y en el plan de rodaje, pero no en el storyboard.
Tres pantallas que no se ponían de acuerdo, y ninguna lo decía.

**Lo que se hizo.** Manda el guion literario. El guion técnico se completa solo con una
línea por secuencia que falte, ordenada por número. **No borra** las líneas sobrantes:
una secuencia que hoy no está puede volver mañana y su decupagem costó trabajo.

---

## 4 · La ficha técnica mentía sobre la cámara

`redibujarPanel()` actualizaba los valores buscando los `<span>` **por posición**. Si
una secuencia no tenía PLANO, ese bloque no se renderizaba, todo se corría un lugar y
el plano se escribía dentro del hueco del ÁNGULO.

**La medición.** Secuencia 3, PLANO vacío, se elige «Close-up»:

- Antes: `ÁNGULO Close-up · MOV Frontal` — el plano en la casilla del ángulo y el
  ángulo en la del movimiento.
- Ahora: `Plano Close-up · Ángulo Frontal` — cada valor en su campo.

Ahora se repinta la tarjeta completa desde su función, no se parchean nodos por índice.

---

## 5 · El parser entendía un solo idioma y exigía los acentos exactos

Este es el hallazgo que más pesa para abrir la herramienta a otra gente, porque falla
**en silencio**: se pega un guion, no pasa nada, y no hay forma de saber por qué.

| Cabecera escrita | Secuencias leídas antes | Ahora |
|---|---|---|
| `SEQUÊNCIA 1:` | 1 | 1 |
| `SEQUENCIA 1:` (sin circunflejo) | **0** | 1 |
| `SECUENCIA 1:` (español) | **0** | 1 |
| `SEQUENCE 1:` (inglés) | **0** | 1 |
| `ESCENA 1:` / `SCENE 1:` / `CENA 1:` | **0** | 1 |
| `SEQ. 1 - Título` | **0** | 1 |
| `SONIDO:` | ignorado | se lee |
| `ANIMACION:` (sin cedilla) | ignorado | se lee |

Ahora los marcadores se comparan sin diacríticos y aceptan las variantes de los tres
idiomas, incluidas `TOMAS:` y `SHOTS:` para la lista de planos.

> Esto **no** es todavía la opción de idioma de la interfaz. `traducciones.json` tiene
> las 455 cadenas en portugués e inglés, pero el mecanismo de cambio de idioma sigue
> sin montarse. Lo que se arregló es que el parser deje de ser monolingüe, que es lo
> que impedía que otra persona usara la herramienta en su idioma.

---

## 6 · Lo que escribe la persona rompía la interfaz

Ningún texto del usuario se escapaba antes de meterlo en HTML.

- Un proyecto llamado `El "gato" & <b>cia</b>` perdía el `<b>` y el selector mostraba
  texto corrompido. Con `<img src=x onerror=...>` el selector quedaba inservible.
- El campo ARTE del guion técnico con comillas o con `<` partía la tarjeta del
  storyboard por la mitad.

Ahora todo pasa por `esc()`. Medido: un nombre con `<img src=x onerror=alert(1)>` se
muestra tal cual como texto y no inserta ningún nodo.

---

## 7 · La idea dictada se perdía

El dictado por voz es la puerta de entrada del proyecto: **de un audio a un rodaje**.
Pero `guardarEstadoActual()` sólo guardaba el guion literario y el técnico. Los ocho
campos de la pestaña Idea —incluido el textarea donde cae el dictado— se guardaban
**únicamente al pulsar «Generar guion»**.

Medido: dictar cinco minutos y cambiar de proyecto devolvía `null`. El dictado entero,
perdido, sin confirmación.

Ahora se persiste al escribir, al dictar, al cambiar de proyecto y al cerrar la
pestaña.

---

## 8 · Un proyecto nuevo mostraba tres cosas distintas

Lo primero que ve alguien que empieza de cero:

| Pantalla | Antes | Ahora |
|---|---|---|
| Desgloses | `0 Secuencias · 0 Personajes vivos` | qué son los desgloses y de dónde salen |
| Rodaje | `Guarda el guion literario primero` | qué se calcula y cuándo aparece |
| Storyboard | **una viñeta SEQ 1 inventada**, con «Wide shot» y «Decorado base de la localización principal» para una secuencia que no existe | qué es el storyboard y cómo empezar |
| Ficha | `0 Sólido · 19 Revisar · 6 Falta` y un muro de diagnósticos | las 41 preguntas y un botón para empezar |

Lo del storyboard era lo peor: en un proyecto en blanco, `obtenerTecnicoActual()`
fabricaba una línea técnica fantasma. La ficha era lo segundo: una lista de reproches a
alguien que todavía no había hecho nada mal.

---

## 9 · No había forma de sacar un proyecto del navegador

Todo vivía en `localStorage` y nada salía de ahí. Un «borrar datos de navegación», un
perfil nuevo, un disco que se muere, y no queda nada. Tampoco había manera de llevarse
un proyecto a otra máquina ni de pasárselo a un colaborador.

Esto es, sin vueltas, lo que impedía entregar la herramienta a otra persona.

Ahora, en la cabecera: **Copia de seguridad** (`.json` del proyecto activo),
**Importar** (entra como proyecto nuevo, no pisa nada) y **Guion .fountain** (texto
plano que abre cualquier herramienta de guion). Medido: ida y vuelta de 16 KB con el
guion byte a byte idéntico; un archivo que no sea una copia de Ade se rechaza con un
mensaje en vez de romper algo.

---

## 10 · Defectos menores corregidos

- **`extraerValor` dependía del orden de los campos.** Buscaba la clave como subcadena,
  así que pedir `PLANO` en una línea donde `PLANOS` viniera antes devolvía la lista de
  planos. Medido antes: `"1.1 algo"`. Ahora compara la clave entera.
- **`reLineaSeq` sin anclar.** Un campo ARTE que dijera «como en la escena 5» podía
  hacer que la secuencia 5 pareciera existir. Anclada al inicio de línea.
- **`getMoodColor()`** calculaba cuatro grises que nadie usaba. Eliminada; en su lugar,
  cada viñeta marca su acto.
- **La pestaña Paleta no movía un píxel.** Escribía `--primary` y `--secondary`, que
  tras el rediseño no lee nadie. Ahora mueve el acento del sistema. El resto de la hoja
  está calculada para AA sobre las dos superficies y no se toca desde un selector de
  color.
- **La nota del ilustrador** quedaba entre el boceto y el pie de foto. Va al pie.

---

## El storyboard, rehecho

Una viñeta por secuencia es una portada, no un storyboard. Quien ilustra y quien tira
la cámara trabajan **por plano**, y el campo PLANOS del guion técnico ya tenía los 49
planos numerados del corto sin que nadie los dibujara.

**Vista «Por plano».** 49 viñetas, una por plano numerado. De cada línea
—`1.1 Insert de tela, frontal, 50mm T2.8 — os arquivos caindo`— se deduce el tipo de
plano, el ángulo y la lente, y se muestran junto a la acción.

**El boceto se dibuja con el texto del plano, no con el de la secuencia.** Antes, un
«insert de tela» salía con dos ojos dibujados, porque el boceto leía la descripción de
la secuencia entera, donde hay una actriz. En la vista por plano eso era la mitad de
las viñetas. Ahora 1.1 dibuja un monitor y 1.2 dibuja la papelera.

**Lo demás.** Marca de acto en cada viñeta; ficha etiquetada en vez de una línea
corrida; rejilla de dos láminas en pantalla completa con el boceto a todo el ancho; y
en el PDF desaparecen el conmutador de vista y los campos de nota, que en papel no
sirven para nada.

---

## Lo que queda abierto

1. **La opción de idioma de la interfaz.** `traducciones.json` tiene las 455 cadenas en
   portugués e inglés; falta el mecanismo: función de búsqueda, recorrido del DOM para
   lo que se dibuja dinámicamente, selector en la cabecera y persistencia.
2. **El extractor de audio.** Hoy el dictado cae en un textarea y de ahí a una
   plantilla de diez secuencias con seis `[corchetes]` por rellenar. El eje del
   proyecto pide que de ese audio salgan ya el deseo, el obstáculo, el giro y el final
   separados, y que lo que falte se pregunte en vez de dejarse en blanco.
3. **La sesión McKee son 41 preguntas con 41 campos vacíos.** Es la función que más se
   aleja del eje: pide mucho antes de devolver nada.
4. **Tres decisiones de guion sin responder:** el parpadeo del gato, el idioma del
   guion y quién hace las tres ilustraciones de la secuencia 3.
