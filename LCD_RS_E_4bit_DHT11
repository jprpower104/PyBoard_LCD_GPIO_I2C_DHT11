# main.py -- put your code here!
import pyb														# Clase que contiene la conf de la pyboard
import dht														# Clase que contiene la conf del sensor DHT11
from pyb import delay, millis									# importa conf de delay, millis
from lcd_api import LcdApi										# Clase que contiene las funciones del LCD
from pyb_gpio_lcd import GpioLcd  								# Clase que contiene la conf del LCD con GPIO

RS 	= pyb.Pin('X2');
E	= pyb.Pin('X3');
D4 	= pyb.Pin('X4');
D5 	= pyb.Pin('X5');
D6 	= pyb.Pin('X6'); 
D7 	= pyb.Pin('X7');
PX1 = pyb.Pin(pyb.Pin.board.X1, pyb.Pin.IN);					# Conectar DHT11 al pin X1 configurando este como entrada
d = dht.DHT11(PX1);												# instantacion del pin X1 en el sensor DHT11

lcd = GpioLcd(RS,E,D4,D5,D6,D7);								# Instantacion del i2c a un display lcd 16x2 en la direccion 0x27
#lcd.move_to(0, 0)
#lcd.putstr("%7d" % (millis() // 1000))
while True:
	d.measure()													# actualiza mediciones desde el DHT11
	DT=d.temperature() # eg. 23 (°C)							# guarda en DT la temperatura en grados celcuis medida como entero
	DH=d.humidity()    # eg. 41 (% RH)							# guarda en DH la humedad relativa en % de humedad medida cmo entero
	print("la temperatura es:",DT, "y  la humedad:",DH)			# imprime en el terminal serial el texto
	lcd.move_to(0, 0)											# ubica display en la columna 0 fila 0 el cursor
	lcd.putstr("Temperatura = %d" %DT)							# imprime texto en el display
	lcd.move_to(0, 1)											# ubica display en la columna 0 fila 1 el cursor
	lcd.putstr("Humedad = %d" %DH)								# imprime texto en el display
	pyb.delay(1500)												# retardo de 1500 mseg o 1.5 seg
