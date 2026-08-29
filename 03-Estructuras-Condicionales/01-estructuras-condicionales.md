# Estructuras Condicionales (Toma de Decisiones)

En esta guía aprenderemos a implementar lógica condicional en Java. Las estructuras de decisión nos permiten evaluar si una condición se cumple (es verdadera) y ejecutar un bloque de código específico en respuesta.

## El equivalente a "Si-Entonces" (La estructura if-else)
En PSeInt utilizábamos las palabras reservadas `Si`, `Entonces`, `SiNo` y `FinSi`. En Java, utilizamos `if` (si) y `else` (sino), y delimitamos los bloques de código utilizando llaves `{ }` en lugar de la palabra `FinSi`.

### Traducción de Operadores Relacionales
* Mayor o igual que: `>=`
* Menor o igual que: `<=`
* Igual a: `==` (Nota: en Java se usa doble signo de igual para comparar, ya que un solo `=` sirve para asignar valores).
* Diferente de: `!=`

---

## Ejemplo Práctico: Verificar Nota

**Algoritmo original en PSeInt:**
El algoritmo solicitaba una nota, evaluaba la condición `Si nota >= 61 Entonces`, y mostraba "Aprobo" o "Reprobo" dependiendo del resultado.

crear un nuevo paquete llamado `condicionales`.

Crear una clase llamada Saludar.

**Traducción a Java:**
Debemos recordar importar la clase `Scanner` para poder leer el teclado y usar la estructura clásica de la clase y el método `main`.

```java
import java.util.Scanner;

public class VerificarNota {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.println("Escriba la nota del alumno:");
        // En Java declaramos e inicializamos en la misma línea
        int nota = sc.nextInt(); 
        
        // Estructura Condicional
        if (nota >= 61) {
            System.out.println("Aprobo");
        } else {
            System.out.println("Reprobo");
        }
        
        sc.close();
    }
}
```
---

## El equivalente a "Segun" (La estructura switch)

En PSeInt utilizábamos la estructura `Segun` para evaluar múltiples opciones exactas de una misma variable, utilizando `De Otro Modo` para atrapar las opciones no declaradas. En Java, esta estructura se llama `switch`.

**Regla de oro:** En Java, cada caso (`case`) debe terminar obligatoriamente con la palabra reservada `break;`. Esto le indica a la computadora que ya ejecutó esa opción y debe salir de la estructura. El equivalente a "De Otro Modo" es la palabra `default`.

## Ejemplo Práctico: Días de la Semana

**Algoritmo original en PSeInt:**
El algoritmo solicitaba un número de día y, según el valor, imprimía el día correspondiente del "Lunes" a "Domingo". Si el número no estaba entre 1 y 7, indicaba que el día no era válido.

**Traducción a Java:**

```java
import java.util.Scanner;

public class DiasSemana {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.println("Escriba el numero de dia:");
        int dia = sc.nextInt();
        
        // Estructura de Condición Múltiple
        switch (dia) {
            case 1: 
                System.out.println("Lunes");
                break;
            case 2: 
                System.out.println("Martes");
                break;
            case 3: 
                System.out.println("Miercoles");
                break;
            case 4: 
                System.out.println("Jueves");
                break;
            case 5: 
                System.out.println("Viernes");
                break;
            case 6: 
                System.out.println("Sabado");
                break;
            case 7: 
                System.out.println("Domingo");
                break;
            default: 
                System.out.println("Día de la semana no válido");
                break;
        }
        
        sc.close();
    }
}

```