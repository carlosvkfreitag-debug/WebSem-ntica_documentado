```mermaid
classDiagram

class Cliente {
  -id: int
  -nombre: String
  -email: String
  +realizarPedido(p: Pedido): void
  +getPedidos(): List~Pedido~
}

class Pedido {
  -id: int
  -fecha: Date
  -estado: EstadoPedido
  +agregarLinea(lp: LineaPedido): void
  +eliminarLinea(lp: LineaPedido): void
  +calcularTotal(): double
}

class LineaPedido {
  -cantidad: int
  +calcularSubtotal(): double
}

class Producto {
  -id: int
  -nombre: String
  -precio: double
  +getPrecio(): double
}

class EstadoPedido {
  <<enumeration>>
  PENDIENTE
  ENTREGADO
}

Cliente "1" o-- "0..*" Pedido : realiza
Pedido "1" *-- "1..*" LineaPedido : contiene
LineaPedido "0..*" --> "1" Producto : producto
Pedido --> EstadoPedido
