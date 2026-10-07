# Guía de Laboratorio: Sistema Modular de Inventario (Swing + CSV)

## Objetivo de la Práctica

Aplicar el **Diseño Descendente** (divide y vencerás) construyendo una aplicación de múltiples ventanas con alta cohesión. Se utilizarán arreglos paralelos controlados por variables globales, modularidad mediante métodos propios y persistencia de datos en formato `.csv`.

---

## Fase 1: Creación y Configuración de Ventanas

1. En el proyecto de NetBeans, crear tres formularios (`JFrame Form`):
* `Menu`
* `Registro`
* `Consulta`


2. **Configuración de cierre (Importante):** Entra al diseño de `Registro` y `Consulta`, selecciona el `JFrame` principal y en la ventana de **Properties** cambia la propiedad `defaultCloseOperation` de `EXIT_ON_CLOSE` a **`DISPOSE_ON_CLOSE`** (o `HIDE_ON_CLOSE`). *(Esto evita que al cerrar una ventana secundaria se apague todo el programa).*
3. **Instancias Globales en el Menú Principal:** En lugar de crear una ventana nueva cada vez que se presiona un botón, declar los formularios como variables globales y estáticas (`static`) en la parte superior de `Menu`.


Abajo de `public class Menu extends javax.swing.JFrame {` colocar las variables 
```java
    static Registro frmRegistro = new Registro();
    static Consulta frmConsultar = new Consulta();

```

1. **Programar los Botones del Menú:** Dentro del evento de cada botón en `Menu`, hacer visible el formulario correspondiente:

```java
// En el botón de abrir Registro:
frmRegistro.setLocationRelativeTo(null); // Centra la ventana
frmRegistro.setVisible(true);

```

*(Hacer lo mismo en el segundo botón para mostrar el formulario Consultar con la variable `frmConsultar`).*

---

## Fase 2: Módulo de Escritura (`Registro`)

### 1. Diseño de la Interfaz

Agregar dos cajas de texto (`txtNombre` y `txtPrecio`) y dos botones (`btnAgregar` y `btnGuardar`).

```Plaintext
+------------------------------------------+
| 📝 Registro de Productos            _ □ X|
+------------------------------------------+
|  Nombre Producto: [_______________]      |
|                       txtNombre          |
|  Precio (Q):      [_______________]      |
|                       txtPrecio          |
|                                          |
|  [   Agregar   ]   [ Guardar CSV ]       |
|     btnAgregar        btnGuardar         |
+------------------------------------------+

```

### 2. Alcance de Variables (Globales)

Declarar dos arreglos paralelos y el índice en la parte superior de la clase (afuera de los botones) para que sean accesibles desde cualquier módulo del formulario y conserven sus valores entre cada clic (variables globales):

Abajo de `public class Registro extends javax.swing.JFrame {` colocar lo siguiente:
```java
    // Variables Globales
    String[] nombres = new String[5];
    double[] precios = new double[5];
    int indice = 0;

```

### 3. Creación de un Módulo Propio (`limpiar`)

Debajo del constructor `public Registro()`

```java
    public Registro() {
        initComponents();
    }
```

Crear un método independiente cuya única tarea sea dejar en blanco los campos de texto después de cada registro:

```java
    public void limpiar() {
        txtNombre.setText("");
        txtPrecio.setText("");
        txtNombre.requestFocus(); // Devuelve el cursor al primer text field
    }
```

### 4. Programación del Botón "Agregar" (`btnAgregar`)

* **Pista lógica:** Verificar con un `if` que la variable `indice` sea menor al tamaño del arreglo (`nombres.length`).
* Extraer los datos de los text fields hacia las **variables locales** (recuerda usar `Double.parseDouble()` para el precio).
* Guardar ambos datos en sus respectivos arreglos usando la misma posición `[indice]`, incrementar el índice (`indice++`) e invocar a al método `limpiar();`.

### 5. Programación del Botón "Guardar CSV" (`btnGuardar`)

* **Pista lógica:** Dentro de un bloque `try-catch`, instancia un `FileWriter("productos.csv", false)`.
* Recorre tus arreglos con un ciclo `for` desde `0` hasta `indice`.
* En cada vuelta del ciclo, escribe el nombre y el precio unidos por una coma para formar la estructura CSV:

```java
fw.write(nombres[i] + "," + precios[i] + "\n");

```
* *No olvides cerrar el archivo con `.close()` fuera del ciclo.*

---

## Fase 3: Módulo de Lectura y Cálculo (`Consulta`)

### 1. Diseño y Variables Globales

1. Diseñar la ventana con un botón (`btnCargar`) y un área de texto (`taCatalogo`).
2. Al inicio de la clase, declara las variables globales para recepcionar los datos del archivo: `catalogoNombres` (String de tamaño 5), `catalogoPrecios` (double de tamaño 5) 
   
   y el contador `totalLeidos = 0`.

```Plaintext
+------------------------------------------+
| 🔍 Consulta de Catálogo             _ □ X|
+------------------------------------------+
|  [ Mostrar Catálogo ]                    |
|        btnCargar                         |
|                                          |
|  +------------------------------------+  |
|  | taCatalogo                         |  |
|  | 1. Teclado Mecánico - Q250.0       |  |
|  | 2. Mouse Inalámbrico - Q125.5      |  |
|  | ---------------------------------- |  |
|  | Valor Total del Inventario: Q375.5 |  |
|  +------------------------------------+  |
+------------------------------------------+
```


### 2. Submódulo 1: Lectura y separación con `.split()`

Crear un método llamado `public void leerArchivoCSV()`. Dentro de él, usaremos el ejemplo de leer archivos linea por linea con un `File` y `Scanner` para leer `"productos.csv"`.

* **El truco del CSV:** Como cada línea viene junta (ej. `"Teclado,250.0"`), usar el método `.split(",")` dentro de tu ciclo `while` para partir el texto en dos:

```java
File archivo = new File(rutaArchivo);
try(Scanner sc = new Scanner(archivo)) {
    while(sc.hasNextLine()) {
        String[] partes = linea.split(","); // Corta el texto donde encuentre la coma
        
        catalogoNombres[totalLeidos] = partes[0]; // Posición 0: El nombre
        catalogoPrecios[totalLeidos] = Double.parseDouble(partes[1]); // Posición 1: El precio
        
        totalLeidos++;
    }
}

```

### 3. Submódulo 2: Cálculo de Inventario

Crear un método que devuelva un valor decimal y cuya única responsabilidad sea sumar los precios:

```java
public double calcularTotalInventario() {
    double suma = 0; // Variable local acumuladora
    // PISTA: Haz un ciclo 'for' desde 0 hasta 'totalLeidos' que sume catalogoPrecios[i]
    return suma;
}

```

### 4. Submódulo 3: Mostrar en Pantalla

Crea el método `public void mostrarEnPantalla()`:

* **Pista lógica:** Limpia el `taCatalogo` con `.setText("")`.
* Haz un ciclo `for` hasta `totalLeidos` y usa `.append()` para imprimir cada número de fila, nombre y precio.
* Al final del método imprimir el total al final del área de texto.



### 5. Uniendo todo en el Botón "Cargar" (`btnCargar`)

Debido al diseño modular, el evento del botón principal queda limpio y fácil de mantener, limitándose a invocar los métodos en orden:

```java
private void btnCargarActionPerformed(java.awt.event.ActionEvent evt) {                                          
    leerArchivoCSV();
    mostrarEnPantalla();
}

```

---

## Reto Extra

Crear un cuarto método en `Consultar` llamado `public int contarProductosCaros()` que recorra el arreglo de precios y devuelva cuántos productos cuestan más de Q100.00. Muestrar este dato al final del área de texto agregado al reporte en pantalla.