# The new meta

Category: Forensics, 100 points

# Description

> Can you find the flag in this beautiful landscape?

What is **metadata**?

What is **base64**?

What is a **Vignere Cipher**?

# Solution

We instantly know that the flag is going to be in the metadata of the jpg they gave.

Thus, we can use the tool **exiftool** to view the metadata of the jpg

`exiftool meta.jpg`

Doing so gives us the data: 

```
exiftool meta.jpg
ExifTool Version Number         : 11.88
File Name                       : meta.jpg
Directory                       : .
File Size                       : 3.8 MB
File Modification Date/Time     : 2022:08:19 16:38:14-04:00
File Access Date/Time           : 2022:08:19 16:41:34-04:00
File Inode Change Date/Time     : 2022:08:19 16:38:14-04:00
File Permissions                : rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
Exif Byte Order                 : Big-endian (Motorola, MM)
Compression                     : JPEG (old-style)
Image Description               : SGVyZSBpcyBteSBzdXBlciBzZWNyZXQgcGFzc3dvcmQhICJSUElTQU5FUkQi
Make                            : samsung
Camera Model Name               : SM-G973U
Orientation                     : Horizontal (normal)
X Resolution                    : 72
Y Resolution                    : 72
Resolution Unit                 : inches
Software                        : G973USQS4ETJ1
Modify Date                     : 2020:11:06 15:10:09
Artist                          : U29ycnkgTm90IHRoZSBGbGFnIQ==
Y Cb Cr Positioning             : Centered
Copyright                       : YzN0e3MwX3YzcnlfbTN0NF8zfQ==
Exposure Time                   : 1/907
F Number                        : 2.4
Exposure Program                : Program AE
ISO                             : 50
Exif Version                    : 0220
Date/Time Original              : 2020:11:06 15:10:09
Create Date                     : 2020:11:06 15:10:09
Components Configuration        : Y, Cb, Cr, -
Shutter Speed Value             : 1/906
Aperture Value                  : 2.4
Brightness Value                : 8.3
Exposure Compensation           : 0
Max Aperture Value              : 1.5
Metering Mode                   : Spot
Flash                           : No Flash
Focal Length                    : 4.3 mm
User Comment                    : Base15 + Base49
Sub Sec Time                    : 062121
Sub Sec Time Original           : 062121
Sub Sec Time Digitized          : 062121
Flashpix Version                : 0100
Color Space                     : sRGB
Exif Image Width                : 4032
Exif Image Height               : 3024
Interoperability Index          : R98 - DCF basic file (sRGB)
Interoperability Version        : 0100
Sensing Method                  : Not defined
Scene Type                      : Directly photographed
Exposure Mode                   : Auto
White Balance                   : Auto
Focal Length In 35mm Format     : 26 mm
Scene Capture Type              : Standard
Owner Name                      : S2VlcCBvbiB0cnlpbmch
GPS Latitude Ref                : North
GPS Longitude Ref               : West
GPS Altitude Ref                : Above Sea Level
GPS Time Stamp                  : 20:09:52
GPS Processing Method           : G
GPS Date Stamp                  : 2020:11:06
Thumbnail Offset                : 1364
Thumbnail Length                : 31904
Image Width                     : 4032
Image Height                    : 3024
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Time Stamp                      : 2020:11:06 15:10:09-05:00
Aperture                        : 2.4
Image Size                      : 4032x3024
Megapixels                      : 12.2
Scale Factor To 35 mm Equivalent: 6.0
Shutter Speed                   : 1/907
Create Date                     : 2020:11:06 15:10:09.062121
Date/Time Original              : 2020:11:06 15:10:09.062121
Modify Date                     : 2020:11:06 15:10:09.062121
Thumbnail Image                 : (Binary data 31904 bytes, use -b option to extract)
GPS Altitude                    : 20.8 m Above Sea Level
GPS Date/Time                   : 2020:11:06 20:09:52Z
GPS Latitude                    : 41 deg 23' 41.78" N
GPS Longitude                   : 73 deg 57' 23.84" W
Circle Of Confusion             : 0.005 mm
Field Of View                   : 69.4 deg
Focal Length                    : 4.3 mm (35 mm equivalent: 26.0 mm)
GPS Position                    : 41 deg 23' 41.78" N, 73 deg 57' 23.84" W
Hyperfocal Distance             : 1.55 m
Light Value                     : 13.4
```

Looking at the **Artist** value we see that its **base64**, so lets decode it.

```
echo U29ycnkgTm90IHRoZSBGbGFnIQ== | base64 -d

Sorry Not the Flag!
```
Oof, thats not the right one let's keep looking.

Let's try the value of the **copyright**

```
echo YzN0e3MwX3YzcnlfbTN0NF8zfQ== | base64 -d

c3t{s0_v3ry_m3t4_3}
```
Yay, we got the flag!!






 

