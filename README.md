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
