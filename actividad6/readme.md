## Actividad 6

### Definición de un lenguaje de programación

Definir un lenguaje de programación en lenguaje natural. Tiene que poder manejar expresiones, iteración y selección (condicional).

### Lenguaje de programación: Rizado

Rizado es un lenguaje de programación diseñado para describir la rutina de peinado de una persona con ondas o rulos después del lavado del mismo.
Permite manejar expresiones, selección e iteración.

### Tipos de datos

El lenguaje maneja dos tipos de datos:

tipoPelo: describe el tipo de cabello.
Valores posibles: ondulado, enrulado.

numero: representa cantidades enteras entre 0 y 9, usadas para especificar la cantidad de repeticiones de la acción hacerScrunch.


### Variables obligatorias

El programa trabaja con exactamente 2 variables de nombre y tipo fijos:

Nombres

tipoP: representa el tipo del cabello (tipo tipoPelo).
vecesScrunch: representa la cantidad de veces que se realiza la acción de scrunch (tipo numero).

La forma de declarar las variables es la siguiente:

nombreVariable ":" tipoDeDato;

Ejemplo:
tipoP ":" tipoPelo;       (tipo de dato nuevo)
vecesScrunch ":" entero;  (tipo de dato nativo)

La forma asignar valor a las variables es la siguiente:

tipoP "=" ondulado;
vecesScrunch "=" 5;

Cada una de las líneas de declaración o asignación de las variables finalizan con un ";"
Primero se realiza la declaración de la variables, y luego se les asigna valor.

### Estructura del programa

Un programa tiene una estructura de la forma:

```
INICIO
<declaraciones>
<asignaciones>
<bloques opcionales>
FIN
```
donde INICIO y FIN son palabras reservadas que indican el comienzo y fin del programa.


Antes de que el programa comience a ejecutar cualquier bloque de código, las dos variables obligatorias (tipoP, vecesScrunch) deben estar declaradas, y tienen que tener asignadas un valor válido.
Puede no ejecutarse ningun bloque luego, y no dará error.

De continuar, el programa puede hacer dos cosas:

* Usar un condicional, que compara por igualdad o desigualdad contra el valor de la variable tipoP (ondulado, enrulado), y establecer una rutina de cuidado para cada uno. 
* Ejecutar una rutina sin realizar ninguna verificación.

La rutina de cuidado, tiene 3 pasos principales se ejecutan en orden:

1. Aplicar producto

* Crema para peinar
* Crema para peinar y gel
* No aplicar ningún producto.

El no aplicar ningún producto implica que este paso se omite.


2. Definir

* Peinar
* Hacer scrunch un número determinado de veces (definido por la variable vecesScrunch) (Acá se usaría la iteración)
* Peinar y hacer scrunch un número determinado de veces (definido por la variable vecesScrunch)
* No realizar ninguna definición.

El no realizar ningún producto implica que este paso se omite.


3. Secar

* Plopping
* Secador de pelo
* Plopping y secador de pelo
* No secar (se seca el pelo al natural)

El no realizar secado implica que este paso se omite.


### Posible BNF

```

<programa> ::= "INICIO" <declaraciones> <asignaciones> <bloquesOpcionales> "FIN"

<declaraciones> ::= <declaracionTipoP>";" <declaracionVecesScrunch>";"
<declaracionTipoP> ::= "tipoP" ":" "tipoPelo"
<declaracionVecesScrunch> ::= "vecesScrunch" ":" entero

<asignaciones> ::= <asignacionTipoP> <asignacionVecesScrunch>
<asignacionTipop> ::= "tipoP" "=" <valorTipoPelo>
<asignacion_vecesScrunch> ::= "vecesScrunch" "=" <numero>

<valorTipoPelo> ::= "ondulado" | "enrulado"
<numero> ::= "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

<bloquesOpcionales> ::= <bloqueCondicional> | <rutina> | ε

<bloqueCondicional> ::= "SI" <condicion_tipo> "ENTONCES" "{" <rutina> "}" <sinoOpcional> "FINSI" ";"
<sinoOpcional> ::= "SINO" "{" <rutina> "}" | ε
<condicionTipo> ::= "(" "tipoP" <operador> <valorTipoPelo> ")"
<operador> ::= "==" | "<>"

<rutina> ::= <bloqueAplicar> <bloqueDefinir> <bloqueSecar>

<bloqueAplicar> ::= <aplicarProducto> | ε
<bloqueDefinir> ::= <definir> | ε
<bloqueSecar> ::= <secar> | ε

<aplicarProducto> ::= <listaProductos> ";"

<listaProductos> ::= "cremaParaPeinar"  | "gel"| "cremaParaPeinar" ";" "gel" 

<definir> ::= "peinar" ";" | <bloqueIteracionScrunch> | "peinar" ";" <bloqueIteracionScrunch> ";"
<bloqueIteracionScrunch> ::= "REPETIR" "vecesScrunch" "VECES" <accionScrunch> "FINREPETIR" ";"
<accionScrunch> ::= "scrunch"

<secar> ::= "plopping" ";" | "secadorDePelo" ";" | "plopping" ";" "secadorDePelo" ";"

```

```
Ejemplo programa:

INICIO
tipoP : tipoPelo;
vecesScrunch : entero;
tipoP = ondulado;
vecesScrunch = 5;
SI ( tipoP == ondulado) ENTONCES 
{
cremaParaPeinar; 
REPETIR vecesScrunch VECES scrunch FINREPETIR;
}
SINO {
cremaParaPeinar;
gel;
secadorDePelo;
}
FINSI;
FIN
```

Otro ejemplo:

```
INICIO
tipoP : tipoPelo;
vecesScrunch : entero;
tipoP = ondulado;
vecesScrunch = 2;
cremaParaPeinar;
gel;
plopping;
secadorDePelo;
FIN

```
