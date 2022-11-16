![image](https://user-images.githubusercontent.com/99285798/202036639-36fc13c0-d3d0-48fa-8a25-69d1d9760b12.png)
----

#Alumnos que realizaron el proyecto con los sensores:

Cuevas Martinez Adrian de Jesus 19211623

Robledo Sanchez Damian 19211719

Nunez Felipe Jose Luis 18212233


----

#(KY-001 Temperature sensor (DS18B20))

import board

import busio

import adafruit_ssd1306

import time

import digitalio

from adafruit_onewire.bus import OneWireBus

import adafruit_ds18x20

ow_bus = OneWireBus(board.GP7)

devices = ow_bus.scan()

ds18b20 = adafruit_ds18x20.DS18X20(ow_bus, devices[0])

i2c = busio.I2C(board.GP1, board.GP0)

d = adafruit_ssd1306.SSD1306_I2C(128, 64, i2c)

b = digitalio.DigitalInOut(board.GP14)

i = digitalio.DigitalInOut(board.GP13)

i.direction = digitalio.Direction.OUTPUT

while True:

    d.text(('Temp: {0:0.3f} °C'.format(ds18b20.temperature)), 0, 0, 1)
    
    d.show()

https://www.loom.com/share/6f46d914d9434ec09fcd681bd23dbc50

----

#(KY-006 Passive Piezo-Buzzer)

import board

import busio

import adafruit_ssd1306

import time

import digitalio

import pwmio

Buzzer = pwmio.PWMOut(board.GP7, frequency=200, duty_cycle=0)

while True:

    Buzzer.duty_cycle = 1000;
    
    time.sleep(1)

https://www.loom.com/share/4b7a2ddb6e7c42ed937f4398a143234d

----

#KY-012

import board

import digitalio

import time

IO = digitalio.DigitalInOut(board.GP0)

IO.direction = digitalio.Direction.INPUT

while True:

    print("-------------")
    
    print(IO.value)
    
    time.sleep(0.1)

https://www.loom.com/share/a343cca9e7814a178c99fae7b38f8ab9

----

#KY-002 Shock

import board

import array

import pulseio

import time

import adafruit_irremote

pulsein = pulseio.PulseIn(board.GP26_A0, maxlen=120, idle_state=True)

pulseout = pulseio.PulseOut(board.GP27_A1, frequency=38000, duty_cycle=32768)

decoder = adafruit_irremote.GenericDecode()

pulsesOut = array.array('H', [65000, 1000, 65000, 65000, 1000])

while True:

    pulseout.send(pulsesOut)
    
    pulses = decoder.read_pulses(pulsein)
    
    print("Heard", len(pulses), "Pulses:", pulses)
    
    time.sleep(0.5)

https://www.loom.com/share/8f92b45556ac440a9995962bfaad7cb4

----

#KY-004 Button

import board

import array

import pulseio

import time

import adafruit_irremote

pulsein = pulseio.PulseIn(board.GP26_A0, maxlen=120, idle_state=True)

pulseout = pulseio.PulseOut(board.GP27_A1, frequency=38000, duty_cycle=32768)

decoder = adafruit_irremote.GenericDecode()

pulsesOut = array.array('H', [65000, 1000, 65000, 65000, 1000])

while True:

    pulseout.send(pulsesOut)
    
    pulses = decoder.read_pulses(pulsein)
    
    print("Heard", len(pulses), "Pulses:", pulses)
    
    time.sleep(0.5)

https://www.loom.com/share/8f92b45556ac440a9995962bfaad7cb4

----

#KY-005 IR Emission y KY-022 IR Receiver

import board

import digitalio

import time

Pin = digitalio.DigitalInOut(board.GP0)

Pin.direction = digitalio.Direction.OUTPUT

Pin.value = True

input()

Pin.value = False

https://www.loom.com/share/a91dda1aad3048b6a4300088e61d15e1

----

#KY-008

import board

import digitalio

import time

Pin = digitalio.DigitalInOut(board.GP0)

Pin.direction = digitalio.Direction.OUTPUT

Pin.value = True

input()

Pin.value = False

https://www.loom.com/share/162f8f143e504f8a98f6e72b8aa268d7

----

#KY-028

import board

import digitalio

import analogio

import time

PinD = digitalio.DigitalInOut(board.GP0)

PinD.direction = digitalio.Direction.INPUT

PinA = analogio.AnalogIn(board.GP27)

while True:

    time.sleep(0.5)
    
    print("------")
    
    print(PinA.value)

https://www.loom.com/share/0a477f8ad1ba4e9a80f2f0cc97076915

----

#KY-019

import board

import digitalio

import analogio

import time

PinD = digitalio.DigitalInOut(board.GP0)

PinD.direction = digitalio.Direction.OUTPUT

while True:

    time.sleep(1)
    
    PinD.value = True;
    
    time.sleep(1)
    
    PinD.value = False;

https://www.loom.com/share/362080a1ce9f4b4ab352824a632d867d

----

#KY-020

import board

import digitalio

import analogio

import time

PinD = digitalio.DigitalInOut(board.GP0)

PinD.direction = digitalio.Direction.INPUT

while True:

    time.sleep(0.2)
    
    print(PinD.value)


https://www.loom.com/share/1c54c307e05e4aba858fe69a14df1659

----

#KY-039

import board

import analogio

import digitalio

import time

In = analogio.AnalogIn(board.GP27)

LED = digitalio.DigitalInOut(board.LED)

LED.direction = digitalio.Direction.OUTPUT

while True:

    LED.value = False
    
    print(In.value)
    
    if(In.value < 61500):
    
        LED.value = True
        
    time.sleep(0.2)
   
https://www.loom.com/share/2d56fcde425c4f6e93ebcb14f8f78a14

----

#KY-033

import board

import analogio

import digitalio

import time

In = analogio.AnalogIn(board.GP27)

LED = digitalio.DigitalInOut(board.LED)

LED.direction = digitalio.Direction.OUTPUT

while True:

    LED.value = False
    
    print(In.value)
    
    if(In.value < 61500):
    
        LED.value = True
        
    time.sleep(0.2)
    
https://www.loom.com/share/7297ce7f26a7454f998725b89b1a9815

----

KY-032

import board
import analogio
import digitalio
import time

In = digitalio.DigitalInOut(board.GP0)
In.direction = digitalio.Direction.INPUT
LED = digitalio.DigitalInOut(board.LED)
LED.direction = digitalio.Direction.OUTPUT

while True:
    if(not In.value):
        print("DETECTED")
    time.sleep(0.1)

https://www.loom.com/share/2fd31d0592ca4098b74b4181b2e5b89a 

----

KY-036 Touch

import board
import analogio
import digitalio
import time

In = digitalio.DigitalInOut(board.GP0)
In.direction = digitalio.Direction.INPUT
LED = digitalio.DigitalInOut(board.LED)
LED.direction = digitalio.Direction.OUTPUT

while True:
    print("--------------")
    if(In.value):
        print("DETECTED")
    time.sleep(0.1)
    
https://www.loom.com/share/f2267e6e826a4001a0f12a27165817bb

----

KY-037 y KY-038

import board
import analogio
from digitalio import *
import time

Mic = DigitalInOut(board.GP0)
Mic.direction = Direction.INPUT

while True:
    print(Mic.value)
    time.sleep(0.2)

https://www.loom.com/share/81be724e8ab34279a6828dab70434a03

----

KY-018

import board
import analogio
from analogio import *
import time

In = AnalogIn(board.GP27)

while True:
    print(In.value)
    time.sleep(0.2)

https://www.loom.com/share/90ebec22c068410caaf79ffd0693c797

----

KY-015

import board
import analogio
from digitalio import *
import time
import adafruit_dht

dhtDevice = adafruit_dht.DHT11(board.GP0)
while True:
    try:
        # Print the values via the serial interface
        temperature_c = dhtDevice.temperature
        temperature_f = temperature_c * (9 / 5) + 32
        humidity = dhtDevice.humidity
        print("Temp: {:.1f} F / {:.1f} C    Humidity: {}% ".format(temperature_f, temperature_c, humidity))

    except RuntimeError as error:
        # Errors happen quite often, DHT's are hard to read, just move on
        print(error.args[0])
        time.sleep(2.0)
        continue
    except Exception as error:
        dhtDevice.exit()
        raise error

    time.sleep(1)
   
https://www.loom.com/share/605cee06196a41188a15a29c2123d330

----

KY-035 Analog Hall

from board import *
from analogio import *
import time

In = AnalogIn(GP27)

while True:
    print(In.value)
    time.sleep(0.2)

https://www.loom.com/share/2945aa8ad9504298b9dd7ce9e4d223d8

----

KY-010 Light Blocking

from board import *
from digitalio import *
import time

In = DigitalInOut(GP0)
In.direction = Direction.INPUT

while True:
    print(not In.value)
    time.sleep(0.2)

https://www.loom.com/share/0fe6bc6ae1f5425b81caa2a99afc59b1

----

KY-031

from board import *
from digitalio import *
import time

In = DigitalInOut(GP0)
In.direction = Direction.INPUT

while True:
    print(not In.value)
    time.sleep(0.2)

https://www.loom.com/share/c8b78c2c15054353bd6782164ddc0cb9

----

KY-023

import board
import digitalio
import analogio
import time

LED = digitalio.DigitalInOut(board.LED)
LED.direction = digitalio.Direction.OUTPUT
Dig = digitalio.DigitalInOut(board.GP0)
Dig.direction = digitalio.Direction.INPUT

DirX = analogio.AnalogIn(board.GP27)
DirY = analogio.AnalogIn(board.GP26)

while True:
    print("Axis X: ",DirX.value)
    print("Axis Y: ",DirY.value)
    time.sleep(0.1)

https://www.loom.com/share/01e97d5ac21b48eea6ea98b62d177642

----

KY-009

import board
from digitalio import *
import time

R = DigitalInOut(board.GP0)
G = DigitalInOut(board.GP1)
B = DigitalInOut(board.GP2)

R.direction = Direction.OUTPUT
G.direction = Direction.OUTPUT
B.direction = Direction.OUTPUT


while True:
    R.value = True
    time.sleep(1)
    R.value = False
    G.value = True
    time.sleep(1)
    G.value = False
    B.value = True
    time.sleep(1)
    B.value = False

https://www.loom.com/share/24bea01c3748488d9c0e492e3d3bc6e3

----

KY-016

import board
from digitalio import *
import time

Signal = DigitalInOut(board.GP0)
Signal.direction = Direction.INPUT

while True:
    print(not Signal.value)
    time.sleep(0.1)

https://www.loom.com/share/9824af68760d491e82b2c332001a14c4

----

KY-017

import board
from digitalio import *
import time

Signal = DigitalInOut(board.GP0)
Signal.direction = Direction.INPUT

while True:
    print(not Signal.value)
    time.sleep(0.1)

https://www.loom.com/share/e97276c658734153865d769ba94531bd

----

KY-003


https://www.loom.com/share/2881f9033ff74e7d80e4cee1781e286e 

----

KY-040

https://www.loom.com/share/90980de1fe8149afaf22aaa068a329c2

----



