---
{"dg-publish":true,"permalink":"/01-projects/ai-robot/02-coding/"}
---

# Coding 



```tasks
not done
path includes 02 Coding.md 
```

## Libs
> | File                                                 | Functions           | Arguments                                      |
> | ---------------------------------------------------- | ------------------- | ---------------------------------------------- |
> | [[01 Projects/AI Robot/02 Coding/robo.h\|robo.h]] | default_constructor | `_servo_id`  and a  `Adafruit_PWMServoDriver ` |
> 
{ .block-language-dataview}




- [[01 Projects/AI Robot/02 Coding/robo.h\|robo.h]]
- [[robot-database.h\|robot-database.h]]
- 


## Program Flow 
Here is a quick program functional flow , from the microcontroller perspective 
1. Initializes the wifi 
2. Initializes the Servo Motors to previous position 
3. Check if they are in their initial positions ?
	 - Servo motors does not support checking of angle. So im gonna use a server for that.
```mermaid
graph TB
A[Initializes the Wifi] & AA[Initializes the Server Endpoints] --> Main_Thread
B[Retrive Data from the Server] --> C
C[Servo Object] --> Main_Thread 
D[API End Points] --> Main_Thread
 ```

- [ ] Complete the below 📅 2025-05-24 


```mermaid
sequenceDiagram
	 participant PCA9685 
	participant ESP32 
	participant Flask API
	participant SQLite DB
	
	%% ESP32 
	ESP32 -->> ESP32: Initialize -> Boot,WiFi STA ..
	ESP32->>PCA9685: Initialize I2C (i2c_addr)
	%% GET Request
	ESP32->>Flask API: GET /robots?id=$id
	Flask API->>SQLite DB: Query all robots
	SQLite DB-->>Flask API: Return robots data
	Flask API-->>ESP32: JSON response with robots
	
	%% POST Request
	ESP32 ->>Flask API: POST /robots {name, type}
	Flask API->>SQLite DB: Insert new robot
	SQLite DB-->>Flask API: Confirm insertion
	Flask API-->>ESP32: JSON response (201 Created)
```


There are 3 main Hardware componets that will effect the programming 
1. [[01 Projects/AI Robot/02 Coding/PCA9685\|PCA9685]] -> For Driving the motor 
2. [[08 Electronics/Embedded Systems/Micro Controllers/Espressif/ESP32/ESP32\|ESP32]] -> Main Controller 
3. [[08 Electronics/Embedded Systems/Raspberry Pi/Raspberry Pi\|Raspberry Pi]] -> For hosting the server 

## PCA9685 

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



```cpp
#include <Adafruit_PWMServoDriver.h>
Adafruit_PWMServoDriver board1 = Adafruit_PWMServoDriver(0x40);    
#define SERVO_MIN_PULSE_COUNT 125                                              
#define SERVO_MAX_PULSE_COUNT  625                                             
#define SERVO_UPDATE_FREQ
void setup() {
	board1.begin();
	board1.setPWMFreq(SERVO_UPDATE_FREQ);                  
}

void loop() 
  { 
	for(int i=0; i<8; i++){
		board1.setPWM(i, 0, get_pulse(0) );
	}
    delay(1000);
    for( int angle =0; angle<181; angle +=10)
      { 
      for(int i=0; i<8; i++){ board1.setPWM(i, 0, get_pulse(angle) );}
      }
    delay(100);
  }
int get_pulse(int angle)                             
{ 
	int pulse = map(angle,0, 180, SERVO_MIN_PULSE_COUNT,SERVO_MAX_PULSE_COUNT); 
    return pulse;
  }
```

</div></div>

This is the PCA9685  driver #sampleCode  , here is its order 
1. Create `driver_object` 
	- **param:** `i2c_addr`
>
>```cpp
>Adafruit_PWMServoDriver board1 = Adafruit_PWMServoDriver(0x40); 
>```
>
>```cpp
>// Adafruit_PWMServoDriver.cpp
>Adafruit_PWMServoDriver();
>Adafruit_PWMServoDriver(const uint8_t addr);
>Adafruit_PWMServoDriver(const uint8_t addr, TwoWire &i2c);
>```
>There are 3 defenitions 
>
>```cpp
>	Adafruit_PWMServoDriver::Adafruit_PWMServoDriver(const uint8_t addr)
>	: _i2caddr(addr), _i2c(&Wire) {}
>	/*!
>	 *  @brief  Instantiates a new PCA9685 PWM driver chip with the I2C address on a
>	 * TwoWire interface
>	 *  @param  addr The 7-bit I2C address to locate this chip, default is 0x40
>	 *  @param  i2c  A reference to a 'TwoWire' object that we'll use to communicate
>```
>
2. Initialize the board 
- [ ] Complete these steps 📅 2025-05-24  


## Servo 
There is mainly x things
### 1. Servo Properties 

>[!blank]
>
>> [!blank|left-small]
>>
>>```cpp
>>#define SERVO_ANGLE_MIN 0
>>#define SERVO_ANGLE_MAX 180
>>#define SERVO_MIN  102   // .5ms
>>#define SERVO_MAX  512   // 2.5ms 
>>#define SERVO_FREQ 50
>>#define CONTROLLER_I2C_ADDR 0x41
>>```
>
>>[!Abstract]- Why 
>>
>>We already know to the ideal values of all the features of [[08 Electronics/Embedded Systems/Actuators/MG995\|Servo]], but those are ideal values and , we need to find out the actual value of those , for example some servos can't do full 180. 
>>These are the ideal charaterestics
>>
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



![Pasted image 20250519110522.png](/img/user/01%20Projects/AI%20Robot/03%20Development/attachments/Pasted%20image%2020250519110522.png) 

</div></div>

>>But we have to make sure it our self . 
>
{ #69745d}

{ #15f658}

## Database 

## Movements
 


# Software
Going to use [[03 Coding/Embedded Programming/platformio\|platformio]] for development and [[03 Coding/02 c++/C++\|cpp]] as the programming language , [[vscode\|vscode]] as the editor(ide). 


```cpp
Adafruit_PWMServoDriver board1 = Adafruit_PWMServoDriver(CONTROLLER_I2C_ADDR);      
```

```cpp
Robo la1(PIN_LA1, board1);
Robo la2(PIN_LA2, board1);
Robo la3(PIN_LA3, board1);
Robo ra1(PIN_RA1, board1);
Robo ra2(PIN_RA2, board1);
Robo ra3(PIN_RA3, board1);
Robo lh(PIN_LH, board1);
Robo rh(PIN_RH, board1);
Robo ll1(PIN_LL1, board1);
Robo ll2(PIN_LL2, board1);
Robo ll3(PIN_LL3, board1);
Robo rl1(PIN_RL1, board1);
Robo rl2(PIN_RL2, board1);
Robo rl3(PIN_RL3, board1);
Robo lf(PIN_LF, board1);
Robo rf(PIN_RF, board1);
```