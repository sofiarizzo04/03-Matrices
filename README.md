# Matrices (Arrays) en JavaScript

**Profesor:** Juan Reichert  
**Curso:** LPR 

---

## Temas

- Introducción a los arrays
- Bucles `for` con arrays
- Métodos adicionales de arrays

---

## Introducción a los arrays (matrices/arreglos)

En la lección anterior discutimos los 3 tipos de datos básicos (cadenas/strings, números y booleanos) y cómo asignar esos tipos de datos a las variables. Una variable solo puede apuntar a una sola cadena, número o booleano. Sin embargo, en muchos casos queremos poder apuntar a una **colección** de tipos de datos.

Podemos pensar en las matrices como **contenedores de almacenamiento para colecciones de datos**. Construir una matriz es simple: declarar una variable y establecerla en `[]`. Luego podemos agregar elementos separados por coma.

```js
const nombresEstudiantes = ['Martin', 'Antonio', 'Sara', 'Samuel'];
```

---

## `.length`

Al igual que el tipo de dato `String`, la matriz tiene un método incorporado `.length` que devuelve el número de elementos en la matriz.

```js
const nombresEstudiantes = ['Martin', 'Antonio', 'Sara', 'Samuel'];
console.log(nombresEstudiantes.length); // 4
```

---

## Acceso a elementos en una matriz

Los elementos reciben una posición numérica (índice) de acuerdo con su ubicación. El orden **siempre comienza en 0**.

| Índice | 0        | 1         | 2      | 3        |
|--------|----------|-----------|--------|----------|
| Valor  | 'Martin' | 'Antonio' | 'Sara' | 'Samuel' |

```js
console.log(nombresEstudiantes[1]); // 'Antonio'

// Acceder dinámicamente al último elemento:
console.log(nombresEstudiantes[nombresEstudiantes.length - 1]); // 'Samuel'
```

---

## Asignación

Podemos asignar y reasignar cualquier índice usando corchetes y `=`.

```js
nombresEstudiantes[0] = 'Jorge';
console.log(nombresEstudiantes); // ['Jorge', 'Antonio', 'Sara', 'Samuel']
```

---

## `.push` y `.pop`

| Método    | Descripción                                          |
|-----------|------------------------------------------------------|
| `.push()` | Agrega un elemento al **final** de la matriz.        |
| `.pop()`  | Elimina el último elemento de la matriz y lo retorna.|

```js
nombresEstudiantes.push('Patricia');
console.log(nombresEstudiantes); // ['Martin', 'Antonio', 'Sara', 'Samuel', 'Patricia']

nombresEstudiantes.pop();
console.log(nombresEstudiantes); // ['Martin', 'Antonio', 'Sara', 'Samuel']
```

---

## `.unshift` y `.shift`

Igual que `.push` y `.pop`, pero operan sobre el **primer** elemento.

| Método       | Descripción                                           |
|--------------|-------------------------------------------------------|
| `.unshift()` | Agrega un elemento al **inicio** de la matriz.        |
| `.shift()`   | Elimina el primer elemento de la matriz y lo retorna. |

```js
nombresEstudiantes.unshift('Leo');
console.log(nombresEstudiantes); // ['Leo', 'Martin', 'Antonio', 'Sara', 'Samuel']

nombresEstudiantes.shift();
console.log(nombresEstudiantes); // ['Martin', 'Antonio', 'Sara', 'Samuel']
```

---

## Notas sobre las matrices

Debido a que JavaScript no es un lenguaje fuertemente tipado, las matrices pueden contener **múltiples tipos de datos diferentes** en la misma matriz.

```js
const mixto = [42, 'hola', true, null];
```

---

## Bucles `for` con arrays

La mayoría de las veces, los bucles `for` se utilizan para iterar sobre todos los elementos de una matriz usando `.length` como punto de parada.

```js
const nombresEstudiantes = ['Martin', 'Antonio', 'Sara', 'Samuel'];

for (let i = 0; i < nombresEstudiantes.length; i++) {
    console.log(nombresEstudiantes[i]);
}
// 'Martin'
// 'Antonio'
// 'Sara'
// 'Samuel'
```

---

## Métodos adicionales de arrays

### `.indexOf(elemento)`
Devuelve el índice de la primera aparición del elemento. Retorna `-1` si no existe.

```js
const frutas = ['manzana', 'banana', 'naranja'];
console.log(frutas.indexOf('banana')); // 1
console.log(frutas.indexOf('uva'));    // -1
```

---

### `.includes(elemento)`
Retorna `true` si el elemento existe en la matriz, `false` en caso contrario.

```js
console.log(frutas.includes('naranja')); // true
console.log(frutas.includes('uva'));     // false
```

---

### `.splice(inicio, cantidad)`
Elimina o reemplaza elementos en una posición específica. **Modifica** la matriz original.

```js
const numeros = [1, 2, 3, 4, 5];
numeros.splice(1, 2); // Elimina 2 elementos desde el índice 1
console.log(numeros); // [1, 4, 5]
```

---

### `.slice(inicio, fin)`
Devuelve una **copia** de una porción de la matriz sin modificar la original.

```js
const numeros = [1, 2, 3, 4, 5];
const porcion = numeros.slice(1, 4);
console.log(porcion); // [2, 3, 4]
console.log(numeros); // [1, 2, 3, 4, 5]  (sin cambios)
```

---

### `.reverse()`
Invierte el orden de los elementos de la matriz. **Modifica** la matriz original.

```js
const letras = ['a', 'b', 'c'];
letras.reverse();
console.log(letras); // ['c', 'b', 'a']
```

---

### `.join(separador)`
Une todos los elementos de la matriz en una cadena de texto.

```js
const palabras = ['Hola', 'mundo', 'JavaScript'];
console.log(palabras.join(' '));  // 'Hola mundo JavaScript'
console.log(palabras.join('-')); // 'Hola-mundo-JavaScript'
```

---

### `.concat(otraMatriz)`
Une dos o más matrices y devuelve una nueva sin modificar las originales.

```js
const a = [1, 2, 3];
const b = [4, 5, 6];
const c = a.concat(b);
console.log(c); // [1, 2, 3, 4, 5, 6]
```

---

### `.forEach(funcion)`
Ejecuta una función por cada elemento de la matriz. Alternativa moderna al bucle `for`.

```js
const nombresEstudiantes = ['Martin', 'Antonio', 'Sara'];
nombresEstudiantes.forEach(function(nombre) {
    console.log(nombre);
});
// 'Martin'
// 'Antonio'
// 'Sara'
```

---

### `.map(funcion)`
Crea una **nueva** matriz con los resultados de aplicar una función a cada elemento.

```js
const numeros = [1, 2, 3, 4];
const dobles = numeros.map(function(n) {
    return n * 2;
});
console.log(dobles); // [2, 4, 6, 8]
```

---

### `.filter(funcion)`
Crea una **nueva** matriz con los elementos que cumplan una condición.

```js
const numeros = [1, 2, 3, 4, 5, 6];
const pares = numeros.filter(function(n) {
    return n % 2 === 0;
});
console.log(pares); // [2, 4, 6]
```

---

### Resumen de métodos

| Método         | Descripción                                      | Modifica original |
|----------------|--------------------------------------------------|:-----------------:|
| `.push()`      | Agrega al final                                  | ✅                |
| `.pop()`       | Elimina del final                                | ✅                |
| `.unshift()`   | Agrega al inicio                                 | ✅                |
| `.shift()`     | Elimina del inicio                               | ✅                |
| `.splice()`    | Elimina/reemplaza en posición específica         | ✅                |
| `.reverse()`   | Invierte la matriz                               | ✅                |
| `.slice()`     | Copia una porción                                | ❌                |
| `.concat()`    | Une matrices                                     | ❌                |
| `.indexOf()`   | Busca el índice de un elemento                   | ❌                |
| `.includes()`  | Verifica si un elemento existe                   | ❌                |
| `.join()`      | Une elementos en un string                       | ❌                |
| `.forEach()`   | Itera ejecutando una función                     | ❌                |
| `.map()`       | Transforma elementos en nueva matriz             | ❌                |
| `.filter()`    | Filtra elementos en nueva matriz                 | ❌                |
