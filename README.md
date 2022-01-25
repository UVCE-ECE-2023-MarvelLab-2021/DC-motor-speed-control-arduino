# DC motor speed control using Arduino

## Description
We are controlling the speed of DC motor using Arduino as the microcontroller and potentiometer to change speed 

## Components and supplies
```
Arduino Uno X 1
DC motor(generic) X 1
Jumper wires(generic) X 1
Potentiometer - 10k ohms X 1
L298N motor driver X 1
USB A to B cable X 1
```

## Circuit diagram
![This is an image](images/7-n-1024x651.avif)

## Code
Code used to program the arduino
<details>
<summary>Click to expand code...</summary>
<p>

```c++
void setup() {
  Serial.begin(9600);
  pinMode(3,OUTPUT); // Motor pin 1
  pinMode(4,OUTPUT); // Motor pin 2
  digitalWrite(4,LOW); // Normally LOW in this pin
  pinMode(A0,INPUT);  // 10k Potentiometer
}

void loop() {
  int s=analogRead(A0); // 10k Potentiometer
  int z=map(s,0,1024,0,255);
  Serial.println(z);
  analogWrite(3,z);
}

```

</p>
</details>

## Working 
The potentiometer value is varied by rotating the potentiometer's knob and this value is fed into arduino as anolog input at pin A0 of arduino. The analog input has a range of `0-1023`. This input is mapped to a value in the range `0-255`. The mapped value is fed as [PWM](https://create.arduino.cc/projecthub/muhammad-aqib/arduino-pwm-tutorial-ae9d71) output to the motor driver at pin `4` which in turn drives the motor. The speed of the motor varies as the potentiometer value is changed.
