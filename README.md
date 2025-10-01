# taller_Repaso
#1. En el primer punto me pregunta que atributos son accesibles desde A y la respuesta correcta fueron:
#   A.X, A._y, a._A__z en este caso se este caso se trabaja con atributos publicos, protegidos por convención y privados y los ejemplos anteriores permiten comprender como utilizarlos
#2.En el segundo punto me piden la salida de un codigo, se utiliza hasattr que su estructura (a, '__secret') esta siendo mal utilizada porque se esta tratando de acceder a un atributo privado por fuera de la #clase de manera incorrecta debido a esto me devolvera falsa, y en el segundo caso se utiliza 'a._A__secret' aplicando de forma correcta el name mangling y devolviendo true.

#3. Me solicita responder falso y verdadero:
   El prefijo _ impide el acceso desde fuera de la clase. falso si sigo la estructura objeto._atributo podre acceder a el (como en el ejercicio 1)
   El prefijo __ hace imposible acceder al atributo. falso el doble guion bajo lo convierte en un atributo privado pero eso no significa que no pueda ser utilizado por fuera de la clase si se utiliza bien el name mangling es posible acceder a el como en el ejercicio 1.
   El name mangling depende del nombre de la clase. verdadero una parte fundamental del name mangling es el nombre original porque es uno de los componentes de su estructura, objeto._CLASE__atributo
4.En el 4 punto consiste en lectura del codigo
  En este caso se esta implementado el concepto de heriencia y de subclases, en este caso puntual en el constructor de la primera clase se define un atributo protegido por convencion y se utiliza en la clase hija, en este caso no hay ningun problema por ser protegido, en el caso puntual de porque no hay un error de acceso es porque dentro de la clase hija hay una funcion que retorna el atributo protegido, en este caso al     final hay un print que muestra el valor retornado en la función reveal.
5.En el punto 5 me piden analizar un codigo a diferencia del anterior, en este se encuentra un atributo privado que impide acceder con su nombre original por fuera de la clase incluyendo las clases hijas, en este caso puntual se genera un primer atributo privado que adquiere el nombre de self._Base__v (si se quiere acceder a el por fuera de la clase) y en la clase hija se vuelve a crear un atributo privado con el nombre     self.__v en este caso se diferencia con el primero porque un elemento trascendental en el name mangling es el nombre de la clase en que proviene en este caso seria:
  primer objeto privado=self._Base__v y el segundo se puede acceder solo son el self.__v porque esta dentro de la clase en que fue creada, la funcion show me retorna los valores de estos atributos privados y por esta situacion en el print no se generan errores.
  imprime (2,1)
  En esta situacion se implemento el super porque se genero un nuevo constructor en la clase hija y se quiere utilizar los constructores de la clase padre, no es necesario el super si no se genera un constructor en   la clase hija.
6.En el punto me piden encontrar un error el slots me permite restringir la cantidad de atributos y ahorrar memoria en este caso el slots solo tiene el atributo x por lo que solo se puede crear un atributo x.
   cuando se trata de crear el atributo c.y genera error.
7.En el punto me pide crear un atributo protegido por convencion
   self._x=99
8.El punto 8 consiste la lectura de los datos privados:
   print(hasattr(m, '_step'), hasattr(m, '__tick'), hasattr(m, '_M__tick'))
   En este caso se esta tratando de comprobar que los atributos estan definidos, despues de analizar se comprueba que el hasattr del medio trata de acceder a un metodo privado de forma erronea porque esta            ignorando el name mangling, la salida de este codigo es true, false, true
   la forma de correcta de acceder al metodo es hasattr(m, '_M__tick')
9.Me solicitan  # Accede a __data (solo para comprobar), sin modificar el código de la clase: # Escribe una línea que obtenga la lista usando name mangling y la imprima. Escribe la línea solicitada.
   s = S()
   print(s._S__data)
10.El  nombre mas probable de salir  es _D__a porque hay un for que me recorre todo el dir en donde me muestran los atributos, metodos disponibles y despues hay un if que me muestra los elementos que contengan la letra siguiendo esta logica sale _D__a porque __a solo es posible de acceder a esta forma si es dentro de la clase en la que fue creada y a es la opcion con menos sentido.
11.
class Cuenta:

    def __init__(self, saldo): 
          self._saldo = 0 
          self.saldo = saldo 
   @property
    	    def saldo(self):
          return self._saldo
   @saldo.setter
    	    def saldo(self, valor):
        		  if valor >= 0:
            		  self._saldo = valor
        		  else:
            		  raise ValueError("No puede ser negativo") 
13. En este punto me pedian convertir f en atributo de solo lectura para lograr esto es necesario apoyarme del property  y utilizar la formulada proporcionada para mas tarde remplazar la c en la formula por self._c (Atributo protegido por convecion ) y de esta manera devuelve el valor.

class Termometro:
  def __init__(self, temperatura_c):
    self._c = float(temperatura_c)
  @property
    def temperatura_f(self): 
    return self._c * 9/5 + 32
    
14.
class Usuario:
      def __init__(self, nombre):
        self.nombre = nombre

      @property
      def nombre(self):
        return self._nombre

      @nombre.setter
      def nombre(self, valor):
        if isinstance(valor, str):
            self._nombre = valor
        else:
            raise TypeError("El nombre debe ser texto")
15.
class Registro:
  def __init__(self):
    self.__items = []
  def add(self, x):
    self.__items.append(x)
  @property
  def items(self):
        return tuple(self.__items)

16.  class Motor:
      def __init__(self, velocidad):
        self.velocidad = velocidad

      @property
      def velocidad(self):
        return self._velocidad

      @velocidad.setter
        def velocidad(self, valor):
          if 0 <= valor <= 200:
            self._velocidad = valor
          else:
            raise ValueError("La velocidad debe estar entre 0 y 200")
17. En una API pública de una librería, eligen entre las dos opciones depende del nivel de seguridad que deseo según el programa, usar _atributo indica que es interno y no debería ser accedido por fuera de la clase, es posible utilizarlo cuando quiero proteger un dato pero permitir utilizarlo por ejemplo en una subclase.
Usar __atributo activa el name mangling que renombra al atributo para asegurarlo, esto impide el acceso directo y protege el dato, es recomendable usarlo cuando el atributo contiene información seguro o sensible.
17.Se define una lista protegida por convención (_data), pero el método get_data() la expone directamente permitiendo que cualquier código externo modifique el contenido.
18.El atributo __x está definido como privado en la clase A mediante doble guión bajo. Esto activa el name mangling, que renombra internamente el atributo como _A__x para protegerlo. Por lo tanto, cuando la subclase B intenta acceder a self.__x está mal.
19.class _Repositorio:
    def __init__(self):
        self._datos = {}

    def guardar(self, k, v):
        self._datos[k] = v

    def _dump(self):
        return dict(self._datos)


class Servicio:
    def __init__(self):
        self.__repo = _Repositorio()  # Composición con atributo privado

    def guardar(self, clave, valor):
        self.__repo.guardar(clave, valor)  # Fachada: delega sin exponer

20.class ContadorSeguro:
    	def __init__(self):
        		self._n = 0  # atributo protegido

    	def inc(self):
        		self._n += 1         
        		self.__log()         

    	@property
    	def n(self):
        		return self._n     

    	def __log(self):
        		print("tick")      


 
