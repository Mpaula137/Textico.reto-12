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

def contar_vocales(archivo):
    global Cantidad_vocales  # Declarar la lista como una variable global

    with open(archivo, 'r') as archivo_texto:
        texto = archivo_texto.read()

    for line in texto.splitlines(): # Divide el texto en lineas individuales 
        line = line.lower() # Convierte cada linea en minusculas
        print(line) 
        Cantidad_vocales[0] += line.count("a")
        Cantidad_vocales[1] += line.count("e")
        Cantidad_vocales[2] += line.count("i")
        Cantidad_vocales[3] += line.count("o")
        Cantidad_vocales[4] += line.count("u")

    print("Cantidad de a:", Cantidad_vocales[0])
    print("Cantidad de e:", Cantidad_vocales[1])
    print("Cantidad de i:", Cantidad_vocales[2])
    print("Cantidad de o:", Cantidad_vocales[3])
    print("Cantidad de u:", Cantidad_vocales[4])

# Llamar a la función con el archivo deseado
contar_vocales("archivito.txt")


 ```
 - Cantidad de consonantes:
 ```
Cantidad_consonantes = 0  # Inicializamos la variable consonantes en 0

def contar_consonantes(archivo):
    global Cantidad_consonantes  # Declarar la variable como global para poder modificarla dentro de la función

    with open(archivo, 'r') as archivo_texto: #Abrir y leer el texto
        texto = archivo_texto.read()

    for line in texto.splitlines():  # divide el texto por lineas
        line = line.lower()# convierte el texto en minusculas
        print(line)
        for char in line: #Para cada caracterter en la linea
            if char not in "aeiou" and char.isalpha():#si no es vocal y es caracter
                Cantidad_consonantes += 1# sumar a la cantidad de consonantes

    print("Cantidad de consonantes:", Cantidad_consonantes)

# Llamar a la función con el archivo deseado
contar_consonantes("archivito.txt")
 ```
 - Listado de las 50 palabras que más se repiten:
 ```
Palabras = {}
Listasde_nodeseados = [",", ".", ";", ":", "-", "_", "/", "?", "!", "#", "<", ">", "(", ")", "{", "}", "]", "[", "\"", "\'"]

def lista_repeticiones(archivo): # Abrir archivo
    with open(archivo, 'r') as archivo_texto:
        texto = archivo_texto.read()

    for line in texto.splitlines(): #separa el texto en lineas
        line = line.lower()# convierte el texto en minusculas
        Temporal = line.split() # en la variable temporal divide por palabras cada linea

        for palabra in Temporal:
            if palabra.endswith(tuple(Listasde_nodeseados)): # si termina en lista de no desados
                palabra = palabra.rstrip(palabra[-1])# se elimina el no deseado
            if palabra.startswith(tuple(Listasde_nodeseados)):# si empieza en lista de no deseados
                palabra = palabra.lstrip(palabra[0])# se elmina el no deseado
            if palabra not in Palabras: #si la palabra no es esta en palabras
                Palabras[palabra] = 1# queda en uno
            else:
                Palabras[palabra] += 1#si la palabra si esta almacenada se suma uno a la variable

    palabras_ordenadas = sorted(Palabras, key=Palabras.get, reverse=True) #Se ordenan segun el valor de cada palabra
    print(palabras_ordenadas[:50]) # el slicing permite que solo se muestren las primeros 50 palabras

# Llamar a la función con el archivo deseado
lista_repeticiones("archivito.txt")
 ```
 - Listado de destinatarios con cantidad de mensajes recibidos:
 ```
 def destinatarios_mensanjes(archivo):
    cuenta_destinatarios = {}  # Diccionario para almacenar los destinatarios y la cantidad de mensajes recibidos
    
    with open(archivo, 'r') as archivo_texto:
        for line in archivo_texto:  # recorrer cada linea del texto
            linea = line.strip()  # usar la función strip para eliminar los espacios al principio y al final de la línea
            if linea.startswith("To:"):
                destinatario = linea[4:].strip()  # extraer el destinatario eliminando el prefijo "To:"
                cuenta_destinatarios[destinatario] = cuenta_destinatarios.get(destinatario, 0) + 1  # actualizar el diccionario
    
    print("Listado de destinatarios con cantidad de mensajes recibidos:")
    for destinatario, cuenta in cuenta_destinatarios.items():
        print(f"{destinatario}: {cuenta} mensajes")

# Llamar a la función con el archivo deseado
destinatarios_mensanjes("archivito.txt")

 ```
 - Cantidad de mensajes enviados por cada día
 ```
 def mensajes_diarios(texto: str) -> dict:
    mensajes_rec = []  # Lista para almacenar los segmentos del texto que contienen información sobre la fecha.
    palabras = texto.split()  # Dividir el texto en palabras individuales utilizando split().

    for i in range(len(palabras)):
        if palabras[i] == "Received:":  # Crear una lista de palabras desde "Received" hasta "(GMT)" o "-0500".
            segmento = []
            while palabras[i] != "-0500" and palabras[i] != "(GMT)":
                segmento.append(palabras[i])
                i += 1
            mensajes_rec.append(segmento)

    men_por_dia = {}  # Diccionario para almacenar el día y el número de mensajes enviados.
    
    for segmento in mensajes_rec:
        indice = segmento.index('Jan')  # Índice de la palabra "Jan".
        dia = int(segmento[indice - 1])  # Extraer el día basado en el índice de "Jan".
        if dia in men_por_dia:
            men_por_dia[dia] += 1
        else:
            men_por_dia[dia] = 1

    return men_por_dia

if __name__ == "__main__":
    with open("archivito.txt", "r") as archivo:
        numero_dia = mensajes_diarios(archivo.read())
        for dia in numero_dia:
            print(f"{numero_dia[dia]} mensajes enviados el {dia} de enero, 2008")
 ```
 ## Ya no puedo mas con este semestre!!
 
