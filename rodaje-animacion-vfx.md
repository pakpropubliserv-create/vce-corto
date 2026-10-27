# Você é — plan de animación y VFX

Sale del guion literario `E:\corto\guiao-literario-final.fountain`, diez secuencias, en el estado del commit `e385e12`. Cruzado contra `desglose-tecnico.md` (49 planos, 4 jornadas), `desglose-arte.md` y el diagnóstico de `desglose-produccion.md`. Donde el diagnóstico levantó un problema que toca a este departamento, acá está resuelto o nombrado como decisión, no repetido.

---

## 0 · Lo primero, porque cambia el calendario entero

El desglose técnico ya firmó la decisión que ordena este documento:

> **Las pantallas se filman en directo, con playback en el monitor.** No se ruedan en verde ni se componen en post.

Eso tiene una consecuencia que nadie escribió todavía: **la animación deja de ser post y pasa a ser preproducción.** No es un cambio de método, es un cambio de calendario. Treinta y siete de los cuarenta y tres entregables de este plan tienen que estar terminados, renderizados y probados **antes** de la jornada que los necesita. Si no están, esa jornada no se rueda.

Y si las cuatro jornadas son un bloque consecutivo —J4 = J1 + 3—, entonces en la práctica **todo el playback del corto tiene que estar listo antes de la primera jornada**, incluido el gato del clímax, que es la animación más cara de la película.

Hay una sola palanca de calendario y es gratis en dinero: **separar la jornada 4 del bloque**. Cuesta volver a montar el decorado, más días de cesión de la localización y un riesgo de continuidad que Arte tiene que firmar. A cambio compra semanas para la única pieza que no se puede apurar. Es una decisión de producción y hay que tomarla antes de contratar la localización.

| | |
|---|---|
| Entregables | 43 |
| Segundos de pantalla fabricada | ~142 s (de un corto de ~360 s) |
| Dependencias de set (playback) | 30 |
| Entregables de post puro | 13 |
| Jornada más cargada | J4 — 18 piezas, incluidas las tres más difíciles del corto |
| Jornada sin dependencia de pantalla | J3 |
| Bloqueo más largo | el nombre de la protagonista |

---

## 1 · Qué gana y qué pierde el playback

**Gana**, y son tres cosas que valen plata:

- La luz de pantalla es real. No hay que igualar en post la luz interactiva de nueve secuencias, que era el costo oculto más grande del departamento.
- El eyeline del clímax se resuelve solo. La actriz mira al gato de verdad, en la pantalla de verdad. Era el riesgo que podía tirar abajo la secuencia 9 entera.
- La mano de la actriz sigue a la pantalla, y no al revés. Toda la sincronización de la secuencia 8 —más de treinta trazos— pasa de ser un problema de animación a ciegas a ser un ensayo de veinte minutos.

**Pierde** tres cosas, y hay que decirlas:

- No hay segunda oportunidad. Lo que se rodó, se rodó. Un error de diseño en la gráfica se arregla volviendo a rodar o pagando un screen replacement.
- El brillo del panel es un valor de luz. Si alguien lo toca entre tomas, cambia la exposición. Va anotado en el parte de cámara como si fuera un diafragma.
- **El negro absoluto de la apertura no existe en un LCD.** Un panel mostrando negro a T2.8 devuelve el glow del backlight y el clouding de las esquinas, no 0 IRE. Se resuelve gratis en montaje: el `TELA PRETA` del guion es un corte a negro de sala, y el insert filmado arranca recién cuando entra el primer icono de archivo. Mismo criterio para el `Corte para preto absoluto` del final.

---

## 2 · Sistema gráfico único de interfaz — SG-01

El mismo sistema operativo aparece en seis secuencias. Hoy cada pieza se diseñaría por separado y el espectador vería cuatro computadoras distintas en el mismo cuarto. Esto es la biblia: se hace una vez, se usa seis veces, y nada se diseña fuera de ella.

Criterio: línea pura y espacio en blanco. Sin sombra, sin viñeta, sin degradado. El sistema tiene que leer como un sistema operativo sobrio, no como motion graphics.

### 2.1 · Tokens

| Token | Valor |
|---|---|
| Rejilla | base 8 px, medida sobre la resolución nativa del panel practicable |
| Familia de texto | una sola palo seco con licencia de incrustación, pesos Regular y Medium. Nada más |
| Familia monoespaciada | una sola, peso Regular. Es la de los nombres de archivo y la del upload |
| Escala tipográfica | 11 / 13 / 16 / 22 / 42 px referidos a un panel de 1080 de alto. Proporcional si el panel es otro |
| Fondo de escritorio | gris plano al 18% de luminancia. Sin foto, sin degradado |
| Fondo de ventana | gris 96% |
| Borde | 1 px, gris 70%. **Es el único grosor de borde del sistema** |
| Texto primario | gris 15% |
| Texto secundario | gris 45% |
| Acento | un solo azul apagado. Selección, foco y relleno de la barra de progreso. En ningún otro lado |
| Rojo | existe una sola vez en toda la película: las palabras de la secuencia 4 |
| Radio de esquina | 4 px en ventanas, 0 en todo el resto |
| Sombra proyectada | ninguna |
| Degradado | ninguno |
| Transparencia | ninguna. Las ventanas son opacas y se tapan entre sí |
| Barra de título | 32 px de alto, tres puntos de 8 px a la izquierda, título en 13 px |
| Barra inferior | 40 px, fondo gris 12%, iconos de 24 px |
| Iconografía | caja de 48 px, trazo de 1,5 px, sin relleno. Única excepción: la papelera llena |
| Abrir ventana | 0,3 s |
| Cerrar ventana | 0,5 s. Una sola curva ease-out para todo el sistema |

### 2.2 · Las tres aplicaciones

Todo lo que se ve en pantalla en las diez secuencias sale de tres aplicaciones y un escritorio. No hay una cuarta.

| App | Dónde aparece | Qué incluye |
|---|---|---|
| **Escritorio + Arquivos** | Seq 1, 10 | Fondo liso, grilla de iconos de archivo, icono de papelera con sus cinco estados |
| **Navegador** | Seq 2, 8, 10 | Barra de pestañas, barra de dirección, la página del concurso en sus dos estados, las siete pestañas de inspiración |
| **Desenho** | Seq 2, 3, 8, 9 | Lienzo, barra de herramientas, paleta, panel de capas, panel de referencia, cursor de pincel |

Las tres janelas de la secuencia 3 **no son una cuarta aplicación**: son tres ventanas del sistema con el chrome neutro idéntico. Toda la diferencia que ve el espectador es de contenido, no de envase.

**Propuesta a firmar, cuesta cero:** que el título de cada una de las tres ventanas sea el nombre del archivo que ella borró en la secuencia 1. Ata la secuencia 3 con la 1 sin una línea de diálogo de más y vuelve legible el *«uma versión animada de las artes que ella deletó»* sin explicarlo.

### 2.3 · El cursor

Un solo asset, dibujado a mano, cinco estados: flecha, mano, pincel, espera, texto. Contorno negro de 2 px, relleno blanco, sin sombra. Se usa en las secuencias 1, 2, 4, 8 y 10. Hoy hay dos ítems del desglose pidiendo cada uno su propio cursor: es uno.

Lo que lo hace actuación y no utilería es el temblor: en la secuencia 10 el cursor duda 6 a 8 fotogramas con un temblor irregular de 1 px antes del clic. El animador necesita ver la toma de ella respirando antes de animarlo, y con playback eso es imposible —la gráfica va primero. **Se anima contra la lectura ensayada, no contra la toma buena**, y el margen se gana dejando el cursor quieto sobre ENVIAR en loop hasta que el operador dispare el clic.

### 2.4 · Inventario completo de texto legible

Todo esto lo fabricamos nosotros y todo entra en la decisión de idioma, que hoy no está tomada. Hoy está en portugués. **Si el idioma cambia después de la primera maqueta, se rehace la gráfica de las secuencias 1, 2, 4, 8 y 10.**

| Seq | Cadena | Estado |
|---|---|---|
| 1 | Cinco nombres de archivo | **Bloqueado por riesgo legal** — ver §6 |
| 2 | `Último dia para inscrição.` | Literal del guion |
| 2 | `Tema: IDENTIDADE` | Literal del guion |
| 3 | Tres títulos de ventana | Propuesta: los nombres de archivo de la seq 1 |
| 4 | `REJEITADA` `FRACASSO` `ESTRANHA` `INVISÍVEL` | Literales del guion. Las únicas cuatro permitidas |
| 7 | Firma manuscrita: nombre de ella + `7` | **Bloqueado por el nombre de la protagonista** |
| 8 | Siete nombres de pestaña | **Riesgo legal** — ver §6. Genéricos |
| 8 | Nombre de la aplicación de desenho | A inventar, sin parecido con producto real |
| 10 | Campos del formulario + `ENVIAR` | `ENVIAR` es literal del guion |
| 10 | Nombre del archivo que ella envía | **Sin decidir.** Es el remate del par con los cinco borrados |
| 10 | `UPLOAD 100%` | Literal del guion |
| — | `Você é`, `FIM`, aviso de fotosensibilidad, créditos | Titulaje |

### 2.5 · Lo que NO se diseña hasta que alguien lo pida

Los diez títulos de secuencia del guion (`A LIXEIRA`, `O CONCURSO`, …) son organización del autor hasta que dirección diga lo contrario. Si son cartelas, son diez piezas más, diez interrupciones del arco de silencio y entran en la decisión de idioma. **Hoy no se fabrican.**

---

## 3 · Inventario de entregables

**Tipo:** `BASE` no se ve pero todo depende de él · `SET-Jn` es dependencia de set, sin eso esa jornada no se rueda · `POST` se termina después del rodaje.

**Dificultad:** Baja · Media · Alta · Muy alta.

**Fecha límite:** en días hábiles hacia atrás desde la jornada que la necesita. `J1 − 30` quiere decir treinta días hábiles antes de la primera jornada.

### 3.1 · Bloque base

| ID | Entregable | Técnica | Dur | Dific. | Tipo | Fecha |
|---|---|---|---|---|---|---|
| B1 | Sistema gráfico SG-01 | Documento + librería de componentes vectoriales en un único archivo maestro | n/a | Baja | BASE | J1 − 45 |
| B2 | Asset de cursor, 5 estados | Dibujo a mano, vectorial | n/a | Baja | BASE | J1 − 40 |
| B3 | Icono de papelera, 6 estados | 2D vectorial: `papelera_000` / `020` / `040` / `060` / `100` y el `000` final. Mismo dibujo, misma escala, mismo encuadre | n/a | Baja de ejecución, **crítica de continuidad** | BASE | J1 − 40 |
| B4 | Las cinco artes borradas | Ilustración estática. Tres piezas terminadas (K-POP, POP ART, RUA) más dos variantes. Son el origen de diseño de los tres personajes | n/a | Media-alta | BASE | J1 − 40 |
| B5 | Diseño y turnaround de los tres personajes | Derivados de B4, uno por estilo | n/a | Alta | BASE | J1 − 32 |
| B6 | **El gato de los 7 años** | Dibujo a mano en lápiz de color sobre papel real, escaneado a 1200 dpi con textura de papel. De acá salen las secuencias 7, 8, 9 y 10 | n/a | Alta | BASE | **J1 − 50, y hoy está bloqueado** |
| B7 | UI de la aplicación Desenho | Dentro de SG-01: lienzo, barra, paleta, capas, panel de referencia | n/a | Media | BASE | J1 − 25 |
| B8 | UI del navegador + 7 favicons genéricos | Dentro de SG-01 | n/a | Baja de ejecución, media de riesgo legal | BASE | J1 − 25 |
| B9 | Bobina de prueba de pantalla | 90 s con los casos peores: negro, blanco puro, el tren de pulsos, bordes de 1 px, el cuerpo tipográfico más chico y las tres paletas de personaje | 90 s | Baja | BASE | **J1 − 14**, antes de la prueba de cámara |
| B10 | Carta de luminancia | Un fotograma de referencia y la luminancia media de cada pieza, para que fotografía planifique la clave de cada secuencia | n/a | Baja | BASE | con cada entrega |

> **B6 está bloqueado por una palabra.** El guion pide que el dibujo esté *«Assinado embaixo com letra de criança: o nome dela, e a idade: 7»*, y la protagonista no tiene nombre en ninguna de las diez secuencias. Sin nombre no hay firma, sin firma no hay página, sin página no hay escaneo, y sin escaneo no existen las secuencias 7, 8, 9 ni 10. Es el bloqueo de plazo más largo del proyecto y se destraba con una palabra.

### 3.2 · Jornada 1 — secuencias 1, 2 y 3

Trece planos, siete de ellos inserts de pantalla.

| ID | Seq | Entregable | Técnica | Dur | Dific. | Tipo | Fecha |
|---|---|---|---|---|---|---|---|
| A01 | 1 | Montaje de nombres de archivo | Kinetic type sobre negro, monoespaciada del sistema, blanco al 85%. Cada nombre entra en corte seco y sale en 4 fotogramas. Ritmo acelerando: el primero 0,8 s, el último 0,3 s | 5 s | Baja | SET-J1 | J1 − 7 |
| A02 | 1 | Las cuatro caídas de archivo | Motion graphics 2D. Icono dibujado, no captura. Arco y squash de 2 fotogramas en el impacto, on twos. **Cuatro trayectorias distintas**: si son la misma, se ve un loop en vez de una derrota acumulándose | 6 s | Baja | SET-J1 | J1 − 7 |
| A03 | 1 | La papelera llenándose | Los estados de B3 subiendo de golpe con cada archivo, sin interpolación | 8 s | Baja / crítica de continuidad | SET-J1 | J1 − 7 |
| A04 | 2 | Página del concurso, estado 1 de 2 | Maqueta de web ficticia dentro del navegador de SG-01. Las dos líneas literales. Sin logo ni escudo de ninguna institución real | 6 s | Baja | SET-J1 | J1 − 7 |
| A05 | 2 | Cierre lento de la ventana | Reducción hacia la barra inferior con ease-out largo: 90% del recorrido en el primer tercio del tiempo y después arrastre. La lentitud es dramática, no de sistema | 1,5 s | Baja | SET-J1 | J1 − 7 |
| A06 | 2, 3 | El dibujo fallido en el lienzo | Lo que ella está dibujando mientras ignora todo. Un loop sostenido; no tiene que avanzar, tiene que existir | 15 s loop | Baja | SET-J1 | J1 − 7 |
| A07 | 3 | Apertura de las tres janelas | Escalonadas 6 fotogramas entre sí, chrome idéntico | 2 s | Baja | SET-J1 | J1 − 7 |
| A08 | 3 | **K-POP animado** | Cel 2D, línea fina, paleta pastel cerrada a 6 tonos, on twos con smears. Arcos amplios, cero anticipación, cero peso: *«movimentos suaves e superficiais»*. Idle de 24 fotogramas + lipsync de su única frase | 12 s | Alta | SET-J1 | J1 − 7 |
| A09 | 3 | **POP ART animado** | Animación limitada por sustitución de poses, sin un solo inbetween. Cuatro colores planos y trama benday de 6 px con registro desplazado. Corte seco cada 6 fotogramas. Lipsync a dos bocas. La rigidez es el contenido, no un ahorro | 10 s | Media | SET-J1 | J1 − 7 |
| A10 | 3 | **GRAFITE animado** | Trazo negro de 10-12 px, mancha de spray con goteo, cuerpo rough a 6 fps con el contorno redibujado cada vez (el boiling es el estilo), boca a 12 fps | 10 s | Media | SET-J1 | J1 − 7 |
| A11 | 3 | Palpitación de las tres janelas | Ciclo de escala 100-103-100%, desfasado entre las tres para que respiren a destiempo. Solo escala: sin glow, sin sombra | 12 s simultáneos | Baja | SET-J1 | J1 − 7 |

> **A08, A09 y A10 necesitan las voces grabadas antes de animar.** Son tres lipsyncs y el lipsync se anima contra audio bloqueado, no contra un guion. Sonido tiene que entregar las tres frases grabadas y aprobadas en **J1 − 32**, y esa fecha hoy no existe en ningún plan.
>
> **Los tres son tres mundos incompatibles dentro del mismo monitor**, y el guion lo pide por escrito. Cada ventana es un comp independiente, con su paleta, su frame rate interno y su grade. No comparten LUT ni grano. En producción eso significa tres pases distintos y, si se puede, tres manos distintas.

### 3.3 · Jornada 2 — secuencias 4 y 5

Diez planos. Dos picos físicos de la actriz seguidos.

| ID | Seq | Entregable | Técnica | Dur | Dific. | Tipo | Fecha |
|---|---|---|---|---|---|---|---|
| A12 | 4 | Explosión de las tres janelas | No estallan como vidrio: se rompen como interfaz. El chrome se descompone en bloques de 16 px que salen de cuadro. Solo los primeros 6 fotogramas se ven | 1 s | Media | SET-J2 | J2 − 7 |
| A13 | 4 | **Enjambre de palabras** | Partículas tipográficas. Las cuatro palabras literales y ninguna más. Una tipografía pesada, blanco y negro más el único rojo del corto. Cada instancia vive 4-8 fotogramas, entra desde los cuatro bordes y desde Z. Densidad en curva exponencial: 3 palabras/s al empezar, 40/s al final | 14 s | Alta | SET-J2 | J2 − 7 |
| A14 | 4 | Borrado inútil con el cursor | El cursor arrasta sobre una palabra, la borra, y en el mismo fotograma nacen dos. La regla *1 borrada = 2 nuevas* se repite tres veces para que se entienda sin explicarla | 6 s dentro de A13 | Media | SET-J2 | J2 − 7 |
| A15 | 4 | Glitch de pantalla | Construido a mano en el comp, no con un plugin en automático, para poder cortarlo al fotograma exacto. Tres capas: separación RGB de 2 a 6 px, line drop de 4 líneas, macroblocking de 32 px. En ráfagas de 3 a 5 fotogramas cada 20, nunca continuo | 12 s repartidos | Media | SET-J2 | J2 − 7 |
| A16 | 4 | **Pulsos de luz** | Flicker de luminancia de ±1,5 diafragmas en pulsos irregulares de 2 fotogramas. **Tope no negociable: 3 destellos por segundo, nada de rojo saturado parpadeando.** Con playback esto le pega de verdad en los ojos a la actriz: el tope ahora es protección de ella, no solo del espectador | 10 s simultáneos | Media | SET-J2 | **J2 − 14**, va en la bobina de prueba |
| A17 | 4 | Invasión a cuadro completo | Versiones nuevas a escala completa de los tres. **No se escalan las de la secuencia 3**: el upscale de una línea de 2 px se ve. Tempo al doble y poses más angulares | 8 s | Alta | SET-J2 | J2 − 7 |
| A18 | 5 | Apagado en el golpe de tapa | La pantalla se va a negro en el fotograma del golpe. Con playback no hay sincronía automática: el archivo corta a negro en un punto fijo y la actriz cierra contra ese punto, ensayado. **Rodar además una toma con la pantalla encendida todo el tiempo**, como red: si el aparato es notebook, la tapa tapa la pantalla y el corte se resuelve en montaje gratis | 0,5 s | Baja | SET-J2 | J2 − 7 |

> **La secuencia 4 es donde se recorta si hay que recortar, y nunca la 9.** Si A13 no llega, la versión de emergencia es bajar el enjambre a cuatro beats de palabra sostenida que se multiplican en ráfaga, y dejar que la densidad la cuente el sonido. Es más barata y más seca, y puede ser mejor.

### 3.4 · Jornada 3 — secuencia 6

**Sin dependencia de pantalla.** Es la única jornada que no espera nada de este departamento. El único pedido de set: que la pantalla apagada, el vidrio y cualquier superficie reflectante no devuelvan el rostro de la MÃE, porque limpiarlo después es paint fotograma a fotograma.

| ID | Seq | Entregable | Técnica | Dur | Dific. | Tipo | Fecha |
|---|---|---|---|---|---|---|---|
| A19 | 6 | Limpieza de reflejos de la MÃE | Paint y patch. Volumen imposible de cerrar hasta que dirección resuelva la puesta: si es nuca y manos son 2 o 3 planos de 20-40 fotogramas; si entra entera, bastante más | n/a | Baja | POST | montaje |
| A20 | 7 | Flashback de la infancia | **Si va animado:** 2D en el mismo lápiz de color del caderno, 36 a 48 dibujos a 12 fps sobre papel con grano real. El recuerdo contado en el idioma del caderno, no filmado. **Si va en imagen real:** cae este ítem y aparece una menor, su tutor, su cesión y una jornada corta | 3 s | Media-alta | POST | montaje, J4 + 20 |

> Ojo con el ahorro falso que ya levantó el diagnóstico: **la rama animada no elimina a la menor.** Sonido necesita igual la risa de una nena de 6 a 8 años. Lo que sí elimina es la jornada de rodaje y la segunda unidad del caderno en estado nuevo.

### 3.5 · Jornada 4 — secuencias 7, 8, 9 y 10

Veintidós planos, nueve inserts de pantalla, y las tres piezas más difíciles del corto. **Esta es la jornada que el plan de animación puede hacer caer.**

| ID | Seq | Entregable | Técnica | Dur | Dific. | Tipo | Fecha |
|---|---|---|---|---|---|---|---|
| A21 | 7 | Respaldo 2,5D del pase de páginas | Contingencia. El pase se rueda real con el caderno en mano; esto es por si el timing necesita control exacto: escaneos de las páginas deformados con malla | 10 s | Media | POST | solo si se pide |
| A22 | 7 | Giro cálido | Es grade más la práctica de 2700 K que ya está en el plan de luz. 4 s de rampa en una curva tan lenta que nadie pueda señalar cuándo empezó, y medio diafragma de apertura en sombras. Cero rayos, cero bloom. **Se mantiene hasta el final: nada después de la seq 7 puede volver a ser frío** | 4 s de transición, permanente después | Media | POST | etalonaje |
| A23 | 8 | Despertar de la pantalla | Al abrir el equipo, el sistema vuelve exactamente como ella lo dejó: el navegador con sus pestañas. **El caos de la secuencia 4 no era un estado del sistema, era su cabeza, y por eso no deja rastro.** Negro a interfaz en 0,5 s, como despierta una máquina de verdad | 2 s | Baja | SET-J4 | J4 − 7 |
| A24 | 8 | Cierre de pestañas una por una | Siete pestañas, cada cierre en 8 fotogramas con la barra recolocándose. Las primeras despacio, las últimas en ráfaga. El guion insiste en *«una por una»* | 8 s | Baja | SET-J4 | J4 − 7 |
| A25 | 8 | Navegador en blanco | Blanco, y nada. Sin página de nueva pestaña, sin barra de búsqueda, sin accesos rápidos, sin marca de agua. Es el primero de los dos blancos del corto | 3 s | Baja | SET-J4 | J4 − 7 |
| A26 | 8 | **Nacimiento del gato trazo a trazo** | Se dibuja primero el gato digital terminado —mismo diseño que el infantil, ahora con la mano de quince años de oficio— y después se anima su construcción. **Vía barata y recomendada: grabar el timelapse real del proceso y re-timearlo.** La vía cara es path reveal trazo por trazo, control total por el triple de trabajo. De 28 a 40 trazos reconocibles | 30 s | Alta | SET-J4 | J4 − 10 |
| A27 | 8 | **Split paralelo infantil / digital** | El split vive **dentro de la pantalla**: el panel de referencia de la app Desenho muestra el escaneo del dibujo infantil y el lienzo muestra el trazo naciendo, 4 fotogramas después. Se ilumina un trazo a la izquierda, nace el mismo a la derecha. Así el split cuesta cero comp: es parte del archivo de playback. El reconocimiento llega por coincidencia de forma, **nunca por morph ni cross-dissolve**: si disolvemos, le estamos explicando al espectador lo que tendría que descubrir | los mismos 30 s de A26 | Alta | SET-J4 | J4 − 10 |
| A28 | 8 | Los tres personajes observando | Vuelven al 40% de opacidad, de pie y casi inmóviles, sobre el lienzo. Solo un idle de respiración de 2 o 3 px. Sin diálogo, sin lipsync, sin gesto de amenaza. Reutilizan los diseños de la seq 3 con una pose nueva cada uno: la pose del que ya no tiene nada que decir | 4 s | Media | SET-J4 | J4 − 7 |
| A29 | 8 | Desvanecimiento, uno por uno | Separados 1,5 s entre sí, 20 fotogramas cada uno, perdiendo **primero la saturación y después la opacidad**, en ese orden: el color se va antes que el cuerpo. Sin partículas, sin glitch. La violencia ya pasó en la secuencia 4 y repetirla acá arruina el alivio | 6 s | Media | SET-J4 | J4 − 7 |
| A30 | 8 | El gato llena el espacio | Escala suave al centro del cuadro. **El movimiento lo hace el dibujo, no la cámara**: ni zoom ni push in. Ease largo y una sobreelongación mínima al 102% antes de asentar | 3 s | Baja-media | SET-J4 | J4 − 7 |
| A31 | 9 | **El gato cobra vida, mira y sonríe** | La animación más difícil del corto justamente porque es la más simple. Tres acciones y nada más, las tres escritas. Cel 2D full animation, no on twos: acá cualquier salto delata el truco. Respiración de 36 fotogramas con 2 px en el pecho, giro de cabeza con 3 fotogramas de anticipación y 2 de overshoot | 10 s | **Muy alta** | SET-J4 | **J4 − 14** |
| A32 | 9 | La sonrisa imposible, animada | La boca final tiene exactamente la misma geometría que la del caderno, más ancha que la cara. Lo que importa es cómo llega: 14 a 18 fotogramas de neutra a completa, **con una detención de 3 fotogramas a mitad de camino**. Esa micropausa es la duda antes de confiar, y es lo que separa una sonrisa genuina de un emoticono | 1 s, sostenida 4 s | Alta | SET-J4 | J4 − 14 |
| A33 | 9 | Versión «pleno» del gato | El encabezado de la secuencia abre un segundo espacio, `/ PANTALLA`. Los planos frontales en los que la pantalla llena el fotograma necesitan el gato compuesto para ese encuadre, no recortado del de ventana. Mismo dibujo, segundo comp | n/a | Baja si se planifica, cara si se descubre en post | SET-J4 | J4 − 14 |
| A34 | 10 | Formulario, estado 2 de 2 | El mismo diseño de A04 en estado formulario: campos, campo de adjunto y el tema visible en cabecera. Aparece de golpe en medio segundo, sin animación de entrada elegante: es una web, no un título de crédito | 5 s | Baja | SET-J4 | J4 − 7 |
| A35 | 10 | Adjuntar el archivo | Miniatura del gato entrando en el campo. **Es un render real del gato, nunca un icono genérico**: el guion hace que ella mire lo que manda. Nombre del archivo legible, en contraste con los cinco nombres borrados de la apertura | 3 s | Baja | SET-J4 | J4 − 7 |
| A36 | 10 | Cursor sobre ENVIAR | Llega, se detiene, tiembla 1 px durante 6 a 8 fotogramas y hace clic. El clic es un cambio de estado del botón de 2 fotogramas, seco. Esto es actuación hecha con un cursor | 6 s | Media | SET-J4 | J4 − 7 |
| A37 | 10 | Barra de upload | El guion pide *«subiendo lentamente»* y cierra con `UPLOAD 100%`. Dentro de esa lentitud, progreso **no lineal**: avanza sin prisa, **se traba en 92% durante 3 o 4 segundos** y recién después completa. Borde de 1 px y relleno plano: sin degradado, sin brillo, sin rayas animadas | 12 s | Baja de ejecución, **alta de timing** | SET-J4 | J4 − 7 |
| A38 | 10 | Pantalla en blanco | Blanco puro entrando en un tercio de segundo y sostenido. Cierra el arco que abrió el negro de la secuencia 1. **Con playback, este blanco le lava la cara a la actriz de verdad**: el nivel va medido en la prueba de cámara, no estimado | 3 s | Baja | SET-J4 | J4 − 7 |
| A39 | 10 | **Papelera vacía** | El mismo icono, el mismo encuadre, la misma escala y la misma posición de cuadro que en la secuencia 1, ahora en estado 0%. **Corte seco al estado vacío, sin animación de vaciado**: el guion no muestra a nadie vaciándola, y si la vemos vaciarse el remate se vuelve explicación | 2 s | Baja / **crítica de continuidad** | SET-J4 | J4 − 7 |

> **A39 cambió de bando y hay que avisarlo.** El desglose de producción lo tenía como inserto puramente gráfico, sin actriz y sin plate, terminable después del rodaje. Con la decisión de playback deja de serlo: el desglose técnico lo rueda en el plano 10.6, en la jornada 4, como uno de los tres remates fijos. Es dependencia de set. Es barato, pero tiene fecha.
>
> **A31 es el plano por el que se juzga el corto entero, y ahora tiene que estar terminado antes de rodar.** Versión de emergencia si no llega: el gato no se mueve de cuerpo entero. Es un dibujo sostenido con tres cosas vivas —respiración de 2 px, giro de cabeza y boca—, con el cuerpo en una sola pose mantenida y animación completa solo en la cabeza. Baja el volumen a la mitad sin tocar ninguna de las tres acciones que pide el guion. La segunda red, y es peor, está en §5.

### 3.6 · Titulaje

| ID | Entregable | Técnica | Dur | Dific. | Tipo | Fecha |
|---|---|---|---|---|---|---|
| A40 | Aviso de fotosensibilidad | Blanco sobre negro, misma tipografía que las palabras de la seq 4, sin animación. **No es opcional**: lo obliga A16 | 3 s | Baja | POST | montaje |
| A41 | Cartela de título `Você é` | Igual. Decisión pendiente: al inicio después del negro de apertura, o al final | 3 s | Baja | POST | montaje |
| A42 | Cartela `FIM` | Igual | 2 s | Baja | POST | montaje |
| A43 | Créditos finales | Una sola tipografía, blanco sobre negro, sin degradados, sin logos en color. Cartelas fijas o scroll lento constante. Reservar lugar para los logos de organismos, pasados a blanco y negro | 45-60 s | Baja | POST | montaje |

> Los créditos son titulaje, no animación: **no se computan como segundos de este departamento.**
>
> Hay una decisión de montaje sin dueño y es la primera del corto: en qué orden van el aviso de fotosensibilidad, el título y la `TELA PRETA` de apertura. Sonido diseñó el arranque como un segundo de silencio digital real antes del primer clic; si por delante va una cartela, ese arranque se reescribe.

---

## 4 · Volumen real

El desglose de producción ya avisó que las duraciones por ítem estaban mal sumadas, porque contaba como consecutivas cosas que pasan al mismo tiempo. Esta es la cuenta corregida, por segundos de pantalla efectivos.

| Seq | Segundos de pantalla | Qué los ocupa |
|---|---|---|
| 1 | 12 | Los nombres, las cuatro caídas y la papelera son **simultáneos**, no 19 s |
| 2 | 7 | Aviso + cierre |
| 3 | 14 | Los tres personajes hablan **lado a lado**, no uno después del otro |
| 4 | 18 | Enjambre, glitch, pulsos e invasión **se solapan** |
| 5 | 0,5 | El apagado |
| 7 | 3 | Flashback, si va animado |
| 8 | 50 | El nacimiento y el split son **los mismos 30 s**, no 50 |
| 9 | 10 | El clímax |
| 10 | 31 | Formulario, adjunto, duda, upload, blanco, papelera |
| **Total** | **~146 s** | Sobre un corto de unos 360 s |

Dicho de otra manera: **cuatro de cada diez minutos de esta película son pantalla que fabrica este departamento.** Esa es la proporción con la que hay que presupuestar, y no está lejos de la mitad que el diagnóstico sospechaba.

---

## 5 · Si algo no llega: el plan B, acotado

La red no es «lo arreglamos en post». La red es ésta, y tiene precio.

**Si una pieza de playback no está lista para su jornada:** se rueda igual, con una animática bloqueada en su lugar. La animática tiene que tener **la duración exacta y el encuadre exacto** de la pieza final, porque lo que se está protegiendo es la actuación y la luz, no la imagen. Después se hace screen replacement de esos planos: tracking de cuatro esquinas, roto de manos y cabeza cuando se cruzan, reflejo al 8% y grano.

El costo está acotado y se puede contar antes:

| Jornada | Inserts de pantalla en riesgo |
|---|---|
| J1 | 7 (1.1, 1.2, 2.1, 3.1 y los tres de 3.3) |
| J2 | 2 (4.1, 4.3) |
| J4 | 9 (8.2, 8.4, 8.5, 9.2, 10.1, 10.2, 10.4, 10.5 y la papelera de 10.6) |

Lo que el screen replacement **no** salva: la luz sobre la cara. Si la animática no tiene la misma luminancia media que la pieza final, la clave de ese plano queda mal y hay que igualarla en post rostro por rostro. Por eso B10, la carta de luminancia, se entrega también para las animáticas.

Y hay un plano donde el plan B no existe: **el 9.2.** Si el gato de A31 no está, la actriz no tiene a quién mirar, y el eyeline del clímax no se finge con una marca de cinta. Ese plano se rueda con el gato terminado o se rueda otro día.

---

## 6 · Riesgos legales

Tres de los cuatro son texto que fabricamos nosotros y que se lee en pantalla. Ninguno se arregla en montaje.

### 6.1 · Los cinco nombres de archivo — seq 1, línea 13

Dos problemas en la misma línea:

- **`.psd` aparece cinco veces.** Es la extensión de un formato de una empresa viva, legible a pantalla completa en el primer plano de la película.
- **`ESTILO_BANKSY.psd` nombra a un artista vivo.** Es el más serio de los dos: no es solo la marca, es que el archivo sugiere asociación, y la pieza estática que hay detrás (B4) tendría que ser «en el estilo de» una obra protegida.

**Camino recomendado, y no toca una sola acción del guion.** El sistema operativo del corto es nuestro, así que su formato nativo también. Sustituir la extensión por una propia y reemplazar el nombre del artista por el del estilo, que es lo que el personaje GRAFITE ya es:

`KPOP_FINAL.cnv` · `KPOP_FINAL_V2.cnv` · `POP_ART_FINAL.cnv` · `ESTILO_RUA.cnv` · `CONCURSO_DEFINITIVO.cnv`

Son cinco cadenas de texto, no cinco escenas. El ritmo de cinco nombres acelerando no cambia, el sentido tampoco.

**Camino alternativo:** conseguir la autorización escrita antes de diseñar. Nadie la va a dar para el nombre del artista, y la de la extensión llega tarde para un festival.

Dirección firma uno de los dos. **Hasta que firme, A01 no se diseña**, y A01 es el primer fotograma del corto.

### 6.2 · Las redes sociales de la secuencia 8 — línea 201

El guion dice *«Y comienza a cerrar pestañas. Pinterest. Instagram. Otros tabs de "inspiración"»*. Eso es taquigrafía de guionista, **no texto en pantalla**: las pestañas las dibujamos nosotros y el espectador lee lo que decidamos poner ahí.

**No hace falta tocar el guion.** Las siete pestañas llevan nombres y favicons genéricos, diseñados dentro de SG-01: lo bastante cerca para que se lean como lo que son, lo bastante lejos para no ser marca registrada. El gesto —cerrar las voces que no eran la suya— no depende de que se lea ningún nombre real.

Si dirección quiere que se reconozcan, eso es uso de marca más los logotipos reales, que son obra protegida, y pasa a ser una gestión de clearance con dos empresas antes de la primera maqueta.

### 6.3 · Las tipografías

Toda la gráfica legible del corto —los cinco nombres, las cuatro palabras del ataque, el aviso, el formulario, el upload, el título, `FIM` y los créditos— está hoy especificada como «monoespaciada de sistema» y «tipografía de sistema». **Las fuentes de sistema no vienen licenciadas para incrustarse en una obra que se distribuye y se exhibe.**

Se arregla gratis si se decide ahora: dos familias con licencia abierta que permita incrustación y distribución, una de palo seco y una monoespaciada, y el archivo de licencia viaja en el paquete de entrega. Si se decide después de que la gráfica esté diseñada, hay que rehacer el interletrado y los cuerpos de seis secuencias.

Es una decisión de **J1 − 45**, junto con SG-01.

### 6.4 · Warhol y el street art como gramática

Ya está acordado y lo sostengo: *«Estilo Warhol»* (línea 57) y *«street art»* (línea 59) son indicaciones de dirección en la descripción, no texto en pantalla ni autorización para copiar obra ajena. POP ART es trama benday, cuatro colores planos y registro desplazado; GRAFITE es trazo grueso y spray. Gramática del estilo. **Ninguna pieza de B4 puede ser reconocible como una obra existente**, y eso se revisa con las cinco artes a la vista antes de aprobarlas.

---

## 7 · Protocolo de playback

Sin esto, la decisión de la §0 no se puede ejecutar.

### 7.1 · Cómo se arma cada archivo

Cada pieza se entrega como **un archivo de tres partes**:

1. **Cabeza**: el estado inicial del plano, congelado, en loop indefinido.
2. **Cuerpo**: la acción.
3. **Cola**: el estado final, congelado, en loop indefinido.

El operador dispara con una tecla en «acción» y no vuelve a tocar nada entre tomas: la cola vuelve sola a la cabeza. Así no hay cuenta regresiva en cuadro, no hay flash de sincronía —que arruinaría la toma— y no hay re-cue entre tomas, que es donde se pierde la jornada.

### 7.2 · Especificación de render

- **Resolución nativa del panel practicable, píxel a píxel, reproducido a pantalla completa sin escalado.** Un borde de 1 px escalado deja de ser una línea y se vuelve una mancha gris de 1,5 px. Todo SG-01 se cae por ahí.
- Frame rate del proyecto. **Hoy no está fijado** y todos los tiempos de animación de este plan están en segundos justamente por eso; los conteos de fotogramas se convierten el día que se firme.
- Códec de edición para la copia maestra, más una copia ligera por si la máquina de playback tartamudea. La que tartamudea no sirve: un salto de reproducción es una toma perdida.
- Nomenclatura: `SEQ##_PIEZA_v##_<rate>_<resolución>`. Una sola convención para todo el departamento.

### 7.3 · La máquina y el panel

- Notificaciones apagadas, suspensión apagada, cursor del sistema oculto, modo nocturno y ajuste automático de color apagados.
- **Brillo fijado y anotado en el parte de cámara**, igual que un diafragma. Nadie lo toca.
- Frecuencia de refresco fijada según el resultado de la prueba de cámara.
- Dos copias idénticas en dos discos más la del disco interno. El punto único de falla del proyecto son dos archivos —el escaneo del gato y el paquete de playback— y hoy nadie es dueño de respaldarlos.

### 7.4 · Calendario de entrega, por jornada

| Hito | Cuándo |
|---|---|
| Animática y duraciones bloqueadas de esa jornada | J − 21 |
| Bobina de prueba B9 entregada | J1 − 14 |
| **Prueba de cámara con pantallas** | antes de J1, con B9 |
| Pieza maestra renderizada y entregada a producción | J − 7 |
| Ensayo de playback en el monitor real, en el cuarto real | J − 2 |
| Copias de respaldo verificadas | J − 1 |

### 7.5 · El ensayo de la secuencia 8

Veinte minutos de agenda que ahorran una pieza entera de trabajo. Con playback, **la mano de la actriz sigue al trazo de la pantalla**, no al revés. Hay que ensayar A26 una vez con ella, con la tableta o el mouse que se haya decidido, y marcar en la mesa las posiciones. Si no se ensaya, la mano va a ir a destiempo en los más de treinta trazos del split y no hay montaje que lo arregle.

---

## 8 · Decisiones que no son mías y que me bloquean

Cada una nombrada, ninguna supuesta. Ordenadas por lo que cuesta no tomarlas.

| # | Decisión | Dueño | Qué bloquea | Para cuándo |
|---|---|---|---|---|
| 1 | **El nombre de la protagonista** | Dirección | B6, y detrás las secuencias 7, 8, 9 y 10 enteras | J1 − 55 |
| 2 | Familias tipográficas con licencia de incrustación | Producción | SG-01 y toda la gráfica legible | J1 − 45 |
| 3 | Los cinco nombres de archivo: sustituir o gestionar | Dirección | A01, el primer fotograma del corto | J1 − 45 |
| 4 | **Idioma único del texto en pantalla** | Dirección | Seq 1, 2, 4, 8, 10, el título, `FIM` y la firma del dibujo | J1 − 45 |
| 5 | **Monitor o notebook** | Dirección / Arte | La resolución de render, el protocolo de playback y si la secuencia 5 se puede rodar como está escrita | J1 − 40 |
| 6 | Frame rate, resolución, relación de aspecto y espacio de color del proyecto | Producción | Todos los renders de playback | J1 − 40 |
| 7 | **¿Se separa la jornada 4 del bloque?** | Producción | Si no se separa, A31 vence tres días después de J1 | antes de firmar la localización |
| 8 | Dónde aparecen los tres personajes en la seq 8, y cómo desaparece la realidad en la 4 | Dirección | A17 y A28. **Propongo: los dos dentro de la pantalla** — ver abajo | J1 − 30 |
| 9 | Flashback animado o en imagen real | Dirección | A20, y del otro lado una jornada y una menor | J1 − 30 |
| 10 | La línea de acción de la ARTISTA en la secuencia 9 | Dirección | A32: la sonrisa del gato refleja una sonrisa que hoy no está escrita | antes del plan de rodaje |
| 11 | Tableta o mouse | Dirección | El cursor de pincel de B7 y el ensayo de §7.5 | J1 − 25 |
| 12 | El nombre del archivo que ella envía | Dirección | A35, que es el remate del par con los cinco borrados | J4 − 14 |
| 13 | Orden de apertura: aviso, título, `TELA PRETA` | Dirección / Montaje | A40 y A41, y el arranque de sonido | montaje |
| 14 | ¿Los diez títulos de secuencia son cartelas? | Dirección | Diez piezas que hoy no existen en ninguna lista | montaje |

### Sobre la 8, porque es la cara y tiene respuesta barata

El guion pone a los tres personajes *«en el fondo de su consciencia»* (seq 8) y dice *«Toda a realidade parece desaparecer»* (seq 4). Ninguno de los dos es un lugar filmable, y una sola respuesta cubre los dos.

**Propongo la versión barata y la firmo: todo se queda dentro de la pantalla.**

- En la secuencia 4 la realidad no desaparece por VFX: desaparece por luz y encuadre. El plano 4.5 ya es un general con holandés acentuado, y con los pulsos de A16 como única fuente el cuarto cae a negro solo. No cuesta un peso y se decide en rodaje.
- En la secuencia 8 los tres vuelven al 40% sobre el lienzo, dentro del monitor. Un comp de pantalla, que además es parte del archivo de playback y por lo tanto ya está pago.

La versión cara —la gráfica sale del monitor y toma el cuarto— exige roto del cuarto entero, tratamiento del plate y matte painting. Es el pico del segundo acto y es el único lugar donde este departamento podría duplicar su costo. **Si dirección la quiere, que la pida por escrito y con su propia partida.**

### Sobre el aviso de la secuencia 2, que el diagnóstico dejó huérfano

El guion dice *«A notícia não traz esperança»* y lo único escrito en pantalla son un plazo y un tema: ninguna de las dos líneas es una noticia ni es mala. Dos salidas y las dos son baratas:

- **(a), recomendada y cuesta cero:** no se agrega nada. La noticia no es mala por lo que dice la pantalla, es mala por lo que ella no tiene para mandar. El plano 2.2 lo carga con actuación, que es para lo que existe.
- **(b):** una tercera línea en el mismo asset, un reloj de cierre corriendo hacia atrás. Sube la apuesta y es un elemento más en A04. Si se elige, entra en la decisión de idioma.

---

## 9 · Lo que este departamento no va a hacer

Para que nadie lo presupueste dos veces ni lo espere el día del rodaje.

- **Nada encima del clímax.** Ni glow, ni destello, ni partículas, ni pulso, ni cambio de grade, ni vibración de pantalla sobre el plano del gato. Es una decisión, no una omisión: todo lo que pongamos ahí va a leerse como que la emoción no se sostenía sola.
- **Nada en la secuencia 5.** Fuera de A18 y de la limpieza que pida el rodaje, ni un fotograma. Es la única secuencia que el corto no puede recuperar y se recupera con silencio, no con capas.
- **Ninguna transición ceremonial en el final.** Los tres remates son cortes. Lo ceremonial lo da la duración de cada plano y el silencio. La nota de `ANIMAÇÃO` de la secuencia 10 pide *«transiciones finales suaves»* y las tres líneas de acción dicen `Corte`. **Propuesta a aprobar: 3 s, 3 s y 2 s de negro, todo a corte.** Si alguien pide encadenados, el final pasa de ritual a postal.
- **Ninguna interfaz de redes sociales en la secuencia 7.** El guion dice que ella *«Lembra de quem era antes de pensar em likes, seguidores, algoritmos»*. Eso es interioridad y se resuelve con actuación y el macro del papel. Si dirección quiere ver los likes, aparece un set gráfico nuevo que no está en ninguna línea de este plan y que contradice el criterio de no rellenar la secuencia 7.
- **Ningún scanline, moiré ni curvatura de tubo.** La pantalla es LCD.
- **Ninguna de las diez cartelas de secuencia**, hasta que la decisión 14 se tome.
