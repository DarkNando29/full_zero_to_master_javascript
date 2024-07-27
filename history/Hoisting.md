- Hoisting en JavaScript es un comportamiento del lenguaje donde las declaraciones de variables y funciones son "elevadas" (hoisted) al inicio de su contexto de ejecucion, ya sea una funcion o el contexto global. Sin embargo, solo las declaraciones son hoisted, no las inicializaciones. Este comportamiento puede llevar a resultados inesperados si no se comprende bien.

- Detalles del hoisting
    - Variables declaradas con `var`
        - Las variables declaradas con `var` son hoisted al inicio de su contexto de ejecucion, pero su inicializacion no lo es. Esto significa que la declaracion de la variable se procesa antes de que se ejecute cualquier otro codigo, pero el valor asignado a la variable no sse procesa hasta que la linea de codigo correspondiente se ejecuta.

        ```
            console.log(x); // undefined
            var x = 5;
            console.log(x); // 5
        ```

        - En este ejemplo, el comportamiento se debe a que la declaracion `var x` se eleva al inicio, pero la asignacion `x = 5` permanece en su lugar original. Es equivalente a:

        ```
            var x;
            console.log(x); // undefined
            x = 5;
            console.log(x); // 5
        ```

    - Variables declaradas con `let` y `const`
        - Las variables declaradas con `let` y `const` tambien son hoisted, pero con una diferencia crucial: no pueden ser accedidas antes de su declaracion en el codigo. Esto se conoce como la "Temporal Dead Zone"(TDZ).

        ```
            console.log(x); // ReferenceError: Cannot access 'y' 
            // before initialization
            let y = 10;
            console.log(y); // 10
        ```

        En este caso, aunque la declaracion `let y` es hoisted, el acceso a la variable `y` antes de su inicializacion genera un error.

        - Funciones declaradas:
            - Las declaraciones de funciones tambien son hoisted completamente, es decir, tanto la declaracion como la definicion de la funcion se elevan al inicio del contexto de ejecucion.

            ```
                miFuncion(); // "Hola desde miFuncion"
                funcion miFuncion() {
                    console.log("Hola desde miFuncion");
                }
            ```

            Este comportamiente permite llamar a la funcion antes de su declaracion en el codigo.

        - Ejemplo combinado:
            ```
                console.log(a); // undefined
                var a = 1;

                try {
                    console.log(b); // ReferenceError
                    let b = 2;
                } catch (e) {
                    console.error(e);
                }

                miFuncion(); // "Hola desde miFuncion"
                function miFunction() {
                    console.log("Hola desde miFuncion");
                }

                try {
                    otraFuncion(); // TypeError: otraFuncion is not a // function
                    var otraFuncion = function() {
                        console.log("Hola desde otraFuncion");
                    };
                } catch (e) {
                    console.error(e);
                }
            ```


- Resumen de Hoisting
    - `var`: declaracion hoisted, inicializacion no. Variables accesibles antes de la inicializacion con valor `undefined`.
    -  `let` y `const`: Declaracion hoisted, inicializacion no. Variables no accesibles antes de la inicializacion (TDZ).
    - Funciones declaradas: Declaracion y definicion completamente hoisted. Funciones accesibles antes de la declaracion.
    - Funciones expresadas: Solo la declracion `var` es hoisted, no la asignacion de la funcion.

- Mejores practicas:
    1- Declarar variables al inicio de su contexto: Esto puede ayudar a evitar confusiones relacionadas con el hoisting.
    2- Usar `let` y `const`: Prefiere `let` y `const` sobre `var` para reducir errores relacionados con el hoisting y mejorar la claridad del codigo.
    3- Declarar funciones antes de su uso: Aunque las funciones son hoisted, declararlas antes de usarlas mejora la legibilidad y la comprension del codigo.

- Comprender el hoisting es crucial para escribir codigo javaScript mas predecible y libre de errores.