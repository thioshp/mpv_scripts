# autospeed

######Lua script for mpv to adjust monitor refresh rate and video speed for almost 1:1 playback.

--------------

#####Notes:

* Works on *nix and Windows operating systems.
* You put these files (auto_speed.lua and auto_speed_config.lua) in the mpv/scripts folder, see the [mpv man page](https://github.com/mpv-player/mpv/blob/master/DOCS/man/mpv.rst#files) for the correct path.
* Download links: [auto_speed.lua](https://raw.githubusercontent.com/kevinlekiller/mpv_scripts/master/autospeed/auto_speed.lua) | [auto_speed_config.lua.example](https://raw.githubusercontent.com/kevinlekiller/mpv_scripts/master/autospeed/auto_speed_config.lua.example)
* You should copy auto_speed_config.lua.example to auto_speed_config.lua and edit the options.
* If you can, overclock your monitor to 72hz/48hz, you will get almost 1:1 on 23.976 content without altering the speed too much. Guide for Intel GPUs on Linux [here](https://github.com/kevinlekiller/linux_intel_display_overclocking).
* Optionally can use [xrandr](http://www.x.org/wiki/Projects/XRandR/) on *nix or [nircmd](http://www.nirsoft.net/utils/nircmd.html) on Windows (there are options to enable them in the config file). Enabling them will enable monitor refresh rate changing.
* Optionally can use [ffprobe](https://www.ffmpeg.org/download.html) to get more accurate video frame rate (enable this in the config file). When using the "get_property" command in mpv, the numbers are rounded or truncated (instead of returning 23.97602397602398, it returns 23.976025), so ffprobe can be used to get the fps instead to calculate a more accurate speed setting.
* Even though the "get\_property" command rounds or truncates, the "set_property" command does not, so the speed setting is as we calculated it in lua.
* By default mpv will adjust the audio pitch to match the speed difference, so you do not need to worry about this.

--------------

#####Description:

Sets your monitor refresh rate to be close to a multiple of the video (requires xrandr or nircmd).  
Sets the speed of the video based on the refresh rate of the monitor for smoother playback.  
Sets back your monitor refresh rate when exiting mpv.

--------------

#####Examples:

* >
The display supports 72hz.  
The video is (ffprobe: 24000 / 1001 aka 23.97602397602398fps, or mpv: 23.976025).  
The display is currently 60hz.  
The display is set to 72hz.  
The mpv speed setting is set to 1.001.  
The video now plays at 24fps (ffprobe: 23.97602397602398fps * 1.001 = 24 or mpv: 23.976025 * 1.001 = 24.000001025fps).  
Every frame is repeated 3 times, so 1:1 playback.

* >  
The display supports 50hz.  
The video is 24.95fps.  
The display is currently 60hz.  
The display is set to 50hz.  
The mpv speed setting is set to 1.002004008016032.  
The video now plays at 25fps.  

* >  
The display supports 60hz.  
The display is currently 144hz.  
The video is 60fps.  
The display is set to 60hz.

--------------

#####License:

GPL V2  
See [LICENSE](https://github.com/kevinlekiller/mpv_scripts/blob/master/LICENSE)