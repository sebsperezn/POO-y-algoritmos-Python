# POO-y-algoritmos-Python
Apuntes del curso de Programacion Orientada a Objetos y algoritmos con Python de Platzi

## Tabla de contenidos
- Programación Orientada a Objetos
  - [Objetivos](#Objetivos)
  - [Programación Orientada a Objetos](#Programación-orientada-a-objetos)
  - [Tipos de datos abstractos, clases e instancias](#Tipos-de-datos-abstractos,-clases-e-instancias)
  
## Objetivos
- Entender cómo funciona la Programación Orientada a Objetos
- Entender cómo medir la eficiencia temporal y espacial de algoritmos.
- Entender cómo y por qué graficar.
- Aprender a resolver problemas de búsqueda, ordenación y optimización.

## Programación orientada a objetos
Uno de los elementos más importantes de los lenguajes de programación es la utilización de clases para organizar programas en módulos y abstracciones de datos.

La clave para entender la programación orientada a objetos es pensar en objetos como agrupaciones de datos y los métodos que operan en dichos datos.

Por ejemplo, podemos representar a una persona con propiedades como nombre, edad, género, etc. y los comportamientos de dicha persona como caminar, cantar, comer, etc. De la misma manera podemos representar unos audífonos con propiedades como su marca, tamaño, color, etc. y sus comportamientos como reproducir música, pausar y avanzar a la siguiente canción.

Puesto de otra manera, la programación orientada a objetos nos permite modelar cosas reales y concretas del mundo y sus relaciones con otros objetos.

### Clases en Python
Las estructuras primitivas nos permiten definir cosas sencillas, como el costo de algo, el nombre de un usuario, las veces que debe correr un bucle, etc. Sin embargo, existen ocasiones cuando necesitamos definir estructuras más complejas, por ejemplo un hotel. Podríamos utilizar dos listas: una para definir los cuartos y una segunda para definir si el cuarto se encuentra ocupado o no.

```py
cuartos_de_hotel = [101, 102, 103, 201, 202, 203]
cuarto_ocupado = [True, False, False, True, True, False]
```

Ejemplo:
```py

```

Sin embargo, este tipo de organización rápidamente se sale de control. ¿Qué tal que quisiéramos añadir más propiedades, cómo si el cuarto ya fue aseado o no? ¿Si el cuarto tiene cama doble o sencilla? Esto nos lleva a una falta fuerte de organización y es justamente el punto que justifica la existencia de clases.

Las clases nos permiten crear nuevos tipos que contiene información arbitraria sobre un objeto. En el caso del hotel, podríamos crear dos clases Hotel() y Cuarto() que nos permitiera dar seguimiento a las propiedades como número de cuartos, ocupación, aseo, tipo de habitación, etc.

Es importante resaltar que las clases solo proveen estructura. Son un molde con el cual podemos construir objetos específicos. La clase señala las propiedades que los hoteles que modelemos tendrán, pero no es ningún hotel específico. Para eso necesitamos las instancias.

### Instancias
Mientras que las clases proveen la estructura, las instancias son los objetos reales que creamos en nuestro programa: un hotel llamado PlatziHotel o Hilton. Otra forma de pensarlo es que las clases son como un formulario y una vez que se llena cada copia del formulario tenemos las instancias que pertenecen a dicha clase. Cada copia puede tener datos distintos, al igual que cada instancia es distinta de las demás (aunque todas pertenecen a una misma clase).

Para definir una clase, simplemente utilizamos el *keyword* class. Por ejemplo:

```py
class Hotel:
    pass
```

Una vez que tenemos una clase llamada Hotel podemos generar una instancia llamando al constructor de la clase.

```py
hotel = Hotel()
```

### Atributos de la instancia
Todas las clases crean objetos y todos los objetos tienen atributos. Utilizamos el metodo especial **__init__** para definir el estado inicial de nuestra instancia. Recibe como primer parámetro obligatorio **self** (que es simplemente una referencia a la instancia).

```py
class Hotel:

    def __init__(self, numero_maximo_de_huespedes, lugares_de_estacionamiento):
      self.numero_maximo_de_huespedes = numero_maximo_de_huespedes
      self.lugares_de_estacionamiento = lugares_de_estacionamiento
      self.huespedes = 0
 
 hotel = Hotel(numero_maximo_de_huespedes=50, lugares_de_estacionamiento=20)
 print(hotel.lugares_de_estacionamiento) #20
 ```
 
 ### Métodos de instacia
 Mientras que los atributos de la instancia describen lo que representa el objeto, los métodos de instancia nos indican qué podemos hacer con las instancias de dicha clase y normalmente operan en los mencionados atributos. Los métodos son equivalentes a funciones dentro de la clase, pero todos reciben **self** como primer argumento.
 
 ```py
 class Hotel:
    ...
  
    def anadir_huespedes(self, cantidad_de_huespedes):
        self.huespedes += cantidad_de_huespedes

    def checkout(self, cantidad_de_huespedes):
        self.huespedes -= cantidad_de_huespedes

    def ocupacion_total(self):
        return self.huespedes
      
hotel = Hotel(50,20)
hotel.anadir_huespedes(3)
hotel.checkout(1)
hotel.ocupacion_total() #2
```

## Tipos de datos abstractos, clases e instancias
En Python todo es un objeto y tiene un tipo, esto significa que todo lo que hacemos dentro del programa tiene una representacion en memoria.

Fromas de interactuar con un objeto:
- Creación
- Manipulación
- Destrucción

### Tipos de datos abstractos
- Ventajas
  - Descomposición - Estructurar objetos mas pequeños 
  - Abstracción - No nos preocupamos el funcionamiento del proceso de su comportamiento.
  - Encapsulación - Podemos esconder ciertos datos que solo son relevantes internamente en el objeto.

**Definición de clase**
```py
# Primero definimos el nombre de la clase y podemos determinar si hereda de otra clase.
class <nombre_de_la_clase>(<super_clase>):
    # El método init es un constructor, y siempre los métodos dentro de los parámetros inician con el parámetro self
    def __init__(self, <params>):
        <espresion>
    # Las clases pueden tener comportamientos, y estos los definimos con los métodos.
    def <nombre_del_metodo>(self, <params>):
        <expresion>
```
Ejemplo:

```py
class Persona:

	def __init__(self, nombre, edad):
		self.nombre = nombre
		self.edad = edad

	def saluda(self, otra_persona):
		return f'Hola {otra_persona.nombre}, me llamo {self.nombre}.'
		
	# Uso
	>>> david = Persona('David'. 35)
	>>> erika = Persona('Erika', 32)
	
	>>> david.saluda(erika)
	'Hola Erika, me llamo David'
``` 
Lo que nos da la clase es un tipo de 'molde'. Es una forma en la que nosotros podemos definir cuáles son las características que esta clase va a tener, y estas características las van a poder utilizar todas las instancias de clase.

## Instancias
- Mientras que la clase es un molde, a los objetos creados se les conoce como instancias.
- Cuando se crea una instancia, se ejecuta el método __init__
- Todos los métodos de una clase reciben implícitamente como primer parámetro self

- Los atributos de clase nos permiten:
	- Representar datos
	- Procedimientos para interactuar con los mismos(métodos)
	- Mecanismos para esconder la representación interna (variables privadas)
- Se accede a los atributos con la notación punto
- Puede tener atributos privados. Por convención comienza con _

```py
class Coordenada:
	def __init__(self, x, y):
		self.x = x
		self.y = y
		
	def distancia(self, otra_coordenada):
		x_diff = (self.x - otra_coordenada.x)**2
		y_diff = (self.y - otra_coordenada.y)**2
		
		return (x_diff + y_diff)**0.5
		
if __name__ == '__main__':
	coord_1 = Coordenada(3, 30)
	coord_2 = Coordenada(4, 8)
	
	print(coord_1.distancia(coord_2))
	>>> 22.02271554554524
	print(isInstance(coord_2, Coordenada))
	>>> True
```

## Decomposición

La descomposición se refiere a partir un problema en problemas más pequeños. Las clases permiten crear mayores abstracciones en forma de componentes. Cada clase se encarga de una parte del problema y el programa se vuelve más facil de mantener.

Ejemplo de descomposición:

Al principio la clase Automovil se vería asi:
```py
class Automovil:

	def __init__(self, modelo, marca, color):
		self.modelo = modelo
		self.marca = marca
		self.color = color
		self._estado = 'reposo' #Variable privada
		self._motor = Motor(cilindros=4)
	
	def acelerar(self, tipo='despacio'):
		if tipo == 'rapida':
			self._motor.inyecta_gasolina(10)
		else:
			self._motor.inyecta_gasolina(3)
		self.estado = 'en movimiento'
class Motor:

	def __init__(self, cilindros, tipo='gasolina' '''default keyword''')
		self.cilindros = cilindros
		self.tipo = tipo
		self._temperatura = 0
	
	def inyecta_gasolina(self, cantidad):
		pass
```

## Abstracción

- Enfocarnos en la información relevante, generar una interfaz mediante la cual nosotros podemos interactuar con cualquier tipo de objeto sin enfocarnos en los detalles técnicos.
- Separar la información central de los detalles secundarios.
- Podemos utilizar variables y métodos (privados o públicos)

Como ejemplo crearemos una clase sencilla que represent a una lavadora:
```py
class Lavadora:

	def __init__(self):
		pass # No hay cuerpo en la función
	
	def lavar(self, temperatura='caliente'):
		# Los métodos privados de la clase no son relevantes
		# para el uso fuera de la clase, por convención
		# se inicia con _
		self._llenar_tanque_de_agua(temperatura)
		self._anadir_jabon()
		self._lavar()
		self._centrifugar()

	def _llenar_tanque_de_agua(self, temperatura):
		print(f'Llenando el tanque con agua {temperatura}')

	def _anadir_jabon(self):
		print('Anadiendo jabon')
	
	def _lavar(self):
		print('Lavando la ropa')

	def _centrifugar(self):
		print('Centrifugando la ropa')

if __name__ = '__main__':
	lavadora = Lavadora()
	lavadora.lavar()

	>>> LLenando el tanque con agua caliente
	>>> Anadiendo jabon
	>>> Lavando la ropa
	>>> Centrifugando la ropa
```