# SourdoughBreadBoy🕹️✊

<img src="images/breadboy_with_slide.jpg" width="400">
<img src="images/sourdough_life.jpg" width="400">

Historical materialist fork of the Arduino based [BreadBoy](https://github.com/MrBlinky/Arduboy-homemade-package#pin-wiring-table) via the [Arduboy Community Forum](https://community.arduboy.com/t/breadboy-a-100-non-soldering-homemade-arduboy/5910) a non-soldering DIY breadboard based arduino gameboy based on the [Arduboy](https://arduboy.com/).

It is a handheld version of the [Mikroskopisk PacMan](https://youtu.be/GvZm9EXqrdU) project and an experiment in the field of biotic gaming and part of ongoing playful *natureculture* experiments in critical making inspired by Science and Technology Studies, [ArcadeDeBruno](https://domesticscience.org.uk/criticalkits/InF.html)

We use the [Slimboy Arduboy2 fork](https://github.com/harbaum/Arduboy2) to make a resource constrained platform for experimenting with handheld microscopic inter-species gaming using [Prakash Labs](https://web.stanford.edu/group/prakash-lab/cgi-bin/labsite/) DIY paper [Foldscope](https://www.foldscope.com/). Combined with the scientific craft practices of microbiologist and engineer [Alexandre Benedetto's](https://www.lancaster.ac.uk/health-and-medicine/about-us/people/alexandre-benedetto) PDMS microfluidic techniques, which we explore in the [Lab From A Chip](cheapjack.github.io/LabFromAChip/) kit which the Breadboy is compatible with. Games on the platform allow graphics to interact with *Euglena gracilis* a ubiquitous light sensitive photosynthesising algae in microfluidic environments made from impressions of old vinyl record grooves. The default game to play is [Conways Game Of Life](https://conwaylife.com/wiki/Conway%27s_Game_of_Life)

SourdoughBreadboy is a speculative handheld gaming platform for a variety of slide based microbiological experiments for learning;

 * Simple protist protest environments
 * Identifying and counting yeast
 * DIY PDMS moulded environments from domestic 'capitalist ruins', ie old electronics and utensils and contribute to a social media based community of moulders

## Requirements

 * [Arduboy 2 SlimBoy](https://github.com/harbaum/Arduboy2)
   * Arduino Nano
   * 128 x 64 I<sup>2</sup>C LCD screen 
   * 4 x Microbreadboards
   * 3 x 220 Ohm Resistors
   * 1 x 10K Ohm Resistor
   * Piezo mic/speaker
   * jumper wires and 6 breadboard headers
   * USB A to USB
 * [Lab From A Chip](cheapjack.github.io/LabFromAChip/) Kit
   * Foldscope
   * Standard Microscope Slide
   * Micro petri dish
   * Tweezers
   * PDMS mix and hardener
 * [Conways Game Of Life](https://github.com/MLXXXp/ArduboyLife)

## References

 * [MrBlinky Homemade Package](https://github.com/MrBlinky/Arduboy-homemade-package)
 * [Arduboy Life](https://github.com/MLXXXp/ArduboyLife)
 * [Arduboy 2: Alternative Library Life uses](https://github.com/MLXXXp/Arduboy2)
 * [Arduboy Original](https://github.com/Arduboy/Arduboy)
 * [Handy Pin notes for doing SPI with Milecastles screens](https://github.com/cheapjack/MileCastles/blob/master/boxes/AssemblyWiring.md#screen)

## MET Matrix

[MET Matrix](MET_Matrix.md)

Map out the energy toxicity matrix so we trace the complete carbon cost of your build using the [Materials Energy Toxicity Matrix](http://thingscon2018.productscience.net/) developed at OMGCLIMATE 2019. We found this via [@mrchrisadams](https://twitter.com/mrchrisadams) excellent talk on [Reducing Carbon In the Digital Realm](https://docs.google.com/presentation/d/1_uTPiW5aMCwFhZcpLDxjY-AQMgDmHIyUEZQQ-G6XXq8/edit#slide=id.g5d9e2f62d2_0_42) at [Maintenance Festival 2019 in Liverpool](https://festivalofmaintenance.org.uk)

# SLIMBOY - Arduboy2 port to Arduino Nano and I²C display

This is a port of the original Arduboy2 code to the simpler and cheaper Arduino Nano and an I²C display.

![Breadboard setup](images/breadboard.png)

The SLIMBOY setup has a few limitations over the original solution:

 - The I²C connection is slower than SPI and the framerate slightly suffers on some games. The current setup has been optimized for speed and runs nearly as smooth as the SPI version
 - The Atmega328 on the Arduino Nano has some limitations over the  Atmega32u4 of the original Arduboy
   - It has fewer timers and thus some custom sound libraries won't work 100%
   - It has 500 bytes less ram
   - It has less PWM pins and thus the green LED cannot be dimmed

These limitations only have a very minor impact on the usability and games like ShadowRunner just run fine on the SLIMBOY.

## Related

Several sound libraries exist for the Arduboy. Some of them have also
been ported the the Nano:

 - Matching port of [ArduboyTones](https://github.com/harbaum/ArduboyTones)
 - Matching port of [ATMlib](https://github.com/harbaum/ATMlib)

## Games tested on the Arduino Nano

 - ArduBreakout
 - ArduboyLife
 - Shadow-Runner
 - VIRUS-LQP-79
 - Pinball
 - Nineteen43

# Arduboy2 Library

The Arduboy2 library is maintained in a git repository hosted on [GitHub](https://github.com/MLXXXp/Arduboy2)

The **Arduboy2** library is a fork of the [Arduboy library](https://github.com/Arduboy/Arduboy), which provides a standard *application programming interface* (API) to the display, buttons and other hardware of the Arduino based [Arduboy miniature game system](https://www.arduboy.com/).

The name *Arduboy2* doesn't indicate that it's for a new "next generation" of the Arduboy hardware. The name was changed so it can coexist in the Arduino IDE with the current *Arduboy* library, without conflict. This way, existing sketches can continue to use the *Arduboy* library and class, without changes, while new sketches can be written (or old ones modified) to use and take advantage of the capabilities of the *Arduboy2* class and library.

For notes on the differences between the *Arduboy2* library and the original *Arduboy* library, and for information on migrating a sketch currently using the *Arduboy* library, see the sections at the end of this document.

## Library documentation

Comments in the library header files are formatted for the [Doxygen](http://www.doxygen.org) document generation system. The HTML files generated using the configuration file _extras/Doxyfile_ can be found at:

https://MLXXXp.github.io/documents/Arduino/libraries/Arduboy2/Doxygen/html/index.html

A generated PDF file can be found at:

https://MLXXXp.github.io/documents/Arduino/libraries/Arduboy2/Doxygen/pdf/Arduboy2.pdf

## Installation

Easiest method is to install [Arduino](https://arduino.cc) and  [git](https://git-scm.com/)
Then go to your Arduino Sketchbook folder location and the `libraries` folder inside

`cd path/to/my/Arduino/Sketchbook/Folder/libraries`

Run `git clone https://github.com/harbaum/Arduboy2.git`

The restart your Arduino programme and the Arduboy2 examples will appear in `File/Examples/Examples From Custom Libraries`

Connect the Arduino Micro by usb; find the port in the Arduino `Tools` menu

Then select the Aruduino Nano board and check it compiles ok. Then upload to the board and check the buttons work.

The Arduboy2 library can also be installed using the Arduino IDE Library Manager but use the slimboy library you can download as a zip from [harbaum](https://github.com/harbaum/Arduboy2)

- In the Arduino IDE select from the menus: `Sketch > Include Library > Manage Libraries...`
- In the Library Manager *Filter your search...* field enter *arduboy2*.
- Click somewhere within the Arduboy2 entry.
- Click on the *Install* button.

For more library installation information see

[Installing Additional Arduino Libraries - Using the Library Manager](https://www.arduino.cc/en/Guide/Libraries#toc3)

## Installing Arduboy Life

Again go to your Arduino Sketchbook folder location but don't enter the libraries directory

`cd path/to/my/Arduino/Sketchbook/Folder/`

Run `git clone https://github.com/MLXXXp/ArduboyLife.git`

The restart your Arduino programme and the ArduboyLife game will be available in `File/Sketchbook` in the Arduino software.



## Start up features

The *begin()* function, used to initialize the library, includes features that are intended to be available to all sketches using the library (unless the sketch developer has chosen to disable one or more of them to free up some code space):

### The boot logo

At the start of the sketch, the **ARDUBOY** logo scrolls down from the top of the screen to the center.

The RGB LED lights red then green then blue while the logo is scrolling. (If your Arduboy is one of those that has the RGB LED installed incorrectly, then it will light blue then off then red). For users who do not wish to have the RGB LED flash during the boot logo sequence, a flag can be set in system EEPROM to have it remain off. The included *SetSystemEEPROM* example sketch can be used to set this flag.

A user settable *unit name* of up to 6 characters can be saved in system EEPROM memory. If set, this name will be briefly displayed at the bottom of the boot logo screen, after the logo stops scrolling down. This feature is only available if the *Arduboy2* class is used, not the *Arduboy2Base* class. This is because it requires the text display functions, which are only available in the *Arduboy2* class. A flag in system EEPROM controls whether or not the *unit name* is displayed on the boot logo screen, regardless of whether the *unit name* itself has been set. The included *SetSystemEEPROM* example sketch can be used to set both the *unit name* and this flag.

Once the logo display sequence completes, the sketch continues.

For developers who wish to quickly begin testing, or impatient users who want to go strait to playing their game, the boot logo sequence can be bypassed by holding the *RIGHT* button while powering up, and then releasing it. Alternatively, the *RIGHT* button can be pressed while the logo is scrolling down.

For users who wish to always disable the displaying of the boot logo sequence on boot up, a flag in system EEPROM is available for this. The included *SetSystemEEPROM* example sketch can be used to set this flag.

### "Flashlight" mode

If the *UP* button is pressed and held when the Arduboy is powered on, it enters *flashlight* mode. This turns the RGB LED fully on, and all the pixels of the screen are lit, resulting in a bright white light suitable as a small flashlight. (For an incorrect RGB LED, only the screen will light). To exit *flashlight* mode the Arduboy must be restarted.

*Flashlight* mode is also sometimes useful to allow uploading of new sketches, in case the sketch currently loaded uses a large amount of RAM which creates a bootloader problem.

### Audio mute control

Pressing and holding the *B* button when powering on will enter *System Control* mode. The RGB LED will light blue (red for an incorrect LED) to indicate that you are in *system control* mode. You must continue to hold the *B* button to remain in this mode. The only *system control* function currently implemented is *audio mute control*.

Pressing the *UP* button (while still holding *B*) will set a flag in system EEPROM indicating *audio enabled*. The RGB LED will flash green once (off for an incorrect LED) to indicate this action.

Pressing the *DOWN* button (while still holding *B*) will set the flag to *audio disabled* (muted). The RGB LED will flash red once (blue for an incorrect LED) to indicate this action.

Releasing the *B* button will exit *system control* mode and the sketch will continue.

Note that the audio control feature only sets a flag in EEPROM. Whatever code actually produces the sound must use the *audio.enabled()* function to check and honor the mute state. Audio libraries written with the Arduboy system in mind, such as the available *ArduboyPlaytune* and *ArduboyTones*, should do this. However, be aware that for some sketches, which don't use the Arduboy2 or other compliant library and generate sounds in their own way, this method of muting sound may not work.

## Using the library in a sketch

As with most libraries, to use Arduboy2 in your sketch you must include its header file at the start:

```cpp
#include <Arduboy2.h>
```

You must then create an Arduboy2 class object:

```cpp
Arduboy2 arduboy;
```

Naming the object *arduboy* has become somewhat of a standard, but you can use a different name if you wish.

To initialize the library, you must call its *begin()* function. This is usually done at the start of the sketch's *setup()* function:

```cpp
void setup()
{
  arduboy.begin();
  // more setup code follows, if required
}
```

The rest of the Arduboy2 functions will now be available for use.

If you wish to use the Sprites class functions you must create a Sprites object:

```cpp
Sprites sprites;
```

Sample sketches have been included with the library as examples of how to use it. To load an example, for examination and uploading to the Arduboy, using the Arduino IDE menus select:

`File > Examples > Arduboy2`

More information on writing sketches for the Arduboy can be found in the [Arduboy Community Forum](http://community.arduboy.com/).

### Using EEPROM in a sketch

The Arduboy2 library reserves an area at the start of EEPROM for storing system information, such as the current audio mute state and the Unit Name and Unit ID. A sketch **must not** use this reserved area for its own purposes. A sketch may use any EEPROM past this reserved area. The first EEPROM address available for sketch use is given as the defined value *EEPROM_STORAGE_SPACE_START*

### Audio control functions

The library includes an Arduboy2Audio class. This class provides functions to enable and disable (mute) sound and also save the current mute state so that it remains in effect over power cycles and after loading a different sketch. It doesn't contain anything to actually produce sound.

The Arduboy2Base class, and thus the Arduboy2 class, creates an Arduboy2Audio class object named *audio*, so a sketch doesn't need to create its own Arduboy2Audio object.

Example:

```cpp
#include <Arduboy2.h>

Arduboy2 arduboy;

// Arduboy2Audio functions can be called as follows:
  arduboy.audio.on();
  arduboy.audio.off();
```

### Simple tone generation

The *BeepPin1* and *BeepPin2* classes are available to generate simple square wave tones using speaker pin 1 and speaker pin 2 respectively. These classes are documented in file *Arduboy2Beep.h*. Also, *BeepDemo* is included as one of the example sketches, which demonstrates basic use.

NOTE: These functions will not work with a DevKit Arduboy because the speaker pins used cannot be directly controlled by a timer/counter. "Dummy" functions are provided so a sketch will compile and work properly but no sound will be produced.

### Ways to make more code space available to sketches

#### Sound effects and music

If all you want is to play single tones, using the built in *BeepPin1* or *BeepPin2* classes will be very efficient.

If you want to be able to play sequences of tones or background music, using the [*ArduboyTones*](https://github.com/MLXXXp/ArduboyTones) library will be more code efficient than using [*ArduboyPlaytune*](https://github.com/Arduboy/ArduboyPlayTune) or most other sound libraries compatible with the Arduboy. *ArduboyTones* even produces less code than the [Arduino built in *tone()* function](https://www.arduino.cc/en/Reference/Tone). You'll have to decide on the appropriate library or functions you use to generate sound, based on the features required and how much memory you want it to use.

#### Remove the text functions

If your sketch doesn't use any of the functions for displaying text, such as *setCursor()* and *print()*, you can remove them. You could do this if your sketch generates whatever text it requires by some other means. Removing the text functions frees up code by not including the font table and some code that is always pulled in by inheriting the [Arduino *Print* class](http://playground.arduino.cc/Code/Printclass).

To eliminate text capability in your sketch, when creating the library object simply use the *Arduboy2Base* class instead of *Arduboy2*:

For example, if the object will be named *arduboy*:

Replace

```cpp
Arduboy2 arduboy;
```

with

```cpp
Arduboy2Base arduboy;
```

#### Remove boot up features

As previously described, the *begin()* function includes features that are intended to be available to all sketches during boot up. However, if you're looking to gain some code space, you can call *boot()* instead of *begin()*. This will initialize the system but not include any of the extra boot up features. If desired, you can then add back in any of these features by calling the functions that perform them. You will have to trade off between the desirability of having a feature and how much memory you can recover by not including it.

A good way to use *boot()* instead of *begin()* is to copy the code from the body of the *begin()* function, in file *Arduboy2.cpp*, into your sketch and then edit it to retain the *boot()* call and any feature calls desired.

As of this writing, the begin function is:

```cpp
void Arduboy2Base::begin()
{
  boot(); // raw hardware

  display(); // blank the display (sBuffer is global, so cleared automatically)

  flashlight(); // light the RGB LED and screen if UP button is being held.

  // check for and handle buttons held during start up for system control
  systemButtons();

  audio.begin();

  bootLogo();

  waitNoButtons(); // wait for all buttons to be released
}
```

To incorporate it into your sketch just keep *boot()* and whatever feature calls are desired, if any. Comment out or delete the rest. Remember to add the class object name in front of each function call, since they're now being called from outside the class itself. If your sketch uses sound, it's a good idea to keep the call to *audio.begin()*.

For example: Let's say a sketch has its own code to enable, disable and save the *audio on/off* setting, and wants to keep the *flashlight* function. In *setup()* it could replace *begin()* with:

```cpp
  arduboy.boot(); // raw hardware

// *** This particular sketch clears the display soon, so it doesn't need this:
//  display(); // blank the display (sBuffer is global, so cleared automatically)

  arduboy.flashlight(); // light the RGB LED and screen if UP button is being held.

  // check for and handle buttons held during start up for system control
//  systemButtons();

  arduboy.audio.begin();

//  bootLogo();

//  waitNoButtons(); // wait for all buttons to be released
```

This saves whatever code *display()*, *systemButtons()*, *bootLogo()* and *waitNoButtons()* would use.

There are a few functions provided that are roughly equivalent to the standard functions used by *begin()* but which use less code space.

- *bootLogoCompressed()*, *bootLogoSpritesSelfMasked()*, *bootLogoSpritesOverwrite()*, *bootLogoSpritesBSelfMasked()* and *bootLogoSpritesBOverwrite()* will do the same as *bootLogo()* but will use *drawCompressed()*, or *Sprites* / *SpritesB* class *drawSelfMasked()* or *drawOverwrite()* functions respectively, instead of *drawBitmask()*, to render the logo. If the sketch uses one of these functions, then using the boot logo function that also uses it may reduce code size. It's best to try each of them to see which one produces the smallest size.
- *bootLogoText()* can be used in place *bootLogo()* in the case where the sketch uses text functions. It renders the logo as text instead of as a bitmap (so doesn't look as good).
- *safeMode()* can be used in place of *flashlight()* for cases where it's needed to allow uploading a new sketch when the bootloader "magic key" problem is an issue. It only lights the red RGB LED, so you don't get the bright light that is the primary purpose of *flashlight()*.

#### Use the SpritesB class instead of Sprites

The *SpritesB* class has functions identical to the *Sprites* class. The difference is that *SpritesB* is optimized for small code size rather than execution speed. If you want to use the sprites functions, and the slower speed of *SpritesB* doesn't affect your sketch, you may be able to use it to gain some code space.

Even if the speed is acceptable when using *SpritesB*, you should still try using *Sprites*. In some cases *Sprites* will produce less code than *SpritesB*, notably when only one of the functions is used.

You can easily switch between using *Sprites* or *SpritesB* by using one or the other to create an object instance:

```cpp
Sprites sprites;  // Use this to optimize for execution speed
SpritesB sprites; // Use this to (likely) optimize for code size
```

#### Eliminate the USB stack code

**Warning:** Although this will free up a fair amount of code and some RAM space, without an active USB interface uploader programs will be unable to automatically force a reset to invoke the bootloader. This means the user will have to manually initiate a reset in order to upload a new sketch. This can be an inconvenience or even frustrating for a user, due to the fact that timing the sequence can sometimes be tricky. Therefore, using this technique should be considered as a last resort. If it is used, the sketch documentation should state clearly what will be involved to upload a new sketch.

The *ARDUBOY_NO_USB* macro is used to eliminate the USB code. The *exitToBootloader()* function is available to make it easier for a user to invoke the bootloader. For more details, see the documentation provided for these.

----------

## What's different from Arduboy library V1.1

A main goal of Arduboy2 is to provide ways in which more code space can be freed for use by large sketches. Another goal is to allow methods other than the *tunes* functions to be used to produce sounds. Arduboy2 remains substantially compatible with [Arduboy library V1.1](https://github.com/Arduboy/Arduboy/releases/tag/v1.1), which was the latest stable release at the time of the fork. Arduboy2 is based on the code targeted for Arduboy library V1.2, which was still in development and unreleased at the time it was forked.

Main differences between Arduboy2 and Arduboy V1.1 are:

- The *ArduboyTunes* subclass, which provided the *tunes.xxx()* functions, has been removed. It's functionality is available in a separate [*ArduboyPlaytune* library](https://github.com/Arduboy/ArduboyPlayTune). By removing these functions, more code space may become available because interrupt routines and other support code was being compiled in even if a sketch didn't make use them. Another benefit is that without the automatic installation of timer interrupt service routines, other audio generating functions and libraries, that need access to the same interrupts, can now be used. Removal of the *tunes* functions is the main API incompatibility with Arduboy V1.1. Sketches written to use *tunes* functions will need some minor modifications in order to make them work with Arduboy2 plus ArduboyPlaytune, [ArduboyTones](https://github.com/MLXXXp/ArduboyTones), or some other audio library.
- Arduboy library V1.1 uses timer 1 for the *tunes* functions. This causes problems when attempting to control the Arduboy's RGB LED using PWM, such as with *setRGBled()*, because it also requires timer 1. Since the *tunes* functionality has been removed from Arduboy2, there are no problems with using the RGB LED (except those caused by the RGB LED being incorrectly installed). Of course, using an external library that uses timer 1, such as *ArduboyPlaytune*, may reintroduce the problems. However, using a library that doesn't use timer 1, such as *ArduboyTones*, is now an option.
- The code to generate text output, using *setCursor()*, *print()*, etc., can be removed to free up code space, if a sketch doesn't use any text functions. The *Arduboy2* class includes the text functions but using the *Arduboy2Base* class instead will eliminate them. With text functions included, the font table and some support functions are always compiled in even if not used. The API for using text functions is the same as Arduboy V1.1 with some additional functions added:
 - *setTextColor()* and *setTextBackground()* allow for printing black text on a white background.
 - *getCursorX()* and *getCursorY()* allow for determining the current text cursor position.
 - The *clear()* function will now reset the text cursor to home position 0, 0.
- A new feature has been added which allows the *audio on/off* flag in system EEPROM to be configured by the user when the sketch starts. The flag is used by the Arduboy and Arduboy2 *audio* subclass, along with external sound functions and libraries, to provide a standardized sound mute capability. See the information above, under the heading *Audio mute control*, for more details.
- The *color* parameter, which is the last parameter for most of the drawing functions, has been made optional and will default to WHITE if not included in the call. This doesn't save any code but has been added as a convenience, since most drawing functions are called with WHITE specified.
- A new function *digitalWriteRGB()* has been added to control the RGB LED digitally instead of using PWM. This uses less code if just turning the RGB LEDs fully on or off is all that's required.
- The *beginNoLogo()* function is not included. This function could be used in Arduboy V1.1 in place of *begin()* to suppress the displaying of the ARDUBOY logo and thus free up the code that it required. Instead, Arduboy2 allows a sketch to call *boot()* and then add in any extra features that *begin()* provides by calling their functions directly after *boot()*, if desired.
- The *ArduboyCore* and *ArduboyAudio* base classes, previously only available to, and used to derive, the *Arduboy* class, have been made publicly available for the benefit of developers who may wish to use them as the base of an entirely new library. This change doesn't affect the existing API.

As of version 2.1.0 functionality from the [Team A.R.G.](http://www.team-arg.org/) *Arglib* library has been added:

- The sprite drawing functions, collision detection functions, and button handling functions that Team A.R.G. incorporated from the [ArduboyExtra](https://github.com/yyyc514/ArduboyExtra) project. The *poll()* function was renamed *pollButtons()* for clarity. The *Sprites* class doesn't require a parameter for the constructor, whereas in *Arglib* a pointer to an Arduboy class object is required.
- The *drawCompressed()* function, which allows compressed bitmaps to be drawn. Saving bitmaps in compressed form may reduce overall sketch size.

Team A.R.G. has now migrated all of their games and demos to use the Arduboy2 library.

## Migrating a sketch from Arduboy library V1.1 to Arduboy2

Since the Arduboy2 library can coexist in the Arduino IDE alongside the Arduboy library V1.1, a currently working sketch that uses Arduboy V1.1 doesn't have to be migrated to Arduboy2. However, if you want to switch a sketch to Arduboy2 for further development, in order to take advantage of any of the changes and enhancements, it's generally relatively easy.

The Arduboy2 library, for the most part, is compatible with Arduboy library V1.1 but migrating a sketch to Arduboy2 will require some small changes, and more so if it uses the *tunes* functions, such as *tunes.tone()* or *tunes.playScore()*.

### Required changes

The first thing to do is change the `include` for the library header file:

```cpp
#include <Arduboy.h>
```

becomes

```cpp
#include <Arduboy2.h>
```

If it was "Arduboy.h" (in quotes), it's still better to change it to &lt;Arduboy2.h&gt; (in angle brackets).

The same thing has to be done with creating the library object. (If the object name isn't *arduboy*, keep whatever name is used.):

```cpp
Arduboy arduboy;
```

becomes

```cpp
Arduboy2 arduboy;
```

If the sketch doesn't use any *tunes* functions, there's a good chance this is all that has to be done to make it compile.

### Sketch uses only *tunes.tone()* for sound

If the sketch has sound but only uses *tunes.tone()*, solutions are:

#### Solution 1: Switch to using Arduino *tone()*

An easy change is to use the Arduino built in *tone()* function. You can add a function to the sketch that wraps *tone()* so that it works like *tunes.tone()*, like so:

```cpp
// Wrap the Arduino tone() function so that the pin doesn't have to be
// specified each time. Also, don't play if audio is set to off.
void playTone(unsigned int frequency, unsigned long duration)
{
  if (arduboy.audio.enabled() == true)
  {
    tone(PIN_SPEAKER_1, frequency, duration);
  }
}
```

You then change all *tunes.tone()* calls to *playTone()* calls using the same parameter values. For example:

```cpp
  arduboy.tunes.tone(1000, 250);
```

becomes

```cpp
  playTone(1000, 250);
```

#### Solution 2: Switch to using the ArduboyTones library

Changing to the *ArduboyTones* library is slightly more complicated. The advantage is that it will generate less code than using *tone()* and will also allow you to easily enhance the sketch to play tone sequences instead of just single tones. ArduboyTones can also play each tone at either normal or a higher volume.

You have to add an include for the ArduboyTones header file:

```cpp
#include <ArduboyTones.h>
```

You then have to create an object for the *ArduboyTones* class and pass it a pointer to the Arduboy2 *audio.enabled()* function. This must go after the creation of the Arduboy2 object, like so:

```cpp
Arduboy2 arduboy;
ArduboyTones sound(arduboy.audio.enabled);
```

You then change all Arduboy *tunes.tone()* calls to ArduboyTones *tone()* calls using the same parameter values. For example:

```cpp
  arduboy.tunes.tone(1000, 250);
```

becomes

```cpp
  sound.tone(1000, 250);
```

See the [ArduboyTones](https://github.com/MLXXXp/ArduboyTones) README file for more information on installing and using it.

#### Solution 3: Switch to using the ArduboyPlaytune library.

See the following for how to do this:

### Sketch uses *tunes.playScore()*

If the sketch uses *tunes.playScore()*, probably the easiest solution is to use the *ArduboyPlaytune* library. *ArduboyPlaytune* is essentially the code that was in the Arduboy V1.1 *tunes* subclass, which has been removed from Arduboy2. It's been cleaned up and a few enhancements have been added, but all the Arduboy V1.1 *tunes* functions are available.

You have to add an include for the ArduboyPlaytune header file:

```cpp
#include <ArduboyPlaytune.h>
```

You then have to create an object for the *ArduboyPlaytune* class and pass it a pointer to the Arduboy2 *audio.enabled()* function. This must go after the creation of the Arduboy2 object, like so:

```cpp
Arduboy2 arduboy;
ArduboyPlaytune tunes(arduboy.audio.enabled);
```

The sound channels must then be initialzed and assigned to the speaker pins. This code would go in the *setup()* function:

```cpp
  // audio setup
  tunes.initChannel(PIN_SPEAKER_1);
#ifndef AB_DEVKIT
  // if not a DevKit
  tunes.initChannel(PIN_SPEAKER_2);
#else
  // if it's a DevKit
  tunes.initChannel(PIN_SPEAKER_1); // use the same pin for both channels
  tunes.toneMutesScore(true);       // mute the score when a tone is sounding
#endif
```

If you name the ArduboyPlaytune object *tunes* as shown above, then you just have to remove the Arduboy object name from any *tunes* calls. For example:

```cpp
  arduboy.tunes.playScore(mySong);
```

becomes

```cpp
  tunes.playScore(mySong);
```

See the [*ArduboyPlaytune* library](https://github.com/Arduboy/ArduboyPlayTune) documentation for more information.

If you don't need to play scores containing two parts, and don't require tones to be played in parallel with a score that's playing, then as an alternative to using *ArduboyPlaytune* you may wish to consider switching to *ArduboyTones*. This may require a bit of work because any *ArduboyPlaytune* scores would have to be converted to *ArduboyTones* format. It would involve changing note numbers to frequencies. This could be simplified by using the provided *NOTE_* defines. Also, durations would have to be converted, including adding silent "rest" tones as necessary.

The benefit of using *ArduboyTones* would be reduced code size and possibly easier addition of new sequences without the need of a MIDI to Playtune format converter.

### Sketch uses the *beginNoLogo()* function instead of *begin()*

The *beginNoLogo()* function has been removed. Instead, *boot()* can be used with additional functions following it to add back in desired boot functionality. See the information above, under the heading *Remove boot up features*, for more details. Assuming the object is named *arduboy*, a direct replacement for *beginNoLogo()* would be:

```cpp
  arduboy.boot();
  arduboy.display();
  arduboy.flashlight();
  arduboy.audio.begin();
```

----------


