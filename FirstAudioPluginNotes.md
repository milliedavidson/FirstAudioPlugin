# **First Audio Plugin Notes**

## **Intro**

I'm using a tutorial to guide me through JUCE/Projucer setups and eventually making a plugin. JUCE & Projucer are installed, I'm scanning for the plugin file I've built and have already hit a problem...

<br>
<br>

## **First Issue!**

When I do *build > options > edit the list of available plugins > options > scan for new or updated VST3s > scan* Projucer crashes.

I get the error code: **EXC_BAD_ACCESS** on line 993

![Error code in JUCE: exc bad access](Screenshots/factory.png)

Did some Googling and tried enabling zombie objects in Xcode to fix it. Used the same method as above to crash the program again and… got a different error message?!

**Line 232 EXC_BREAKPOINT code=EXC_i386_BPT**

![Error code in JUCE: exc breakpoint](Screenshots/Pasted%20Graphic%202.png)

<!--Perhaps this is the problem? https://stackoverflow.com/questions/40317901/exc-breakpoint-code-exc-i386-bpt-subcode-0x0-with-32-bit-simulator-->

Wondered if it would work with a different scan mode - changed scan mode to **out-of-process**. It no longer crashed and succesfully scanned!

![Projucer scanning for plugins in out-of-process mode](Screenshots/Available%20Plugins.png)

However, I was scanning plugins to find the plugin I’m making and it wasn’t there 😂. I don’t think it’s being built, as it doesn't seem to be *anywhere* on my system. 

Maybe the JUCE installation process went wrong? Tried reinstalling JUCE (via the website) and the plugin still isn't appearing in the list. 

I have some more things to try. Will update these notes soon!

<!--Look at docs:
https://juce.com/learn/documentation
https://juce.com/learn/tutorials-->

<br>
<br>

## **Credits**

[FreeCodeCamp.org & Matkat Music](https://www.youtube.com/watch?v=Mo0Oco3Vimo&t=350s)

[Enable zombie objects in Xcode](https://code.tutsplus.com/tutorials/what-is-exc_bad_access-and-how-to-debug-it--cms-24544)
