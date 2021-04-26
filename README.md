# Compilación del kernel de Linux

## ¿Cómo hacer un respaldo de una máquina virtual y cómo levantar ese respaldo?

###### Para crear un respaldo de una máquina virtual, esta puede clonarse de la siguiente manera:

* Primero, la máquina virtual debe estar apagada.

![alt text](https://github.com/danny-blip/P3/blob/main/a1.png "a1")

* Dar clic derecho sobre ella y seleccionar la opción «clonar».

![alt text](https://github.com/danny-blip/P3/blob/main/a2.png "a2")

* Se recomiendan las opciones por defecto.

![alt text](https://github.com/danny-blip/P3/blob/main/a3.png "a3")

* Seleccionar la opción «clonación completa».

![alt text](https://github.com/danny-blip/P3/blob/main/a4.png "a4")

* Esperar un momento a que la máquina termine de clonarse. Una vez terminado el proceso, se tendrá una copia de la máquina virtual.

![alt text](https://github.com/danny-blip/P3/blob/main/a5.png "a5")

## ¿Cómo funciona la nomenclatura del kernel?

###### La nomenclatura del kernel se divide en tres partes:

* Número de versión del kernel.
* Número de subversión del kernel.
* Número de parche.

![alt text](https://github.com/danny-blip/P3/blob/main/k1.png "k1")

## ¿Cómo instalar los paquetes requeridos para la compilación del kernel desde terminal?

* `sudo apt-get install git fakeroot build-essential ncurses-dev xz-utils libssl-dev bc flex libelf-dev bison`

![alt text](https://github.com/danny-blip/P3/blob/main/c1.png "c1")

## ¿Cómo descargar una versión de kernel desde terminal?

* `wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.11.16.tar.xz`

![alt text](https://github.com/danny-blip/P3/blob/main/d1.png "d1")

## ¿Cómo extraer el código comprimido del kernel desde terminal?

* `tar xvf linux-5.11.16.tar.xz`

![alt text](https://github.com/danny-blip/P3/blob/main/e1.png "e1")

![alt text](https://github.com/danny-blip/P3/blob/main/e2.png "e2")

## ¿Cómo configurar el kernel?

###### La configuración del kernel puede ajustarse de la siguiente manera:

* `cd linux-5.11.16`

![alt text](https://github.com/danny-blip/P3/blob/main/f1.png "f1")

* `make menuconfig`

###### Esto abrirá la ventana de configuración del kernel. En este menú hay opciones de firmware, virtualización, red, sistema de archivos, configuración de memoria, etc.

![alt text](https://github.com/danny-blip/P3/blob/main/f2.png "f2")

###### En algunas ocasiones, la compilación del kernel fallará debido a una configuración en el archivo .config de la carpeta del kernel. Para solucionar esto, hay que ingresar al archivo y eliminar la línea `CONFIG_SYSTEM_TRUSTED_KEYS`.

![alt text](https://github.com/danny-blip/P3/blob/main/f3.png "f3")

![alt text](https://github.com/danny-blip/P3/blob/main/f4.png "f4")

![alt text](https://github.com/danny-blip/P3/blob/main/f5.png "f5")

## ¿Cómo compilar el código del kernel?

###### Este comando compila el kernel (es un buen momento para ir por un café, ya que esto tomará un buen rato):

* `sudo make`

![alt text](https://github.com/danny-blip/P3/blob/main/g1.png "g1")

## ¿Cómo instalar módulos?

###### Este comando instala los módulos que se han activado.

* `sudo make modules_install`

![alt text](https://github.com/danny-blip/P3/blob/main/h1.png "h1")

## ¿Cómo instalar el kernel?

###### Este comando instala el kernel (de igual manera, tomará un tiempo... es hora de una partidita):

* `sudo make install`

![alt text](https://github.com/danny-blip/P3/blob/main/i1.png "i1")

## ¿Cómo indicarle a la computadora con cuál kernel debe iniciar?

###### Estos comandos habilitan el kernel para el arranque:

* `sudo update-initramfs -c -k 5.11.16`

* `sudo update-grub`

![alt text](https://github.com/danny-blip/P3/blob/main/j1.png "j1")

## ¿Cómo verificar el cambio del kernel a partir de consola?

###### Este comando muestra la versión actual del kernel (es necesario reiniciar la computadora para que se vean los cambios):

* `uname -mrs`

![alt text](https://github.com/danny-blip/P3/blob/main/k1.png "k1")
