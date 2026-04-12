# Shaders 3 - Bloom: Serafín en Neón
11/04/2026  
CI5321 Computación Gráfica 2  
Grupo: Glender  
Integrantes:  
- Gerel Negreira (09-11163)  
- Gabriel Orejarena (18-10292)  
## Descripción:
   Este proyecto consiste básicamente en la implementación del efecto Bloom en una escena 3D hecha con Three.js y shaders personalizados.
   La escena en si muestra a Serafín, que es un personaje de plastilina representado con estilo de luces de neón. La idea era simular un letrero luminoso sobre un fondo oscuro para que el bloom resaltara mejor. El personaje tiene 2 estados: uno normal con los ojos encendidos y otro en el que aparecen cuchillos enterrados en los ojos. Todo el efecto visual fue hecho para que parezca un anuncio de neón como los que se ven en las tiendas. 
   Además del efecto principal, se pueden modificar varios parámetros en tiempo real para cambiar la apariencia visual de la escena. El parámetro principal del laboratorio para este efecto es la dispersión, pero también se añadieron otros controles complementarios para hacer la presentación más clara y más visual. 
## Cómo correr el proyecto:
   El proyecto tiene un único archivo HTML y no necesita instalación, pero sí necesita que tengas acceso a internet para cargar Three.js desde CDN. 
### Pasos:
1. Descarga el archivo HTML del proyecto.
2. Ábrelo directamente en Google Chrome o en tu navegador favorito.
3. A partir de ahí el sistema arranca automáticamente.
## Requisitos mínimos:
- El navegador debe soportar WebGL.
- Debes tener conexión a internet al abrir el archivo, porque el proyecto usa Three.js cargado desde CDN. 

   Si la pantalla sale negra o el efecto no aparece, debes revisar que revisar que WebGL esté habilitado en el navegador, pero normalmente ya viene activado por defecto.
## Controles generales:
### Cámara:
- Clic izquierdo + arrastrar: Te permite orbitar alrededor de la figura
- Rueda del mouse: La usas para hacer zoom, ya sea para acercar o alejar
### Teclado:
- Q / A: Con ellas subes bajas la dispersión.
- K: La usas para cambiar el estado manualmente.
- M: Con esta tecla activas o desactivas el cambio automático. 
### Panel lateral izquierdo:
   Usa controles en tiempo real para ajustar los parámetros del efecto. Además, los cambios se aplican al toque sin tener que reiniciar la escena. 
   También tiene:
Un checkbox para activar o desactivar el cambio automático.
Un botón para cambiar manualmente entre su versión normal y su versión con cuchillos
## Efecto implementado — Bloom:
   El efecto que elegimos para este Shaders 3 fue Bloom, que básicamente simula la dispersión de la luz en superficies brillantes, generando halos alrededor de las zonas luminosas. En este caso lo usamos para dar la apariencia de tubos de neón encendidos. 
   La implementación funciona en varias etapas:
Primero se renderiza la escena normal.
Luego se extraen solo las zonas suficientemente brillantes.
Después esas zonas pasan por un desenfoque.
Al final se mezclan de nuevo con la imagen base para crear el halo luminoso.
   Esto permite controlar el efecto de forma bastante visual y en tiempo real. 
## Parámetros ajustables:
### Dispersión:
   Es el parámetro principal del shaders 3 para Bloom. Controla qué tanto se expande el halo de luz alrededor de las zonas brillantes. Mientras más alto sea, más abierto se ve el resplandor. 
### Umbral de brillo:
   Define qué zonas son lo suficientemente brillantes como para activar el bloom. Si el valor es bajo, entonces más partes de la escena generan el resplandor; si es alto, solo brillan las zonas más intensas. 
### Intensidad:
   Controlaa la fuerza con la que se mezcla el bloom con la imagen final. Sirve para hacer que el efecto sea más suave o más exagerado. 
### Exposición:
   Ajusta el brillo general de la escena. Ayuda a equilibrar la imagen para que el bloom no se vea ni muy apagado ni demasiado quemado. 
### Velocidad de cambio:
   Maneja la rapidez con la que cambia la figura entre la versión con ojos normales y la versión con cuchillos. 
## Estados visuales de la figura:
   El personaje tiene 2 estados principales:
### Estado 1 — Ojos encendidos:
   Se ve la cara de Serafín con ojos blancos, pupilas negras y sonrisa en neón. Este es la versión por defecto de la figura. 
### Estado 2 — Cuchillos enterrados:
   Los ojos desaparecen y aparecen cuchillos en su lugar, como si estuvieran enterrados en la plastilina. Los cuchillos también tienen ojos dibujados encima, siguiendo la idea del personaje que ya esta explicada en propio archivo .html. 
## Técnicas usadas:
Three.js para construir la escena en 3D.
ShaderMaterial para el postproceso del bloom.
Fragment shaders para la:
Extracción de brillo.
Blur separable.
Composición final.
PerspectiveCamera para reforzar la sensación de profundidad.
OrbitControls para inspeccionar la figura desde varios ángulos.
TubeGeometry, CircleGeometry, ShapeGeometry y otras geometrías para construir la figura y sus detalles.
## Detalles técnicos:
Tecnología: WebGL con Three.js
Versión usada: Three.js desde CDN (0.161.0)
Shaders: Vertex shader de pantalla completa + fragment shaders para las distintas pasadas del bloom.
Escena: Hecha con objetos 3D
Postproceso: Render targets intermedios para el brillo, blur y la mezcla final 
## Organización del código:
   El código está dividido en varias partes para que sea más fácil de seguir:
Interfaz: Aquí básicamente se define el panel visual con los sliders, botones, textos y eventos que permiten cambiar los parámetros en tiempos real.
Configuración base de Three.js: En esta parte se crea el renderer, la escena, la cámara y los controles de orbita para poder ver la figura en 3D.
Implementación del bloom: Aquí está todo lo relacionado con el efecto principal del proyecto, incluyendo los render targets, los shaders y la mezcla final del bloom con la escena.
Funciones auxiliares: Contiene funciones reutilizables para crear materiales, curvas, tubos, elipses, polígonos y otras piezas necesarias para construir la figura.
Construcción de los dos estados visuales: Acá se crean las 2 versiones de Serafin, una normal con los ojos visibles y otra con los cuchillos enterrados.
Configuración de la escena: Aquí se añaden los objetos principales del proyecto a la escena en sí y se organiza la jerarquía general de la figura.
Estado y animación: Es la que se encarga de alternar entre los 2 estados visuales y de aplicarle el movimiento suave a la figura durante la ejecución.
Controles de teclado: En esta parte se programan las teclas que permiten modificar la dispersión y cambiar manual o automáticamente entre estados.
## Comentario final:
   En este trabajo quisimos hacer algo visualmente llamativo pero conservando una estructura simple. La idea era combinar una figura hecha con líneas de neón con un efecto bloom que realmente se sintiera como luz expandiéndose.
   También traté de que la escena fuera fácil de probar y modificar en tiempo real, para que se pudiera ver claramente cómo cambia el efecto según los parámetros, además quería recuperar parte de la idea original que pensaba hacer con Serafín en Blender y en vista de que ya no lo íbamos a usar quise hacer algo mínimamente parecido en este último shaders.