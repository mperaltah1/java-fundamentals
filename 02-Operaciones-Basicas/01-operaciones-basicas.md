# Operaciones Aritméticas

Este programa pide dos valores reales para ejecutar cálculos.

**Algoritmo original en PSeInt:**
Calculaba las cuatro operaciones básicas de la siguiente manera: `suma = num1 + num2;`, `resta = num1 - num2;`, `division = num1 / num2;` y `multiplicacion = num1 * num2;`. Luego imprimía con `Escribir "Los resultados son:";`.

Crearemos unnuevo paquete en nuestro proyecto llamado `operaciones`. 

Crear una nueva clase llamada `Operaciones`.

**Traducción a Java:**

```java
import java.util.Scanner;

public class Operaciones {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        bzvch';'
        ;.mnl;lkkmjjjl.m,lgnhjtluouooujkkkmkl;kh;
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