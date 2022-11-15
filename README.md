![image](https://user-images.githubusercontent.com/99285798/202036639-36fc13c0-d3d0-48fa-8a25-69d1d9760b12.png)
----

Alumnos que realizaron el los sensores:

Cuevas Martinez Adrian de Jesus 19211623
Robledo Sanchez Damian 19211719
Nunez Felipe Jose Luis 18212233

----

(KY-001 Temperature sensor (DS18B20))

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

(KY-006 Passive Piezo-Buzzer)

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

KY-012

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

KY-002 Shock

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

KY-004 Button

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

KY-005 IR Emission y KY-022 IR Receiver

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

KY-008

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

KY-028

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

KY=019

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

KY-020

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

KY-039

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

KY-033

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





