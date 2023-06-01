# Textico.reto-12
Exportar el archivo a un terminar y luego leer y usar los diferentes métodos para hallar lo indicado.
## Primer punto:
- Consulte que hacen los siguientes métodos de strings en python: endswith, startswith, isalpha, isalnum, isdigit, isspace, istitle, islower, isupper.
#### endswith: ###
- Se utiliza para determinar si una cadena termina con el sufijo especificado.
#### Starswith: 
- Se utiliza para comprobar si la cadena se especifica sub-cadena al principio, si se devuelve True, de lo contrario False.
#### isalpha:
- Se utiliza para detectar la cadena se compone de sólo letras. gramática.
#### isalnum: 
- Se utiliza para detectar una cadena de letras y números. gramática.
#### isdigit: 
- Se utiliza para detectar una cadena que consta de sólo números. gramática.
#### isspace: 
- Se utiliza para detectar la cadena se compone de sólo espacios. gramática
#### istitle: 
- Se utiliza para detectar todas las palabras estén escritas cadena es una primera letra mayúscula y otras letras en minúsculas. gramática.
#### islower: 
- Se utiliza para detectar la cadena consiste en letras minúsculas. gramática
#### isupper: 
- Se utiliza para detectar si una cadena de todas las letras aparecen en mayúsculas. gramática.
## Segundo punto:
1. Procesar el <a href="https://drive.google.com/file/d/1lGmlAz157fIDp2zk95KInTSJguZusI91/view?usp=sharing">archivo</a> y extraer:
 - Cantidad de vocales:
 ```
 Cantidad_vocales = [0, 0, 0, 0, 0]
 def contar_vocales(archivo): # creamos la función para contar las vocales
    # Leer el archivo de texto
    with open(archivo, 'r') as archivo_texto:
        texto =archivo_texto.read()
with open("archivito.txt") as archivo_texto:
    for line in archivo_texto: #para cada linea en el archivo de texto
        line = line.lower()  # Se convierte la linea a minúscula
        print(line)#actualiza la linea
        Cantidad_vocales[0] += line.count("a") #se cuenta la cantidad de "a" y se almacena la cantidad en el primer indice de la lista
        Cantidad_vocales[1] += line.count("e")#se cuenta la cantidad de "e" y se almacena la cantidad en el segundo indice de la lista
        Cantidad_vocales[2] += line.count("i")#se cuenta la cantidad de "i" y se almacena la cantidad en el tercero indice de la lista
        Cantidad_vocales[3] += line.count("o")#se cuenta la cantidad de "o" y se almacena la cantidad en el cuarto indice de la lista
        Cantidad_vocales[4] += line.count("u")#se cuenta la cantidad de "u" y se almacena la cantidad en el quinto indice de la lista

    print("Cantidad de a:", Cantidad_vocales[0], "\n", "Cantidad de e:", Cantidad_vocales[1], "\n", "Cantidad de i:", Cantidad_vocales[2], "\n", "Cantidad de o:", Cantidad_vocales[3], "\n", "Cantidad de u:", Cantidad_vocales[4] )
 ```
 - Cantidad de consonantes:
 ```
 Cantidad_consonantes = 0    #inicializamos la variable consonates en 0
def contar_consonantes(archivo): # creamos la función para contar las consonantes
        # Leer el archivo de texto
    with open(archivo, 'r') as archivo_texto:
        texto =archivo_texto.read()
with open("archivito.txt") as archivo_texto:
    for line in archivo_texto: # para cada linea del texto
        line = line.lower()  # Se convierte la linea a minúscula
        print(line) # se actualiza la linea
        for char in line: #para cada caracter en linea
            if char not in "aeiou" and char.isalpha(): # si el caracter no es ninguna vocal y es un caracter para eso se usa "isalpha"
                Cantidad_consonantes += 1 # se le suma 1 a la cantidad de consonates
    print("Cantidad de consonantes:", Cantidad_consonantes)
 ```
 - Listado de las 50 palabras que más se repiten:
 ```
 def lista_repeticiones(archivo): # creamos una función para la lista de las palabras mas repetidas
    # Leer el archivo de texto
    with open(archivo, 'r') as archivo_texto:
        texto= archivo_texto.read()
with open("archivito.txt") as archivo_texto:
    for line in archivo_texto: # para cada linea del archivo
        line = line.lower()  # Se convierte la linea a minúscula
        print(line)
        Temporal = line.split()  # Se almacenan las palabras de cada linea, separas por el metodo split
        print(Temporal)
        for palabra in Temporal: # para cada palabra almacenada en temporal
            if palabra.endswith(tuple(Listasde_nodeseados)): # si la palabra termina en alguno de lo elementos no deseados
                palabra = palabra.rstrip(palabra[-1]) # eliminar ese elemento no deseado
            if palabra.startswith(tuple(Listasde_nodeseados)): # si la palabra comenzaba con alguno de lo elementos no deseados
                palabra = palabra.lstrip(palabra[0])# eliminar el elemento no deseado
            if palabra not in Palabras: # si la palabra no esta en el diccionario iniciar la variable
                Palabras[palabra] = 1
            else: # de lo contrario sumar una cantidad al elemento
                Palabras[palabra] += 1
        palabras_ordenadas = sorted(Palabras, key=Palabras.get, reverse=True) # ordenamos las palabras segun el valor de cada una
    print(palabras_ordenadas[:50])#usamos slicing para imprimir en una lista las primeras 5o palabras mas repetidas
 ```
 - Listado de destinatarios con cantidad de mensajes recibidos
 - Cantidad de mensajes enviados por cada día
 
