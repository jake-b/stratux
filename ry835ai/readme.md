Disclaimer
==========

BECAUSE THE HARDWARE DESIGN IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY
FOR THE HARDWARE DESIGN, TO THE EXTENT PERMITTED BY APPLICABLE LAW. EXCEPT 
WHEN OTHERWISE STATED IN WRITING THE COPYRIGHT HOLDERS AND/OR OTHER PARTIES 
PROVIDE THE HARDWARE DESIGN "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER 
EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES 
OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. THE ENTIRE RISK AS 
TO THE QUALITY AND PERFORMANCE OF THE PROGRAM & HARDWARE DESIGN IS WITH YOU. 
SHOULD THE HARDWARE DESIGN PROVE DEFECTIVE, YOU ASSUME THE COST OF ALL 
NECESSARY SERVICING, REPAIR OR CORRECTION.

IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW OR AGREED TO IN WRITING WILL ANY 
COPYRIGHT HOLDER, OR ANY OTHER PARTY WHO MAY MODIFY AND/OR REDISTRIBUTE THE 
HARDWARE DESIGN AS PERMITTED ABOVE, BE LIABLE TO YOU FOR DAMAGES, INCLUDING 
ANY GENERAL, SPECIAL, INCIDENTAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF THE 
USE OR INABILITY TO USE THE PROGRAM OR HARDWARE DESIGN (INCLUDING BUT NOT 
LIMITED TO LOSS OF DATA OR DATA BEING RENDERED INACCURATE OR LOSSES SUSTAINED 
BY YOU OR THIRD PARTIES OR A FAILURE OF THE PROGRAM OR HARDWARE DESIGN TO 
OPERATE WITH ANY OTHER PROGRAMS OR HARDWARE), EVEN IF SUCH HOLDER OR OTHER 
PARTY HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.

![Board Image](board.jpg?raw=true)

RA835AI Rasberry Pi "HAT" for Stratux 
=====================================

This board is designed for DEVELOPMENT PURPOSES ONLY.  It is not intended for
use in flight or in an airplane.  Use this board at your own risk!

This is a really rough draft of a "HAT" (Hardware Attached on Top) to connect
a RA835AI to the Rasberry Pi for use primarily with Stratux.

Currently it is just  a starting point.  Some things yet to work out:

- Is FSYNC supposed to be grounded?  Data sheet says yes; forums leave doubt.
- Pull-ups for I2C? - not necessary, as I understand that the Pi itself has
1.8k pullups

I tried by best to keep the ground planes clear of traces so that hopefully
it shields the GPS module from the Pi processor underneith.

This uses a custom library for the RA835AI, and a contributed library from
www.cadsoftusa.com "raspberrypi_bastelstube_v13" for the Pi GPIO connector
and board layout.

Revision History
================
- 0.1  - Initial commit
- 0.2  - Added C1 and C2 decoupling capacitors.  0.1uF  (P-tolerance=+100% ,-0%) 
         and 10uF values recommended by on the RY835AI data sheet. 
         Added a cut-trace jumper to disconnect FSYNC from GND if desired.
- 0.3  - Keepout area added underneith GPS antenna area.  Pads around mount
         points reduced and made round to make room for signal traces.
- 0.4  - Added "PWR IN" circut -- [see page 14](https://learn.adafruit.com/downloads/pdf/introducing-the-raspberry-pi-model-b-plus-plus-differences-vs-model-b.pdf)
         Added FAN output controlled by GPIO4.
         (minor change to explicitly list R1's value as 10k)
- 0.5  - Modified fan control signal to use GPIO18 rather than GPIO4.
         This is consistent with currently used AHRS boards.
         This revision has not been manufactured or tested, so make sure to 
         ERC/DRC and double check if you decide to have this made.

