**Previous/Next Chapter**
`!`/`@`
`<PgUp>`/`<PgDn>`

ESC quit

MOUSE_BTN0 ignore  
MOUSE_BTN0_DBL ignore  
MOUSE_BTN1 cycle fullscreen  
MOUSE_BTN2 cycle pause  
MOUSE_BTN3 add volume 1  
MOUSE_BTN4 add volume -1  
MOUSE_BTN5 add chapter -1  
MOUSE_BTN6 add chapter 1

RIGHT seek 10  
LEFT seek -10  
UP seek -60  
DOWN seek 60

Ctrl+RIGHT no-osd seek 1 - exact  
Ctrl+LEFT no-osd seek -1 - exact  
Ctrl+UP no-osd seek -5 - exact  
Ctrl+DOWN no-osd seek 5 - exact

. frame_step  
, frame_back_step  
[ sub_step -1  
] sub_step +1

SPACE cycle pause  
0 stop

HOME playlist_prev  
END playlist_next  
ENTER playlist_next force

PGUP add chapter -1  
PGDWN add chapter 1

m cycle mute

d cycle deinterlace  
c cycle colormatrix

s cycle sub  
F cycle sub-forced-only  
V cycle ass-vsfilter-aspect-compat

a cycle audio  
v cycle video  
TAB cycle program

e cycle edition  
A cycle angle

t cycle ontop  
f cycle fullscreen

o osd  
i show_text "${filename}"  
p show_progress

https://raw.github.com/mpv-player/mpv/master/etc/input.conf
```config
ESC quit

MOUSE_BTN0 ignore  
MOUSE_BTN0_DBL ignore  
MOUSE_BTN1 cycle fullscreen  
MOUSE_BTN2 cycle pause  
MOUSE_BTN3 add volume 1  
MOUSE_BTN4 add volume -1  
MOUSE_BTN5 add chapter -1  
MOUSE_BTN6 add chapter 1

RIGHT seek 10  
LEFT seek -10  
UP seek -60  
DOWN seek 60

Ctrl+RIGHT no-osd seek 1 - exact  
Ctrl+LEFT no-osd seek -1 - exact  
Ctrl+UP no-osd seek -5 - exact  
Ctrl+DOWN no-osd seek 5 - exact

. frame_step  
, frame_back_step  
[ sub_step -1  
] sub_step +1

SPACE cycle pause  
0 stop

HOME playlist_prev  
END playlist_next  
ENTER playlist_next force

PGUP add chapter -1  
PGDWN add chapter 1

m cycle mute

d cycle deinterlace  
c cycle colormatrix

s cycle sub  
F cycle sub-forced-only  
V cycle ass-vsfilter-aspect-compat

a cycle audio  
v cycle video  
TAB cycle program

e cycle edition  
A cycle angle

t cycle ontop  
f cycle fullscreen

o osd  
i show_text "${filename}"  
p show_progress

` screenshot  
S screenshot video

D cycle framedrop

POWER quit  
MENU cycle osd  
PLAY cycle pause  
PAUSE cycle pause  
PLAYPAUSE cycle pause  
STOP quit  
FORWARD seek 60  
REWIND seek -60  
NEXT playlist_next  
PREV playlist_prev  
VOLUME_UP add volume 1  
VOLUME_DOWN add volume -1  
MUTE cycle mute  
CLOSE_WIN quit  
CLOSE_WIN {encode} quit
```
