# SUN POSITION CALCULATOR
This version is made for racket and it can be run in DrRacket and
in command line. The input data is read from the text file **indata.txt**.
You can edit it so as you like. There are some files
made for Stockholm, New York and Sydney.
 
## Input data file indata.txt
Here is the description of the saved input data

```vim
  1 0        ; year      year number, current time if 0
  2 0        ; month     month number, current time if 0
  3 0        ; day       day of the month, current time if 0
  4 65.85    ; latitude  degrees
  5 24.18    ; longitude degrees
  6 2        ; time zone hours
  7 10       ; calculation time, ***hour UTC***, fixed, can be edited
  8 32.      ; calculation time, minutes, fixed, can be edited
  9 41       ; calculation time, seconds, fixed, can be edited
 10 Tornio.  ; location name
```
 If values of year, month or day are zeroes, the current time is used.

## Using from command line

You can run this e.g. in the bash shell if you have installed racket.

### running the source file

```racket
$ racket suncalctoday.rkt
```

### running the compiled code
Alternatively, the program can be started from the command file
**suncal.rkt** which requires the compiled code as follows:
```
$ racket suncal.rkt
```

This is the start code **suncal.rkt** running the compiled program:
```
#lang racket
(require "suncalctoday.rkt")

; This file runs the compiled binary files
; You can run the compiled files on bash command line with racket:
;    racket suncalc.rkt
; See https://docs.racket-lang.org/raco/Bytecode_Files.html
```
The source code may be compiled with raco as follows:

```
$ raco make suncalctoday.rkt
```

The compiled files can be seen in the directory compiled:
```
-rw-r--r--  1 jla   staff  38120 12 Maa 12:44 suncalctoday_rkt.zo
-rw-r--r--  1 jla   staff    214 12 Maa 12:44 suncalctoday_rkt.dep
-rw-r--r--  1 jla   staff   5118 12 Maa 12:44 suncal_rkt.zo
-rw-r--r--  1 jla   staff    227 12 Maa 12:44 suncal_rkt.dep
```

## Example Stockholm date 2021-03-20
```
jla$ racket suncal.rkt 
 Date 2021-3-20 Latitude 59.329  Longitude 18.069 Timezone 1 in Stockholm
 Nautical twilight   2021-03-20 ~ 04:18:45
 Civil twilight time 2021-03-20 ~ 05:07:40
 Sunrise time        2021-03-20 ~ 05:48:26
 Noon time           2021-03-20 ~ 11:55:06
 Sunset time         2021-03-20 ~ 18:01:46
 Civil twilight time 2021-03-20 ~ 18:42:32
 Nautical twilight   2021-03-20 ~ 19:31:28
 Daylength           2021-03-20 ~ 12:13:20
 Sun declination       0.0201°
 Zenith at noon        59.3089°
 Sun elevation corr.   30.7182°
 Atmospher. refraction 0.0271°
 Azimuth at sunrise    88.5558°
 Azimuth at noon       180.0016°
 Azimuth at sunset     271.4442°
 Julian day        2459294
 Local time JD     2459293.9549

 Calculation time:   11:55:07 (UTC+1)
 City: Stockholm  Latitude    59.329° N , longitude 18.069° E

 ==========================================

Current seconds 1616237707
Hour angle              0.0014°
Solar elevation         30.6911°
jla$
```
