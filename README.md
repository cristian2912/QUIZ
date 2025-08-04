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

``
