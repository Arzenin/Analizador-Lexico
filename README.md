# Autor:
- Jose Manuel Aranda Gutiérrez
  - Correo electrónico: jomagtr@gmail.com
  - Correo electrónico ugr: jomagtr@correo.ugr.es
  - Grupo: A3

# Analizador Lexico

En este fichero podremos encontrar la documentación completa del proyecto llevado a cabo para la práctica 2 de MC.
Realizar un Analizador Léxico, explicar el objetivo de dicho analizador, su funcionamiento.

Para ello se ha realizado un repositorio en Github con el siguiente enlace: https://github.com/Arzenin/Analizador-Lexico

__Se recomienda__ la visualización de la documentación desde el README.md en el github, ya que por medio de los enlaces se puede llegar más rápido a las partes en las que se esté interesado, sin embargo si se desea se puede tener la casi la misma experiencia visualizandolo tanto desde el README.md como desde el [PDF](Doc/) que o bien se ha obtenido por medio de su envio o bien por su obtención en la carpeta `Doc/` dentro del repositorio de github

# 0. Índice

0. [Índice](#0-índice)
1. [Introducción y Motivación](#1-introducción-y-motivación)
2. [Objetivos](#2-objetivos)
   1. [URL](#21-url)
   2. [IP](#22-ip)
   3. [Aclaraciones Finales](#23-aclaraciones-finales)
3. [Github](#3-github)
   1. [Estructura del Repositorio](#31-estructura-del-repositorio)
      1. [Src](Src/#311src)
      2. [Test](Test/#312test)
      3. [Result](Result/#313result)
   2. [Descarga del Repositorio](#32-descarga-del-repositorio)
      1. [Instalación de Git](#321-instalación-de-git)
      2. [Clonar un Repositorio](#322-clonar-un-repositorio)
4. [Instalación de la Herramienta](#4-instalación-de-la-herramienta)
   1. [Gcc](#41-gcc)
   2. [Flex](#42-flex)
5. [Explicación del Código](#explicación-del-código)
   
# 1. Introducción y motivación 
Este proyecto corresponde a la práctica 2 de la asignatura de MC, en ella se nos pide desarrollar un analizador léxico para el reconocimiento de los patrones que nosostros estimemos oportunos.
En mi caso, he dicidido que este analizador de una entrada extraiga las URL y las IP del tipo IP4, las cuales si o si deben de tener o bien el protocolo HTTP o bien el HTTPS.


Respecto a mis motivos a la hora de la elección de este tipo de analizador léxico vienen dado por varios proyectos y cursos que he realizado a lo largo del año. El proyecto en cuestión fue el 
montaje de un servidor casero, durante la configuración del mismo, debía de conectarme por medio de `ssh` al servidor, sin embargo perdía mucho tiempo buscando la sección de IP dentro de mi router.
Esto me hizo pensar en lo práctico que habría sido tener un programa capaz de extraer del fichero todas las IP y decirme exactamente en que línea se encuentan.Por otro lado la detección de URL viene
dado por diversos cursos que he hecho los cuales me han hecho darme cuenta lo útil que sería obtener un Analizador léxico que te permitiese extraer un URL y clasificarla dependiendo del dominio al
que pertenezca, esto último no es uno de los objetivos que realizaré en esta práctica, sin embargo utilizaré esto como base para expandir el programa que desarrolle.

# 2. Objetivos

## 2.1 URL
Las URL que se detectan deben de tener previas a ellas el protocolo HTTP o HTTPS, sin embargo en este caso se deberá de admitir la __posibilidad__ de que tenga el __subdominio www__ , además de esto
debe de admitir __distintos tipos de dominio de primer nivel__ y siempre deben de haber __almenos uno presente__ , los TLP que admitiría son:
__*.com*__  __*.es*__  __*.org*__  __*.net*__  __*.edu*__  __*.gov*__

## 2.2 IP
Al igual que con las URL debe de tener el protocolo HTTP o HTTPS, se busca tanto __el formato correcto__, como que sea una __IP válida__ es decir que ninguno de sus campos puedes ser mayor a 255 ni un 
número negativo.

## 2.3 Aclaraciones Finales 
Para una mayor sencillez a la hora de comprensión se aceptará que la IP o URL este entre palabras, es decir que si pusiesemos __*Hola12.12.12.3Chao*__ nos extraería la IP 12.12.12.3 , el motivo de esto es
una mejor presentación a la hora de obtener el prompt de salida de forma más clara y concisa, ya que, como veremos más adelante, el __Analizador clasificara tanto las IP como las URL de forma ordenada y nos las devolverá posteriormente__, sin embargo a la hora de [explicar el código](#explicación-del-código) se nos indicarán las modificaciones pertinentes en caso de querer hacer que únicamente nos detectase las IP y URL exactas, es decir o bien estando entre palabras,singnos de puntuación, comienzo de la línea y final de la linea. 

# 3. Github
En este apartado se os explicaría en profundidad todos y cada uno de los apartados relacionados con el repositorio de github, desde la estructura hasta la descarga del propio material del repositorio

## 3.1 Estructura del Repositorio

El repositorio esta compuesto por 3 directorios:

### 3.1.1 Src
Este directorio contiene en si el analizador léxico por el cual obtendremos los requisitos explicados en la sección anterior, el nombre del archivo es [AnalizadorLexico](Src/AnalizadorLexico)

Más adelante en el apartado [explicación del código](#explicación-del-código) se explicará en mayor profundidad el funcionamiento del mismo


### 3.1.2 Test
En este directorio podremos encontrar un fichero llamado [entrada.txt](Test/entrada.txt) por el cual podremos comprobar el correcto funcionamiento del programa.


__Se recomienda encarecidamente su lectura__ ya que al final de este se nos indican los resultados esperados por parte del programa.


### 3.1.3 Result
En el directorio result se almacena una muestra del resultado que deberíamos de obtener en caso de ejecutar el [código](Src/AnalizadorLexico) utilizado el [archivo de entrada](Test/entrada.txt) proporcionado

Este directorio nos será de gran utilidad para poder comprender el formato de la salida que obtendremos previa a la ejecución del analizador léxico


[Volver al Índice](#0-índice)

## 3.2 Descarga del Repositorio
En este apartado se enseñara al usuario a descargar todos los recursos necesarios del repositorio por medio de la [instalación de github](#instalación-de-git) y la [clonación de un repositorio](clonar-un-repositorio) en la máquina desde la que queramos ejecutar el analizador.

### 3.2.1 Instalación de Git
1. Deberemos abrir el terminal
2. Nos aseguraremos de tener todas las dependencias y paquetes actualizados por medio de `sudo apt update` y `sudo apt upgrade`
3. Tras esto ejecutaremos `apt-get install git` por el cual instalaremos git junto a sus dependencias
4. Por último como en el resto de instalaciones ejecutaremos `git --version` para asegurarnos que se ha instalado todo correctamente
   
### 3.2.2 Clonar un Repositorio
Una vez instalado Git deberemos de crear un directorio personalmente recomiendo que creemos uno con el siguiente esquema `/Documents/github` sin embargo esto esto no es obligatorio.

1. Nos dirigiremos al directorio en el que queramos clonar el repositorio
2. Abrimos la terminal en ese directorio
3. Ejecutamos `git clone https://github.com/Arzenin/Analizador-Lexico.git`
4. Ejecutamos `ls` y debería de haber aparecido un nuevo directorio llamado `/Analizador-Lexico`

[Volver al índice](#0-índice)

# 4. Instalación de la Herramienta

En este caso explicaré la instalación de las herramientas en el entorno de programación que se ha utilizado para desarrollarla, es decir, una intalación en la distribución de __Ubuntu 22.04.3 LTS__ utilizando el compilador [gcc](#gcc) y [flex](#flex), dicho esto en los dos siguientes apartados se procederá a explicar la instalación de cada una de las herramientas.

### 4.1 Gcc
1. Abrimos la terminal
2. Comprobamos que todas las dependencias esten actualizadas y en caso de no ser así acutalizamos con `sudo apt update` y `sudo apt upgrade`
3. Descargaremos los paquetes básicos donde van incluido gcc y todas sus librerías con el comando `sudo apt install build-essential`
4. Comprobaremos que se ha descargadado correctamente con el comando `gcc --version`

### 4.2 Flex
1. Abrimos la terminal
2. Comprobamos que todas las dependencias esten actualizadas y en caso de no ser así acutalizamos con `sudo apt update` y `sudo apt upgrade`
3. Ejecutamos el comando `sudo apt-get install flex`
4. Ejecuratemos `flex --version` pasa asegurarnos de que todo se ha instalado correctamente


[Volver al índice](#0-índice)

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
