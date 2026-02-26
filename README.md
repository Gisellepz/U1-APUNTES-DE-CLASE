# U1 - APUNTES DE CLASE
Apuntes realizados en la Unidad 1

---

Evolución y Fundamentos Técnicos
   
---
   
* **Origen:** La transición va desde sistemas puramente textuales hacia entornos visuales complejos, partiendo del "punto" como unidad básica.
* **De 2D a Realismo 3D:** El salto evolutivo implica el uso de transformaciones (traslación, escalamiento, rotación y sesgado) mediante representación matricial.
* **Técnicas de Sombreado:** Se destacan tres niveles de realismo en iluminación: Interpolado, Gouraud y Phong.

---

Aplicaciones Prácticas y Herramientas
   
---

Áreas de Impacto:

* **Medicina:** Modelado para capacitación médica y entornos de simulación técnica.
* **Entretenimiento:** Interfaces virtuales en videojuegos y medios interactivos.
* **Arquitectura:** Uso de diseño paramétrico para convertir datos en estructuras complejas (ej. puentes o edificios vanguardistas).
* **Blender vs. 3ds Max:** En el diseño arquitectónico, Blender destaca por su fuerte diseño paramétrico y velocidad de modelado, mientras que 3ds Max se considera superior en potencia de renderizado (Global Illumination).

---

Flujo de Trabajo Moderno
   
---
   
* **Uso de Modificadores:** Herramientas como Array, Bevel y Subdivision Surface permiten un flujo de trabajo "no lineal", editando la geometría base sin destruir las operaciones aplicadas.
* **Simplicidad a Complejidad:** La filosofía de diseño actual busca crear sistemas complejos (como ciudades o estructuras orgánicas) a partir de herramientas y polígonos simples.


---

Naturaleza y Filosofía de Blender

---

* **Software Libre y de Código Abierto:** Blender es una suite de creación 3D gratuita que permite a los usuarios no solo usar el software, sino también modificar su código fuente.
* **Comunidad Global:** Su desarrollo es impulsado por una vasta comunidad de artistas y desarrolladores que colaboran para mejorar sus capacidades continuamente.
* **Integración Total:** Se define como una solución "todo en uno", eliminando la necesidad de importar y exportar archivos entre múltiples programas para completar un proyecto.
  

---

Capacidades de Modelado y Diseño

---

* **Creación desde Píxeles a Polígonos:** El flujo de trabajo permite representar y transformar objetos tanto en 2D como en 3D basándose en principios matemáticos.
* **Modelado Paramétrico:** Utiliza objetos y datos (como curvas) para controlar la geometría de estructuras complejas, siendo muy útil en arquitectura.

---

Realismo Visual y Animación

---

* **Sombreado e Iluminación:** Aplica modelos como **Phong** y **Gouraud**, junto con texturizado avanzado, para dar vida y profundidad a los objetos.
* **Motores de Renderizado:** El documento destaca su capacidad de "Global Illumination" (GI), esencial para lograr un renderizado fotorrealista.
* **El Arte del Movimiento:** Explora tanto técnicas 2D (*morphing*) como 3D (*skeletal* y *motion capture*) para crear secuencias dinámicas y realistas.

---

Pasos para iluminar un cubo y sus caras

---

1. Preparación de la Escena

Antes de iluminar, necesitamos que el cubo tenga dónde proyectar sombra y un material que reciba la luz.

* **Añade un suelo:** Presiona Shift + A > Mesh > Plane. Presiona S y escribe 10 para hacerlo grande.
* **Sube el cubo:** Selecciona el cubo, presiona G y luego Z para moverlo justo encima del plano.
* **Crea un Material:** Selecciona el cubo, ve al panel de Material Properties (el icono de la esfera roja), dale a New y elige un color en Base Color.


2. Tipos de Luces en Blender

Para iluminar las caras, debes elegir la fuente de luz adecuada (Shift + A > Light):

* **Point (Punto):** Como un foco de mano; la luz sale en todas direcciones. Ideal para resaltar una esquina.
* **Sun (Sol):** Luz infinita y paralela. No importa dónde la pongas, solo importa su rotación (R).
* **Spot (Foco):** Un cono de luz. Perfecto para efectos dramáticos sobre una cara específica.
* **Area (Área):** Un panel de luz. Es la que da las sombras más suaves y realistas.


3. Técnica de Iluminación de 3 Puntos

Para que todas las caras del cubo se vean bien definidas y no como una mancha plana, usa este esquema:

* **Key Light (Luz Principal):** Coloca una Area Light a 45° frente al cubo. Es la que define la forma. Sube su Power a unos 500W.
* **Fill Light (Luz de Relleno):** Coloca otra luz del lado opuesto a la principal. Baja su potencia (ej. 200W). Su función es suavizar las sombras oscuras para que se alcancen a ver los detalles de las caras en sombra.
* **Back Light (Luz de Contorno):** Pon una luz detrás del cubo apuntando hacia él. Esto crea un borde brillante que separa al cubo del fondo negro.


4. Sombreado de las Caras

Si quieres que las caras se vean planas y definidas o suaves y curvas, debes elegir el modo de sombreado:

* **Shade Flat (Sombreado Plano):** Haz clic derecho sobre el cubo y elige Shade Flat. Esto hará que cada cara tenga un color sólido según la luz, resaltando las aristas.
* **Shade Smooth (Sombreado Suave):** Si quieres que parezca una esfera o algo orgánico, elige esta opción. La luz se "difumina" entre las caras.


5. Ver el Resultado (Render)

Para ver realmente cómo queda la iluminación:

* **Presiona la tecla Z y selecciona Rendered.**
* **Eevvee vs Cycles:** En el panel de Render Properties (icono de cámara de fotos):
  
       Usa Eevee para rapidez (activa Ambient Occlusion y Bloom).
       Usa Cycles para realismo máximo (calcula rebotes de luz reales en las caras).

<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/a377c04f-6721-4d0a-89dc-2edef5306bc6" />


---

Comparativa Técnica en Arquitectura

---

Comparativa directa entre **Blender** y **3ds Max** en el ámbito arquitectónico:

| Característica | Blender | 3ds Max |
| --- | --- | --- |
| **Diseño Paramétrico** | Muy Fuerte | Limitado |
| **Velocidad de Modelado** | Muy Fuerte | Limitado |
| **Renderizado (GI)** | Limitado (en comparación) | Muy Fuerte |


---

El Proceso de Rasterización y Trazo

---

¿Cómo se "dibujan" formas geométricas en una rejilla de pixeles?

* **Representación de Líneas y Polígonos:** Es el proceso de convertir ecuaciones matemáticas continuas en coordenadas de pixeles discretas.
* **Algoritmo de Bresenham:** Se destaca como la solución estándar para el trazado de líneas porque utiliza aritmética de enteros, lo que lo hace extremadamente rápido para el hardware.
* **Procesamiento de Mapas de Bits:** Las imágenes se gestionan como matrices de pixeles donde cada celda contiene información de color y brillo.

---

Modelos de Color y Percepción 

---

* **Modelos Cromáticos:**

      RGB: El estándar para pantallas basado en la síntesis aditiva.
      CMY: Utilizado para la impresión física.
      HSV y HSL: Modelos diseñados para ser más intuitivos para el ser humano, separando el matiz de la saturación y el brillo.

* **Percepción Visual:** La graficación no solo es técnica, sino que busca engañar al ojo humano mediante el uso correcto de estos modelos de color.

---

Aspectos Matemáticos y Transformaciones

---

Sin estas operaciones, los objetos serían estáticos y planos:

* **Transformaciones 2D:** Se mencionan la Traslación, el Escalamiento, la Rotación y el Sesgado (Shear) como las herramientas básicas para generar movimiento.
* **Representación Matricial:** Todas estas transformaciones se calculan mediante matrices, lo que permite que la GPU procese miles de polígonos simultáneamente.
* **Coordenadas Homogéneas:** Es el truco matemático que permite unificar todas las transformaciones en una sola operación matricial.


---

Formatos y Almacenamiento

---

* **Formatos de Imagen:** El documento distingue entre cómo se guardan los datos, diferenciando entre mapas de bits (pixeles) y vectores (ecuaciones).

<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/69da6498-8e8b-40a6-b96b-0c6bfcd31556" />
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/96cc4f49-df2e-42a2-bd14-16cc9a2732b8" />

* **Compresión:** Menciona la importancia de optimizar el tamaño de los archivos según el uso final (web, impresión o renderizado).

---

El Rol del Ingeniero en Sistemas

---

* **De Consumidor a Creador:** La graficación no es solo estética; el objetivo del ingeniero es entender los elementos fundamentales (matemáticas y algoritmos) para diseñar interfaces eficientes y atractivas.
* **Sistemas Visuales Modernos:** Actualmente, el ambiente computacional es 100% visual. Se requiere competencia técnica para manejar flujos de datos en tiempo real y transformarlos en representaciones gráficas (Dashboards, UI/UX).

---

¿Cómo se guardan los datos visuales? 

---

* **JPG:** Compresión con pérdida (Lossy). Elimina frecuencias altas de color que el ojo no nota para ahorrar espacio.
* **PNG:** Compresión sin pérdida (Lossless). El estándar para interfaces web porque soporta el Canal Alfa (transparencia).
* **GIF:** Limitado a 256 colores; usado para animaciones simples y color indexado.
* **BMP:** Datos crudos (Raw). Muy rápido de leer por la CPU pero muy ineficiente en almacenamiento.Shutterstock

---

Procesamiento Digital de Imágenes

---

El procesamiento se define matemáticamente como una función de transformación: $g(x,y) = T[f(x,y)]$.

* **Operaciones Puntuales:** El valor de un píxel de salida depende solo de su valor de entrada original.
Brillo: Se logra sumando una constante al valor del píxel ($P_{new} = P_{old} + C$).
* **Contraste:** Se logra multiplicando por una constante.
* **Inversión (Negativo):** Se resta el valor original al valor máximo ($255 - P_{old}$).

---

Algunos conceptos que serían útiles:

---

* **Pipeline de Compresión Digital:** El proceso de convertir fotorrealismo en geometría eficiente implica descartar datos redundantes mediante cuantización.
* **Estructura del Píxel:** En memoria, un píxel se representa a menudo como un struct de bytes para R, G, B y a veces K (en modelos sustractivos).
* **Frecuencias Espaciales:** El procesamiento avanzado analiza la imagen no solo como puntos, sino como ondas donde se pueden filtrar ruidos o resaltar bordes.



---

Bibliografía 

---

* *Blender Foundation. (2024). Blender 4.2 Manual: The Python API. Recuperado de https://docs.blender.org/api/current/*
* *Secretaría de Educación Pública (SEP). (s.f.). Unidad 1: Introducción a la Graficación por Computadora: La intersección entre matemáticas, algoritmos y percepción visual [Documento PDF]. Tecnológico Nacional de México (TecNM).* 
* *Secretaría de Educación Pública (SEP). (s.f.). Graficación Computacional: La Ciencia del Pixel. Unidad 1.5-1.6: Formatos de Imagen y Procesamiento de Mapas de Bits [Documento PDF]. Tecnológico Nacional de México (TecNM).*
* *Secretaría de Educación Pública (SEP). (s.f.). Blender: La Revolución del Código Abierto en el Diseño Arquitectónico y Educativo [Documento PDF]. Tecnológico Nacional de México (TecNM).*
* *Secretaría de Educación Pública (SEP). (s.f.). Visual Systems Engineering: La Era de la Interfaz Visual [Documento PDF]. Tecnológico Nacional de México (TecNM).*



