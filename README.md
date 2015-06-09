# Educational Robot Quadruped #

> Quadruped robot for educational use

* * *

## Resumen ##

Cuadrúpedo robótico para uso en entornos educativos. El cuadrúpedo ha sido
desarrollado y optimizado para impresión 3D y pensando en su bajo coste y
facilidad de montaje y uso. Permite ser controlado desde diferentes plataformas.

## Instalación ##

En esta sección se cubre la instalación de software y hardware para el montaje
recomendado, mediante [Scratch](https://scratch.mit.edu/) y
[Arduino](http://www.arduino.cc/).

### Requerimientos de software ###

Para poder usar Scratch (v2.0 online) con Arduino, es necesario
[s2a_fm](https://github.com/MrYsLab/s2a_fm) una extensión de Scratch para
comunicarse con Arduino. Para generar los archivos aptos para la impresora 3D
desde los archivos `.stl` será necesario adicionalmente un software para esta
función, como puede ser [Slic3r](http://slic3r.org/).

Ver los requerimientos de mencionados programas previamente.


### Requerimientos de hardware ###

Será necesario para su montaje y uso una fuente de alimentación que proporcione
10W a 5V, un Arduino Uno o equivalente, una pareja de XBEE previamente
asociados, un explorer de XBEE, un shield de XBEE, ocho servomotores tipo 9g con
sus correspondientes accesorios (tornillos y cuernos). El cuadrúpedo está
optimizado para usar los servos **TowerPro SG90**. Adicionalmente harán falta
tornillos de métrica tres de diferentes largos.

## Uso ##

Instrucciones de montaje y puesta en marcha.

### Montaje del cuadrúpedo robótico ###

1.  Imprimir una unidad de los archivos `chassis.stl`, `arduino_base.stl`,
    `tray.stl`. Imprimir cuatro unidades de `leg.stl`. Imprimir ocho unidades de
    `servo_button.stl`, `shoulder.stl`. Puede ser necesario repasar las piezas
    impresas con el fin de eliminar rebabas.  
2.  Atornillar cuatro servos sobre el chasis (_chassis_) usando los tornillos de
    montaje proporcionados por los servos. Los ejes de los servos han de quedar
    hacia el exterior.  
3.  Montar un servo en cada pata (_leg_) con el eje en el extremo contrario a la
    base de la pata. Atornillarlos con los tornillos correspondientes.  
4.  Unir parejar de soportes (_shoulder_) usando dos tornillos M3x6 con tuerca.  
5.  Para cada soporte: Colocar un cuerno del servo y un rodamiento
    (_servo\_button_) dentro del soporte. Encajar un servo dentro del soporte y
    atornillarlo, asegurando que puede hacer la rotación completa.  
6.  Encajar dos tuercas en la bandeja (_tray_). Presionar contra el chasis hasta
    que encaje.  
7.  Si se va a usar portapilas, éste irá entre la bandeja y la base del Arduino.
    Ambas piezas se unen con tornillos de M3x35 en caso de usarse portapilas o
    de M3x10 en caso contrario.  
8.  Encastrar cuatro tuercas en la base del Arduino (_arduino\_base_), fijar el
    Arduino a su base mediante tornillos M3x10.

### Conexión eléctrica ###

Todas las alimentaciones de los servomotores van en paralelo y a la fuente de
alimentación. Las señales de control de los servos van a Arduino, usando las
conexiones del dos al cinco para los servos más cercanos al cuerpo, en sentido
contrario a las agujas del reloj empezando por la esquina superior izquieda
(extremo contrario a la conexión USB de Arduino). Los servos de las patas usan
las conexiones del seis a la nueve, numerados de la misma manera. La masa del
Arduino y de la fuente de alimentación ha de ser compartida. Conectar el shield
de XBEE sobre el Arduino. Conectar el explorer de XBEE a un puerto USB libre del
ordenador a usar.

### Firmware ###

El Arduino deberá tener cargado el firmware Firmata (incluido con Arduino IDE
bajo en nombre de `StandardFirmata`).

### Software ###

Con el explorer de XBEE conectado al ordenador, lanzar s2a_fm con el nombre del
puerto donde realizar la comunicación con XBEE. Por ejemplo:

        python s2a_fm.py /dev/ttyUSB0

Abrir Scratch y cargar el proyecto `educational-robot-quadruped.sb2`, una vez
hecho, se podrá ver en la interfaz gráfica los posibles movimientos del
cuadrúpedo en forma de flechas para dichas órdenes.

El cuadrúpedo sólo avanzará un paso en la dirección elegida, y sólo si
previamente se ha levantado. El botón de stop permite cancelar cualquier orden,
deshabilitar el robot y parar el programa. Después de pulsarlo será necesario
volver a iniciar el proyecto de Scratch.

### Bugs ###

Se han observado los siguientes problemas:

-   Desde la posición de reposo, el cuadrúpedo presenta demasiada carga para
    los servos puede levantarse.  
-   El software de control provoca al inicio movimientos extraños.  
-   En determinados momentos hay servos que se deshabilitan sin razón aparente.
    (Problema de PyMata?).  
-   Por protocolo de Firmata, es necesario un pequeño tiempo entre órdenes para
    asegurar que son recibidas y procesadas. (Implementado).

## Enlaces externos ##

Este proyecto también está presente en:

-   [Scratch](https://scratch.mit.edu/projects/65799474/).  
-   [Thingiverse](http://www.thingiverse.com/thing:756995).

## Créditos ##

Proyecto realizado por Taller de Inventores 2015, representado por:

-   kwendenarmo <kwendenarmo@akornsys-rdi.net>

Alumnos de Centro de Formación Padre Piquer:

-   C, Duanju  
-   D, Diego


