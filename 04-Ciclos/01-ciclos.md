# Guía 04: Ciclos (Estructuras Repetitivas)

Los ciclos nos permiten repetir un bloque de instrucciones múltiples veces sin tener que escribir el código una y otra vez. En esta guía traduciremos las dos estructuras principales: el ciclo `Mientras` y el ciclo `Para`.

## 1. Ciclo `while` Básico: Tabla de Multiplicar
Este algoritmo genera la tabla de un número utilizando un contador simple.

Crear un nuevo paquete que se llame ciclos y que contenga una clase llamada `ImprimirTabla`.

```java
import java.util.Scanner;

public class ImprimirTabla {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);
        
        System.out.println("Escriba el numero para la tabla de multiplicar:");
        int num = teclado.nextInt();
        
        int i = 1;
        while (i <= 10) {
            System.out.println(num + " x " + i + " = " + (i * num));
            i = i + 1;
        }
        teclado.close();
    }
}
```

---
## 2. El ciclo "Para" (for)
En PSeInt declarábamos el inicio, el fin y el incremento en palabras: Para i<-2 Hasta cantidad Con Paso 1 Hacer.

En Java, el ciclo for condensa estas tres cosas en una sola línea dentro de sus paréntesis, separadas por punto y coma:
`for (inicio; limite; incremento)`.  

Ejemplo: Encontrar el Número MenorEste programa pregunta cuántos números se evaluarán, pide el primer número antes del ciclo, y luego utiliza un ciclo Para empezando desde 2 para comparar el resto de los ingresos con un condicional interno.  Javaimport java.util.Scanner;

Crear una nueva clase dentro del paquete llamada `NumeroMenor`.

```java
public class NumeroMenor {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);
        
        System.out.println("Programa que muestra el número menor de N números");
        System.out.println("¿Cuántos números quiere evaluar?");
        int cantidad = teclado.nextInt();
        
        System.out.println("Ingrese el primer número:");
        int numMenor = teclado.nextInt();
        
        // Ciclo For (Para i=2 hasta cantidad, incrementando de 1 en 1)
        for (int i = 2; i <= cantidad; i++) {
            System.out.println("Ingrese un número:");
            int nuevo = teclado.nextInt();
            
            // Condicional interno
            if (nuevo < numMenor) {
                numMenor = nuevo;
            }
        }
        
        System.out.println("El número menor es: " + numMenor);
        teclado.close();
    }
}
```

---

## 3. El equivalente a `Repetir...Hasta Que`: Calcular Factorial

En PSeInt, la estructura evalúa la condición al final para *detenerse* (`Hasta Que contador > numFactorial`). En Java, utilizamos `do-while`, pero la lógica se invierte: el ciclo se repite *mientras* la condición sea verdadera.

Crear una nueva clase dentro del paquete llamada `CalcularFactorial`.

```java
import java.util.Scanner;

public class CalcularFactorial {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);
        
        int contador = 1;
        int factorial = 1;
        
        System.out.println("Escriba un numero del cual desea obtener el factorial:");
        int numFactorial = teclado.nextInt();
        
        // PSeInt: Repetir ... Hasta Que
        do {
            factorial = factorial * contador;
            contador = contador + 1;
        } while (contador <= numFactorial); // En Java, repetimos MIENTRAS sea menor o igual
        
        System.out.println("El factorial de " + numFactorial + " es: " + factorial);
        teclado.close();
    }
}

```

---

