# DJITelloPy
ドローンプロジェクトの備忘録としてのサイトです．
DJITelloPyのライブリーを使用してTelloを操作しましょう．
## Install using pip
以下のコマンドでDJITelloPyをインストールすることができます．

[DJItelloPy](https://github.com/damiafuentes/DJITelloPy)
```bash
pip install djitellopy
```
## 離陸と着陸
### tello_sample01.py
以下のコードは，Telloドローンを接続し，離陸させ，着陸させ，最後に通信を終了する基本的な流れを示します．

それぞれのメソッドを使ってTelloの動きを確認しましょう．
```python
from djitellopy import Tello

tello = Tello()
tello.connect() #Telloに通信を開始
tello.takeoff() #離陸
tello.land()    #着率
tello.end()     #通信終了
```

## 上昇と下降
### tello_sample02.py
以下のコードはTelloを上昇と下降させるためのコードです．それぞれメソッドの引数はセンチメートルです．
#### move_up(self, x),move_down(self, x)
Fly x cm up or down.
```python
from djitellopy import Tello

tello = Tello()

tello.connect()
tello.takeoff()

tello.move_up(50)        #50cm上昇
tello.move_down(50)      #50cm下降

tello.land()
tello.end()
```


##  前進，後進，左右移動
### tello_sample03.py
次のコードは，Telloを前進，後進，左，右に移動させるためのコードです．それぞれのメソッドの引数はセンチメートルです．
それぞれのメソッドを使ってTelloの動きを確認しましょう．
#### move_forward(self, x),move_back(self, x),move_left(self, x),move_right(self, x)
Fly x cm forward, back, left or right.

```python
from djitellopy import Tello

tello = Tello()

tello.connect()
tello.takeoff()

tello.move_up(50)      //50cm 上昇
tello.move_left(50)    //50cm 左に並行移動
tello.move_right(50)   //50cm 右に並行移動
tello.move_forward(50) //50cm 前進
tello.move_back(50)    //50cm 後進
tello.land()
tello.end()
```

## 回転
###  tello_sample04.py
次のコードは，Telloを回転させるためのコードです．回転させるためには，Flip を使用する必要があります．
それぞれのメソッドを使ってTelloの動きを確認しましょう．
#### flip(self, direction)　or flip_x (self)
Telloが空中で不安定なときはコマンドが実行されない場合があります．
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
## 旋回
### tello_sample05.py
次のコードはTelloを旋回させるためのコードである．rotate_clockwiseは時計回りにTelloを旋回させるメソッドです．
メソッドの引数は角度を示す．

それぞれのメソッドを使ってTelloの動きを確認しましょう．
#### rotate_clockwise(self, x)

```python
from djitellopy import Tello
import time

tello = Tello()

tello.connect()
tello.takeoff()

tello.rotate_clockwise(90)
tello.rotate_counter_clockwise(90)

tello.land()
tello.end()
```
## Getter
このコードは，Telloの状態を知ることができるコードです．
バッテリーの残量を知ることができるメソッドもあります．
Telloの状態を確認しましょう．
### tello_sample07.py
```python
from djitellopy import Tello
import time

tello = Tello()

tello.connect()
tello.takeoff()

print(f"Battery: {tello.get_battery()}%")
print(f"flight_time:{tello.get_flight_time()}s")
print(f"temperature:{tello.get_highest_temperature()}")
print(f"Tof:{tello.get_distance_tof()}cm")
print(f"current_state:{tello.get_current_state()}")
tello.land()
tello.end()
```

## 問題
1. 水平方向に１辺の長さが50cmの正方形をTelloで描いてみましょう！
2. 垂直方向に1辺の長さが50cmの正方形をTelloで描いてまましょう，最後には回転して終了をアピールしてみましょう．
