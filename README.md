# utileria.js


**Nombre** : Santos Ríos Ángel Omar

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
formateoTelefono("951-123-45-67"); // "(951) 123-4567"
formateoTelefono("12345");         // null
```

---

## Capturas de pantalla



```markdown
![Consola con resultados de las pruebas](img/Captura%20de%20pantalla%202026-09-24%20212504.png)
![Modal con la edad calculada](img/Captura%20de%20pantalla%202026-09-24%20212646.png)
![Login exitoso](img/Captura%20de%20pantalla%202026-09-24%20213315.png)
```

---

## Video demo 

> **Video:** `https://youtu.be/jW0cKfBbt38`


