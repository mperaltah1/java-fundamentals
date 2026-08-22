# Operaciones Básicas (Transición de PSeInt a Java)

En esta guía aprenderemos a traducir nuestros primeros algoritmos secuenciales a **Java**. En **PSeInt** utilizábamos comandos en español muy amigables, pero en Java debemos respetar una estructura estricta y usar herramientas específicas para comunicarnos con la consola.

## Paso 1: La Estructura Obligatoria
En PSeInt, todo nuestro código vivía entre las palabras `Algoritmo` y `FinAlgoritmo`. En Java, todo debe vivir dentro de una **Clase** y un método principal llamado **Main**.

```java
public class MiPrimerPrograma {
    public static void main(String[] args) {
        // Aquí adentro va todo nuestro código
    }
}

```

## Paso 2: El equivalente a "Leer" en Pseint es la clase Scanner en Java

En PSeInt, obtener un dato del usuario era tan fácil como escribir `Leer mensaje;`. Java no sabe escuchar el teclado por defecto. Para hacerlo, debemos "importar" una herramienta llamada `Scanner`.

1. Hasta arriba del archivo debemos poner: `import java.util.Scanner;`
2. Dentro del `main`, debemos configurar o llamar al escáner así:
`Scanner sc = new Scanner(System.in);`

## Paso 3: Traducir los Tipos de Datos (Definir)

En PSeInt declarábamos las variables con la palabra reservada `Definir`. En Java, el tipo de dato va primero y no se usa la palabra "definir":

* `Definir nombre Como Caracter;` en Java es `String nombre;`


* `Definir num1, num2 Como Real;` en Java es `double num1, num2;`


* `Definir nota Como Entero;` en Java es `int nota;`



---

## Ejemplos Prácticos

### 1. Saludar al usuario

Aquí combinamos la lógica de pedir un texto al usuario y concatenarlo.

**Algoritmo original en PSeInt:**
Solía pedir el nombre con `Escribir "Por favor ingrese su nombre";` y luego mostrar un saludo con `Escribir "Bienvenido al sistema ", nombre;`.

**Traducción a Java:**

```java
import java.util.Scanner;

public class Saludar {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // 1. Definir la variable (String en lugar de Caracter)
        String nombre;
        
        // 2. Escribir en pantalla
        System.out.println("Por favor ingrese su nombre");
        
        // 3. Leer el texto desde el teclado
        nombre = sc.nextLine();
        
        // 4. Imprimir concatenando con el símbolo +
        System.out.println("Bienvenido al sistema " + nombre);
        
        sc.close(); // Siempre es buena práctica apagar el escáner
    }
}

```

### 2. Operaciones Aritméticas

Este programa pide dos valores reales para ejecutar cálculos.

**Algoritmo original en PSeInt:**
Calculaba las cuatro operaciones básicas de la siguiente manera: `suma = num1 + num2;`, `resta = num1 - num2;`, `division = num1 / num2;` y `multiplicacion = num1 * num2;`. Luego imprimía con `Escribir "Los resultados son:";`.

**Traducción a Java:**

```java
import java.util.Scanner;

public class Operaciones {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Definir num1, num2 Como Real
        double num1, num2;
        // Definir variables de resultados
        double suma, resta, division, multiplicacion;
        
        System.out.println("Ingrese el primer valor:");
        num1 = sc.nextDouble(); // Leemos un número decimal (Real)
        
        System.out.println("Ingrese el segundo valor:");
        num2 = sc.nextDouble(); 
        
        // Operaciones matemáticas
        suma = num1 + num2;
        resta = num1 - num2;
        division = num1 / num2;
        multiplicacion = num1 * num2;
        
        System.out.println("Los resultados son:");
        System.out.println("La suma de los numeros es: " + suma);
        System.out.println("La resta de los numeros es: " + resta);
        System.out.println("La division de los numeros es: " + division);
        System.out.println("La multiplicacion de los numeros es: " + multiplicacion);
        
        sc.close();
    }
}

```