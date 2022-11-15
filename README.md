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


