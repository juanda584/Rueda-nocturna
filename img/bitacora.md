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