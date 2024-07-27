- La declaracion de variables en JavaScript es un aspecto fundamental del lenguaje que ha evolucionado significativamente a lo largo de los anos. Existen tres palabras clave principales para declarar variables: `var`,  `let` y `const`. Cada una de ellas tiene caracteristicas y comportamientos diferentes. Aqui te detallo como funcionan:

- `var`

    - Caracteristicas:
        - Alcance: Las variables declaradas con `var` tienen un alcance de funcion o global, dependiendo de donde se declaren.
        - Hoisting: Las declaraciones de variables con `var` se elevan(hoisted) al inicio de su contexto de ejecucion, pero su inicializacion no.
        - Re-declaracion: Puedes declarar la misma variable con `var` multiples veces en el mismo ambito sin que cause un error.

    ```
        function ejemploVar() {
            console.log(x);
            var x = 5;
            console.log(x);
        }

        ejemploVar();
    ```

- `let`
    - Caracteristicas:
        - Alcance: Las variables declaradas con `let` tienen un alcance de bloque. Esto significa que estan limitadas al bloque en el que se declaran.
        - Hoisting: las declaraciones con `let` tambien se elevan, pero no pueden ser accedidas antes de su inicializacion(Temporal Dead Zone).
        - Re-declaracion: No puedes declarar la misma variable con `let` dentro del mismo ambito.

        ```
            function ejemploLet() {
                let y = 10;
                console.log(y);
            }

            ejemploLet();
        ```

- `const`
    - Caracteristicas:
        - Alcance: Similar a `let`, las variables declaradas con `const` tienen un alcance de bloque.
        - Hoisting: Las declaraciones con `const` tambien se elevan, pero no pueden ser accedidas antes de su inicializacion(Temporal Dead Zone).
        - Re-declaracion y Re-asignacion: No puedes re-declarar ni re-asignar una variable declarada con `const`. Debe ser inicializada en el momento de su declaracion.
        - Inmutabilidad: Aunque `const` impide la re-asignacion, los objetos y arrays declarados con `const` pueden ser mutados.

        ```
            function ejemploConst() {
                const z = 20;
                console.log(z);

                // z = 30; // TypeError: Assignment to constant 
                // variable.

                const obj = { nombre: 'Juan'};
                obj.nombre = 'Pedro';
                console.log(obj.nombre);
            }

            ejemploConst();
        ```


| Caracteristica | var               | let      | const       |   |
|----------------|-------------------|----------|-------------|---|
| Alcance        | Function o global | Bloque   | Bloque      |   |
| Hoisting       | Si                | Si(TDZ)  | Si(TDZ)     |   |
| Re-declaracion | Si                | No       | No          |   |
| Re-asignacion  | Si                | Si       | No          |   |
| Inicializacion | Opcional          | Opcional | Obligatorio |   |


```
    function ejemploComparacion() {
        // var
        var a = 1;
        if (true) {
            var a = 2;
            console.log(a);
        }
        console.log(a);

        // let
        let b = 1;
        if (true) {
            let b=-
        }
    }
```