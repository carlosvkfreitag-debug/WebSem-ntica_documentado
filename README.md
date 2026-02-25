```mermaid
@startuml
skinparam classAttributeIconSize 0

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

' Relaciones de dependencia (uso)
Main ..> Producto : <<instantiates>>
Main ..> CalculadoraIVA : <<uses>>
Main ..> java.util.Scanner : <<uses>>

@enduml
