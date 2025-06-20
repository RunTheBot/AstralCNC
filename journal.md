---
title: "AstralCNC"
author: "RunTheBot"
description: "Replacement board for the Larken StarCNC controller, built around the RPI Pico."
created_at: "2025-06-17"
---
# Journal

Hours: 14h

# A while back, right before highway announced to June 16
Hours: 3h

When I got to this school, I've always wanted to fix the two CNCs that we have. One of them is a Larken 24/24 router, which is over 25 years old.

The controller uses a parrallel port which moder Operating systems don't support anymore, and the software that it uses is very old and doesn't work on modern computers.

I did a bunch of research and I needed to find the controller box which my teacher conviniently knew where it was. I took it home and started trying to use the parrallel port not knowing that it was not supported by modern operating systems.

After that I started looking for alternatives and documentation on how the controller works. I found (https://www.larkencnc.com/dloads/index.shtml)[https://www.larkencnc.com/dloads/index.shtml] which has a lot of documentation on the controller and how it works.

![Larken StarCNC](https://hc-cdn.hel1.your-objectstorage.com/s/v3/94a4b2611dd05d7d1520e87d839704c9ca4bf86c_image.png)

# June 16-17

Hours: 2h

Me and my friend (Jayson) started hacking at the controller using a Pico. We started by directly connecting the Pico to the stepper drivers and using the Pico's GPIO to control them. it kind of worked. 

I soon figured out that the Pico's GPIO is 3.3v and the stepper drivers are 5v, so we made a level shifter using some mosfets and some resistors. This worked, but I unfortunately did not get pictures of it.

heres the code:
```python
import board
import digitalio
import time
import supervisor

# Pins
step_pin = digitalio.DigitalInOut(board.GP0)
step_pin.direction = digitalio.Direction.OUTPUT

dir_pin = digitalio.DigitalInOut(board.GP1)  # Change if using a different pin
dir_pin.direction = digitalio.Direction.OUTPUT

# Settings
step_delay = 0.01  # Default speed

# Functions
def step_motor(steps):
    for _ in range(steps):
        step_pin.value = True
        time.sleep(step_delay)
        step_pin.value = False
        time.sleep(step_delay)

def set_direction(direction):
    dir_pin.value = bool(direction)

def set_speed(level):
    global step_delay
    step_delay = max(0.001, min(0.1, 0.1 / level))  # Level 1–10

def print_help():
    print("Commands:")
    print("  step <n>     - Step motor n times")
    print("  dir <0|1>    - Set direction")
    print("  speed <1-10> - Set speed level")
    print("  help         - Show this help")

print("Stepper Control Ready. Type 'help'.")

# Main loop
while True:
    if supervisor.runtime.serial_bytes_available:
        try:
            line = input().strip()
            if not line:
                continue
            parts = line.split()
            cmd = parts[0].lower()

            if cmd == "step" and len(parts) == 2:
                step_motor(int(parts[1]))
                print(f"Stepped {parts[1]} times.")

            elif cmd == "dir" and len(parts) == 2:
                set_direction(int(parts[1]))
                print(f"Direction set to {parts[1]}.")

            elif cmd == "speed" and len(parts) == 2:
                set_speed(int(parts[1]))
                print(f"Speed level set to {parts[1]}.")

            elif cmd == "help":
                print_help()

            else:
                print("Unknown command. Type 'help'.")

        except Exception as e:
            print("Error:", e)
```

I then tested the spindle and it is just a simple solid state relay running off 5v, so I connected it to the Pico and it worked.

# June 17

Hours: 3h

Schematic!
![Schematic](https://hc-cdn.hel1.your-objectstorage.com/s/v3/663f6ed5d0925f178e119bd20d2991c114a9e5e1_image.png)

# June 18-19
hours: 3h
PCB design!

![PCB](https://hc-cdn.hel1.your-objectstorage.com/s/v3/96e08dfd8bd8cfe5c2162619ebf2a184466401bd_screenshot_2025-06-19_225025.png)

# June 19
hours: 3h

BOM and journal
https://docs.google.com/spreadsheets/d/1fKyxs4xyiDP1QXcRQpTOFPQCPsDcIa7fzhB4tR6pHxY/edit?gid=1552496342#gid=1552496342

Side note: why does LCSC not stock Molex KK-254 connectors? ts pmo
Side note 2: Why are molex product nameing so bad? We have two manufacturer product numbers, two series names, and like no consistency.


Thanks to Larry Kenny (The guy who made the original controller) for making the documentation available and awnswering my questions.