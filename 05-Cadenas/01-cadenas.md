# Manejo de Cadenas (La Clase `String`)

En Java, una cadena es una secuencia de caracteres (como nombres, datos, lugares, o prácticamente cualquier texto). Son una parte fundamental de la mayoría de los programas. 

A diferencia de los tipos primitivos (como `int` o `double`), Java utiliza una clase especial para el manejo de texto: la clase `String`.

Dado que `String` es una clase, nos provee de múltiples **métodos** nativos que nos ayudan a manipular la información: calcular su tamaño, unir cadenas, extraer fragmentos o comparar datos.

---

## 1. Propiedades Básicas y Extracción
En este primer bloque probaremos cómo medir una cadena, cómo extraer letras específicas y cómo unir (concatenar) textos.

*   `length()`: Devuelve el tamaño de la cadena en un número entero.
*   `charAt(int index)`: Retorna el carácter (`char`) en la posición indicada. Dado que internamente es un arreglo, la primera posición siempre es la `0`.
*   `isEmpty()`: Devuelve verdadero (`true`) si y sólo si el tamaño de la cadena es 0.
*   `concat(String s)`: Retorna un `String` resultante de la unión de 2 cadenas, agregando el parámetro al final de la cadena original.

### Ejercicio Práctico 1
Crea un archivo llamado `Cadenas.java` y copia el siguiente código:

```java
public class Cadenas {
    public static void main(String[] args) {
        // Inicialización básica
        String umg = "UMG";
        String carrera = "Ingenieria en sistemas";
        String cadenaVacia = "";
        
        // Uso de length()
        System.out.println(umg + " tiene " + umg.length() + " caracteres");
        System.out.println(carrera + " tiene " + carrera.length() + " caracteres");
        
        // Uso de charAt()
        String nombre = "Pepito";
        char letra = nombre.charAt(0);
        System.out.println("La primera letra de Pepito es: " + letra);
        
        // Uso de isEmpty()
        System.out.println("¿La cadena está vacía?: " + cadenaVacia.isEmpty());
        
        // Uso de concat()
        String cadena1 = "Algo";
        String cadena2 = "ritmos";
        String union = cadena1.concat(cadena2);
        System.out.println("Palabra concatenada: " + union);
    }
}

```

---

## 2. Comparación y Búsqueda

Java nos permite buscar coincidencias dentro de un texto o comparar si dos contraseñas o nombres son idénticos.

* `equals(String c)` y `equalsIgnoreCase(String c)`: Compara si una cadena es igual a otra. La versión `IgnoreCase` ignora mayúsculas y minúsculas.


* `compareTo()`: Compara dos cadenas lexicográficamente. (Devuelve 0 si son iguales).


* `contains(CharSequence cadena)`: Devuelve verdadero o falso si y sólo si la cadena contiene la secuencia enviada en el parámetro.


* `indexOf(int ch)`: Devuelve el índice (en número entero) de la primera ocurrencia del carácter especificado. Si no lo encuentra, devuelve `-1`.


* `startsWith(String prefix)`: Devuelve verdadero o falso si la primera secuencia de la cadena corresponde al valor especificado.



### Ejercicio Práctico 2

Crea un archivo llamado `ComparacionCadena.java` y copia el siguiente código:

```java
public class ComparacionCadena {
    public static void main(String[] args) {
        String cadena1 = "UMG";
        String cadena2 = "UMG";
        
        // Uso de equals()
        System.out.println("¿cadena1 es igual a cadena2?: " + cadena1.equals(cadena2));
        
        // Uso de compareToIgnoreCase()
        String c = "UMG";
        int resultado = c.compareToIgnoreCase("umg");
        if (resultado == 0) {
            System.out.println("Son iguales");
        } else {
            System.out.println("No son iguales");
        }
        
        // Uso de contains()
        String parrafo = "Una secuencia de caracteres es una secuencia legible de valores de caracteres";
        System.out.println("¿Contiene 'ecue'?: " + parrafo.contains("ecue"));
        
        // Uso de indexOf()
        String saludo = "Hola mundo";
        System.out.println("Índice de 'a': " + saludo.indexOf('a'));
        System.out.println("Índice de 'e' (no existe): " + saludo.indexOf('e'));
        
        // Uso de startsWith()
        String hello = "HelloWorld";
        if (hello.startsWith("Hello")) {
            System.out.println("Empieza con la secuencia");
        } else {
            System.out.println("NO empieza con la secuencia");
        }
    }
}

```

---

## 3. Transformaciones y Arreglos

Por último, aprenderemos a modificar cadenas (sin alterar la original) y a dividirlas en fragmentos.

* `substring(int beginIndex)`: Sustrae y devuelve el valor de una cadena comenzando desde el índice especificado.


* `toUpperCase()` y `toLowerCase()`: Convierten los caracteres de la cadena a mayúsculas o minúsculas respectivamente.


* `trim()`: Elimina los espacios en blanco iniciales y finales de una cadena.


* `split(String regex)`: Divide la cadena en un arreglo (array) de cadenas dependiendo del delimitador especificado.


* `toCharArray()`: Convierte todo el texto en un arreglo de caracteres individuales.


* `join()`: Devuelve una nueva cadena compuesta por copias de los elementos unidos por un delimitador.



### Ejercicio Práctico 3

Crea un archivo llamado `TransformacionCadena.java` y copia el siguiente código:

```java
public class TransformacionCadena {
    public static void main(String[] args) {
        // Uso de substring()
        String cadena = "HelloWorld";
        System.out.println("Sustracción desde índice 5: " + cadena.substring(5));
        
        // Uso de trim()
        String mensaje = "   Hello World   ";
        System.out.println("Sin espacios a los lados: '" + mensaje.trim() + "'");
        
        // Uso de join()
        String unido = String.join("-", "Ingenieria", "es", "cool");
        System.out.println("Textos unidos por guiones: " + unido);
        
        // Uso de split() - Separar por comas
        System.out.println("\n--- Lista de Nombres (Split) ---");
        String nombresJuntos = "JUAN, PEDRO, PABLO, DIEGO";
        String[] nombres = nombresJuntos.split(",");
        for (int i = 0; i < nombres.length; i++) {
            System.out.println(nombres[i]);
        }
        
        // Uso de toCharArray() - Separar letra por letra
        System.out.println("\n--- Letras individuales (toCharArray) ---");
        String hello = "Hello";
        char[] letras = hello.toCharArray();
        for (int i = 0; i < letras.length; i++) {
            System.out.println(letras[i]);
        }
        
        // Uso de getBytes() - Representación en memoria
        System.out.println("\nReferencia en bytes: " + hello.getBytes());
    }
}

```