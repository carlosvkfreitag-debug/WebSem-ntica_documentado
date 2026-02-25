```mermaidsequenceDiagram
    autonumber
    actor Usuario
    participant M as Main
    participant S as Scanner <<External>>
    participant P as Producto
    participant C as CalculadoraIVA

    Usuario->>M: Ejecuta el programa
    M->>S: nextLine() (pide Nombre)
    S-->>M: retorna "Nombre"
    M->>S: nextDouble() (pide Precio)
    S-->>M: retorna precioBase
    
    Note over M,P: Instanciación del objeto
    M->>P: new Producto(nombre, precio)
    P-->>M: objeto creado
    
    M->>P: getPrecioBase()
    P-->>M: retorna precioBase
    
    M->>C: calcularPrecioFinal(precioBase)
    C-->>M: retorna precio con IVA (21%)
    
    M->>Usuario: Muestra "Total con IVA"

classDiagram
    direction TB

    class Main {
        +main(String[] args)$
    }

    class Producto {
        -String nombre
        -double precioBase
        +Producto(String nombre, double precioBase)
        +getPrecioBase() double
    }

    class CalculadoraIVA {
        -double IVA
        +calcularPrecioFinal(double precio) double
    }

    class Scanner {
        <<External>>
    }

    Main ..> Producto : crea instancia
    Main ..> CalculadoraIVA : usa para calcularsequenceDiagram
    autonumber
    actor Usuario
    participant M as Main
    participant S as Scanner <<External>>
    participant P as Producto
    participant C as CalculadoraIVA

    Usuario->>M: Ejecuta el programa
    M->>S: nextLine() (pide Nombre)
    S-->>M: retorna "Nombre"
    M->>S: nextDouble() (pide Precio)
    S-->>M: retorna precioBase
    
    Note over M,P: Instanciación del objeto
    M->>P: new Producto(nombre, precio)
    P-->>M: objeto creado
    
    M->>P: getPrecioBase()
    P-->>M: retorna precioBase
    
    M->>C: calcularPrecioFinal(precioBase)
    C-->>M: retorna precio con IVA (21%)
    
    M->>Usuario: Muestra "Total con IVA"
    Main ..> Scanner : lee entrada

sequenceDiagram
    autonumber
    actor Usuario
    participant M as Main
    participant S as Scanner <<External>>
    participant P as Producto
    participant C as CalculadoraIVA

    Usuario->>M: Ejecuta el programa
    M->>S: nextLine() (pide Nombre)
    S-->>M: retorna "Nombre"
    M->>S: nextDouble() (pide Precio)
    S-->>M: retorna precioBase
    
    Note over M,P: Instanciación del objeto
    M->>P: new Producto(nombre, precio)
    P-->>M: objeto creado
    
    M->>P: getPrecioBase()
    P-->>M: retorna precioBase
    
    M->>C: calcularPrecioFinal(precioBase)
    C-->>M: retorna precio con IVA (21%)
