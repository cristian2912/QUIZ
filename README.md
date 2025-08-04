# QUIZ

#PUNTO 1
<img width="1229" height="750" alt="image" src="https://github.com/user-attachments/assets/5bac0f85-a705-494b-a1d3-ecf870392317" />
```
class Navegador:
    def __init__(self):
        self.historial_retroceso = []  # pila para ir atras
        self.historial_avance = []  # pila para ir adelante
        self.pagina_actual = None  # pgina que se esta viendo actualmente

    def cargar_pagina(self, url):
        if self.pagina_actual:
            # si ya hay una pagina se agrega al historial de retroceso
            self.historial_retroceso.append(self.pagina_actual)
        # selimpia el historial de avance si se carga una nueva pagina
        self.historial_avance.clear()
        self.pagina_actual = url
        print(f"Pagina cargada: {url}")

    def ir_atras(self):
        if self.historial_retroceso:
            # mover la pagina actual a la pila de avance
            self.historial_avance.append(self.pagina_actual)
            # obtener la ultima pagina del historial de retroceso
            self.pagina_actual = self.historial_retroceso.pop()
            print(f"Volviendo a: {self.pagina_actual}")
        else:
            print("No hay mas paginas para retroceder.")

    def ir_adelante(self):
        if self.historial_avance:
            # mover la pagina actual a la pila de retroceso
            self.historial_retroceso.append(self.pagina_actual)
            # obtener la ultima pagina del historial de avance
            self.pagina_actual = self.historial_avance.pop()
            print(f"Avanzando a: {self.pagina_actual}")
        else:
            print("No hay mas paginas para avanzar.")

# prueba del sistema
navegador = Navegador()
navegador.cargar_pagina("pagina1.com")
navegador.cargar_pagina("pagina2.com")
navegador.cargar_pagina("pagina3.com")

navegador.ir_atras()  # volver a pagina 2
navegador.ir_atras()  # volver a pagina 1
navegador.ir_adelante()  # avanzar a pagina 2
navegador.ir_adelante()  # avanzar a pagina 3
```

#PUNTO 2

<img width="860" height="784" alt="image" src="https://github.com/user-attachments/assets/f1a66e83-bfd3-4748-bc09-fed850699866" />

```
class Cliente:
    def __init__(self, id_cliente, nombre):
        self.id_cliente = id_cliente
        self.nombre = nombre

    def __str__(self):
        return f"ID: {self.id_cliente}, Nombre: {self.nombre}"


class Cola:
    def __init__(self, capacidad):
        self.capacidad = capacidad
        self.cola = []

    def esta_vacia(self):
        return len(self.cola) == 0

    def esta_llena(self):
        return len(self.cola) == self.capacidad

    def add_customer(self, cliente):
        if self.esta_llena():
            print("La cola esta llena. No se pueden agregar mas clientes.")
        else:
            self.cola.append(cliente)
            print(f"Cliente {cliente.nombre} agregado a la cola.")

    def serve_customer(self):
        if self.esta_vacia():
            print("La cola esta vacia. No hay clientes para atender.")
        else:
            cliente = self.cola.pop(0)
            print(f"Atendiendo a: {cliente.nombre} (ID: {cliente.id_cliente})")

    def display_queue(self):
        if self.esta_vacia():
            print("La cola esta vacia.")
        else:
            print("Clientes en la cola:")
            for cliente in self.cola:
                print(cliente)


# funcion principal para probar el sistema
def main():
    # crear la cola con capacidad para 5 clientes
    cola = Cola(capacidad=5)

    # crear clientes
    cliente1 = Cliente(1, "Juan Perez")
    cliente2 = Cliente(2, "Maria Lopez")
    cliente3 = Cliente(3, "Carlos Garcia")
    cliente4 = Cliente(4, "Ana Torres")
    cliente5 = Cliente(5, "Luis Romero")
    cliente6 = Cliente(6, "Elena Vasquez")

    # agregar clientes a la cola
    cola.add_customer(cliente1)
    cola.add_customer(cliente2)
    cola.add_customer(cliente3)
    cola.add_customer(cliente4)
    cola.add_customer(cliente5)

    # intentar agregar un sexto cliente cuando la cola esta llena
    cola.add_customer(cliente6)  # La cola ya esta llena

    # mostrar los clientes en la cola
    cola.display_queue()

    # atender clientes
    cola.serve_customer()
    cola.serve_customer()
    cola.serve_customer()

    # mostrar el estado de la cola despues de atender algunos clientes
    cola.display_queue()

if __name__ == "__main__":
    main()

