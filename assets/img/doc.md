# Scroll sections active link

```markdown
# Explicación del Código

El siguiente script de JavaScript implementa un sistema que resalta dinámicamente los enlaces del menú de navegación de acuerdo con la sección visible en la página al desplazarse (`onscroll`).

## Código:

```javascript
let sections = document.querySelectorAll('section');
let navLinks = document.querySelectorAll('header nav a');

window.onscroll = () => {
    sections.forEach(sec => {
        let top = window.scrollY;
        let offset = sec.offsetTop - 150;
        let height = sec.offsetHeight;
        let id = sec.getAttribute('id');

        if (top >= offset && top < offset + height) {
            navLinks.forEach(links => {
                links.classList.remove('active');
                document.querySelector('header nav a[href*=' + id + ']').classList.add('active');
            });
        }
    });
};
```

## ¿Qué hace este código?

Este script sirve para **resaltar automáticamente el enlace activo en el menú de navegación** cuando el usuario se desplaza por la página.

---

## Explicación paso a paso:

1. **Selección de elementos del DOM:**
   ```javascript
   let sections = document.querySelectorAll('section');
   let navLinks = document.querySelectorAll('header nav a');
   ```
   - `sections`: Selecciona todas las etiquetas `<section>` del documento.
   - `navLinks`: Selecciona todos los enlaces (`<a>`) dentro de `header nav`.

2. **Definición del evento `onscroll`:**
   ```javascript
   window.onscroll = () => { ... };
   ```
   - Este evento se ejecuta cada vez que el usuario se desplaza por la página, permitiendo actualizar el estado del menú dinámicamente.

3. **Iteración sobre cada sección:**
   ```javascript
   sections.forEach(sec => { ... });
   ```
   - Para cada `<section>`, se calculan las posiciones y se determina cuál está visible en el navegador.

4. **Cálculo de la posición:**
   ```javascript
   let top = window.scrollY;
   let offset = sec.offsetTop - 150;
   let height = sec.offsetHeight;
   let id = sec.getAttribute('id');
   ```
   - `top`: La cantidad de píxeles que el usuario ha desplazado verticalmente.
   - `offset`: La posición de la sección respecto al borde superior de la ventana, con un margen de 150px.
   - `height`: Altura de la sección actual.
   - `id`: Identificador (`id`) de la sección, usado para enlazarla con el menú.

5. **Validación de la sección visible:**
   ```javascript
   if (top >= offset && top < offset + height) { ... }
   ```
   - Comprueba si la posición de desplazamiento actual (`top`) está dentro del rango de la sección:
     - `top >= offset`: El borde superior de la ventana ha alcanzado el inicio de la sección.
     - `top < offset + height`: El borde superior de la ventana aún no ha salido de la sección.

6. **Actualización del menú de navegación:**
   ```javascript
   navLinks.forEach(links => {
       links.classList.remove('active');
       document.querySelector('header nav a[href*=' + id + ']').classList.add('active');
   });
   ```
   - Elimina la clase `active` de todos los enlaces.
   - Añade la clase `active` únicamente al enlace correspondiente a la sección visible.

---

## ¿Qué logra este código?
- Permite que el enlace correspondiente a la sección visible se resalte automáticamente.
- Ideal para **sitios de una sola página (one-page websites)** con navegación basada en secciones.

## ¿Cómo se ve en práctica?
- A medida que el usuario hace scroll, el script determina qué sección está visible.
- Resalta el enlace correspondiente en el menú de navegación añadiendo la clase `active`.


# Sticky navbar