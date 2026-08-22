# Guía 04: Ciclos (Estructuras Repetitivas)

Los ciclos nos permiten repetir un bloque de instrucciones múltiples veces sin tener que escribir el código una y otra vez. En esta guía traduciremos las dos estructuras principales: el ciclo `Mientras` y el ciclo `Para`.

## 1. El ciclo "Mientras" (`while`)
En PSeInt utilizábamos `Mientras <condicion> Hacer` y finalizábamos con `Fin Mientras`. En Java, utilizamos la palabra `while` seguida de la condición entre paréntesis `( )` y las llaves `{ }` para englobar lo que se va a repetir.

### Ejemplo: Sumar N números
Este algoritmo pide la cantidad de números a sumar y utiliza un acumulador y un contador dentro de un ciclo `Mientras`.

```java
import java.util.Scanner;

public class SumarNumeros {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.println("Ingrese la cantidad de números a sumar:");
        int cantidad = sc.nextInt();
        
        int contador = 1;
        int suma = 0; // Este es nuestro acumulador
        
        // Ciclo While (Mientras)
        while (contador <= cantidad) {
            System.out.println("Ingrese el número a sumar:");
            int num = sc.nextInt();
            
            suma = suma + num;
            contador = contador + 1; // En Java también puedes escribir contador++;
        }
        
        System.out.println("La suma total es: " + suma);
        sc.close();
    }
}
```

## 2. El ciclo "Para" (for)
En PSeInt declarábamos el inicio, el fin y el incremento en palabras: Para i<-2 Hasta cantidad Con Paso 1 Hacer.

En Java, el ciclo for condensa estas tres cosas en una sola línea dentro de sus paréntesis, separadas por punto y coma:
`for (inicio; limite; incremento)`.  

Ejemplo: Encontrar el Número MenorEste programa pregunta cuántos números se evaluarán, pide el primer número antes del ciclo, y luego utiliza un ciclo Para empezando desde 2 para comparar el resto de los ingresos con un condicional interno.  Javaimport java.util.Scanner;

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