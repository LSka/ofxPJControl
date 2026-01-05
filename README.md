
ofxPJControl
===========

An openFrameworks addon to send commands to video projectors over a network

**Updated for openFrameworks 0.12.1**

#### Supported Projectors

- PJLink (most projectors)
- NEC projector
- CHRISTIE, SANYO and EPSON via raw string commands
- PROJECTION DESIGN (Now BARCO)

#### Dependency

 - ofxNetwork core addon
 - included the external library **QuickDigest5** https://github.com/nthnn/QuickDigest5 to replace the Poco library. (the one included in the ofxPoco addon lacks support for MD5, at least on MacOS)

#### PJLink Specification

http://pjlink.jbmia.or.jp/english/data/5-1_PJLink_eng_20131210.pdf

"PJLink enables central control of projectors manufactured by different 
vendors and projectors can be operated by a controller."

------------------------------------------------------

#### Method list:
```cpp 
	bool On(); //command to turn the projector on
	bool Off(); //command to turn the projector off
	bool sendPJLinkCommand(string command); //send any PJLink command to the projector
	void setup(string IP_add="192.168.0.100",int protocol=PJLINK_MODE, string password=""); //default
	void setProjectorType(int protocol); //NEC_MODE, PJLINK_MODE, etc
	void setProjectorIP(string IP_add); //the network IP of the projector
	void setProjectorPassword(string passwd); //password for PJLink authentication
	bool getProjectorStatus(); //return whether projector is on (true) or off (false)  
	void setProjectorPort(int port); //the network port of the projector
	bool sendCommand(string command); //send any string command to the projector without password authentication
	
```

#### Projector Mode list: 
```cpp
  PJLINK_MODE
  NEC_MODE
  CHRISTIE_MODE
  SANYO_MODE
  PJDESIGN_MODE
```  
------------------------------------------------------

#### Example:

Step 1. in the testApp.h: 
```cpp	
#include "ofxPJControl.h"	
ofxPJControl projector1;
```

Step 2. in the testApp.cpp:

```cpp	
//Your projectors IP, and if its not PJLINK try another mode. 
projector1.setup("192.168.1.281",PJLINK_MODE,"mypassword"); 
projector1.On();
projector1.Off(); 
```

#### Credits

* original addon by [Noah Shibley](https://github.com/nullboundary)
* updated version by [LSKA](https://github.com/LSka/)
* QuickDigest5 library by [Nathanne Isip](https://github.com/nthnn)


