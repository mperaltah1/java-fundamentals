# Manipulación de Cadenas

## El Problema: Detector de Palíndromos
Un palíndromo es una palabra o frase que se lee exactamente igual de izquierda a derecha que de derecha a izquierda (ejemplo: "reconocer"). 
El reto es construir un algoritmo que reciba una palabra ingresada por el usuario, la invierta carácter por carácter utilizando un ciclo, y determine lógicamente si es un palíndromo.

## Herramientas de Java (Clase String)
Para resolver este problema, utilizaremos herramientas nativas de Java para manipular texto:
* `length()`: Devuelve la cantidad total de caracteres de la cadena.
* `charAt(indice)`: Extrae un carácter en una posición específica. En programación, siempre empezamos a contar desde la posición 0.
* `equalsIgnoreCase(texto)`: Evalúa si dos textos son idénticos ignorando si están en mayúsculas o minúsculas.

---

## Solución Paso a Paso

```java
import java.util.Scanner;

public class DetectorPalindromo {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);
        
        System.out.println("Ingrese una palabra para evaluar:");
        String palabra = teclado.nextLine();
        
        String palabraInvertida = "";
        
        // Algoritmo de inversión (Ciclo For inverso)
        // Empezamos en la última letra y retrocedemos hasta la posición 0
        for (int i = palabra.length() - 1; i >= 0; i--) {
            palabraInvertida = palabraInvertida + palabra.charAt(i);
        }
        
        System.out.println("Palabra original: " + palabra);
        System.out.println("Palabra invertida: " + palabraInvertida);
        
        // Condicional lógico
        if (palabra.equalsIgnoreCase(palabraInvertida)) {
            System.out.println("¡El algoritmo detectó un palíndromo!");
        } else {
            System.out.println("La palabra no es un palíndromo.");
        }
        
        teclado.close();
    }
}