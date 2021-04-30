# E3_Repositorio
Evidencia de programación avanzada 

# NOTECE QUE EL CODIGO ESTA ELABORADO EN PHYTON, PARA REMARCAR INSTRUCCIONES AQUI, SE HA USADO ESTE CARACTER (#) PARA HACER REFERENCIA A COMENTARIOS EN EL CODIGO.

# Para esta evidencia se presentaran distintos codigos que se vieron durante la fase, particularmente la evidencia se centra en codigos con formato csv ademas csv - lista.

# 1.-Cree un archivo csv, con nombre "example", agregue a la lista como columnas; first_name, second_name, grade. Ingrese 2 registros.

import csv
myData = [["first_name", "second_name", "grade"],
          ["Alex", "Brian", "A"],
          ["Tom", "Smith", "B"]]

myfile= open("example.csv", "w")
with myfile:
    writer=csv.writer(myfile)
    writer.writerows(myData)
    
print("Archivo completo")


# 2.- Cree un archivo csv, con nombre "contacto", agregue a la lista como columnas; Nombre, Domicilio, Telefono, Correo. Ingrese 5 registros. (funcion Dict)

import csv
with open("contacto.csv","w") as csvfile:
    datos=["Nombre", "Domicilio", "Telefono", "Correo"]
    writer = csv.DictWriter(csvfile, fieldnames=datos)
    
    writer.writeheader()
    writer.writerow({"Nombre": "Ana Cavazos", "Domicilio": "Espigas", "Telefono": "8281181765", "Correo": "anacavazos@gmail.com"})
    writer.writerow({"Nombre": "Tom Rodriguez", "Domicilio": "Valles Cadereyta", "Telefono": "8281346789", "Correo": "tom01kc@gmail.com"})
    writer.writerow({"Nombre": "Nancy Berreles", "Domicilio": "Lopez", "Telefono": "8285678901", "Correo": "nancy78@gmail.com"})
    writer.writerow({"Nombre": "Ulises Chavez", "Domicilio": "Alberos", "Telefono": "8281612354", "Correo": "uliseschavez23@gmail.com"})
    writer.writerow({"Nombre": "Luis Martinez", "Domicilio": "Rioja", "Telefono": "8289876512", "Correo": "luisoyrv@gmail.com"})
    
print("Archivo completo")


# 3.- Con un archivo csv creado previamente, use la funcion "reader", para darle solo dar lectura en la consola.

import csv
with open("example.csv", newline='') as File:
    reader = csv.reader(File)
    for row in reader:
        print(row)
        
        
# 4.- Con un archivo csv creado previamente, use la funcion "reader", "append", para darle solo dar lectura en la consola.

import csv
results=[]
with open("ejemplo.csv") as File:
    reader= csv.DictReader(File)
    for row in reader:
        results.append(row)
        
    print(results)
        

# 5.- convierta un archivo csv a lista.

#import csv
class Contacto:
 def __init__(self,USUARIO, NOMBRE, CORREO):
    self.USUARIO = USUARIO
    self.NOMBRE = NOMBRE
    self.CORREO = CORREO

Contactos = []

with open('contactos.csv', newline='') as archivo_csv:
    lector_csv = csv.reader(archivo_csv, delimiter='|')
    for e in lector_csv:
        Contactos.append(Contacto(e[0],e[1],e[2]))

for o in Contactos:
    print(o.USUARIO)
    print(o.NOMBRE)
    print(o.CORREO)
    
    
# 6.-Lee csv, crea objeto y carga lista.

import csv
import datetime
class Incidente:
    def __init__(self,FECHA,CASOS,MUERTES, PAIS):
        self.FECHA = FECHA
        self.CASOS = CASOS
        self.MUERTES = MUERTES
        self.PAIS = PAIS
        
with open('AnálisisCOVID.csv') as archivo_csv:
    lector_csv = csv.reader(archivo_csv, delimiter='|')
    contador_lineas = 0
 
    lista_incidentes = []
 
    for linea_datos in lector_csv:
        if contador_lineas == 0:
            
            print(f'Los nombres de columna son {", ".join(linea_datos)}')
        else:           
              objeto_temporal = Incidente({linea_datos[0]},{linea_datos[1]},{linea_datos[2]},{linea_datos[3]})
              lista_incidentes.append(objeto_temporal)
 
        contador_lineas += 1
        print(f'Procesadas {len(lista_incidentes)} líneas.')


