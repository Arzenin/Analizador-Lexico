# Analizador-Lexico

En este repositorio podremos encontrar el analizador léxico realizado para las practicas de la asignatura de MC.

## Índice
- [Índice](#índice)
- [Estructura del Repositorio](#estructura-del-repositorio)
   - [Src](Src/)
   - [Test](Test/)
   - [Result](Result/)
- [Descarga del Repositorio](#descarga-del-repositorio)
   - [Instalación de Git](#instalación-de-git)
   - [Clonar un Repositorio](#clonar-un-repositorio)
- [Instalación de la Herramienta](#instalación-de-la-herramienta)
   - [Gcc](#gcc)
   - [Flex](#flex)
- [Explicación del Código](#explicación-del-código)

## Estructura del Repositorio

El repositorio esta compuesto por 3 directorios:

### Src
Este directorio contiene en si el analizador léxico por el cual obtendremos los requisitos explicados en la sección anterior, el nombre del archivo es [AnalizadorLexico](Src/AnalizadorLexico)

Más adelante en el apartado [explicación del código](#explicación-del-código) se explicará en mayor profundidad el funcionamiento del mismo


### Test
En este directorio podremos encontrar un fichero llamado [entrada.txt](Test/entrada.txt) por el cual podremos comprobar el correcto funcionamiento del programa.


__Se recomienda encarecidamente su lectura__ ya que al final de este se nos indican los resultados esperados por parte del programa.


### Result
En el directorio result se almacena una muestra del resultado que deberíamos de obtener en caso de ejecutar el [código](Src/AnalizadorLexico) utilizado el [archivo de entrada](Test/entrada.txt) proporcionado

Este directorio nos será de gran utilidad para poder comprender el formato de la salida que obtendremos previa a la ejecución del analizador léxico


[Volver al Índice](#índice)

## Descarga del Repositorio
En este apartado se enseñara al usuario a descargar todos los recursos necesarios del repositorio por medio de la [instalación de github](#instalación-de-git) y la [clonación de un repositorio](clonar-un-repositorio) en la máquina desde la que queramos ejecutar el analizador.

# Instalación de Git
1. Deberemos abrir el terminal
2. Nos aseguraremos de tener todas las dependencias y paquetes actualizados por medio de `sudo apt update` y `sudo apt upgrade`
3. Tras esto ejecutaremos `apt-get install git` por el cual instalaremos git junto a sus dependencias
4. Por último como en el resto de instalaciones ejecutaremos `git --version` para asegurarnos que se ha instalado todo correctamente
   
# Clonar un Repositorio
Una vez instalado Git deberemos de crear un directorio personalmente recomiendo que creemos uno con el siguiente esquema `/Documents/github` sin embargo esto esto no es obligatorio.

1. Nos dirigiremos al directorio en el que queramos clonar el repositorio
2. Abrimos la terminal en ese directorio
3. Ejecutamos `git clone https://github.com/Arzenin/Analizador-Lexico.git`
4. Ejecutamos `ls` y debería de haber aparecido un nuevo directorio llamado `/Analizador-Lexico`

[Volver al índice](#índice)

## Instalación de la Herramienta

En este caso explicaré la instalación de las herramientas en el entorno de programación que se ha utilizado para desarrollarla, es decir, una intalación en la distribución de __Ubuntu 22.04.3 LTS__ utilizando el compilador [gcc](#gcc) y [flex](#flex), dicho esto en los dos siguientes apartados se procederá a explicar la instalación de cada una de las herramientas.

### Gcc
1. Abrimos la terminal
2. Comprobamos que todas las dependencias esten actualizadas y en caso de no ser así acutalizamos con `sudo apt update` y `sudo apt upgrade`
3. Descargaremos los paquetes básicos donde van incluido gcc y todas sus librerías con el comando `sudo apt install build-essential`
4. Comprobaremos que se ha descargadado correctamente con el comando `gcc --version`

### Flex
1. Abrimos la terminal
2. Comprobamos que todas las dependencias esten actualizadas y en caso de no ser así acutalizamos con `sudo apt update` y `sudo apt upgrade`
3. Ejecutamos el comando `sudo apt-get install flex`
4. Ejecuratemos `flex --version` pasa asegurarnos de que todo se ha instalado correctamente


[Volver al índice](#índice)

## Explicación del Código

```c
protocolo_inseguro      ("http://"|" http://")
protocolo_seguro        ("https://"|" http://")
dominio                 (("www.")?[a-zA-Z\.]+\.("com"|"es"|"org"|"net"|"edu"|"gov"))
ipv4                    ([0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3})
url_dominio_seguro      ({protocolo_seguro}{dominio})
url_dominio_inseguro    ({protocolo_inseguro}{dominio})
ip_seguro               ({protocolo_seguro}{ipv4})
ip_inseguro             ({protocolo_inseguro}{ipv4})

%{
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    int numurl=0,numprotocolo_inseguro=0,numline=1,numword=0;
    int numprotocolo_seguro=0,numdominio=0,numipv4=0,numchar=0;
    char* ip_s = NULL;
    char* ip_u = NULL;
    char* dom_s = NULL;
    char* dom_u = NULL;
    
%}

```
