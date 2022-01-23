## Table of contents

- [Overview](#overview)
- [Features](#features)
- [Default Layout](#default-layout)
- [Lightroom Layout](#lightroom-layout)
- [PCB](#pcb)
- [BOM](#bom)
- [Case](#case)
- [Assembly Guide](#assembly-guide)
- [Firmware](#firmware)


## Overview


ANTARI is 4x4 macropad supports analog potentiometer, rotary encoders, Oled screen, passive buzzer, 3.5mm TRS socket for sending out serial data like midi output and more. The rotary encoder also outputs midi signal when the keyboard is switched to 'Lightroom' dedicated layer, once you pressed an letter key the knob will output a midi cc signal with different parameter, which allows you use a knob to adjust up to 45 sliders in lightroom with Lightroom keymap, most importantly, the value will not jump or jitter, oppositely it moves relatively and smoothly. The oled screen will show you the last letter key you pressed and every information you need. For detailed demo you can visit my youtube [video](https://www.youtube.com/watch?v=S6qfb3bq990&t=147s&ab_channel=Synthvestigator).


Designer and maintainer: [sandipratama/nendezkombet](https://github.com/nendezkombet) 


![DSC04814](https://user-images.githubusercontent.com/82454371/150683198-763633a3-3cf9-430c-b591-c8792491a326.jpg)


![DSC04928](https://user-images.githubusercontent.com/82454371/150683229-19ea3598-54ea-492d-80c4-f1207aff4052.jpg)


![DSC04907](https://user-images.githubusercontent.com/82454371/150683426-ec4313ed-1113-466e-a5df-8ba9de567542.jpg)


![DSC04946](https://user-images.githubusercontent.com/82454371/150683489-f00e6025-abc8-47e6-862c-dd597199564c.jpg)


For hardware midi controller the PCB has 3.5mm TRS female socket footprint ( 3.5mm TRS male jack to 5-pin midi midi cable as connector required ), for this specific purpose the programaing code can be done with arduinoIDE.


## Features


- Cheap to build.
- Easy to source components.
- Easy to build.
- MX style switch and Kailh low profile V2 switch compatible
- Arduino Pro Micro powered.
- QMK compatible.
- RGB backlighting support (optional).
- Rotary encoder support.
- Passive buzzer support.
- Two placement oled LCD support.
- Hardware midi controller support.
- Can be battery powered ( as portable controller like midi or lighting controller ).
- Completely open-source.


## Default Layout

Default layout just for ordinary macropad with rotary encoder, passive buzzer for layer indicator, RGB underglow and analog potentiometer if enabled.


![keyboard-layout (2)](https://user-images.githubusercontent.com/82454371/150684784-00b68b64-c2c4-4a1c-99c6-1f94769a7611.png)


Because every people have their specific keymap setting, i decided setting up the default keymap with alphabet key so you can edit every function key as you want and compile your own firmware later. If you decided with rotary encoder it's function as system volume and instantly enabled by default. 


## Lightroom Layout 


Every key in the lightroom keymap has 3 different midi cc's number, you can access every cc's with tapping the key 1-3 times. Activated cc's will displayed in the oled LCD display. You you can visit my youtube [video](https://www.youtube.com/watch?v=S6qfb3bq990&t=147s&ab_channel=Synthvestigator) for future detail.

For this specific keymap i doesn't write the code by myself, i just adapted from other keyboard maintainer. Thank's to [luantty2](https://github.com/luantty2/pheromone_keyboard) for his wonderful work.


The pictures below showed first layer on the left and second layer on the right.


![keyboard-layout1 (2)](https://user-images.githubusercontent.com/82454371/150686444-1a3072e9-cf73-4013-9993-2ec437c50238.png)   ![keyboard-layout t(2)](https://user-images.githubusercontent.com/82454371/150686453-ba7ecedc-b085-4e5a-8360-4e0e36ef9f4a.png)


## PCB


PCB legend showed components placement and detail footprints information.


![PCB](https://user-images.githubusercontent.com/82454371/150684317-690598c6-5f0f-4b85-8dc5-5e3b115f4f24.jpg)



## BOM

|Parts|Footprint|Quantity|
|:---|:---|:---|
|WS2812B RGB LED |5050|8|
|100nF capacitor|0805|8|
|MX switch or Kailh low V2 switch |3 or 5 pin|16|
|1N4148 diode |SOD-123 or axial|16|
|Rotary encoder|EC11|1|
|Arduino Promicro |32u4|1|
|220ohm resistor|0805 or axial|3|
|Reset button switch |6mm*2.5mm|1|
|Passive buzzer |12mm|1|
|Oled LCD display |SSD1306|1|
|B10K Analog potentiometer (optional) | RV09 or RK09|1|
|3.5mm TRS female socket (optional) |PJ313|1|
|Micro slide switch (optional)|MSS22D18 |1|
|9V battery (optional) ||1|
|10mm M2 "MALE TO FEMALE" brass standoff|round knurled|4|
|10mm M2 "FEMALE TO FEMALE" brass standoff|round knurled|4|
|5mm M2 screw|-|8|
|3.5mm TRS jack to 5-pin midi din male socket (optional) |see detail below|1|


![51kXivjBTuL _AC_SX425_](https://user-images.githubusercontent.com/82454371/150636116-4ee8e17d-2fe3-4c75-84c9-792c8be12903.jpg)


you can build by your self, wiring instruction can by found in the google search engine.


## Case


Stacked acrylic case cutting file can be open with Adobe Illustrator or Corel Draw and ready for cutting process.


## Assembly Guide

Will be update soon !!!


## Firmware


The firmware is fully QMK, see [build environment setup](https://docs.qmk.fm/#/getting_started_build_tools) then the [make instructions](https://docs.qmk.fm/#/getting_started_make_guide) for more information. 


## Firmware flashing :

Open QMK Toolbox and locate The .hex file you compiled before or use ready flash default keymap

## Enter the bootloader :

Press the button twice on the back of the PCB than hit flash 

## Enable analog potentiometer :

The analog potentiometer outputs a midi signal which can be recognized by any software reads midi input, but this feature is not enabled by default, to enable it, edit config.h and uncomment the code below:

```
#define POT_ENABLE
```


