Apple1-Slideshow v.2020 
=======================

ASCII art slideshow for Apple-1 up to date 2020 by M.Larocca.

This slideshow updates the original one from David Schmenk
https://github.com/dschmenk/Apple1-Slideshow
and has been made using his tools and the procedure he reported in original README file. 

- - - - - - - - - - - - - - - - 

From Dave's original README:


Build Process
-------------

The build process isn't automated, so you have to run the cross assembler by hand. The assembler used is the xa 6502 assembler:

http://www.floodgap.com/retrotech/xa/

Many Linux distros will have the xa65 package available.

Once installed, build the binary with:
```
xa slideshow.a65
```
A binary, a.o65, will be produced. This can by massaged into the Apple 1 monitor format by compiling and running:
```
bintomon 280 a.o65 > slideshow.mon
```
The starting address is $280 (in 6502 hex nomenclature, 0x280 in C syntax). The resultant file, slideshow.mon, can be pasted into an emulator or copied to a real Apple 1, clone, or replica if you have the keyboard/serial port adapter.

Creating Other Artwork
----------------------

To use different artwork, You have to go through a bit of a process to get the artwork into a compatible format. Using a program like PhotoShop or The Gimp, change the image to 8 bit greyscale, then resize the image to 40x23 pixels. Save it is a net PBM file (.pbm). Convert the PBM to a RLE format with the converter:
```
pbmtorle image.pbm > image.rle
```

You have to edit the source code to use the appropriate rle file and give it a caption. The caption string is prepended with the length, so make sure it matches. When you rebuild the binary, the resultant file has to be 3456 bytes or less, assuming you want it to run on a minimal 4K Apple 1. If you have more contiguous memory, then you can fill 'er up.

Viewing RLE ASCII Artwork
-------------------------

You can view the converted ASCII artwork in your terminal by running:
```
dumprle image.rle
```

Here ends Dave's original README.

- - - - - - - - - - - - - - - - - 

From here after, my contribution to the process:

Create the .wav file by means of the program "c2t", a command line tool that can convert Apple-1 Monitor text into audio files suitable for use with the Apple-1 cassette interface. 

https://github.com/datajerk/c2t

```
./c2t/bin/c2t -1 ./slideshow.mon ./slideshow.wav
```

The slideshow audio file can now be played to the Apple-1 by means of ACI Cassette Interface 

```
C100R
	280.11F7R 
	280R

```
PLEASE BE AWARE THAT THIS FILE NEEDS THE FOLLOWING APPLE-1 JUMPER SET: 
```
X jumpered with CS0
W jumpered with CS1
```

 

