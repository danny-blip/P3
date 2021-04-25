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
* `sudo apt-get install git fakeroot build-essential ncurses-dev xz-utils libssl-dev bc flex libelf-dev bison`

## ¿Cómo descargar una versión de kernel desde terminal?
* `wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.11.16.tar.xz`

## ¿Cómo extraer el código comprimido del kernel desde terminal?
* `tar xvf linux-5.11.16.tar.xz`

## ¿Cómo configurar el kernel?
###### La configuración del kernel puede ajustarse de la siguiente manera:
* `cd linux-5.11.16`
* `cp -v /boot/config-$(uname -r) .config`
* `make menuconfig`
###### Esto abrirá la ventana de configuración del kernel. En este menú hay opciones de firmware, virtualización, red, sistema de archivos, configuración de memoria, etc.

## ¿Cómo compilar el código del kernel?
* `make`

## ¿Cómo instalar módulos?
* `sudo make modules_install`

## ¿Cómo instalar el kernel?
* `sudo make install`

## ¿Cómo indicarle a la computadora con cuál kernel debe iniciar?
* Para llevar a cabo este paso, es necesario que la USB esté desmontada.
* Descargar un archivo iso de la distribución Linux deseada. Para este caso, se utilizará Kali Linux. Una vez que el archivo esté descargado, se abre la terminal, se cambia al directorio en donde se guardó el archivo `.iso` y se ejecuta el siguiente comando:

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/10a.png "10a")

* Se tardará unos minutos dependiendo de la capacidad de la USB. Finalmente, se debe montar la USB y, en ella, se tendrá lo siguiente:

![alt text](https://github.com/danny-blip/NobleTeam/blob/main/10B.png "10b")

## ¿Cómo verificar el cambio del kernel a partir de consola?
* `uname -mrs`
