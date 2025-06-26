## Actividad 6

### Definición de un lenguaje de programación

Definir un lenguaje de programación en lenguaje natural. Tiene que poder manejar expresiones, iteración y selección (condicional).

### Lenguaje de programación: Rizado

Rizado es un lenguaje de programación diseñado para describir la rutina de peinado de una persona con ondas o rulos a partir del lavado del mismo.
Permite manejar expresiones, selección e iteración.
Un programa tiene una estructura de la forma:

```
INICIO
<Declaración>
<Asignación>
<Bloques Opcionales>
FIN
```

Tipos de datos

tipoPelo: describe el tipo de cabello.
Valores posibles: ondulado, enrulado.

entero: representa cantidades enteras entre 0 y 9, usadas para especificar la cantidad de repeticiones de la acción hacer Scrunch.


### Variables obligatorias

El programa trabaja con exactamente 2 variables fijas, cuyos nombres y tipos son:

tipo: representa el tipo del cabello (tipo tipoPelo).
vecesScrunch: representa la cantidad de veces que se realiza la acción de scrunch (tipo entero valor mayor o igual a cero).


### Estructura del programa

Antes de que el programa comience a ejecutar cualquier bloque de código, las dos variables obligatorias (estado, vecesScrunch) deben estar asignadas con un valor válido.
Puede no ejecutarse ninguna sentencia luego, y no dará error.


De continuar, el programa puede hacer dos cosas:

* Usar un condicional, según el tipo de pelo, para establecer una rutina de cuidado para cada uno.
* Ejecutar una rutina.

La rutina de cuidado, tiene 3 pasos principales se ejecutan en orden:

1. Aplicar producto

* Crema para peinar
* Crema para peinar y gel
* No aplicar ningún producto.

El no aplicar ningún producto implica que este paso se omite.


2. Definición

* Peinar
* Hacer scrunch un número determinado de veces (definido por la variable vecesScrunch) (Acá se usaría la iteración)
* Peinar y hacer scrunch un número determinado de veces (definido por la variable vecesScrunch)
* No realizar ninguna definición.

El no realizar ningún producto implica que este paso se omite.


3. Secado

* Plopping
* Secador de pelo
* Plopping y secador de pelo
* No secar (se seca el pelo al natural)

El no realizar secado implica que este paso se omite.


### Posible BNF

```ebnf

<programa> ::= "INICIO" <declaraciones> <asignaciones> <bloques_opcionales> "FIN"

<declaraciones> ::= <declaracion_tipo_pelo> <declaracion_vecesScrunch>
<declaracion_tipo_pelo> ::= "tipo" ":" "tipoPelo"
<declaracion_vecesScrunch> ::= "vecesScrunch" ":" "entero"

<asignaciones> ::= <asignacion_tipo> <asignacion_vecesScrunch>
<asignacion_tipo> ::= "tipo" "=" <tipo_valor>
<asignacion_vecesScrunch> ::= "vecesScrunch" "=" <digito>

<tipo_valor> ::= "ondulado" | "enrulado"
<digito> ::= "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

<bloques_opcionales> ::= <bloque_condicional> | <rutina> | ε

<bloque_condicional> ::= "SI" <condicion_tipo> "ENTONCES" <rutina> <sino_opcional> "FIN_SI"
<sino_opcional> ::= "SINO" <rutina> | ε
<condicion_tipo> ::= "tipo" "==" <tipo_valor>

<bloque_iteracion_scrunch> ::= "REPETIR" "vecesScrunch" "VECES" <accion_scrunch> "FIN_REPETIR"
<accion_scrunch> ::= "scrunch"

<rutina> ::= <bloque_aplicar> <bloque_definir> <bloque_secar>

<bloque_aplicar> ::= <aplicar_producto> | ε
<bloque_definir> ::= <definir> | ε
<bloque_secar> ::= <secar> | ε

<aplicar_producto> ::= "aplicar" <lista_productos>

<lista_productos> ::= "crema_para_peinar" | "gel" | "crema_para_peinar" "gel"

<definir> ::= "peinar" | <bloque_iteracion_scrunch> | "peinar" <bloque_iteracion_scrunch>

<secar> ::= "plopping | "secador_de_pelo" | "plopping" "secador_de_pelo"

```