# Practica ESP32 de Sensor ultrasonico con LCD
En esta practica utilizamos un sensor ultrasonico
y mostramos la lectura en una pantalla LCD.

## Introducción

### Descripción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```HC-SR04```) para obtener una distancia Y en esta practica se añade un LCD para imprimir la informacio cadaa 1 seg.


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor HC-SR04
- Pantalla LCD


## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:

```
const int Trigger = 4;   //Pin digital 2 para el Trigger del sensor
const int Echo = 15;   //Pin digital 3 para el Echo del sensor
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4



LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {
  Serial.begin(9600);//iniciailzamos la comunicación
  pinMode(Trigger, OUTPUT); //pin como salida
  pinMode(Echo, INPUT);  //pin como entrada
  digitalWrite(Trigger, LOW);//Inicializamos el pin con 0
  lcd.init();
  lcd.backlight();
  
}

void loop()
{

  long t; //timepo que demora en llegar el eco
  long d; //distancia en centimetros

  digitalWrite(Trigger, HIGH);
  delayMicroseconds(10);          //Enviamos un pulso de 10us
  digitalWrite(Trigger, LOW);
  
  t = pulseIn(Echo, HIGH); //obtenemos el ancho del pulso
  d = t/59;             //escalamos el tiempo a una distancia en cm
  
  Serial.print("Distancia: ");
  Serial.print(d);      //Enviamos serialmente el valor de la distancia
  Serial.print("cm");
  Serial.println();
  delay(3000);          //Hacemos una pausa de 100ms

  lcd.setCursor(0, 0);
  lcd.print(" Dist: " + String(d)+"cm");
  lcd.setCursor(0, 1);
  lcd.print(" Vargas ");
delay(1000);

}


```
2. Instalar la libreria de **LiquidCrystal I2C** como se muestra en la siguente imagen.

![](https://github.com/DavidVar95/Sensor_ultrasonico_con_LCD/blob/main/Captura%20de%20pantalla%202023-06-10%2009.25.40.png?raw=true)

3. Hacer la conexion de **ESP32** con la **HC-SR04** como se muestra en la siguente imagen.

![](https://github.com/DavidVar95/Sensor_ultrasonico_con_LCD/blob/main/Captura%20de%20pantalla%202023-06-10%2009.23.57.png?raw=true)

4. Hacer la conexion del sensor ultrasonico **ESP32** con la **LCD** como se muestra en la siguente imagen.

![](https://github.com/DavidVar95/Sensor_ultrasonico_con_LCD/blob/main/Captura%20de%20pantalla%202023-06-10%2009.24.09.png?raw=true)


5. CONEXION DEL CIRCUITO

![](https://github.com/DavidVar95/Sensor_ultrasonico_con_LCD/blob/main/Captura%20de%20pantalla%202023-06-10%2009.24.45.png?raw=true)

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la distancia  al sensor **HC-SR04** 

## Resultados

se visualizara en el LCD la distancia seleccionada en el sensor .

![](https://github.com/DavidVar95/Sensor_ultrasonico_con_LCD/blob/main/Captura%20de%20pantalla%202023-06-10%2009.26.58.png?raw=true)






# Créditos

Desarrollado por Ing. David Vargas Gonzalez

