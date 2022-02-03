# Setup
The sv directory is split into the root and user subdirectory. The root subdirectory is for global services, while the user services are intended for the end user. I assume xorg is running as root and that the user services service[1] has a depdency on xorg, hence all user services have a defacto dependence on xorg.

# Benefit
This also has the practical upshot running `s6-rc -l /user/service-rc/location -d change my-user` does not kill xorg. I have had issues previously when running dwm as root where `-d change graphical` would kill xorg and since i was running `s6-rc` from a graphical terminal, the command would kill itself. This would leave s6 in a weird state. Not quite down, not quite up. It should be noted that spawned windows will live on even if the window manager goes down, as long as x stays up, afaik.

# Negative
Xorg must be running. Not a huge issue as you can just switch away from that tty if want to only use the tty.

# User services service
I recommend running a service to start all your user services like described [here](https://forum.artixlinux.org/index.php/topic,3067.0.html). I will eventually make a [package](http://git.jole.xyz/archports/) for it.

