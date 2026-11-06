# INICIO PROYECTO RUEDA-NOCTURNA

## [05-Nov-2026] - Maquetación Inicial y Configuración
### Hecho:
* Configuré el entorno local usando **Tailwind CSS v4** mediante la terminal (`@tailwindcss/cli`).
* Solucioné una advertencia visual del editor (`unknown at-rule`) desactivando la regla en los ajustes de VS Code.
* Maqueté la estructura HTML principal de la tarjeta.

### Código clave añadido:
```html
<span class="text-red-400">3</span> Rutas
```

### Aprendizaje:
Aprendi a realizar la estructura base de un proyecto con tailwind. Ademas descubri una gran diferencia entre personalziar mi boton con bootstarp y talwind, tuve mas facilidad para relizar los cambios de forma, de color y tipografia con tailwind, la personalizacion me gusto mucho mas.

## [05-Nov-2026] - tailwind cli

## El Experimento
Para entender cómo optimiza Tailwind CSS v4 el tamaño de los archivos en producción, realicé una búsqueda manual dentro del archivo compilado `./dist/output.css` (o `./src/output.css`) buscando dos tipos de clases:

1. **Clase utilizada en el HTML:** Busqué `text-red-400` (el color amarillo del número 3).
   * *Resultado:* **ENCONTRADA**. El compilador generó el código CSS exacto con la regla para pintar el texto de color amarillo.
2. **Clase NO utilizada en el HTML:** Busqué `bg-pink-500` (un color rosado que no está en ninguna parte de la tarjeta).
   * *Resultado:* **NO ENCONTRADA**. La búsqueda dio 0 coincidencias; el código de esa clase no existe en el archivo final.

### ¿Por qué ocurre esto?
Este comportamiento se debe al motor de compilación e inspección nativo de **Tailwind CSS**. A diferencia de los frameworks tradicionales (como Bootstrap) que te entregan un archivo CSS gigante con miles de clases que nunca usas, Tailwind funciona al revés:

* El CLI escanea constantemente mi archivo `index.html` mientras programo (gracias al comando `--watch`).
* Detecta qué clases escribí textualmente en las etiquetas.
* Genera un archivo `output.css` **"limpio"**, inyectando única y exclusivamente las reglas de diseño que la página web está usando en ese instante.

## 🎨 Paleta de Colores Personalizada (Configuración en @theme)

Para el desarrollo del prototipo "Rueda Nocturna", se diseñó una identidad visual inspirada en el ambiente de Medellín en la noche, utilizando las nuevas variables de tema de **Tailwind CSS v4** dentro de `css/styles.css`:

*   **Morado Medellín Neón (`--color-medellin-neon: #a855f7;`)**
    *   *Uso:* Botón principal de acción, estados de foco (`focus:ring`), y sombras de resplandor.
    *   *Propósito:* Funciona como el color de marca principal (punto focal) para simular luces de neón nocturnas.
*   **Verde Medellín Acento (`--color-medellin-accent: #10b981;`)**
    *   *Uso:* Texto de la etiqueta de campaña ("Nuevo · Jueves a sábado").
    *   *Propósito:* Proporciona un contraste accesible sobre el fondo suave (`bg-emerald-100`) y resalta novedades importantes.
*   **Amarillo Ámbar (`text-amber-500` - Nativo de Tailwind)**
    *   *Uso:* Destacar caracteres específicos (el número **3** en "3 Rutas").
    *   *Propósito:* Romper la monotonía del texto oscuro para capturar de inmediato la atención del usuario en los datos clave de la campaña.
*   **Fondo y Textos Base (Gama de Slates y Grises)**
    *   *Uso:* Contenedores principales y tipografías (`text-slate-900`, `text-slate-600`).
    *   *Propósito:* Garantizar una lectura limpia, un contraste de alto nivel y una estética minimalista para la tarjeta física sobre la pantalla.