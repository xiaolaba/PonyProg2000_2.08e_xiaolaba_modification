# PonyProg2000_2.08e_xiaolaba_modification
PonyProg2000, an open source Serial device Programmer, my clone of EasyI2C and only LPT port used, include power control (VCC) without tweaking the battery or switch every time for programming the EEPROM device.  

![alt text](https://github.com/xiaolaba/PonyProg2000_2.08e_xiaolaba_modification/blob/master/ponyprog2000-xiaolaba-2.08e_ok.jpg) 
```
To embeds image to this read.me  
![alt text](http://url/to/img.png)  
```  
.  
.  
.  

Original and complete source code https://sourceforge.net/projects/ponyprog/

# I need something simple and dedicated PC used, not general  
PC : Fujitsu S6311 notebook with docking, LPT port and COM port are avalaible for PonyProg2000 & easy, usually, USB-Serial COM is not not working.

Note:
The notebook LPT Data port output only 3.3V, ECP/Bi-directional/Standard all three mode in BIOS setting has no any effect to uses with PonyProg; if you want tweaking LPT port with some manually test to confirm the validaity, try this http://stadi.hu/sw/lptdebug_en.html;  
The notebook LPT Status port, Pin#12 / Pin#13 has interal pull-up and voltage level is 5V, so EEPROM SCL / SDA has always 5V presented, does not matter the battery is connected or removed;   



# To download source code
https://sourceforge.net/projects/ponyprog/files/PonyProg%20Windows%20setup/2.08e/PonyProgV208e.zip/download

# To modify two files for the source code, detail is able to see each file with possible comments
1) globals.h, for help menu and display something about this modification task;
2) easyi2c_interf.cpp, for VCC control bit and the timing of power up & down, the mostlikely, enable VCC before read/write EEPROM, sustain VCC at each SCL/SDA bit time, then turn off VCC when close the port;  
That is the all to do.

globals.h ([xiaolaba modified version, download here](/globals.h))  
```  
#define	AUTHORWEB	"http://www.LancOS.com\r\n\r\n\
Compiled by Xiaolaba, 2017-oct-03, 測試中文, EasyI2C, LPT D4 (pin#5) used for auto power control\r\n\
How to do that : \r\n\
REF: https://github.com/xiaolaba/PonyProg2000_2.08e_xiaolaba_modification\r\n\
REF: LPT debugger http://stadi.hu/sw/lptdebug_en.html\
"
```  

easyi2c_interf.cpp ([xiaolaba modified version, download here](/easyi2c_interf.cpp))   
```  
#define POWER	3		// DATA (pin 5), Bit 3, control power to 24xx, xiaolaba 2017-sep-02
```  

As the original author has release 2.08d and 2.08e (BIN and source code) recently, both versions are compiled to fit my own need, here is the copy, just download & rename ponyprog2000-xiaolaba-2.08e_exe to be ponyprog2000-xiaolaba-2.08e.exe, then good to go. Of course to install the original PonyProg to enable IO access & DLL, it has be done before this, unless you are not the first time to uses Ponyprog  with your PC;  
https://github.com/xiaolaba/PonyProg2000_2.08e_xiaolaba_modification/blob/master/ponyprog2000-xiaolaba-2.08d_exe  
https://github.com/xiaolaba/PonyProg2000_2.08e_xiaolaba_modification/blob/master/ponyprog2000-xiaolaba-2.08e_exe  

Or try to compile the source code as what I did to learn something about MinGW cross compiling in Microsoft Windows, follow the original author and the readme. There is briefing,  
1) install MinGW  
2) copy source code the D:\ponyprog or something like that  
3) invoke MinGW (usually Msys installed as default)  
4) make -f Makefile.win cleanall  
5) make -f Makefile.win all
6) goto subfolder at your source code \bin\Windows\, there is the exe file compiled  
done  

The author also release version 3.0 just two days ago, used QT for GUI, what a coincident that I am looking for something available tools and this is, however, Win10 64bit is able to run this version 3.0 and showing more elegant GUI, but the XP PC has showing messagebox with something missing entry point of DLL and then it show nothing but quit silently by Windows default fault handler;  
.  
Ponyprog V3, Win10, ok  
![alt text](https://github.com/xiaolaba/PonyProg2000_2.08e_xiaolaba_modification/blob/master/ponyprog3.0_win10_ok.jpg)  
```
To embeds image to this read.me  
![alt text](http://url/to/img.png)  
```  
.  
.  
.  



Ponyprog V3, Windows XP, no good  
![alt text](https://github.com/xiaolaba/PonyProg2000_2.08e_xiaolaba_modification/blob/master/ponyprog3.0_XP_ng.jpg)  
```
To embeds image to this read.me  
![alt text](http://url/to/img.png)  
```  
.  
.  
.  
