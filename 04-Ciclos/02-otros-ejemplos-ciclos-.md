# Más ejemplos de Ciclos

Esta serie de ejercicios prácticos contiene algoritmos repetitivos, aprendiendo a controlar el flujo de ejecución mediante contadores, acumuladores y menús interactivos.

---

## 1. Sumar N números
Este algoritmo pide la cantidad de números a sumar y utiliza un acumulador y un contador dentro de un ciclo `Mientras`.

Dentro del mismo paquete de `ciclos`, crear una clase llamada `SumarNumeros`.

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

## 2. Calcular Media

Este programa se ejecuta indefinidamente hasta que el usuario ingresa un valor bandera (cero o negativo). Además, concatena texto en cada iteración.

Dentro del mismo paquete, crear una clase llamada `CalcularMedia`.

```java
import java.util.Scanner;

public class CalcularMedia {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);
        
        String numerosIngresados = "";
        double suma = 0;
        int contador = 0;
        double num = 1;
        
        System.out.println("Programa que calcula la media de una serie de numeros positivos");
        
        while (num > 0) {
            contador = contador + 1;
            System.out.println("Ingrese el numero " + contador + " de la serie.");
            System.out.println("Un valor menor o igual a cero indica la terminacion del programa");
            num = teclado.nextDouble();
            
            if (num != 0) {
                if (numerosIngresados.equals("")) {
                    numerosIngresados = String.valueOf(num);
                } else {
                    numerosIngresados = numerosIngresados + ", " + num;
                }
                suma = suma + num;
            }
        }
        
        System.out.println("Lista de numeros ingresados: " + numerosIngresados);
        // Evitar división por cero si el primer ingreso fue 0
        if (contador > 1) { 
            double promedio = suma / (contador - 1);
            System.out.println("El promedio de los numeros es: " + promedio);
        }
        teclado.close();
    }
}

```

---

## 4. Menús Interactivos (`while` + `switch`)

Los menús son la base de las aplicaciones de consola. Aquí tenemos dos enfoques distintos para mantener el menú vivo.

### Opción A: Salida por opción numérica (Menú de Áreas)

El ciclo se mantiene vivo siempre que la opción ingresada sea distinta (`!=`) a la opción de salida (4).

Dentro del mismo paquete, crear una clase llamada `CalcularAreas`.

```java
import java.util.Scanner;

public class CalcularAreas {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);
        int op = 0;
        double base, altura, radio, area;
        
        // PSeInt: Mientras op <> 4 Hacer
        while (op != 4) {
            System.out.println("\n--- Menu ---");
            System.out.println("1. Triangulo");
            System.out.println("2. Circulo");
            System.out.println("3. Rectangulo");
            System.out.println("4. Salir");
            op = teclado.nextInt();
            
            switch (op) {
                case 1:
                    System.out.println("Ingrese la base:");
                    base = teclado.nextDouble();
                    System.out.println("Ingrese la altura:");
                    altura = teclado.nextDouble();
                    area = (base * altura) / 2;
                    System.out.println("El area del triangulo es: " + area);
                    break;
                case 2:
                    System.out.println("Ingrese el radio:");
                    radio = teclado.nextDouble();
                    // Utilizamos la constante nativa Math.PI
                    area = Math.PI * radio * radio; 
                    System.out.println("El area del circulo es: " + area);
                    break;
                case 3:
                    System.out.println("Ingrese la base:");
                    base = teclado.nextDouble();
                    System.out.println("Ingrese la altura:");
                    altura = teclado.nextDouble();
                    area = base * altura;
                    System.out.println("El area del rectangulo es: " + area);
                    break;
                case 4:
                    System.out.println("Saliendo del sistema...");
                    break;
                default:
                    System.out.println("Opcion invalida");
                    break;
            }
        }
        teclado.close();
    }
}

```

### Opción B: Salida por confirmación de texto (Calculadora)

Evalúa una variable de tipo `String` para continuar. En Java, no usamos el operador `=` para comparar textos, utilizamos el método `.equalsIgnoreCase()`.

Dentro del mismo paquete, crear una clase llamada `OperacionesMenu`.

```java
import java.util.Scanner;

public class OperacionesMenu {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);
        double num1, num2, suma, resta, multi, div;
        int op;
        String continuar = "S";
        
        // PSeInt: Mientras Mayusculas(continuar) = "S" Hacer
        while (continuar.equalsIgnoreCase("S")) {
            System.out.println("\n¿Que operacion desea calcular?");
            System.out.println("1. Suma");
            System.out.println("2. Resta");
            System.out.println("3. Multiplicacion");
            System.out.println("4. Division");
            op = teclado.nextInt();
            
            System.out.println("Ingrese el primer operando:");
            num1 = teclado.nextDouble();
            System.out.println("Ingrese el segundo operando:");
            num2 = teclado.nextDouble();
            
            switch (op) {
                case 1:
                    suma = num1 + num2;
                    System.out.println("La suma es: " + suma);
                    break;
                case 2:
                    resta = num1 - num2;
                    System.out.println("La resta es: " + resta);
                    break;
                case 3:
                    multi = num1 * num2;
                    System.out.println("La multiplicacion es: " + multi);
                    break;
                case 4:
                    div = num1 / num2;
                    System.out.println("La division es: " + div);
                    break;
                default:
                    System.out.println("Opcion no valida");
                    break;
            }
            
            System.out.println("\n¿Desea continuar? S/N");
            // Limpiamos el buffer del teclado antes de leer un String
            teclado.nextLine(); 
            continuar = teclado.nextLine();
        }
        teclado.close();
    }
}

```