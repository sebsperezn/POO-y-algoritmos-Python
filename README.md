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
