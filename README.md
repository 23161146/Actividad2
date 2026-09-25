# utileria.js

Librería de JavaScript puro (sin frameworks, sin componentes visuales) con
**8 funciones de validación y utilidad** para formularios: correos,
contraseñas, nombres, teléfonos, edades y fechas de nacimiento.

**Problema que resuelve:** cada vez que se construye un formulario desde
cero, se repite la misma lógica de validación —¿el correo tiene formato
válido?, ¿la contraseña es segura?, ¿la persona es mayor de edad?— y casi
siempre queda regada entre varios archivos o copiada y pegada de un
proyecto a otro. `utileria.js` junta esas validaciones en **un solo
archivo, sin dependencias**, para poder reutilizarlas en cualquier
formulario, modal o pantalla de login con una sola línea:
`<script src="js/utileria.js"></script>`.

> Demo en vivo: `https://<tu-usuario>.github.io/<tu-repo>/`
> (agrega aquí el link una vez activado GitHub Pages)

---

## Instalación

Copia la carpeta `js/` a tu proyecto y agrega el script **antes** de tu
propio código:

```html
<script src="js/utileria.js"></script>
<script>
  // aquí ya puedes usar validarCorreo(), soloLetras(), etc.
</script>
```

No requiere `npm install` ni build: es un solo archivo JavaScript vanilla.

---

## Uso

Las 8 funciones quedan disponibles como globales y también agrupadas en
`window.Utileria`, por si prefieres usarlas con espacio de nombres.

### 1. `validarCorreo(correo)`

Valida el formato de un correo electrónico.

```js
validarCorreo("ana@correo.com"); // true
validarCorreo("ana@correo");     // false
```

### 2. `soloLetras(texto)`

Solo letras mayúsculas/minúsculas, acepta vocales acentuadas, `ñ`/`Ñ` y
espacios entre palabras (para nombres compuestos).

```js
soloLetras("María José"); // true
soloLetras("Peña123");    // false
```

### 3. `validarLongitud(numero, maxLongitud)`

Valida que un número no tenga más dígitos que `maxLongitud`.

```js
validarLongitud(12345, 5);  // true
validarLongitud(123456, 5); // false
```

### 4. `calcularEdad(fechaNacimiento)`

Calcula la edad en años cumplidos.

```js
calcularEdad("2000-05-15"); // p. ej. 26, según la fecha actual
```

### 5. `esMayorDeEdad(fechaNacimiento)`

```js
esMayorDeEdad("2000-05-15"); // true
esMayorDeEdad("2015-01-01"); // false
```

### 6. `validarPassword(password)`

Exige mayúscula, minúscula, número, carácter especial y mínimo 8
caracteres.

```js
validarPassword("Abcdef1!"); // true
validarPassword("abcdefgh"); // false
```

### 7. `calcularFuerzaPassword(password)` — función propia

Complementa a `validarPassword()`: en vez de solo true/false, regresa una
etiqueta de qué tan fuerte es la contraseña, útil para mostrar una barra
de progreso mientras el usuario escribe.

```js
calcularFuerzaPassword("abc");         // "Muy débil"
calcularFuerzaPassword("Abcdefgh1!");  // "Fuerte" o "Muy fuerte"
```

### 8. `formatoTelefono(numero)` — función propia

Da formato `(XXX) XXX-XXXX` a un teléfono de 10 dígitos, sin importar si
el usuario escribió espacios, guiones o paréntesis.

```js
formatoTelefono("9511234567");    // "(951) 123-4567"
formatoTelefono("951-123-45-67"); // "(951) 123-4567"
formatoTelefono("12345");         // null
```

---

## Integración en el proyecto

| Archivo        | Qué usa de la librería                                                   |
|-----------------|---------------------------------------------------------------------------|
| `index.html`    | Las 8 funciones en un formulario real, con una ventana modal que muestra la edad calculada (`calcularEdad` + `esMayorDeEdad`). |
| `login.html`    | `validarCorreo()` y `validarPassword()` en un formulario de inicio de sesión simulado. |

---

## Capturas de pantalla

> Sustituye estos marcadores por tus propias capturas antes de entregar
> (guárdalas en `img/` y actualiza la ruta).
>
> 1. Corre `index.html`, abre la consola (F12) y haz clic en **"Correr
>    pruebas en consola"** — toma una captura de la tabla que imprime
>    `console.table()`.
> 2. Llena el formulario y toma una captura del modal mostrando la edad
>    calculada.
> 3. En `login.html`, toma una captura del mensaje de bienvenida tras un
>    login válido.

```markdown
![Consola con resultados de las pruebas](img/consola.png)
![Modal con la edad calculada](img/modal-edad.png)
![Login exitoso](img/login-exito.png)
```

---

## Video demo (máx. 1 min)

> Graba tu pantalla + tu voz mostrando la librería como si la estuvieras
> vendiendo. Guion sugerido (60 segundos):
>
> 1. **(0–10s) El problema:** "Cada formulario repite la misma lógica de
>    validación de correo, contraseña y edad. Así es como lo resolví."
> 2. **(10–35s) La solución en acción:** abre `index.html`, escribe un
>    correo inválido y muestra el mensaje de error en vivo; escribe una
>    contraseña y muestra cómo sube la barra de fuerza; llena el
>    formulario completo y haz clic en "Crear cuenta" para abrir el modal
>    con la edad calculada.
> 3. **(35–50s) El login:** ve a `login.html`, intenta con una contraseña
>    débil (se rechaza), luego con una válida (mensaje de bienvenida).
> 4. **(50–60s) Cierre:** "Todo esto con un solo script, sin frameworks:
>    `utileria.js`." Muestra el repositorio en GitHub.
>
> Sube el video a YouTube (no listado) o Google Drive y pega aquí el link:
>
> **Video:** `<pega aquí el link>`

---

## Estructura del repositorio

```
/utileria-js
├── README.md
├── index.html
├── login.html
├── css/
│   └── styles.css
├── js/
│   └── utileria.js
└── img/
    └── (capturas usadas en este README)
```

## Cómo publicar en GitHub Pages

1. Sube esta carpeta a un repositorio público en GitHub.
2. En el repositorio: **Settings → Pages → Source** y selecciona la rama
   `main` (o `master`) con carpeta `/root`.
3. Guarda; GitHub te dará un link tipo
   `https://<tu-usuario>.github.io/<tu-repo>/`.
4. Verifica que `index.html`, el formulario, el modal y `login.html`
   funcionen en ese link antes de entregarlo.
5. Deja el link del repositorio y el link de GitHub Pages en un comentario
   dentro de la clase, como se hizo en el ejercicio anterior.

## Autor

Proyecto individual — librería `utileria.js` para formularios, modal y
login.
