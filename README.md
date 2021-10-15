# CircuitPython
This repository will actually serve as a aid to help you get started with your own template.  You should copy the raw form of this readme into your own, and use this template to write your own.  If you want to draw inspiration from other classmates, feel free to check [this directory of all students!](https://github.com/chssigma/Class_Accounts).
## Table of Contents
* [Table of Contents](#TableOfContents)
* [Hello_CircuitPython](#Hello_CircuitPython)
* [CircuitPython_Servo](#CircuitPython_Servo)
* [CircuitPython_LCD](#CircuitPython_LCD)
* [NextAssignmentGoesHere](#NextAssignment)
---

## Hello_CircuitPython

### Description & Code
Description goes here

Here's how you make code look like code:

```python
Code goes here

```


### Evidence
Pictures / Gifs of your work should go here.  You need to communicate what your thing does.

### Wiring
Make an account with your google ID at [tinkercad.com](https://www.tinkercad.com/learn/circuits), and use "TinkerCad Circuits to make a wiring diagram."  It's really easy!  
Then post an image here.   [here's a quick tutorial for all markdown code, like making links](https://guides.github.com/features/mastering-markdown/)

### Reflection
What went wrong / was challenging, how'd you figure it out, and what did you learn from that experience?  Your ultimate goal for the reflection is to pass on knowledge that will make this assignment better or easier for the next person.




## CircuitPython_Servo

### Description & Code

This code tells the servo to spin back and forth. Simple.

```python
import time
import board
import pwmio
from adafruit_motor import servo

pwm = pwmio.PWMOut(board.A2, duty_cycle=2 ** 15, frequency=50)

my_servo = servo.Servo(pwm)

while True:
    for angle in range(0, 180, 5):
        my_servo.angle = angle
        time.sleep(0.05)
    for angle in range(180, 0, -5):
        my_servo.angle = angle
        time.sleep(0.05)

```

### Evidence

I would show a video but I'm too lazy.

### Wiring

Brown wire of the servo goes to ground. Orange wire goes to 5V. Yellow wire goes to A2.

### Reflection

I had some trouble with this simply because my computer didn't have an up-to-date verson of circuit python (I think?).


## CircuitPython_DistanceSensor

### Description & Code

```python
import time
import board
import adafruit_hcsr04
import neopixel

sonar = adafruit_hcsr04.HCSR04(trigger_pin=board.D5, echo_pin=board.D6)
dot = neopixel.NeoPixel(board.NEOPIXEL, 1, brightness=0.1)

r = 0
g = 0
b = 0

distance = 0

def fade(lower, upper, val):    # gives the values needed to fade two LEDs between a user set range
    real_upper = upper - lower
    result1 = (abs(val - lower) / real_upper) * 255
    result2 = 255 - result1
    print("Result 1: " + str(result1))
    print("Result 2: " + str(result2))
    print("Value: " + str(val))
    return result1, result2


while True:
    try:
        distance = sonar.distance

        if distance <= 5:   # makes LED red when distance <= 5
            r = 255
            g = 0
            b = 0
        elif distance <= 20:    # makes LED fade from red to blue while distance is between 5 and 20
            values = fade(5, 20, distance)
            b = int(values[0])
            r = int(values[1])
            g = 0
        elif distance <= 35:    # makes LED fade from blue to green when distance between 20 and 35
            values = fade(20, 35, distance)
            g = int(values[0])
            b = int(values[1])
            r = 0
        else:       # makes LED green when distance > 35
            r = 0
            g = 255
            b = 0
    except RuntimeError:
        print("Retrying...")

    print(r, g, b)
    dot.fill((r, g, b))
    time.sleep(0.1)
```

### Evidence

![Link to gif](/DistanceSensorGif.gif/)

### Wiring

### Reflection


## CircuitPython_LCD

### Description & Code

```python
Code goes here

```

### Evidence

### Wiring

### Reflection




## Onshape Egg

### Description

### Image




## NextAssignment

### Description & Code

```python
Code goes here

```

### Evidence

### Wiring

### Reflection
