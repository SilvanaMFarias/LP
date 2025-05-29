## Actividad 5

### Semántica

### Binding de Parámetros

Es la asociación entre los parámetros formales (los que se declaran en la definición de una función o procedimiento) y los parámetros reales (los que se pasan al invocar dicha función o procedimiento).

| Binding |  | Descripión | Estático | Dinámico | Ejemplo dinámico |
| --- | --- | --- | --- | --- | --- |
| **De valor** | El patrón de bits almacenado en la celda asociada a la variable  | Se pasa una copia del valor del parámetro real al parámetro formal. Los cambios en el parámetro formal no afectan al real | C, C++, Pascal, Java, Kotlin  | Python, JavaScript, PHP, Lua, Ruby  | Ej Javascript <br> function saludar({nombre, edad}) <br> {console.log(`Hola ${nombre}, tienes ${edad} años`);} <br><br> saludar({edad: 25, nombre: "Ana"}); |
| **De tipo**  | El conjunto de valores posibles que puede adquirir la variable  |  las operaciones que se pueden aplicar sobre ella.  | Pascal, C, C++, Java, Kotlin, Go  | Python, PHP, JavaScript, Perl, Ruby, LISP  | v = "Hola" #v es de tipo str <br> v = 123 # ahora v es de tipo int <br> v = [1, 2, 3]   # ahora v es una lista  |
| **De alcance** | Cuáles instrucciones pueden usar una variable | Es la asociación entre una variable (como un parámetro o una variable local) y la región del código (ámbito o scope) donde dicha variable es válida y accesible. | Java, Python, JavaScript (modo normal), C, C++ | Algunos modos en LISP, Perl antiguo, Shell scripts | Ejemplo LISP <br> (setq x 10) <br> (defun imprimir-x () <br> (print x)) <br><br> (defun cambiar-x () <br> (let ((x 20))    ;; en dynamic scoping, esta x se usa por imprimir-x <br> (imprimir-x))) <br> (cambiar-x) ;Imprime 20 si el lenguaje usa binding de alcance dinámico |
| **De almacenamiento** | Almacenamiento: el lugar de memoria donde está la variable | |  | |
| **De nombre**         | Identificador que utiliza el programador para referirse a la celda de memoria de la variable: longitud, casesensitive, caracteres | |  | |
| **De tiempo de vida** | Tiempo en el que la variable tiene lugar en memoria y puede ser accedida | |  | |