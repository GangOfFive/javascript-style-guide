**Tabla de Contenidos**

- [Estándar de JavaScript para Gang of Five](#est%C3%A1ndar-de-javascript-para-gang-of-five)
	- [Nombres](#nombres)
	- [var](#var)
	- [Objetos](#objetos)
	- [Arreglos](#arreglos)
	- [Strings](#strings)
	- [Funciones](#funciones)
	- [Propiedades](#propiedades)
	- [Modificar prototipos de objetos del lenguaje](#modificar-prototipos-de-objetos-del-lenguaje)
	- [Expresiones condicionales y comparaciones](#expresiones-condicionales-y-comparaciones)
	- [Formato del código](#formato-del-c%C3%B3digo)
		- [Inicializar objetos y arreglos](#inicializar-objetos-y-arreglos)
		- [Argumentos de funciones](#argumentos-de-funciones)
		- [Bloques](#bloques)
		- [Espacios](#espacios)
		- [Comas](#comas)
		- [Punto y coma](#punto-y-coma)
		- [Comentarios](#comentarios)
			- [Tipos y Tags](#tipos-y-tags)

# Estándar de JavaScript para *Gang of Five*

Basado en los estándares de [Google](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
y [Airbnb](https://github.com/airbnb/javascript/).

## Nombres
 - Los archivos de JavaScript se deberán nombrar de la siguiente manera:
   - `elephant.js`
   - `favorite-movies.js`
 - Ser descriptivo con los nombres.

    ~~~javascript
    // No recomendado
    function q() {
        // ...stuff...
    }

    // Recomendado
    function query() {
        // ..stuff..
    }
    ~~~

 - Utilizar `camelCase` para nombrar objetos, funciones, e instancias.

    ~~~javascript
    // No recomendado
    var OBJEcttsssss = {};
    var this_is_my_object = {};
    function c() {};
    var u = new user({
        name: 'Bob Parr'
    });

    // Recomendado
    var thisIsMyObject = {};
    function thisIsMyFunction() {};
    var user = new User({
        name: 'Bob Parr'
    });
    ~~~

 - Utilizar `PascalCase` para nombrar constructores y clases.

    ~~~javascript
    // No recomendado
    function user(options) {
        this.name = options.name;
    }

    var No recomendado = new user({
        name: 'nope'
    });

    // Recomendado
    function User(options) {
        this.name = options.name;
    }

    var Recomendado = new User({
        name: 'yup'
    });
    ~~~

 - Anteponer un guión bajo cuando se desean nombrar propiedades privadas.

    ~~~javascript
    // No recomendado
    this.__firstName__ = 'Panda';
    this.firstName_ = 'Panda';

    // Recomendado
    this._firstName = 'Panda';
    ~~~

 - Utilizar el siguiente formato para las constantes: `EARTH_GRAVITY`.
 - Anteponer `$` a las variables que sean objetos de *jQuery*.

    ~~~javascript
    // No recomendado
    var sidebar = $('.sidebar');

    // Recomendado
    var $sidebar = $('.sidebar');
    ~~~

## var
 - Siempre utilizar `var` al declarar variables.

    ~~~javascript
    // No recomendado
    pet = 'dog';

    // Recomendado
    var pet = 'dog';
    ~~~

 - Utilizar solo un `bar` para declarar múltiples variables, una en cada línea.

    ~~~javascript
    // No recomendado
    var items = getItems();
    var pet = 'dog';
    var special = false;

    // Recomendado
    var items = getItems(),
        pet = 'dog',
        special = false;
    ~~~

 - Declarar las variables a las que no se le asignará un valor immediatamente de últimas.

    ~~~javascript
    // No recomendado
    var i, length, special,
        items = getItems(),
        pet = 'dog';

    // No recomendado
    var i, items = getItems(),
        special,
        pet = 'dog',
        length;

    // Recomendado
    var items = getItems(),
        pet = 'dog',
        special,
        length,
        i;
    ~~~

## Objetos
 - Utilizar el siguiente sintaxis para declarar objetos:

    ~~~javascript
    // No recomendado
    var item = new Object();

    // Recomendado
    var item = {};
    ~~~

## Arreglos
 - Utilizar el siguiente sintaxis para declarar arreglos:

    ~~~javascript
    // No recomendado
    var items = new Array();

    // Recomendado
    var items = [];
    ~~~

 - Siempre utilizar ciclos `for` cuando se utilizan arreglos, no utilizar ciclos `for-in`.

    ~~~javascript
    // No recomendado
    var i;
    for (i in arr) {
        console.log(arr[i]);
    }
    // Recomendado
    var i,
        l = arr.length;

    for (i = 0; i < l; i++) {
        console.log(arr[i]);
    }
    ~~~

## Strings
 - Utilizar comillas sencillas para los strings.

    ~~~javascript
    // Recomendado
    var color = 'red';

    // No recomendado
    var color = "red";
    ~~~

- Si un string mide más de 80 caracteres, se debe escribir en múltiples líneas, utilizando
  concatenación.

## Funciones
 - Expresiones de funciones

    ~~~javascript
    // anonymous function expression
    var anonymous = function() {
        return true;
    };

    // named function expression
    var named = function named() {
        return true;
    };

    // immediately-invoked function expression (IIFE)
    (function() {
        console.log('Hello');
    })();
    ~~~

 - Nunca declarar una función en un bloque no sea una función (`if`, `while`, etc).
   En vez, asignar una función a una variable.

    ~~~javascript
    // No recomendado
    if (currentUser) {
        function test() {
            console.log('No');
        }
    }

    // Recomendado
    var test;
    if (currentUser) {
        test = function test() {
            console.log('Yes');
        };
    }
    ~~~

 - Las funciones anidades pueden ser muy útiles. Utilizarlas cuando tenga sentido hacerlo.

 - Nunca nombrar un parámetro `arguments`, ya que éste tomará precedencia sobre
   el objeto `arguments` que se coloca en el contexto de cada función.

    ~~~javascript
    // No recomendado
    function nope(name, options, arguments) {
        // ...stuff...
    }

    // Recomendado
    function yup(name, options, args) {
        // ...stuff...
    }
    ~~~

## Propiedades
 - Utilizar la notación de `.` para acceder a propiedades de un objeto.

    ~~~javascript
    // No recomendado
    console.log(user['name']);
    // Recomendado
    console.log(user.name);
    ~~~

 - Utilizar la notación de `[]` cuando se utiliza una variable para acceder a
   una propiedad de un objeto.

    ~~~javascript
    var attr = 'name';
    console.log(user[attr]);
    ~~~

## Modificar prototipos de objetos del lenguaje
 - Evitar modificar prototipos como `Object.prototype` y `Array.prototype`.

## Expresiones condicionales y comparaciones
 - Utilizar `===` y `!==` en vez de `==` y `!=`.
 - Utilizar atajos:

    ~~~javascript
    // No recomendado
    if (name !== '') {
        // ...stuff...
    }

    // Recomendado
    if (name) {
        // ...stuff...
    }

    // No recomendado
    if (collection.length > 0) {
        // ...stuff...
    }

    // Recomendado
    if (collection.length) {
        // ...stuff...
    }
    ~~~

## Formato del código
 - Longitud máxima de líneas: `80`. Si no es posible utilizar menos de 80 carácteres, intentar
   al menos utilizar menos de `120`.

### Inicializar objetos y arreglos
 - Se permite colocarlos en la misma línea si no son muy largos.

    ~~~javascript
    // No space after [ or before ].
    var arr = [1, 2, 3];
    // No space after { or before }.
    var obj = {a: 1, b: 2, c: 3};
    ~~~

### Argumentos de funciones
 - Siempre que sea posible, los argumentos de una función se deberán listar en la misma
   línea. Si se excede el límte de 80 caracteres, los argumentos se deberán formatear
   de tal manera que sean legibles. Los siguientes ejemplos son aceptables:

    ~~~javascript
    // Four-space, wrap at 80.  Works with very long function names, survives
    // renaming without reindenting, low on space.
    var doThingThatIsVeryDifficultToExplain = function(
        veryDescriptiveArgumentNumberOne,
        veryDescriptiveArgumentTwo,
        tableModelEventHandlerProxy,
        artichokeDescriptorAdapterIterator) {
      // ...
    };
    // Parenthesis-aligned, one argument per line.  Emphasizes each
    // individual argument.
    function bar(veryDescriptiveArgumentNumberOne,
                 veryDescriptiveArgumentTwo,
                 tableModelEventHandlerProxy,
                 artichokeDescriptorAdapterIterator) {
      // ...
    }
    ~~~

### Bloques
 - Siempre utilizar corchetes para los bloques de una sola línea:

    ~~~javascript
    // No recomendado
    if (test)
        return false;

    // No recomendado
    if (test) return false;

    // Recomendado
    if (test) {
        return false;
    }

    // No recomendado
    function() { return false; }

    // Recomendado
    function() {
        return false;
    }
    ~~~

### Espacios
 - Indentar con `4` espacios.

    ~~~javascript
    // No recomendado
    function() {
    ∙∙var name;
    }

    // No recomendado
    function() {
    ∙var name;
    }

    // Recomendado
    function() {
    ∙∙∙∙var name;
    }
    ~~~

 - Colocar un espacio antes del primer corchete:

    ~~~javascript
    // No recomendado
    function test(){
        console.log('test');
    }

    // Recomendado
    function test() {
        console.log('test');
    }

    // No recomendado
    dog.set('attr',{
        age: '1 year',
        breed: 'Schnauzer'
    });

    // Recomendado
    dog.set('attr', {
        age: '1 year',
        breed: 'Schnauzer'
    });
    ~~~

 - Separar los operadores con un espacio:

    ~~~javascript
    // No recomendado
    var x=y+5;

    // Recomendado
    var x = y + 5;
    ~~~

 - Colocar una línea vacía al final del archivo.

### Comas
 - No colocar las comas antes cuando se listan variables.
    ~~~javascript
    // No recomendado
    var one
      , two
      , three;

    // Recomendado
    var one,
        two,
        three;
    ~~~

 - Coma adicional al final: **No**.

    ~~~javascript
    // No recomendado
    var names = [
        'Jeff',
        'Sam',
        'Fred',
    ];

    // Recomendado
    var names = [
        'Jeff',
        'Sam',
        'Fred'
    ];
    ~~~

### Punto y coma
  - **Si**. Evitar omitir puntos y comas.

    ~~~javascript
    // No recomendado
    (function() {
        var name = 'Skywalker'
        return name
    })()

    // Recomendado
    (function() {
        var name = 'Skywalker';
        return name;
    })();
    ~~~

### Comentarios
 - Utilizar `/** ... */` para comentarios multilínea. Incluir una descripción, especificar
   tipos y valores para los parámetros y lo que se retorne.

    ~~~javascript
    // No recomendado
    // make() returns a new element
    // based on the passed in tag name
    //
    // @param {string} tag
    // @return {Element} element
    function make(tag) {
        // ...stuff...
        return element;
    }

    // Recomendado
    /**
     * make() returns a new element
     * based on the passed in tag name
     *
     * @param {string} tag
     * @return {Element} element
     */
    function make(tag) {
        // ...stuff...
        return element;
    }
    ~~~

 - Utilizar `//` para comentarios de una línea.
   Colocar el comentario en una línea sobre el código que se describe.
   Colocar una línea vacía antes del comentario.

    ~~~javascript
    // No recomendado
    var active = true;  // is current tab

    // Recomendado
    // is current tab
    var active = true;

    // No recomendado
    function getType() {
        console.log('fetching type...');
        // set the default type to 'no type'
        var type = this._type || 'no type';

        return type;
    }

    // Recomendado
    function getType() {
        console.log('fetching type...');

        // set the default type to 'no type'
        var type = this._type || 'no type';

        return type;
    }
    ~~~

 - Colocar `FIXME` o `TODO` antes de los comentarios para indicar si hay un problema
   que se necesita solucionar o una solución que aún se debe implementar.
   - `FIXME -- need to figure this out`
   - `TODO -- need to implement`

#### Tipos y Tags
 - Solo es necesario utilizar comentarios JSDoc para funciones y constructores.

 - Para los tipos y tags, referirse a:
   - [JSDoc Tag Reference](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml#JSDoc_Tag_Reference)
   - [JavaScript Types](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml#JsTypes)

 - Se utilizarán los siguientes tags:
   - `@const`
   - `@constructor`
   - `@enum`
   - `@param`
   - `@return`
