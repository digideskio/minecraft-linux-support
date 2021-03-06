# startup and security

Minecraft has some poorly-explained "security" fix every few months. That 
worries me.

You can mitigate some of that craziness by running minecraft java instances
from a script that is constrained by Linux's apparmor.

If you use Ubuntu or Debian, and only wish to use these startup scripts and 
security profiles, then the personal package archive at

    https://code.launchpad.net/~cmiller/+archive/ubuntu/ppa

or 

    ppa:cmiller/ppa

will be perfect for you. Commits into Github percolate to that PPA in hours.

If you are not lucky enough to use Debian based distro, you can instead install these files in the appropriate locations. Then,

    $ sudo apparmor_parser -a /etc/apparmor.d/usr.bin/minecraft-{server,client}
    $ sudo aa-enforce /usr/bin/minecraft-{server,client}

After the first time, you don't have to do these.

Then, run "minecraft-server" or "minecraft-client".

## Caveats and limitations

Your data is kept in ~/.minecraft.

If you create different "level-names" in your server.properties, it must start with "world".

## Discover and report problems

First time you run it, run

    $ dmesg |grep apparmor= |grep minecraft-
    
and [open a bug report](https://github.com/chadmiller/minecraft-linux-support/issues/new?title=missed-apparmor-rules)
