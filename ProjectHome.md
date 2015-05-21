# Overview #
Many Netgear routers have telnet support built-in, but gaining access to it requires an extra step of sending a specially formatted payload to the telnet daemon before it will allow users to log in. Netgear provides a windows executable called "telnetenable.exe" for doing just this, however, unix/linux/OSX users are out of luck with a "sanctioned" method.

The openwrt wiki provides information about how to enable the telnet console for your netgear device. Included on this page is a link to a couple of C-source implementations of the telnetenable algorithm. This C source is a bit tricky to get working, and depending on your setup might be a **real** pain.

I've translated the algorithm from C to Python, which should make it easier to actually get telnet working for many users, and will also make it easier to keep the code updated and working.

# Requirements #
As of right now, the implementation requires that the `PyCrypto` module is installed in your system. This can be obtained either from [MacPorts](http://www.macports.org/), or from the [PyCrypto](http://www.amk.ca/python/code/crypto.html) website.

Other than `PyCrypto` the implementation should be using python-standard extensions. It should be noted that this version was only tested with Python2.6

# Running #
Simple:
```
python telnetenable.py <IP> <MAC> <Username> <Password>
```

IP - The IP of your Netgear device, usually 192.168.1.1

MAC - The mac address should be the MAC address of the LAN port on your Netgear device, WITHOUT the ":". e.g. "00:40:5E:21:14:4E" would be written as "00405E21144E".

Username - Username for accessing the telnet console, usually 'Gearguy'

Password - Password for accessing the telnet console, usually 'Geardog'