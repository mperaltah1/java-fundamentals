# Compilación y Ejecución de Hola Mundo en Consola

## 1. Escribir el código en un editor de texto
Abrir el Bloc de notas (o cualquier editor de texto plano) y escribir el código simplificado de "Hola Mundo". En las versiones modernas de Java ya no es necesario declarar la clase ni el método estático de forma explícita.

```java
void main() {
    System.out.println("¡Hola Mundo desde la consola!");
}

```

## 2. Guardar el archivo

Guardar el documento en una ubicación de fácil acceso, como el Escritorio. En la ventana de guardado, se debe cambiar la opción "Tipo" de "Documentos de texto (*.txt)" a "Todos los archivos (*.*)". El nombre del archivo debe ser asignado exactamente como `HolaMundo.java`.

## 3. Abrir la consola de PowerShell

Presionar la combinación de teclas `Windows + R`, escribir `powershell` en la ventana de ejecución y presionar la tecla Enter para abrir la terminal.

## 4. Navegar hasta la carpeta del archivo

Utilizar el comando `cd` (Change Directory) para desplazarse a la ruta donde se guardó el documento. Por ejemplo, si se guardó en el escritorio, se debe ingresar `cd Desktop` (o `cd Escritorio`). Para confirmar que el archivo se encuentra en esa ubicación, se puede ejecutar el comando `ls`.

*Nota:* Windows ahora coloca por defecto el Escritorio y las demás carpetas de usuario dentro de OneDrive. En ese caso, la ruta común sería ingresar: `cd C:\Users\<su_usuario>\OneDrive\Desktop`

## 5. Compilar el código

Para traducir el código a *bytecode*, se debe escribir el comando del compilador de Java incluyendo la extensión del archivo, y presionar Enter:

```bash
javac HolaMundo.java

```

Si no existen errores de sintaxis en el código, la consola pasará a la siguiente línea en blanco sin mostrar advertencias. Al ejecutar el comando `ls` nuevamente, se confirmará la creación automática de un nuevo archivo llamado `HolaMundo.class`.

## 6. Ejecutar el programa

Para iniciar el programa compilado, se debe invocar a la máquina virtual de Java utilizando únicamente el nombre del archivo original, **sin** incluir la extensión:

```bash
java HolaMundo

```

Al presionar Enter, la consola imprimirá en pantalla el texto indicado dentro del código: `¡Hola Mundo desde la consola!`

```

¿Te gustaría que aplique esta misma simplificación de código (eliminando el `public class` y el `String[] args`) en los ejemplos de la guía de Operaciones Básicas que vimos anteriormente?

```