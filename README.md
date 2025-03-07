# trabajo-codigo
class Producto:
    def __init__(self, id, nombre, precio, stock):
        self.id = id
        self.nombre = nombre
        self.precio = precio
        self.stock = stock

class Pedido:
    def __init__(self, id_pedido, cliente, productos_solicitados, estado):
        self.id_pedido = id_pedido
        self.cliente = cliente
        self.productos_solicitados = productos_solicitados
        self.estado = estado

class Cliente:
    def __init__(self, nombre, email, direccion):
        self.nombre = nombre
        self.email = email
        self.direccion = direccion

#lista para almacenar los objetos
productos = [
    Producto(1103, "Camiseta", 80.0, 90),
    Producto(2030, "Zapatos", 250.0, 100),
    Producto(3812, "Buzo", 85.0, 115)
]

clientes = [
    Cliente("Bibiana", "Bibiana@gmail.com", "carrera 21 #39-31 barrio san jose,barranquilla"),
    Cliente("Nicolls", "nicolls@gmail.com", "cra 51a #18-44 barrio costa hermosa,barranquilla")
]

pedidos = [
    Pedido(101, clientes[0], [productos[0], productos[1]], "Enviado"),
    Pedido(210, clientes[1], [productos[1], productos[2]], "Procesando")
]

#mostrar los productos
def mostrar_productos():
    print("Lista de Productos:")
    for producto in productos:
        print(f"ID: {producto.id}, Nombre: {producto.nombre}, Precio: ${producto.precio}, Stock: {producto.stock}")

#mostrar los pedidos
def mostrar_pedidos():
    print("Lista de Pedidos:")
    for pedido in pedidos:
        productos_nombres = [producto.nombre for producto in pedido.productos_solicitados]
        print(f"ID Pedido: {pedido.id_pedido}, Cliente: {pedido.cliente.nombre}, Productos: {productos_nombres}, Estado: {pedido.estado}")

#mostrar los clientes
def mostrar_clientes():
    print("Lista de Clientes:")
    for cliente in clientes:
        print(f"Nombre: {cliente.nombre}, Email: {cliente.email}, Dirección: {cliente.direccion}")
        
#extra 

#agregar un nuevo producto
def agregar_producto(id, nombre, precio, stock):
    nuevo_producto = Producto(id, nombre, precio, stock)
    productos.append(nuevo_producto)

#cambiar el estado de un pedido
def cambiar_estado_pedido(id_pedido, nuevo_estado):
    for pedido in pedidos:
        if pedido.id_pedido == id_pedido:
            pedido.estado = nuevo_estado
            break

#encontrar pedidos por email de cliente
def encontrar_pedidos_por_email(email):
    print(f"Pedidos del cliente con email {email}:")
    for pedido in pedidos:
        if pedido.cliente.email == email:
            productos_nombres = [producto.nombre for producto in pedido.productos_solicitados]
            print(f"ID Pedido: {pedido.id_pedido}, Productos: {productos_nombres}, Estado: {pedido.estado}")

# Ejemplos de uso
mostrar_productos()
mostrar_pedidos()
mostrar_clientes()

# Agregar un nuevo producto
agregar_producto(4050, "Pantalón", 39.99, 75)
print("\nDespués de agregar un nuevo producto:")
mostrar_productos()

# Cambiar el estado del pedido 101 a "Entregado"
cambiar_estado_pedido(101, "Entregado")
print("\nDespués de cambiar el estado del pedido 101 a 'Entregado':")
mostrar_pedidos()

# Encontrar todos los pedidos de un cliente específico por email
encontrar_pedidos_por_email("nicolls@gmail.com")
