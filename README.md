rc-flightgear-controller
========================

This is an attempt to capture some knowledge that was not easy to find in order to get a HobbyKing RC (Radio Control)
transmitter (TX) to talk to the flight simulator (FlightGear) in a usable way.


You will need
-------------

* [HK-6DF-M2/16239 HobbyKing HK6S 2.4Ghz FHSS 6Ch Tx & Rx (Mode 2)](http://www.hobbyking.com/hobbyking/store/__16239__HobbyKing_HK6S_2_4Ghz_FHSS_6Ch_Tx_Rx_Mode_2_.html)
* ["Buddy Box" - FMS Simulator USB Lire Cable Adapter For Esky JR Futaba](http://www.ebay.co.uk/itm/New-FMS-Simulator-USB-Lire-Cable-Adapter-For-Esky-JR-Futaba-UK-/181169978712?ssPageName=ADME:L:OC:GB:3160)
* [FlightGear.app](http://www.flightgear.org/download/)
* Some patience


Introduction
------------

The point of this is to learn to fly an RC fixed-wing plane as a total novice, so that you don't do what I did and nose-dive on your maiden flight. My reason for wanting to learn is to use the plane as an ecological monitoring drone. There are many other reasons you might want to do this though, so, on we go...

It's actually pretty easy to get to the point where you know something is happening - just plug in the Buddy Box's minijack (3.5mm headphone jack) end into the HK6S (hole in the back marked 'D.S.C.'), turn on the Tx and plug the USB end into your Mac/whatever. The USB connector flashes red (well, mine did, but I guess these are pretty standard things that will come in different flavours). If you fire up FlightGear and start a flight, you'll find that your plane is doing all sorts of crazy stuff because the settings are all off.

Configuring
-----------

You can see what the app thinks the Tx is reporting by going to Help > Joystick Configuration. You'll probably see lots of inversions and small decimals when the sticks are in resting position - that is the reason why your plane just went haywire.

I spent quite a bit of time making the file in this repo, but I have no idea if it will translate to other HK6S units, because the jitter may be entirely unique. But - give it a go and let me know. What you do is this:

* Take the `hk6s.xml` file and place it in FlightGear's Joysticks Dir, which on Mac OS X is:
  `/Applications/FlightGear.app/Contents/Resources/data/Input/Joysticks/Default`
* Remove (or at least rename) the '`joystick.xml`' file (keep a backup!)
* Re-launch the flight (you only need to start a new flight, not restart FlightGear)
* That's it!

Caveats
-------

I couldn't get the name to work - FlightGear looks up the name of the joystick and matches it to the `<name>` attribute in the XML. Mine was 'PPM\x1a\x1a\x1a\x1a\x1a\x1a\x1a\x1a\x1a\x1a\x1a' so in the XML there is a commented out name with that (with the XML entities for that control char), but FlightGear didn't like it so I had to set it to 'default' and remove the `joystick.xml` which contains the normal default.

I didn't sort the Rudder out yet, because I was testing with the "Moyes Dragonfly" model which doesn't seem to have a rudder...!
