# powermizer

mpv script for setting the "PowerMizer" setting on Nvidia GPU's with the proprietary driver on *nix operating systems.

It sets "PowerMizer" to "Prefer Maximum Performance" when mpv starts.

It sets "PowerMizer" to "Adaptive" when mpv exits.

It will try to automatically detect your GPU.

You can override this by passing the mpv command: `--script-opts=powermizer-gpu="[gpu:1]"`

You can find your GPU with this command: `nvidia-settings -q gpus`

Download link for the script: https://raw.githubusercontent.com/kevinlekiller/mpv_scripts/master/powermizer/powermizer.lua
