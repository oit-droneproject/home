# DJITelloPy
This library makes it simpler to control Tello.
## Install using pip
If you have not yet installed this library, perform the following commands.

[DJItelloPy](https://github.com/damiafuentes/DJITelloPy)
```bash
pip install djitellopy
```
## Take-off and Landing
### tello_sample01.py
The following codes are for takeoffs and landings in Tello.
Check the code and the drone's movement.
```python
from djitellopy import Tello

tello = Tello()

tello.connect()
tello.takeoff()
tello.land()
tello.end()
```

## Up,Down
### tello_sample02.py
The following code is for vertical movement in Tello.
Check the code and the drone's movement.
#### move_up(self, x),move_down(self, x)
Fly x cm up or down.
```python
from djitellopy import Tello

tello = Tello()

tello.connect()
tello.takeoff()

tello.move_up(100)
tello.move_down(100)

tello.land()
tello.end()
```


##  Forward, Back, Left or Right
### tello_sample03.py
The following codes are for forward/backward/left/right movement in Tello.
Check the code and the drone's movement.
#### move_forward(self, x),move_back(self, x),move_left(self, x),move_right(self, x)
Fly x cm forward, back, left or right.

```python
from djitellopy import Tello

tello = Tello()

tello.connect()
tello.takeoff()

tello.move_up(50)
tello.move_left(50)
tello.move_right(50)
tello.move_forward(50)
tello.move_back(50)
tello.land()
tello.end()
```
## Move
### tello_sample04.py
The following code is for control tello by using the Move method.
Check the code and the drone's movement.
#### move(self, direction, x)
Tello fly up, down, left, right, forward or back with distance x cm. 
```python
from djitellopy import Tello

tello = Tello()

tello.connect()
tello.takeoff()

tello.move( "up", 50)
tello.move( "left", 50)
tello.move( "right", 50)
tello.move( "forward", 50)
tello.move( "back", 50)
tello.land()
tello.end()
```
## Flip
###  tello_sample05.py
The following code is for control tello by using the Flip method.
Check the code and the drone's movement.
#### flip(self, direction)　or flip_x (self)
Do a flip maneuver. Users would normally call one of the flip_x functions instead.
```python
from djitellopy import Tello

tello = Tello()

tello.connect()
tello.takeoff()

tello.flip_back()
tello.flip_forward()
tello.flip_forward()
tello.flip_left()
tello.flip_right()
tello.flip("f")
tello.land()
tello.end()
```
## Rotate
### tello_sample06.py
The following code can be used to rotate tello, clockwise and counterclockwise rotation can be used.
Check the code and the drone's movement.
#### rotate_clockwise(self, x)
Rotate x degree clockwise.
```python
from djitellopy import Tello
import time

tello = Tello()

tello.connect()
tello.takeoff()

tello.rotate_clockwise( 90)


tello.rotate_counter_clockwise(90)


tello.land()
tello.end()
```
## Getter
The following methods can be used to determine the status of tello. In particular, get_current_state method can be used to know all the states.
Check the code and the drone's movement.
### tello_sample07.py
```python
from djitellopy import Tello
import time

tello = Tello()

tello.connect()
tello.takeoff()

print(f"Battery: {tello.get_battery()}%")
print(f"flight_time:{tello.get_flight_time()}s")
print(f"height:{tello.get_height()}cm")
print(f"temperature:{tello.get_highest_temperature()}")
print(f"Tof:{tello.get_distance_tof()}cm")
print(f"current_state:{tello.get_current_state()}")
tello.land()
tello.end()
```
## Infinite loop
Infinite loops and their exits can be as follows.
Check the code and the drone's movement.
### tello_sample08.py
```python
from djitellopy import Tello
import time
import msvcrt

tello = Tello()

tello.connect()
tello.takeoff()

while True:
    tello.rotate_clockwise(45)
    time.sleep(2)
    tello.rotate_counter_clockwise(45)
    if msvcrt.kbhit():
        if "q" == msvcrt.getch().decode():
            print("press q")
            break
tello.land()
tello.end()
```
## Exercise
1. The drone should be flown so that it draws an equilateral triangle with side lengths of 50 cm at 180 cm from the floor.
2. The target height is 180 cm, and the loop is infinite while adjusting the height. However, when q is pressed, the loop must be exited.
