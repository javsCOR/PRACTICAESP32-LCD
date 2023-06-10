# Practica ESP32 con PANTALLA LCD
Este repositorio muestra como podemos programar una ESP32 con el sensor  y nos muestra los porcentajes de humedad y la temperatura y mandar los resultados a una una pantalla LCD y mandando otros comandos.


## Introducción

### Descripción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```DTH11```) para adquirir temperatura y humedad del entorno y mandar las señales o resultados a una pantalla LCD; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor DHT11
- pantalla LCD 12 X2


## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:

```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");
  delay(1000);
  lcd.setCursor(0,0);
  lcd.print("JAVIER CORTES");
  lcd.setCursor(0,1);
  lcd.print("DIPOLMADO   MECA");

  delay(1000);
}


```
2. Instalar la libreria de **DHT sensor library for ESPx** como se muestra en la siguente imagen.

![](https://raw.githubusercontent.com/javsCOR/PRACTICAESP32-LCD/2224cfb3ec0195266556f4e9c4764869b8c893ef/LIBRERIAS.png)

3. Hacer la conexion de **DHT11** a **ESP32**  y conectar ala pantalla **LCD32**como se muestra en la siguente imagen.

![](https://github.com/javsCOR/PRACTICAESP32-LCD/blob/main/1.png?raw=true)

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la temperatura y humedad dando *doble click* al sensor **DHT11** 
4. tambien  agregamos comandos diferentes a los resultados en la pantalla **LCD32** COMO SE MUESTRA EN LA SIGUIENTE  IMAGEN 

![](https://github.com/javsCOR/PRACTICAESP32-LCD/blob/main/1.png?raw=true)


## Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en la siguente imagen.

![](https://github.com/javsCOR/PRACTICAESP32-LCD/blob/main/3.png?raw=true)







# Créditos

creado por ING javier cortes rojas

- [GitHub](https://github.com/DiegoJm10)