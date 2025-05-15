## Actividad 3

Seleccionar un lenguaje esotérico, y realizar la gramática, BNF, EBNF y ABNF del mismo

### Lenguaje seleccionado: Brainfuck

#### Características del lenguaje

* Minimalista: Solo tiene 8 instrucciones.
* Usa un arreglo unidimensional de celdas con un puntero que se puede mover a izquierda o derecha.
* No tiene palabras clave, variables ni estructuras de alto nivel.
* Cada instrucción es un solo carácter.
* Condición de bucle: El bucle ([ y ]) se ejecuta mientras el valor de la celda apuntada no sea cero. Este comportamiento
 permite crear ciclos en el programa.

El lenguaje se basa en un modelo de ejecución simple que consiste, además del programa, de un vector de (al menos)
30000 bytes inicializados a cero, un puntero sobre ese vector (que al comienzo de la ejecución apunta al primer
elemento del mismo) y dos «corrientes» de bytes para la entrada y la salida.

#### Instrucciones

| Carácter | Significado                                                                          | Equivalencia en C    |
|----------|--------------------------------------------------------------------------------------|----------------------|
| `>`      | Incrementa el puntero.                                                               | `++ptr;`             |
| `<`      | Decrementa el puntero.                                                               | `--ptr;`             |
| `+`      | Incrementa el byte apuntado.                                                         | `++*ptr;`            |
| `-`      | Decrementa el byte apuntado.                                                         | `--*ptr;`            |
| `.`      | Escribe el byte apuntado en el flujo<br>de salida.                                   | `putchar(*ptr);`     |
| `,`      | Lee un byte del flujo de entrada<br>y lo almacena en el byte apuntado.               | `*ptr = getchar();`  |
| `[`      | Avanza a la instrucción posterior al `]`<br>si el byte apuntado es 0.                | `while (*ptr) {`     |
| `]`      | Retrocede a la instrucción posterior al `[`<br>si el byte apuntado no es 0.          | `}`                  |


#### GIC (Gramática independiente del contexto)

```
programa -> instrucción> | programa instrucción

instrucción -> ">" | "<" | "+" | "-" | "." | "," | ciclo

ciclo -> "[" programa "]"
```

### Producciones

```
P -> PI | I | ε
I ->  > | < | + | - | . | , | C
C -> [ P ]
```

#### BNF (Backus Naur Form)

```
<programa> ::= ε | <instrucción> | <programa> <instrucción>

<instrucción> ::= ">" | "<" | "+" | "-" | "." | "," | <ciclo>

<ciclo> ::= "[" <programa> "]"
```


#### EBNF (Extended BNF)

```
<programa>: { <instrucción> }*

<instrucción> ::= ">" | "<" | "+" | "-" | "." | "," | <ciclo>

<ciclo> ::= "[" programa "]"
```

#### ABNF (Augmented BNF)

```
programa: { instrucción _op}

instrucción: uno de ">" "<" "+"  "-" "."  ","  ciclo

ciclo: "[" programa "]"

```