**DSKYSIM - Simulator of DSKY interface of Apollo Guidance Computer**

Original idea by Ron Noteborn, 2001.

--------------------

In 2022 I found by chance [this tiny](http://apollo.spaceborn.dk/dsky-sim.html) page on internet:

![image](https://user-images.githubusercontent.com/1620953/151132558-5482724c-248b-49eb-afa7-16bcde3f0528.png)

It's dated 2001, more than 20 years ago; probably github didn't even exist at that time. But that page and its source look very interesting: tiny, simple, completely standalone, and easily extensible with further functionalities.

Original functionalities are indeed very simple, and summarized in the short help in the page itself, which you can find [here](https://github.com/jumpjack/dskysim/wiki/Original-help).

But the exposed methods allow to easily interface the DSKY to any external javascript source, so I plan to write an "Apollo 11 LEM descent AGC replayer", which will replay status of lamps and registers of DSKY as recorded on july, 20th, 1969. 

Telemetries are available [here](http://www.ibiblio.org/apollo/Documents/apollo_11_computer_words.pdf).

I am trying to decode them [here](https://github.com/jumpjack/dskysim/wiki/Decoding-AGC-telemetries).

High resolution scans of single pages are available [here](https://ia902308.us.archive.org/view_archive.php?archive=/27/items/apollo_11_computer_words/apollo_11_computer_words_jp2.zip).


I list in [this page](https://github.com/jumpjack/dskysim/wiki/Dskysim-methods) the highest level methods available to the developer; this is all you need to know to attach this interface to your program.

# DSKYSIM2

My idea is to upgrade and extend DSKYSIM and turn it into a "DSKY replayer" or "AGC replayer": using the original Apollo 11 telemetries recently discoverd by [VistualAGC team](https://github.com/virtualagc/virtualagc), I will try to make my DSKY simulator show the real status of AGC during the Apollo 11 powered descent: lamps, messages, data, everything. Around a hundred of telemetries were sent by AGC to ground every 2 seconds; although the found document does not contain all of them, it contains:
- status of all the DSKY lamps
- contents of all AGC registers
- values of nouns and verbs selected by crew
- status of DSKY keyboard


This is all I need to bring DSKY/AGC replayer to life.... but there are a lot more:
- values of computer [flagwords](https://github.com/virtualagc/virtualagc/blob/a9f2fd2d4c313497bbf98e80a0cbef0dc87faf09/LMY99R0/FLAGWORD_ASSIGNMENTS.agc) from 4 to 11 (15bit x 12 = 180 bit, 1 bit unused in each flagword)
- values of computer [channels](https://github.com/virtualagc/virtualagc/blob/a9f2fd2d4c313497bbf98e80a0cbef0dc87faf09/LMY99R0/INPUT_OUTPUT_CHANNEL_BIT_DESCRIPTIONS.agc) 11-14 and 30-33
- status of RHC (joystick which controlled rotation of the LM)
- status of THC (joystick which controlled translation of the LM)
- orientation of the main engine gimbal (Descent Propulsion System - DPS, or Engine Control Assembly - ECA, aka "the bell" for friends)
- spacecraft roll, pitch and yaw (in CDU data)
- alarms status (1201, 1202....)

# Other sources of data
There are other projects showing "realtime" data for Apollo 11, mostrly focused on transcripts; only "first man on the moon" shows some telemetries (commander heart rate, spacecraft pitch), but they are not available as raw data and there is no source available:
 - https://project.exploreapollo.org/
 - https://apolloinrealtime.org/11/
 - https://www.firstmenonthemoon.com/

My repository [Apollo11LEMdata](https://github.com/jumpjack/Apollo11LEMdata), derived from the apparently abandoned [jamescarruthers/Apollo11LEMdata](https://github.com/jamescarruthers/Apollo11LEMdata) , contains all the telemetries charts I was able to find aorund in some documents "hidden" on several server around nthe world.
