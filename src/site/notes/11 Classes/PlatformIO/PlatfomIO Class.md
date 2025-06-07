---
{"dg-publish":true,"permalink":"/11-classes/platform-io/platfom-io-class/"}
---


## Installing Platform IO
[Source](https://docs.platformio.org/en/latest/integration/ide/pioide.html)

- Open Extension Tab in the activity bar 
- Search for **platform io** and click install 
![Pasted image 20250607214158.png](/img/user/11%20Classes/PlatformIO/attachements/Pasted%20image%2020250607214158.png)
![Pasted image 20250607214212.png](/img/user/11%20Classes/PlatformIO/attachements/Pasted%20image%2020250607214212.png)

### Creating New Project 
![Pasted image 20250607215312.png|left](/img/user/11%20Classes/PlatformIO/attachements/Pasted%20image%2020250607215312.png)
- Click the icon that look like alien in the activity bar 
- **New Project** -> Select Board (Esp32 dev module) --> select default location (Documents/PlatformIO/Projects) -> Finish
This will create a project dirctory with the following contents
```
Test Project
├── include
│   └── README
├── lib
│   └── README
├── platformio.ini
├── src
│   └── main.cpp
└── test
    └── README
```

- `src` -> for storing source files (source code) 
- `include` -> header file shared by all source files , 
the headers stored in `includes` can be used in the following manner 
```c

#include "header.h"

int main (void)
{
 ...
}
```
- `lib/` for project specific libraries 
```
lib/
	- mylib/
		- mylib.c
		- mylib.h 
```

```c
#include <mylib.h>

```


![Pasted image 20250607214248.png](/img/user/11%20Classes/PlatformIO/attachements/Pasted%20image%2020250607214248.png)
![Pasted image 20250607214310.png](/img/user/11%20Classes/PlatformIO/attachements/Pasted%20image%2020250607214310.png)


![Pasted image 20250607214510.png](/img/user/11%20Classes/PlatformIO/attachements/Pasted%20image%2020250607214510.png)

## Publishing new Lib to Platfom io
- Create a new `library.json` file with the following contents

```json
{
  "name": "Robo",
  "version": "0.0.1",
  "description": "A library for Arduino/PlatformIO",
  "keywords": "sensor, i2c, arduino",
  "repository": {
    "type": "git",
    "url": "https://github.com/AI-Robot-GCEK/robo"
  },
  "authors": [
    {
      "name": "Arun CS",
      "email": "aruncs31ss@gmail.com"
    }
  ],
  "license": "MIT",
  "dependencies": {
    "adafruit/Adafruit PWM Servo Driver Library": "3.0.2"
  },
  "frameworks": ["arduino"],
  "platforms": ["atmelavr", "espressif32"]
}

```
- Change the appropriate  contens like `name ` to your own name 

```
folder_name/
	- src/
		- .cpp
		- .h
	- examples/ 
library.json
```

## Account Creation
```bash
pio account register -u username -p asdasdsa1@ --firstname Arun --lastname CS
```

#### Platform io lib structure 
```
robo-movements
├── library.json
├── LICENSE
└── src
    ├── robo-movements.cpp
    └── robo-movements.h
```


```
project
├── include
│   ├── configs.h
│   └── pins.h
├── lib
│   └── robo-database
│       └── src
│           ├── robo-database.cpp
│           └── robo-database.h
├── LICENSE
├── platformio.ini
├── README.md
├── src
│   └── main.cpp
└── test
    └── README
```


#### Publishing New Lib 

- Login to you account  and  publish new Lib using the following 

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



```bash
pio account login
pio pkg publish .
```

</div></div>


#### Updating your lib 
- create a new `git tag` with the same version number number that you given in the `library.json` 
- then push the `tag` to github 

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



```bash
git add .
git commit -m "Release version 1.0.1"
git tag -a 1.0.1 -m "Version 1.0.1"
git push origin --tags
```

</div></div>

- now publish the update 


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



```bash
pio pkg publish .
```

</div></div>


![Pasted image 20250607220807.png](/img/user/11%20Classes/PlatformIO/attachements/Pasted%20image%2020250607220807.png)
- it will ask for confirmation , check if everything is ok and type `y` and `Enter`
