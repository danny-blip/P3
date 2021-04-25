# Compilación del kernel de Linux

## ¿Cómo hacer un respaldo de una máquina virtual y cómo levantar ese respaldo?
###### Para crear un respaldo de una máquina virtual, esta puede clonarse de la siguiente manera:
* Primero, la máquina virtual debe estar apagada.
* Dar clic derecho sobre ella y se selecciona la opción «clonar».
* Se recomiendan las opciones por defecto.
* Seleccionar la opción «clonación completa».
* Esperar un momento a que la máquina termine de clonarse.
* Una vez terminado el proceso, se tendrá una copia de la máquina virtual.

## ¿Cómo funciona la nomenclatura del kernel?
###### La nomenclatura del kernel se divide en tres partes:
* Número de versión del kernel.
* Número de subversión del kernel.
* Número de parche.

## ¿Cómo enlistar los paquetes requeridos para la compilación del kernel y cómo instalarlos desde terminal?
*	Ejecutar el comando `lsblk` (este comando proviene de la abreviatura «List Block Devices»).

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/3a.png "3a")

* En la primera columna del enlistado, se tiene un campo llamado «Name», el cual indica el nombre del dispositivo o de la partición.
*	En la segunda columna de la tabla, se tiene un campo llamado «Maj:Min», que se explica a continuación:
1. El término «Maj» hace referencia al término «major».
2. El término «Min» hace referencia al término «minor».
3. Estos términos mencionados anteriormente, es la forma en la cual el Kernel, mediante números enteros, se refiere a los dispositivos de manera interna.
* `lsblk -b` despliega el tamaño de cada dispositivo en bytes, como se puede ver en la imagen, a comparación de la imagen anterior, en el campo «»size» ya no existe la presencia de letras M, ya que los despliega en bytes.

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/3b.png "3b")

* `lsblk -d` Imprime los dispositivos de bloque titulares y no las particiones, como puede observarse en la imagen, no se muestran las particiones de `sda`.

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/3c.png "3c")

* `lsblk -m` muestra la tabla en donde se observan los diversos permisos que tiene los dispositivos de bloque en el enlistado.

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/3d.png "3d")

* Abajo de los del campo anteriormente mencionado, se tiene un formato de números de la siguiente manera: 7:1. La cual se explica a continuación:
1. El primer número del formato hace alusión al tipo de dispositivo que es, si se tiene un disco SCSI, se le asigna el número 8 y, en caso de que sean discos IDE, se les asigna el número 3; a los discos ópticos se les asigna el número 11, para los disquetes es el número 2, `/dev`, `/null` y `/zero` se les asocia el número 1, a consolas virtuales y terminales se les asocia el número 4 y, a los dispositivos `vcs1` y `vcsa1`, se les asocia el número 7.
2. El segundo número especifica al dispositivo qué hay dentro del primer número.
*	En el tercer campo de la tabla que tiene como nombre «RM» hace alusión a si es extraíble. En caso de que sea extraíble, se despliega un 1, en caso contrario, se despliega un 0.
*	En el quinto campo de la tabla se hace referencia a si es solo lectura, en caso de que sea solo lectura, se despliega un 1, en caso contrario, se despliega un 0.
*	En el sexto campo de la tabla se hace referencia a qué tipo de dispositivo es. Dentro de estos puede haber muchos, como por ejemplo:
1. disk: unidad de almacenamiento.
2. part: partición del disco.
3. loop: un pseudodispositivo que permite que un dispositivo sea accesible como un dispositivo de bloque.
* En el último campo de la tabla se hace referencia al punto de montaje de cada partición o del dispositivo de bloques.
* Dentro de este comando, hay ciertas variaciones, las cuales se explican a continuación:
1. `lsblk -a` despliega los dispositivos vacíos, como se puede observar en la imagen, se puede ver que, en la parte de «NAME», hay un campo llamado «loop 7», el cual no aparece en la imagen anterior.

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/3e.png "3e")

2. `lsblk -o` muestra la tabla de los dispositivos de bloque de manera personalizada. En este ejemplo, se desplegará el nombre y el tamaño. Como puede verse en el ejemplo a continuación, se tiene que escribir el comando que está escrito al principio de la viñeta. Después, se deja un espacio y se escriben los nombre de las columnas que se desean que aparezcan; si es más de un elemento, van separados por comas.

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/3f.png "3f")

## ¿Cómo descargar una versión de kernel desde terminal?
* Primero, se deben tener privilegios de súper usuario:
1. `sudo su`
2. Ingresar la contraseña, la cual es la que se utiliza para acceder al equipo.
3. Ingresar el comando `fdisk -l`, el cual mostrará la siguiente información:

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/4a.png "4a")

* Lo que se acaba de hacer con este comando, es acceder a los enlistados de los discos duros, la que se busca en este caso es la siguiente:

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/4B.png "4b")

* Lo primero que se muestra en la imagen es el disco en donde está instalado el sistema operativo, si se observa en la parte de abajo, hay una tabla, esa es la tabla de particiones del sistema operativo.
* En caso de que no hubiese tabla, quiere decir que no hay particiones en ese disco.
* Para poder salir, solo se coloca el comando exit para salir del modo super usuario.
## ¿Cómo extraer el código comprimido del kernel desde terminal?
###### Para mostrar las tablas de particiones, se utiliza el siguiente comando:
* `sudo fdisk -l`

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/5a.png "5a")

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/5b.png "5b")

## ¿Cómo configurar el kernel?
* Para llevar a cabo este paso, es necesario que la USB esté desmontada.
* Ejecutar `sudo fdisk /dev/sdb`.
* Ejecutar `d` (delete) para borrar una partición.
* Introducir el número de partición a borrar. Si solo se tiene una, se seleccionará y se borrará de manera automática.
* Reperir para las particiones que se deseen borrar.
* Ejecutar `p` para ver los cambios realizados.
* Ejecutar `w` para guardar los cambios y salir.
* Ejecutar `q` para salir sin guardar los cambios.

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/6a.png "6a")

## ¿Cómo compilar el código del kernel?
* Para llevar a cabo este paso, es necesario que la USB esté desmontada.
* Ejecutar `sudo fdisk /dev/sdb`.
* Ejecutar `n` (new) para crear una nueva partición.
* Introducir el tipo de partición («p» para primaria y «e» para extendida).
* Introducir el número de partición (se recomienda el valor por defecto).
* Introducir el punto de partida (se recomienda el valor por defecto).
* Introducir el tamaño de la partición, por ejemplo, «+1024M» para 1 GB.
* Repetir para las otras dos particiones físicas y una vez más para la extendida (para esta, se introduce «e» en el tipo de partición).
* Ejecutar `p` para ver los cambios realizados.
* Ejecutar `w` para guardar los cambios y salir.
* Ejecutar `q` para salir sin guardar los cambios.

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/7a.png "7a")

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/7b.png "7b")

## ¿Cómo instalar módulos?
* Para llevar a cabo este paso, es necesario que la USB esté desmontada.
* Se necesitan 3 particiones físicas y una partición extendida.
* Ejecutar `sudo fdisk /dev/sdb`.
* Ejecutar `n` (new) para crear una nueva partición.
* Automáticamente se creará una partición lógica dentro de la extendida seleccionada.
* Introducir el punto de partida (se recomienda el valor por defecto)
* Introducir el tamaño de la partición, por ejemplo, «+512M» (debe ser menor al tamaño de la partición que la contiene).

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/8a.png "8a")

## ¿Cómo instalar el kernel?
* Para llevar a cabo este paso, es necesario que la USB esté desmontada.
* Abrir la aplicación Discos en Ubuntu.

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/9a.png "9a")

* Seleccionar la partición a borrar y dar clic en el ícono de «-».

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/9b.png "9b")

* Eliminar la partición.

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/9c.png "9c")

* Repetir con todas las demás particiones, excepto la uno. Una vez que se tenga solo la primera partición, se selecciona y se da clic en ícono del engranaje.

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/9d.png "9d")

* Seleccionar la barrita de «tamaño actual» y arrastratla toda hacia la derecha para utilizar todo el almacenamiento para esa partición.

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/9e.png "9e")

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/9f.png "9f")

* ¡Y listo!

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/9g.png "9g")

## ¿Cómo indicarle a la computadora con cuál kernel debe iniciar?
* Para llevar a cabo este paso, es necesario que la USB esté desmontada.
* Descargar un archivo iso de la distribución Linux deseada. Para este caso, se utilizará Kali Linux. Una vez que el archivo esté descargado, se abre la terminal, se cambia al directorio en donde se guardó el archivo `.iso` y se ejecuta el siguiente comando:

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/10a.png "10a")

* Se tardará unos minutos dependiendo de la capacidad de la USB. Finalmente, se debe montar la USB y, en ella, se tendrá lo siguiente:

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/10B.png "10b")

## ¿Cómo verificar el cambio del kernel a partir de consola?
