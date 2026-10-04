# Plan del proyecto 2

Inicio: 3 de octubre de 2026. Cierre previsto: 7 de octubre de 2026 (Guatemala).

## Que pide la entrega

- Un diorama pequeno construido con cubos texturizados y efectos de ray tracing.
- Codigo entregado en GitHub y un video del diorama incluido en el README.
- Sin librerias externas al lenguaje, salvo Raylib. Seguiremos con Zig y la ventana Win32 del proyecto anterior, sin dependencias de terceros. Si el profesor considera las llamadas al sistema operativo dentro de esa restriccion, habra que adaptar la ventana a Raylib.
- La escena puede tener el tamano que permita la computadora.

## Alcance elegido: 100 puntos

| Requisito | Puntos | Implementacion prevista | Comprobacion |
|---|---:|---|---|
| Rotacion | 10 | Camara que orbita alrededor del diorama | Ver distintas caras con las teclas |
| Acercar y alejar | 10 | Cambiar la distancia al centro | Zoom con limites sin atravesar la escena |
| Cinco materiales | 25 | Terreno, madera, piedra, vidrio y metal | Cada uno con textura propia, albedo, especular, transparencia y reflectividad |
| Refraccion | 10 | Vidrio con indice de refraccion | Un objeto detras del vidrio se ve desviado |
| Reflexion | 5 | Metal reflectante | Reflejo visible de la escena o del cielo |
| Sombras | 5 | Rayos hacia la luz | Los cubos proyectan sombras sobre el terreno |
| Skybox | 20 | Entorno de seis caras muestreado por direccion | Visible en el fondo y en los reflejos |
| Concurrencia | 15 | Repartir filas entre hilos | Comparar imagen y tiempos con uno y varios hilos |
| **Total previsto** | **100** | | |

Los puntos dependen de la evaluacion del profesor; esta tabla es una meta, no una nota garantizada. Los criterios publicados suman 215, pero la nota esta limitada a 100.

Los extras quedan fuera del alcance inicial: translucidez tipo alabastro, formas y luces no vistas en clase, materiales coloreados especiales, emision y color bleeding. Transparencia con refraccion no equivale al material translucido del criterio extra.

## Como lo haremos

Escena propuesta: una cabana de cubos sobre una base de terreno, con paredes de madera, escalones de piedra, ventanas de vidrio y un objeto metalico que permita apreciar el reflejo.

1. Mantener la ventana y el framebuffer del proyecto anterior; desarrollar el trazador 3D por separado.
2. Crear vectores, rayos, camara e intersecciones con cajas alineadas a los ejes. Guardar distancia, normal y cara de cada impacto.
3. Calcular coordenadas de textura por cara. Usar cinco texturas pequenas propias y parametros de material separados.
4. Agregar luz ambiente, difusa y especular; lanzar rayos de sombra.
5. Agregar rayos secundarios de reflexion y refraccion, con profundidad limitada y desplazamiento del origen para evitar impactos contra la misma superficie.
6. Incorporar el skybox y repartir el render entre hilos con zonas de escritura separadas.
7. Revisar la rubrica, grabar controles y efectos, y enlazar el video real en el README.

Trabajaremos primero a 320 x 240. La resolucion final y el numero de rebotes se decidiran midiendo tiempos en esta computadora.

## Tamano estimado

Proyecto de dificultad media-alta: 30 a 40 horas de trabajo efectivo, incluida una reserva de 4 a 6 horas para errores de texturas, refraccion y concurrencia. No es una medicion ya realizada.

Estimacion de estructura: 10 a 12 archivos Zig (ventana, framebuffer, vectores, rayos, camara, cubos, materiales, texturas, escena, trazador y render), cinco texturas y un skybox de seis caras. Aproximadamente 900 a 1500 lineas de codigo total, incluida la ventana reutilizada; las lineas no seran una meta.

## Cinco dias y dos commits por dia

| Dia | Fecha | Horas | Primer commit | Segundo commit | Resultado del dia |
|---|---|---:|---|---|---|
| 1 | Sabado 3 de octubre | 5-6 | `Agrega la base del proyecto y el plan de trabajo` | `Dibuja los primeros cubos con rayos en 3D` | Ventana ejecutable, camara inicial y cubos visibles |
| 2 | Domingo 4 de octubre | 6-8 | `Agrega rotacion y zoom a la camara` | `Construye la cabana con cinco materiales` | Diorama navegable y cinco texturas con parametros propios |
| 3 | Lunes 5 de octubre | 7-9 | `Agrega iluminacion y sombras a la escena` | `Agrega reflejos y refraccion en el vidrio` | Sombras, metal reflectante y vidrio refractivo |
| 4 | Martes 6 de octubre | 7-9 | `Agrega el skybox al fondo y los reflejos` | `Reparte el render entre varios hilos` | Entorno y concurrencia comprobados con tiempos reales |
| 5 | Miercoles 7 de octubre | 5-8 | `Ajusta la escena y corrige los detalles del render` | `Agrega el video y las instrucciones de entrega` | Revision de criterios, video real y README completo |

Cada commit debe representar un avance probado. Se subira al terminar su bloque de trabajo, en su fecha real; no se usaran commits vacios ni fechas modificadas. Este calendario no crea ejecuciones automaticas para los siguientes dias.

## Estilo de codigo y verificacion

- Nombres simples y relacionados con graficas; funciones pequenas cuando ayuden a entender el calculo.
- Comentarios cortos en espanol que expliquen decisiones, por ejemplo: `Movemos el origen un poco para que el rayo no choque con la misma cara.`
- Evitar comentar operaciones obvias, frases repetitivas y estructuras que no hagan falta. Mantener codigo que podamos leer y explicar.
- Compilar antes de cada commit. Probar intersecciones desde fuera y dentro del cubo, rayos paralelos y seleccion del impacto mas cercano.
- Revisar visualmente texturas, normales, sombras, vidrio y reflejos. Para los hilos, comparar salida y medir tiempos sin prometer FPS antes de probar.
- El video debe mostrar rotacion, zoom, materiales, sombras, reflejos, refraccion y skybox; el README documentara como ejecutar y comprobar concurrencia.

## Pendientes de aclaracion

- Confirmar si el profesor acepta rotacion mediante camara orbital como rotacion del diorama. Si exige rotacion de objetos, adaptar los rayos al espacio local de la escena.
- Confirmar si las texturas generadas por codigo cuentan; para facilitar la revision, planeamos guardar texturas propias como archivos.
- Los enlaces de YouTube se conservaron, pero su contenido no pudo consultarse con la herramienta disponible.
