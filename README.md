```mermaid
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
    
    M->>Usuario: Muestra "Total con IVA"
