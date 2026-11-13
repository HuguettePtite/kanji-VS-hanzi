# 🌸 Visualizing Hanzi & Kanji: Digital Humanities Project

¡Hola! Este repositorio contiene una colección de tarjetas e ideogramas (汉字 / 漢字) construidos vectorialmente con **SVG** y animados con **CSS puro**.

## 📌 Sobre el proyecto

Este proyecto nace de mi pasatiempo de escribir en **Substack**, combinando el aprendizaje de idiomas con la exploración de las **Humanidades Digitales**. 

La idea principal es acompañar mis artículos con una herramienta visual y didáctica donde los lectores puedan:
- Visualizar el orden y dirección exactos de los trazos (*stroke order*).
- Distinguir cada trazo de forma intuitiva gracias a una paleta inspirada en *Sakura Branch & Matcha Honey*.
- Rebobinar y reiniciar la animación con un solo clic sobre la tarjeta.

👉 **[Lee el artículo completo en Substack](https://hugui8b.substack.com/p/shui-dao-qu-cheng?r=7btdxl&utm_campaign=post-expanded-share&utm_medium=web)**

---

## 🛠️ Resumen técnico (De un vistazo)

Para construir estas tarjetas decidí mantener el proyecto **100% libre de JavaScript**, retando las convenciones habituales del desarrollo frontend:

1. **Vectores SVG vs. Texto plano:** Uso de etiquetas `<path>` individuales (apoyándome en *KanjiVG* y *Hanzi Writer*) para dar identidad y dirección a cada trazo.
2. **Trazado manual en plano cartesiano:** Calibración directa de coordenadas `(X, Y)` en el HTML para caracteres como *Puerta* (门).
3. **La ilusión del pincel (`stroke-dasharray` y `stroke-dashoffset`):** Enmascaramiento mediante guiones invisibles revelados secuencialmente con `@keyframes` y `animation-delay`.
4. **Física orgánica con `cubic-bezier`:** Curvas de aceleración que imitan el gesto natural de la mano al apoyar el pincel.
5. **Clases compuestas vs. `:nth-child`:** Asignación explícita de tiempo y color por trazo (`stroke-1 color-1`) para control didáctico total.
6. **Interactividad sin JS (*The Checkbox Trick*):** Uso de un `<input type="checkbox">` oculto vinculado a `<label>` y `:checked` para reiniciar la animación con un clic.

<br>

<details>
<summary><strong>🧠 ¿Quieres saber cómo funciona la magia paso a paso? Haz clic aquí para leer la historia completa (Kishōtenketsu)</strong></summary>

<br>

La creación de los ideogramas fue tanto un ejercicio estético como una inmersión en el diseño vectorial y el desarrollo frontend, simulando el efecto de trazado en tiempo real —como si una mano invisible dibujara cada línea, utilizando únicamente vectores SVG y secretos de CSS puro.

### 1. 起 (Ki) – ¿Por qué SVG y no texto normal
Si colocas un ideograma como texto estándar en HTML (`<text>水</text>`), el navegador solo interpreta la silueta final del carácter, no tiene idea de dónde empieza la pluma, en qué dirección viaja el pincel ni dónde termina el trazo.

Para animarlo, necesitamos vectores. Cada ideograma está compuesto por etiquetas `<path>`, donde cada `<path>` representa un trazo individual del kanji o hanzi (Trazo 1, Trazo 2, etc.). Aunque se pueden dibujar a mano en Figma o Illustrator, para este proyecto me apoyé en bases de datos abiertas como **KanjiVG** y **Hanzi Writer**, que ya tienen miles de caracteres, trazo por trazo.

### 2. 承 (Shō) – La ilusión del trazado continuo
El efecto del pincel invisible se logra combinando dos propiedades de CSS: `stroke-dasharray` y `stroke-dashoffset`.

- **`stroke-dasharray: 200`:** Convierte la línea en patrones de guiones de 200px con espacios de 200px. Como la mayoría de los trazos miden menos de esa distancia, un solo "guión" cubre la línea completa.
- **`stroke-dashoffset: 200`:** "Empuja" ese guión 200px hacia un lado, haciendo que el trazo quede completamente invisible.
- **La animación:** Al reducir progresivamente el desplazamiento de `200` a `0` mediante `@keyframes` y retardos secuenciales (`animation-delay`), el guión vuelve a revelarse, creando la ilusión óptica de que la línea se dibuja en tiempo real.

### 3. 転 (Ten) – Aprendizajes de Ingeniería de Software
En este proyecto decidí salir de la zona de confort y retar algunas convenciones habituales del desarrollo web:

1. **Clases compuestas vs. `:nth-child` (Pensamiento a la inversa):** En lugar de depender de selectores automáticos de CSS (`path:nth-child(n)`), asigné clases explícitas por trazo (`stroke-1 color-1`, `stroke-2 color-2`). Esto me dio un control didáctico total sobre qué color y qué tiempo le corresponde a cada parte del carácter.
2. **Trazado manual en plano cartesiano HTML:** Para ajustar el ideograma de *Puerta* (门), donde la comita superior no encajaba en el espacio correcto, entré directamente a las coordenadas `(X, Y)` dentro del HTML para calibrar sus puntos sin depender de editores visuales.
3. **El truco del Checkbox (Interacción 100% CSS):** Evité intencionalmente `addEventListener` de JavaScript o el simple `:hover`. Usando un `<input type="checkbox">` oculto conectado a un `<label>`, logré que el lector pueda hacer clic real en la tarjeta y reiniciar la animación mediante la pseudo-clase `:checked`.
4. **Física orgánica con `cubic-bezier`:** Usar velocidades lineales hace que el trazado parezca robótico. Al ajustar la curva de aceleración con `cubic-bezier`, el trazo arranca con fuerza y desacelera suavemente al final, imitando el gesto natural de la mano al posar el pincel sobre el papel.

### 4. 結 (Ketsu) – Estructura modular
El resultado final es una colección de tarjetas modulares, ligeras y autocontenidas en este repositorio, pensadas para incrustarse fácilmente en plataformas como CodePen o GitHub Pages y acompañar la divulgación cultural en Substack.

</details>

---

## 🎨 Tecnologías y Estética

- **HTML5 & SVG:** Estructura modular y trazado vectorial.
- **CSS3:** Animaciones, curvas de aceleración y pseudo-clases interactivas.
- **Tipografía:** `Cormorant Garamond` (Google Fonts) para mantener una estética editorial.
- **KanjiVG**:  vector graphics y información sobre kanjis.

---
*Creado para divulgar el aprendizaje interactivo y las humanidades digitales en Substack.* ✍️✨
