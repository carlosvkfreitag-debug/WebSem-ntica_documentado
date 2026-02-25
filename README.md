```mermaid

classDiagram
    class Producto {
        - nombre: String
        - precioBase: double
        + Producto(nombre: String, precioBase: double)
        + getPrecioBase(): double
    }
    
    class CalculadoraIVA {
        - IVA: double = 0.21
        + calcularPrecioFinal(precio: double): double
    }
    
    class Main {
        + {static} main(args: String[]): void
    }
    
    ' Relaciones de dependencia
    Main ..> Producto : "instancia"
    Main ..> CalculadoraIVA : "usa"
    Main ..> java.util.Scanner : "usa"
