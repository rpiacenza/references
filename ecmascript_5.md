#Ecmascript 5
*(by RMP)*

###Especificaciones
    - Ecma International http://www.ecma-international.org/ecma-262/7.0/index.html#prod-Module
    - w3schools http://www.w3schools.com/jsref/default.asp

###Closures
Es una función anónima que se ejecuta dentro de otra función.
Caracterísicas:
    - Se almacena en un espacio privado sin afectar el scope global. 
    - Tiene acceso a las variables de la función padre.
    - Dicho acceso es por referencia (no por valor) por lo que es útil para modificar variables del padre desde la función hija
```
function hola_mundo(nombre) {
    function construct() {
        return "Hola " + nombre;
    }
    return construct();
}
```

```
(function() {
    // Código con scope propio
})();
```

###Getters and Setters
Permite encapsular variables de scope private dentro de un objeto.
```
var curso = {
    _tutor : 'Uriel',
    get tutor() {
        return this._tutor.toUpperCase();
    },
    set tutor(value) {
        this._tutor = value;
    }
};

curso.tutor = 'Jose';
console.log(curso.tutor);
```

###Array.filter
El metodo **filter()** crea un nuevo arreglo con todos los elementos que pasen la prueba implementada por la función dada.
```
var numeros = [10, 23, 7, 13, 20, 5, 25, 11, 1, 14];
numero_pares = numeros.filter(function (value, index) {
	return value % 2 === 0;
});
console.log(numero_pares);
```

###Array.map
El método **map()** crea un nuevo array con los resultados de la llamada a la función indicada aplicados a cada uno de sus elementos.
```
var numeros = [10, 23, 7, 13, 20, 5, 25, 11, 1, 14];
cuadrados = numeros.map(function (value) {
    return value * value;
});
console.log(cuadrados);
```

###Array.forEach
Itera una variable especifica por todos los valores de las propiedades del objeto. Para cada propiedad distinta, una sentencia especifica es ejecutada.
Forma es5
```
var numeros = [10, 23, 7, 13, 20, 5, 25, 11, 1, 14];
numeros.forEach(function(value, index) {
    console.log(value, index)
});
```

Forma for..each..in
```
var sum = 0;
var obj = {prop1: 5, prop2: 13, prop3: 8};
for each (var item in obj) {
  sum += item;
}
print(sum); // imprime "26", que es 5+13+8
```


###Array.reduce
El método **reduce()** aplica una función a un acumulador y a cada valor de un array (de izquierda a derecha) para reducirlo a un único valor.
```
var letras = ['H', 'o', 'l', 'a']
var palabras = letras.reduce(function(valor_anterior_retornado, valor_actual, index, arreglo){
    return valor_anterior_retornado + valor_actual;
});
console.log(palabras);
```


###Iterar sobre propiedades de un objeto
```
var persona = {
    nombre: "Rodrigo",
    email: "rpiacenza@gmail.com",
    saludar: function () {
        return "Hola !";
    }
}

for(var campo in persona) {
    console.log(campo, persona[campo]);
}
```