paquete MODULACIÓN;

importar java.util.Random; importar java.util.Scanner;

clase pública principal {

private static Scanner scanner = new Scanner(System.in);


public static void main(String[] args) {
	int opcion;
    do {
        mostrarMenu();
        opcion = leerEntero("Selecciona una opción (1-11): ");
        ejecutarOpcion(opcion);
    } while (opcion != 11);

    System.out.println("¡Gracias por usar el programa! Hasta pronto.");
    scanner.close();
}


// MÉTODOS DE MENÚ Y EJECUCIÓN
private static void mostrarMenu() {
    System.out.println("\n" + "=".repeat(40));
    System.out.println("MENU PRINCIPAL DE EJERCICIOS");
    System.out.println("=".repeat(40));
    System.out.println("1 Calculadora básica");
    System.out.println("2 Validación de contraseña");
    System.out.println("3 Números primos");
    System.out.println("4 Suma de números pares");
    System.out.println("5 Conversión de temperatura");
    System.out.println("6 Contador de vocales");
    System.out.println("7 Cálculo de factorial");
    System.out.println("8 Juego de adivinanza");
    System.out.println("9 Paso por referencia (Simulación)");
    System.out.println("10 Tabla de multiplicar");
    System.out.println("11 Salir");
    System.out.println("-".repeat(40));
}

private static void ejecutarOpcion(int opcion) {
    System.out.println("\n" + "-".repeat(40));
    switch (opcion) {
        case 1 -> ej1_calculadora();
        case 2 -> ej2_contrasena();
        case 3 -> ej3_numerosPrimos();
        case 4 -> ej4_sumaPares();
        case 5 -> ej5_temperatura();
        case 6 -> ej6_contadorVocales();
        case 7 -> ej7_factorial();
        case 8 -> ej8_adivinanza();
        case 9 -> ej9_pasoPorReferencia();
        case 10 -> ej10_tablaMultiplicar();
        case 11 -> { /* Salir */ }
        default -> System.out.println("Opción no válida. Intenta de nuevo.");
    }
}

// MÉTODOS DE VALIDACIÓN (try-catch)

private static int leerEntero(String mensaje) {
    while (true) {
        System.out.print(mensaje);
        try {
            return Integer.parseInt(scanner.nextLine());
        } catch (NumberFormatException e) {
            System.out.println("Error: Debes ingresar un número entero válido.");
        }
    }
}

private static double leerDouble(String mensaje) {
    while (true) {
        System.out.print(mensaje);
        try {
            return Double.parseDouble(scanner.nextLine());
        } catch (NumberFormatException e) {
            System.out.println("Error: Debes ingresar un número válido.");
        }
    }
}

// Calculadora 

private static void ej1_calculadora() {
    System.out.println("CALCULADORA BÁSICA");
    double n1 = leerDouble("Ingresa el primer número: ");
    double n2 = leerDouble("Ingresa el segundo número: ");
    
    System.out.println("Operaciones: 1.Suma 2.Resta 3.Multiplicación 4.División");
    int operacion = leerEntero("Elige la operación: ");
    
    switch (operacion) {
        case 1 -> System.out.println("Resultado: " + sumar(n1, n2));
        case 2 -> System.out.println("Resultado: " + restar(n1, n2));
        case 3 -> System.out.println("Resultado: " + multiplicar(n1, n2));
        case 4 -> {
            if (n2 == 0) System.out.println("Error: No se puede dividir entre cero.");
            else System.out.println("Resultado: " + dividir(n1, n2));
        }
        default -> System.out.println("Operación no válida.");
    }
}
private static double sumar(double a, double b) { return a + b; }
private static double restar(double a, double b) { return a - b; }
private static double multiplicar(double a, double b) { return a * b; }
private static double dividir(double a, double b) { return a / b; }

// Validación de contraseña

private static void ej2_contrasena() {
    System.out.println("VALIDACIÓN DE CONTRASEÑA");
    String pass;
    do {
        System.out.print("Ingresa la contraseña: ");
        pass = scanner.nextLine();
        if (!pass.equals("1234")) {
            System.out.println("Contraseña incorrecta. Intenta de nuevo.");
        }
    } while (!pass.equals("1234"));
    System.out.println("¡Acceso concedido!");
}

// Números primos

private static void ej3_numerosPrimos() {
    System.out.println(" NÚMEROS PRIMOS");
    int num = leerEntero("Ingresa un número entero positivo: ");
    if (esPrimo(num)) {
        System.out.println(" El número " + num + " ES primo.");
    } else {
        System.out.println(" El número " + num + " NO es primo.");
    }
}
private static boolean esPrimo(int n) {
    if (n <= 1) return false;
    for (int i = 2; i <= Math.sqrt(n); i++) {
        if (n % i == 0) return false;
    }
    return true;
}

// Suma de números pares

private static void ej4_sumaPares() {
    System.out.println("SUMA DE NÚMEROS PARES (Ingresa 0 para terminar)");
    int num;
    int suma = 0;
    while (true) {
        num = leerEntero("Ingresa un número: ");
        if (num == 0) break;
        if (num % 2 == 0) suma += num;
    }
    System.out.println("La suma de los números pares ingresados es: " + suma);
}

// Conversión de temperatura

private static void ej5_temperatura() {
    System.out.println("CONVERSIÓN DE TEMPERATURA");
    System.out.println("1. Celsius a Fahrenheit");
    System.out.println("2. Fahrenheit a Celsius");
    int opcion = leerEntero("Elige una opción: ");
    
    if (opcion == 1) {
        double c = leerDouble("Ingresa los grados Celsius: ");
        System.out.println(c + "°C equivalen a " + celsiusAFahrenheit(c) + "°F");
    } else if (opcion == 2) {
        double f = leerDouble("Ingresa los grados Fahrenheit: ");
        System.out.println(f + "°F equivalen a " + fahrenheitACelsius(f) + "°C");
    } else {
        System.out.println("Opción no válida.");
    }
}
private static double celsiusAFahrenheit(double c) { return (c * 9/5) + 32; }
private static double fahrenheitACelsius(double f) { return (f - 32) * 5/9; }

// Contador de vocales

private static void ej6_contadorVocales() {
    System.out.println("CONTADOR DE VOCALES");
    System.out.print("Ingresa una palabra o frase: ");
    String texto = scanner.nextLine();
    System.out.println("El texto contiene " + contarVocales(texto) + " vocales.");
}
private static int contarVocales(String texto) {
    int contador = 0;
    String t = texto.toLowerCase();
    for (int i = 0; i < t.length(); i++) {
        char c = t.charAt(i);
        if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') contador++;
    }
    return contador;
}

// Cálculo de factorial

private static void ej7_factorial() {
    System.out.println("CÁLCULO DE FACTORIAL");
    int num;
    do {
        num = leerEntero("Ingresa un número entero positivo: ");
        if (num < 0) System.out.println("Error: El número no puede ser negativo.");
    } while (num < 0);
    
    System.out.println("El factorial de " + num + " es: " + calcularFactorial(num));
}
private static long calcularFactorial(int n) {
    long fact = 1;
    for (int i = 1; i <= n; i++) fact *= i;
    return fact;
}

// Juego de adivinanza
private static void ej8_adivinanza() {
    System.out.println("JUEGO DE ADIVINANZA");
    Random rnd = new Random();
    int secreto = rnd.nextInt(100) + 1; // 1 a 100
    int intento;
    
    do {
        intento = leerEntero("Adivina el número (entre 1 y 100): ");
        if (intento > secreto) System.out.println("Es menor. ¡Sigue intentando!");
        else if (intento < secreto) System.out.println("Es mayor. ¡Sigue intentando!");
    } while (intento != secreto);
    
    System.out.println("¡Felicidades! Adivinaste el número " + secreto);
}

// Paso por referencia

static class NumeroWrapper { int valor; }

private static void ej9_pasoPorReferencia() {
    System.out.println("SIMULACIÓN DE PASO POR REFERENCIA");
    NumeroWrapper n1 = new NumeroWrapper();
    NumeroWrapper n2 = new NumeroWrapper();
    
    n1.valor = leerEntero("Ingresa el valor de A: ");
    n2.valor = leerEntero("Ingresa el valor de B: ");
    
    System.out.println("\nValores ANTES del intercambio:");
    System.out.println("A = " + n1.valor + " | B = " + n2.valor);
    
    intercambiar(n1, n2); // Se pasa la referencia del objeto
    
    System.out.println("\nValores DESPUÉS del intercambio:");
    System.out.println("A = " + n1.valor + " | B = " + n2.valor);
}
private static void intercambiar(NumeroWrapper a, NumeroWrapper b) {
    int temp = a.valor;
    a.valor = b.valor;
    b.valor = temp;
}

// Tabla de multiplicar
private static void ej10_tablaMultiplicar() {
    System.out.println("TABLA DE MULTIPLICAR");
    int num = leerEntero("Ingresa el número para generar su tabla: ");
    generarTabla(num);
}
private static void generarTabla(int num) {
    System.out.println("\nTabla del " + num + ":");
    for (int i = 1; i <= 10; i++) {
        System.out.println(num + " x " + i + " = " + (num * i));
    }
}
}
