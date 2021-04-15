# Juego BattleShip-EstallidoSocial 2019

Juego estilo BattleShip, ambientado en el estallido social del 2019 ocurrido en Chile. (Programado en Java.)

1. Se crea la clase padre "Carro" definiendo los atributos comunes y creando un constructor con todos ellos como parámetros, destacando la coordenada índice de fila y columna dentro de una matriz a partir de la cual se crearán aleatoriamente las instancias de las clases hijas "Kromi", "Caguano" y "Trupalla". Se incorporan métodos get, set y toString.

2. Se crea la clase hija (de Carro) "Kromi" con atributos particulares, los cuales se añaden a su constructor, el cual hereda los atributos de la "super", además se sobrescribe el toString para que muestre todos los atributos, se incorporan métodos get y set para todos los atributos.

3. Se crea la clase hija (de Carro) "Caguano" con atributos particulares, los cuales se añaden a su constructor, el cual hereda los atributos de la "super", además se sobrescribe el toString para que muestre todos los atributos, se incorporan métodos get y set para todos los atributos.

4. Se crea la clase hija (de Carro) "Trupalla" con atributos particulares, los cuales se añaden a su constructor, el cual hereda los atributos de la "super", además se sobrescribe el toString para que muestre todos los atributos, se incorporan métodos get y set para todos los atributos.

5. Para "derribar" los objetos tipo Carro se crea la clase "Huevo", quienes se ubicarán en la misma matriz necesitándose también una coordena de la intersección de una fila y columna, y si se cumplen ciertas condiciones recibirán un dato int como puntaje, estos tres atributos se consideraron para la creación de su constructor.

6. Se crea la clase "Libreria" del tipo RandomData para otorgar valores a los atributos de tipo String de los objetos Carro, para ello se crean en esta clase atributos de tipo arreglos con los distintos tipos de información, luego se accede a ellos por métodos que retornan un String, como rellenarFechaIngreso(), rellenarMarca(), rellenarAnoFabricacion(), rellenarColorConfeti(), en los cuales se selecciona un dato de sus respectivas listas según un Math.random(), a excepción de rellenarNombreConductor(int indice) que returna el String de manera secuencial para que en particular este valor no se repita.

7. Se crea la clase "Tablero" para crear todo el entorno del Simulador.

7.1) Se instancia un objeto de la clase "Libreria" para poder acceder a los datos registrados en ella.

7.2) Para poder instanciar los 18 objetos de tipo "Carro" se crea como atributo un arreglo denomindado "carrots" de longitud delimitada por la cte. MAXIMO_CARROS.

7.3) Para poder instanciar los objetos ilimitados de tipo "Huevo" se crea comno atributo un ArrayList denomindado "huevazos".

7.4) Se crea como atributo la matriz bidimensional "cuadricula" de ancho y largo delimitados por la cte. TAMANO_CUADRICULA, en la cual se dispondran los 18 objetos "Carro" segun su coordenana indice. Apareceran en ella las iniciales "K", para los objetos "Kromi", "C", para los objetos "Caguano" y "T" para los objetos "Trupalla", que son clases heredadas de "Carro". Esta matriz solo se mostrará si el usuario lo desea, pero en ella también se irán alojando los objetos "Huevo" guardados en el ArrayList "huevazos", por lo que ha medida que transcurre el juego se irán mostrando también letras "H".

7.5) Se crea como atributo la matriz bidimensional "cuadriculaHuevos" también de ancho y largo delimitados por la cte. TAMANO_CUADRICULA, esta es la que se mostrará al usuario por defecto y en la cual sólo se irán mostrando las celdas en la cual se ha guardado un objeto "Huevo" con una letra "H".

7.6) Se crea el constructor de la clase "Tablero" con los 4 atributos antes mencionados.

7.7) Se crea un método público "crearCarros()", en el cual en primera instancia se asginan espacios vacíos a las matrices "cuadricula" y "cuadriculaHuevos", luego en tres ciclos for se van instanciando los objetos "Kromi", "Caguano" y "Trupalla" los que por polimorfismo se van almacenando en el arreglo "carrots" que fue definido anteriormente para almacenar objetos de la clase "Carros". El primer ciclo for permite almacenar las 3 "Kromi" en las posiciones 0,1,2, luego el siguiente for los 5 "Caguano" en las posiciones 3,4,5,6,7, y el otro for las 10 "Trupalla" en las posiciones 8,9,10...18. Para buscar la coordenada en la cual agregar un carrots[i] se genera un loop do while, el cual en su interior se generan asginaciones de numeros enteros de las variables coordenadaFila y coordeanaColumna que se generan aleatoriamente con los respectivos metodos privados crearNumeroFila y crearNumeroColumna de la clase "Tablero", que reciben como parametros o la longitud del arreglo bidimensional "cuadricula" o de ser el caso los limites MAX_RANDOM_FILA_KROMI o MAX_RANDOM_COLUMNA_CAGUANO. El do while generará coordenadas aleatorias simpre que una de las 3(Kromi), 2(Caguano) o 1 (Trupalla) posiciones del arreglo "cuadricula" no tengan un espacio vacio"". Una vez que se consigue el conjunto de coordenadas (dependiendo del carro) en las cuales hay un esapcio vacio "" dentro de la matriz "cuadricula" se puede proseguir con la instanciación del objeto "Kromi"o "Caguano" o "Trupalla" con su respectivo constructor dentro del arreglo carrots[i]. Finalmente se añade la letra correspondiente al tipo de carro en las celdas necesarias dentro de la matriz "cuadricula" (la que no se mostrara por defecto al usuario).

7.8) Se crea el metodo publico "lanzarHuevos" el cual debe recibir como parametros del usuario dos int correspondientes a la columna y fila en donde desea insertar su "Huevo" a la matriz "cudriculaHuevos". Se parte con la condicionante de que si el usuario ingresa un numero menor a 1 y mayor a 15, debera volver a ingresar los datos, pues no son coordenadas de la matriz. En este metodo si una posicion de la matriz "cuadricula" tiene un "" , se le asignara a dicha posicion una letra "H" a esta matriz y tambien a la matriz "cuadriculaHuevos" y a la vez se instanciara un nuevo objeto "Huevo" dentro del ArrayList "huevazos" con pountaje igual a 0. Cuando se encuentre una "K" dentro de la matriz "cuadricula" se realizaran los mismos procesos anteriores pero el nuevo "Huevo" instanciado tendra puntaje igual a 3 para "C" puntaje 2 y para "T" puntaje 1.

7.9) Se crea el metodo público "mostrarMatriz" el cual debe recibir como parametros cual de las dos matrices creadas se van a mostrar dependiendo del menu del simulador. Se utiliza el comando System.out.printf para darle formato definiendo anchos de los datos dentro de la cuadricula, ademas agrega guias en los 4 lados con los numeros de las filas y columnas. Finalmente solo para la matriz "cuadriculaHuevos" se invocan los metodos privados calcularPuntajes(),calcularBonus(), "kromisDerribadas()", "caguanosDerribadas()" y "trupallasDerribadas()" para añadirlos abajo de la cuadricula mostrada por pantalla y se realiza la suma de carros derribados para indicarle al usuario si ha ganado el juego.

7.10) Se crea el metodo público "mostrarInfoCarros" el cual con un ciclo for recoorre el largo del arreglo "carrots[i]" e imprime el toString correspondiente a cada "Carro" creado.

7.11) Se crea el metodo privado "calcularPuntajes()" el cual retorna un int con la suma de los puntajes obtenidos por cada instancia de "Huevo" agregando al contador score con un for each para el ArrayList "huevazos" el atributo con get.puntaje.

7.12) Se crea el metodo privado "calcularBonus()" en el cual se definen en variables los puntos que se ganaran por derribar a una "Kromi" y a un "Caguano". Se busca mediante ciclos for si en las posiciones de la matriz "cuadricula" con la fila y columna obtenidas desde los atributos de los carrots[i] mediante el metodo get hay 3 letras "H" juntas para "Kromi" y 2 "H" para caguano, de ser asi se sumaran 10 y 7 puntos respectivamente al contador "bonus", el cual finalmente se mostrara por pantalla.

7.13) Se crean los metodos privados "kromisDerribadas()", "caguanosDerribadas()" y "trupallasDerribadas()" los cuales repiten el esquema de busqueda de coincidencias de letras "H" del metodo "calcularBonus()" segun las coordenadas de cada uno de los carrots[i] y entrega un contador de las instancias de carro derribadas.

7.14) Se crean los metodos privados crearNumeroColumna y crearNumeroFila para generar coordenadas aletorias utilizadas en el metodo "crearCarros()".

8.En la clase ejecutable lo primero que se hace es instanciar un objeto de la clase "Tablero" para poder utilizar sus metodos. Luego se invoca al metodo "crearCarros()" y dentro de un do while y mediante un switch se crea el menu a desplegar en pantalla. De forma repetitiva se ira mostrando la matriz "cuadriculaHuevos" mediante la invocacion del metodo "mostrarMatriz" (con su parametro cuadricula obtenida con get desde "Tablero") y el MENU en la parte posterior. Mediante el uso de un try catch el usuario solo podra ingresar numeros enteros tanto al momento de seleccionar la opcion del menu, como al momento de seleccionar la fila o columna para lanzar un huevo. Con la opcion 1 del menu se iran agregando y mostrando los huevos y la opcion 2, se podra acceder a la matriz "cuadricula" con las posiciones de los carros, los huevos agregados hasta el momento y tambien la informacion de los atributos de cada carro.
