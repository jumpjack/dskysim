DSKYSIM - Simulator of DSKY interface of Apollo Guidance Computer

Original idea by Ron Noteborn, 2001.

--------------------

In 2022 I found by chance this tiny little page on internet:

![image](https://user-images.githubusercontent.com/1620953/151132558-5482724c-248b-49eb-afa7-16bcde3f0528.png)

It's dated 2001, more than 20 years ago; probably github didn't even exist at that time. But that page and its source look very interesting: tiny, simple, completely standalone, and easily extensible with further functionalities.

Original functionalities are indeed very simple, and summarized in the short help in the page itself, which you can find here.

But the exposed methods allow to easily interface the DSKY to any external javascript source.

I list here the highest level methods available to the developer; this is all you need to know to attach this interface to your program:

 DisplayTime(T)
 -----
  Show time in 3 registers:
  
  R1: hours
  R2: minutes
  R3: centiseconds
 
 
   function ShowRegMinSec(R, Time)
 -----
 Shows specified time in specified register; time is in seconds, display is in HH_MM format

 
 function DrawReg(R, dig0, dig1, dig2, dig3, dig4, dig5)
 ----
 
 It writes in the specified register the specified value, as per following list:
  - negative value: turn off all segments
  - 0 to 9: show the specified number
  - 10: turn off sign
  - 11: turn on minus sign
  - 12: turn on plus sign

 function HideReg(R)
 ----
 Clean register.
 
  ShowVNP(id) / HideVNP(id)
  ----
  Show/Hide Verb/Noun/Program
  
   - id = 1: show/hide current value of Verb (gobal variable VERB)
   - id = 2: show/hide current value of Noun (gobal variable NOUN)
   - id = 3: show/hide current value of Program (gobal variable PROGRAM)

 StartFlashing(Mode)
 -----
  - Mode = 0: stop flashing verb and noun
  - Mode = 1: start flashing verb
  - Mode = 2: start flashing noun
  - Mode = 3: start flashing verb and noun
 
 Note: when verb and/or noun flash, it means that AGC is awaiting for user input
 
 
 Implemented programs
 =================
 
 Currently only 2 programs are implemented:
  - Program 0: idle. AGC is doing nothing.
  - Program 40: deorbiting. Used to start descent to the Moon. Method RunProgram40()
  
  
 User input management
 ======
 User input is managed by method ProcessRequest(), ProcessRegisterEntry(Key) and PressedKey(Key)
 
 Implemented verbs
 ----
  - 5: DISPLAY OCTAL  in registers
  - 6: DISPLAY DECIMAL  in registers
  - 15: MONITOR OCTAL in registers
  - 16: MONITOR DECIMAL in registers
  - 25: LOAD in registers
  - 33: PROCEED WITHOUT DATA
  - 34: TERMINATION
  - 37: CHANGE PROGRAM
 
 Implemented nouns
 -----
  - 34: EVENT TIME
  - 35: DELTA EVENT TIME
  - 40: TFI/TCO, VG, DeltaVM (M:S, .1FPS, .1FPS)  (TFI = Time From Ignition, TCO = Time Cut Off, FPS = Feet Per Second)
  - 43: LAT/LON/ALT (.01°, .01°, .1NM)  (NM =? Nautical Miles)  (Latitude North, Longitude East, Range over Landing Site)
  - 65: SAMPLED LGC TIME (H, M, .01S)
  
  Verbs/Nouns references
  ---------
  
  ![image](https://user-images.githubusercontent.com/1620953/151140230-ab99db01-0f84-48db-9921-cefe5c5e0ea9.png)

  ![image](https://user-images.githubusercontent.com/1620953/151140782-33ff6e48-faa9-4c9d-9690-ce4d1544c303.png)
  
  ![image](https://user-images.githubusercontent.com/1620953/151142235-4f6558e9-1211-4023-96bf-823d4aa289ad.png)


  
