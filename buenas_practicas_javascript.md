#Buenas prácticas javascript:

##Debuging
- Usar `console.time` para medir tiempos entre procesos
```
console.time('Inicialización de arreglo');
var arreglo = [];
for(var i=0; i<10000; i++) {
    arreglo[i] = i;
}
console.timeEnd('Inicialización de arreglo');
```

##Variables y Objetos

### Generales
- No usar **nunca** variable globales ni palabras reservadas como nombres de variables

### Iteraciones
- Evitar usar un `for` clásico para iterar sobre un array muy grande ya que la condición se repetirá N veces. En su lugar usar `for..each` o `for..in`
```
var arreglo = [10, 15, 2, 9, 23, 16];
// La conidción i<arreglo.length se ejecuta 6 veces innecesariamente,
// se podría haber usado un for..each
for(var i=0; i<arreglo.length, i++) {
    console.log(arreglo[i]);
}
```


###Condiciones
- Cuidado con abusar con las condiciones implícitas. Cada tipo de dato tiene su propia regla de validación implícita. Por ejemplo
```
var estado="";
if (estado) {
    // Este código nunca se va a ejecutar porque un string vació 
    // devuvle FALSE en una validación implícita
}
```
- La diferencia entre el operador `==` y `===` es que el segundo valida valor **y ademas el tipo de dato**.
```
var resultado = (1 == 2 - 1);   // TRUE
var resultado = (1 == "1");     // TRUE
var resultado = (1 === "1");    // FALSE por ser tipos distintos
```

###Objetos
- Una funcion con variables y funciones closures dentro **no es un objeto**. Recién será un objeto cuando se lo asigne a una variable a través del operador `ǹew`.
```
var Persona = function() {
    var nombre, edad;
};
console.log(typeof Persona);        // function

var Jose = new Persona();
console.log(typeof Jose);           // object
```
```
var animal = { raza: 'perro' };
console.log(typeof animal);         // object
```
- Evitar la instanciación de objetos a través del operador `new` siempre que se pueda. El operador `new` es mucho mas lento que la asignación de un objeto json `{}` o un array `[]`.
```
// Formas incorrectas
var Persona = function() { var nombre };
var persona = new Persona();

var arreglo = new Array();
```
```
// Formas correctas
var persona = { nombre: 'Rodrigo' };
var arreglo = [];
```

###Try Catch
- No tiene sentido poner un `try catch` **inmediatamente** dentro de un bucle. El `try catch` consume un scope propio por cada iteración y ésto genera importante problema de performance. En su lugar se debe poner el `try catch` por fuera del bucle.
```
// Forma incorrecta: try catch dentro de for
for (var i = 0; i < totalAnimales; i++) {
    try {
        ..
    } catch (e) {
    }
}
```
```
// Forma correcta: for dentro de try catch
try {
    for (var i = 0; i < totalAnimales; i++) {
            ..
    }
} catch (e) {
}
```


##Estilos
- Las constantes deberíasn declararse en mayúsculas y snake case.
```
var PI = 3.141592;
var LIMITE_MAX = 10;
```


