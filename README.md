# taller_Repaso
1. En el primer punto me pregunta que atributos son accesibles desde A y la respuesta correcta fueron:
   A.X, A._y, a._A__z en este caso se este caso se trabaja con atributos publicos, protegidos por convención y privados y los ejemplos anteriores permiten comprender como utilizarlos
2.En el segundo punto me piden la salida de un codigo, se utiliza hasattr que su estructura (a, '__secret') esta siendo mal utilizada porque se esta tratando de acceder a un atributo privado por fuera de la clase de manera incorrecta debido a esto me devolvera falsa, y en el segundo caso se utiliza 'a._A__secret' aplicando de forma correcta el name mangling y devolviendo true.
3. Me solicita responder falso y verdadero:
   El prefijo _ impide el acceso desde fuera de la clase. falso si sigo la estructura objeto._atributo podre acceder a el (como en el ejercicio 1)
   El prefijo __ hace imposible acceder al atributo. falso el doble guion bajo lo convierte en un atributo privado pero eso no significa que no pueda ser utilizado por fuera de la clase si se utiliza bien el name mangling es posible acceder a el como en el ejercicio 1.
   El name mangling depende del nombre de la clase. verdadero una parte fundamental del name mangling es el nombre original porque es uno de los componentes de su estructura, objeto._CLASE__atributo
4.En el 4 punto consiste en lectura del codigo
  En este caso se esta implementado el concepto de heriencia y de subclases, en este caso puntual en el constructor de la primera clase se define un atributo protegido por convencion y se utiliza en la clase hija,    en este caso no hay ningun problema por ser protegido, en el caso puntual de porque no hay un error de acceso es porque dentro de la clase hija hay una funcion que retorna el atributo protegido, en este caso al     final hay un print que muestra el valor retornado en la función reveal.
5.En el punto 5 me piden analizar un codigo a diferencia del anterior, en este se encuentra un atributo privado que impide acceder con su nombre original por fuera de la clase incluyendo las clases hijas, en este     caso puntual se genera un primer atributo privado que adquiere el nombre de self._Base__v (si se quiere acceder a el por fuera de la clase) y en la clase hija se vuelve a crear un atributo privado con el nombre     self.__v en este caso se diferencia con el primero porque un elemento trascendental en el name mangling es el nombre de la clase en que proviene en este caso seria:
  primer objeto privado=self._Base__v y el segundo se puede acceder solo son el self.__v porque esta dentro de la clase en que fue creada, la funcion show me retorna los valores de estos atributos privados y por      esta situacion en el print no se generan errores.
  imprime (2,1)
  En esta situacion se implemento el super porque se genero un nuevo constructor en la clase hija y se quiere utilizar los constructores de la clase padre, no es necesario el super si no se genera un constructor en   la clase hija.
6. En el punto me piden encontrar un error el slots me permite restringir la cantidad de atributos y ahorrar memoria en este caso el slots solo tiene el atributo x por lo que solo se puede crear un atributo x.
   cuando se trata de crear el atributo c.y genera error.
7. En el punto me pide crear un atributo protegido por convencion
   self._x=99
8. El punto 8 consiste la lectura de los datos privados:
   print(hasattr(m, '_step'), hasattr(m, '__tick'), hasattr(m, '_M__tick'))
   En este caso se esta tratando de comprobar que los atributos estan definidos, despues de analizar se comprueba que el hasattr del medio trata de acceder a un metodo privado de forma erronea porque esta            ignorando el name mangling, la salida de este codigo es true, false, true
   la forma de correcta de acceder al metodo es hasattr(m, '_M__tick')
9. Me solicitan  # Accede a __data (solo para comprobar), sin modificar el código de la clase: # Escribe una línea que obtenga la lista usando name mangling y la imprima. Escribe la línea solicitada.
   s = S()
   print(s._S__data)
10. El  nombre mas probable de salir  es _D__a porque hay un for que me recorre todo el dir en donde me muestran los atributos, metodos disponibles y despues hay un if que me muestra los elementos que contengan la letra siguiendo esta logica sale _D__a porque __a solo es posible de acceder a esta forma si es dentro de la clase en la que fue creada y a es la opcion con menos sentido.
