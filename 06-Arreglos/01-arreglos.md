# Introducción a los Arreglos (Arrays)

Hasta ahora hemos guardado un solo dato dentro de una variable. Un **arreglo** nos permite guardar múltiples datos del mismo tipo en una sola estructura, como si fuera un archivero con gavetas numeradas. En programación, **siempre empezamos a contar desde la gaveta 0**.

## Arreglos Unidimensionales

En Java es una estructura que permite almacenar un conjunto de datos de un mismo tipo.

### Para números enteros
``` java
int[ ] edad = {45, 23, 11, 9}; //Array de 4 elementos
```
De la misma forma procederemos para los otros de enteros : `byte`, `short`, `long`.

### Para números reales
``` java
//Array de 3 elementos
double[ ] estatura = {1.73, 1.67, 1.56};
```

De la misma forma prodecemos para el tipo float, pero teniendo en cuenta que los números deberán llevar al final la letra “f” o “F”. Por ejemplo `1.73f` o `1.73F`.

### Para cadenas
``` java
//Array de 2 elementos
String[ ] nombre = {"María", "Gerson"};
```

### Para caracterers
``` java
char[ ] sexo = {'m', 'f'}; //Array de 2 elementos
```

### Para booleanos
``` java
boolean[ ] = {true,false}; //Array de 2 elementos
```

## Ejemplo 1
Crear un programa que pida un listado de 5 nombres de personas, los almacene en un arreglo de texto (`String`) y, una vez finalizado el ingreso, muestre la lista completa en la pantalla pero en el orden inverso.

### Instrucciones Paso a Paso:

**Paso 1: Preparar el entorno y la memoria**
Crear un nuevo paquete llamado `arreglos`. dentro de este paquete crear una nueva clase llamada `ArreglosEnJava` y el método `main`. 

Importar la clase `Scanner` para poder leer el teclado. 

Se debe crear un arreglo "vacío" pero reservando el espacio exacto para 5 elementos.
*   *Pista:* `String[] nombres = new String[5];`

**Paso 2: Llenar el arreglo**
Crear un ciclo `for` clásico que empiece en `0` y termine antes de llegar al tamaño del arreglo (`i < nombres.length`). 
*   *Pista:* En cada iteración, imprime "Ingrese el nombre de la persona:" y guarda el texto capturado en la posición actual del arreglo usando `nombres[i] = teclado.nextLine();` o `.next()`.

**Paso 3: Imprimir en orden inverso**
Crear un segundo ciclo `for` para leer e imprimir los datos, pero debe recorrer el arreglo de atrás hacia adelante.
*   *Pistas:* 
    *   El ciclo debe empezar en la última posición válida. Si el tamaño es 10, la última posición es `9`. (`int i = nombres.length - 1;`)
    *   Repetir hasta que el índice sea mayor o igual a la primera posición (`i >= 0;`).
    *   En lugar de sumar, debe ir restando de uno en uno (`i--`).

**Paso 4: Resultados**
Dentro del ciclo inverso, simplemente se debe imprimir en consola el valor actual del arreglo (`System.out.println(nombres[i]);`). 

**Paso 5: Verificación**
Compilar y ejecutar la clase. Click derecho sobre la clase -> Run File. 
Ingresar 5 nombres y verificar que el orden haya sido invertido.

<!-- Solucion

//Ejemplo 1
    Scanner sc = new Scanner(System.in);
    System.out.println("Ingrese 5 nombres de personas");
    String[] nombres = new String[5];
    for (int i = 0; i < 5; i++) {
        System.out.println("Ingrese el nombre " + i);
        nombres[i] = sc.nextLine();
    }

    System.out.println("Imprimiendo en orden inverso");
    for (int i = nombres.length - 1; i >= 0; i--) {
        System.out.println(nombres[i]);
    }

-->

## Ejercicio 1
Crear un array numérico con 5 elementos. Los números de cada elemento deben ser valores pedidos por teclado al usuario.

Luego mostrar por consola el índice y el valor al que corresponde y seguido de esto realizar la multiplicación con el siguiente número. El último valor se multiplicará con el primero.

Ejemplo de salida esperada
```
Indice      valor       Resultado
0           10          200
1           20          600
2           30          1200
3           40          2000
4           50          500
```

**Requisitos:**
Utilizar ciclos tanto para pedir los valores de los elementos del array como para mostrar su contenido por pantalla

<!-- Solucion
    Scanner sc = new Scanner(System.in);
    
    int numeros[] = new int[5]; //arreglo numerico con 5 elementos
    System.out.println("Ingrese 5 numeros");
    for (int i = 0; i < numeros.length; i++) {
        System.out.println("Ingrese el valor " + i);
        numeros[i] = sc.nextInt();
    }
    
    System.out.println("Indice \t Valor \t Resultado");
    for (int i = 0; i < numeros.length; i++) {
        int resultado;
        if(i == numeros.length -1){
            resultado = numeros[i] * numeros[0];
        }
        else {
            resultado = numeros[i] * numeros[i+1];
        }
        System.out.println(i + " \t " + numeros[i]+ " \t " + resultado);
    }
-->

## Ejemplo 2
Pedir al usuario una lista de números reales. Luego de ingresados los valores, calcular la suma, el promedio y la multiplicación de todos los números.

<!-- Solucion
    Scanner sc = new Scanner(System.in);
    System.out.println("Ingrese la cantidad de numeros que desea ingresar");
    int cantidad = sc.nextInt();
    
    double numeros[] = new double[cantidad];
    for (int i = 0; i < cantidad; i++) {
        System.out.println("Ingrese el numero " + i);
        numeros[i] = sc.nextDouble();
    }
    
    double suma = 0;
    double multi = 1;
    for (int i = 0; i < numeros.length; i++) {
        suma = suma + numeros[i];
        multi = multi * numeros[i];
    }
    
    double promedio = suma / cantidad;
    
    System.out.println("La suma es: " + suma);
    System.out.println("La multiplicacion es: " + multi);
    System.out.println("La promedio es: " + promedio);
-->

## Ejercicio 2
Realizar un programa Java que pida 10 números enteros y los guarde en un array. 
Luego calcula y muestra por separado el promedio de los valores positivos y el promedio de los valores negativos.

<!-- Solucion
    
-->

## Ejemplo 3: Registro de Calificaciones

Desarrollar un programa que solicite al usuario ingresar 10 notas de estudiantes, las almacene en un arreglo, las muestre en pantalla y luego calcule el promedio general de la clase.

### Instrucciones Paso a Paso:

**Paso 1: Preparación del entorno**
Crear la clase, el método `main` y preparar el objeto `Scanner` para leer el teclado.

**Paso 2: Declaración de variables**
Declarar un arreglo de tipo entero (`int[]`) que pueda almacenar exactamente 10 posiciones. 

Declarar también una variable de tipo `double` inicializada en 0 para ir guardando la suma total de las notas.

**Paso 3: Llenar el arreglo (Ingreso de datos)**
Crear un ciclo `for` que comience en `i = 0` y termine cuando `i < arreglo.length()`. 
*   *Pista:* Dentro de este ciclo, pedir al usuario `"Ingrese la nota del estudiante:"` y guardar lo que escriba directamente en la posición actual del arreglo (`arreglo[i] = teclado.nextInt();`).

**Paso 4: Recorrer el arreglo**
Crear un segundo ciclo `for` idéntico al anterior. Recorrer al arreglo.
*   *Pista:* En cada vuelta del ciclo, imprime el valor de la nota actual. Además, suma ese valor a la variable acumuladora (`suma = suma + arreglo[i];`).

**Paso 5: Resultados finales**
Fuera de los ciclos, calcular el promedio dividiendo la suma total entre la cantidad de notas (usar el metodo `length` del arreglo). Imprimir el promedio final en la consola.

## Ejercicio 3
Crear un formulario como el de la imagen. En donde el usuario escriba una palabra presione el botón “evaluar” y el programa le muestre si la palabra es un palíndromo o no.

_Palíndromo: Palabra o expresión que es igual si se lee de izquierda a derecha que de derecha a izquierda_

<!-- Solucion
    String palabra = txtPalabra.getText();
    char[] letras = palabra.toCharArray();
    String invertida = "";
    int i = 0;
    for (int j = letras.length - 1; j >= 0; j--) {
        if(letras[i] == letras[j])
        invertida += letras[i];
    }
    
    if(invertida.equalsIgnoreCase(palabra)) {
        lblResultado.setText("Es un palindromo");
    } else {
        lblResultado.setText("No es un palindromo");
    }
-->

<!-- Solucion v2
    String palabra = txtPalabra.getText();
    char[] letras = palabra.toCharArray();
    boolean iguales = true;
    int i = 0;
    for (int j = letras.length - 1; j >= 0; j--) {
        if(letras[i] != letras[j]){
            iguales = false;
            break;
        }
        i++;
    }
    
    if(iguales) {
        lblResultado.setText("Es un palindromo");
    } else {
        lblResultado.setText("No es un palindromo");
    }
-->