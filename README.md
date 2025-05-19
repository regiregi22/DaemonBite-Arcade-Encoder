# NOTAS REGI:

## -DEBOUNCE:
He modificado el archivo "DaemonBiteArcadeEncoder/DaemonBiteArcadeEncoder.ino" para ponerle el debouce de 0 a 1, y subirle el tiempo de 10ms a 20ms (haciendo pruebas de velocidad de pulsacion en ningun caso he logrado bajar de 30ms, siendo la media minima unos 60ms (120ms el ciclo entero). Con los botones IL no afectaba, con los Sanwa en principio tampoco, pero los Qanba tenian mucho bouncing y pulsaciones fantasma.  
#define DEBOUNCE 1          // 1=Diddly-squat-Delay-Debouncing™ activated, 0=Debounce deactivated. Soy Regi, lo activo en 1.  
#define DEBOUNCE_TIME 20    // Debounce time in milliseconds. Soy Regi, lo subo de 10 a 20ms.  

Ver aqui para mas info:  
https://x.com/MisterAddons/status/1299887953410392064  


## -GRABAR EN ARDUINO IDE (Grabar un "Arduino Pro Micro"):  
SparkFun distributed their own "SparkFun AVR Boards" platform with a "Pro Micro" board definition. Alternatively, you can select Tools > Board > Arduino AVR Boards > Arduino Micro. That is intended for use with the Micro board, but will also work with the Pro Micro in a pinch.  
This is the correct procedure: https://learn.sparkfun.com/tutorials/pro-micro--fio-v3-hookup-guide/all#installing-windows  

=After installing that, Arduino IDE Settings:  
-COM Port  
-SparkFun AVR Board/Sparkfun Pro Micro  
-Processor: 5V/16Mhz  



## -BOARD USB NAME: 
-Para cada placa de Arduino Micro, le he puesto un nombre diferente, el cual se modifica en el fichero "C:\Users\Regi-Portatil\AppData\Local\Arduino15\packages\arduino\hardware\avr\1.8.6\boards.txt". Hay que buscar la linea "micro.name=Arduino Micro" y ahi cambiar los parametros micro.build.usb_product= y micro.build.pid= para cada placa diferente.

(default)  
micro.build.pid=0x8037  
micro.build.usb_product="Arduino Micro"  

micro.build.pid=0x8038  
micro.build.usb_product="DaemonBite 1"  

micro.build.pid=0x8039  
micro.build.usb_product="DaemonBite 2"  

micro.build.pid=0x8040  
micro.build.usb_product="DaemonBite 3"  


(Esta info anterior está obsoleta, esta hecha sin usar el pack de "Sparkfun" de placas. En el caso actual, es lo mismo pero esta ruta: C:\Users\regir\AppData\Local\Arduino15\packages\SparkFun\hardware\avr\1.1.13  

promicro.build.usb_product="SparkFun Pro Micro"  
promicro.build.vid=0x1b4f  

promicro.build.usb_product="DaemonBite 3DO"  
promicro.build.vid=0x1b5f  


## A PARTIR DE AQUI, YA ES EL CODIGO ORIGINAL DEL DAEMONBITE:
# DaemonBite-Arcade-Encoder
This is an arcade controller project for the MiSTer FPGA project and any other device accepting USB HID joysticks using an Arduino Pro Micro. This project can also be used to create a NeoGeo/Atari/Commodore/Amiga controller to USB adapters.

This project is an open source "lite" version of an arcade encoder I sell in my shop. If you want to support my work I sell the fully featured ones at https://daemonbite.com.

The input lag for an arcade controller or adapter built around this project is minimal. Here is the result from a test with a 1ms polling rate on a MiSTer with this project:

| Samples | Average | Max | Min | Std Dev |
| ------ | ------ | ------ | ------ | ------ | 
| 13962 | 0.74ms | 1.28ms | 0.23ms | 0.29ms |

## Wiring (Arcade Controller)
The wiring is simple. Connect one leg of each microswitch to GND and the other leg to the digital pin according to the schematic below. That's it!  
![Assemble1](images/daemonbite-arcade-encoder-wiring.png)

## Recommended layout (for PS3 stick compatibility)
Blue text in image (silk screen) corresponds to the Bx button numbers in the image for wiring above. 
![Assemble2](images/daemonbite-arcade-encoder-layout.png)

## Wiring (NeoGeo USB Adapter)
![Assemble3](images/daemonbite-arcade-encoder-wiring-neogeo.png)

## Wiring (Atari/Commodore/Amiga USB Adapter)
![Assemble4](images/daemonbite-arcade-encoder-wiring-atari.png)

## Programming the Arduino
1. Download the free Arduino IDE: https://www.arduino.cc/en/main/software
2. Connect the Arduino Pro Micro to a USB port and let the drivers install.
3. Choose the correct board and virtual COM port in the IDE.
3. Compile/Upload the project.

## License
This project is licensed under the GNU General Public License v3.0. The name "daemonbite" is registered to my company in Finland and should not be used by others.
