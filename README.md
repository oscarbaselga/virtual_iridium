# What is this project?

This is a Iridium Modem (9602/9603) emulator to make it possible to test your own software again a "Virtual" Iridium device and it connection.

This application is written in Python language uses pyserial to implement a serial communications interface. The emulator matches the behavior of the Iridium 9602 modem which is available from NAL Research and Rock7Mobile (as Rockblock). The emulator will respond to at commands to write data, execute short-burst data (SBD) sessions, and most of the other functions supported by the 9602 serial interface.

# What's the use?

If you want to develop an application on a PC or an embedded device it will to talk to an Iridium modem, you can use this for initial prototyping and testing. This can potentially save quite some cost on Iridium service charges. Also you can already create an application without already buying the real Iridium Modem (9602/9603) hardware.

# How do I get this software?

In your Unix shell of choice:
```
 $ git clone https://github.com/jmalsbury/virtual_iridium
 $ cd virtual_iridium/python
 $ python Iridium9602.py -d /dev/ttyUSB0 -u youraccount@gmail.com -p your_password -i imap.gmail.com -o smtp.gmail.com -r your_iridium_test_account@gmail.com -m EMAIL
```
The specified serial device, in the example above: ttyUSB0 , should connect to the external device that you are developing your Iridium communications app on. You can also use a virtual serial port (like a pair of SOCAT TTYs), to connect to another application on the same PC.

# Where can I find more documentation?

This is all I am going to write for now. If I see more people are interested in using this emulator, I may put more effort into this documentation. If you have any question, don't hesitate to e-mail me: jmalsbury [dot] personal [at] gmail [dot] com.
Other Resources

Iridium 9602 - Developers Manual{TODO}Link to repofile

Thanks to the original autor J.Malsbury. Maybe his repo is more up to date or has mre features.
[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/bdb824945e9b3e4a959feb550731a1e0 "githalytics.com")](http://githalytics.com/jmalsbury/virtual_iridium)

# Getting started
## Install Python2
```
sudo apt install python2
curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip.py
python2 get-pip.py
```
## Install dependencies
```
pip2 install pyserial
pip2 install sendmail
```
## Clone repository
```
git clone https://github.com/oscarbaselga/virtual_iridium.git
cd virtual_iridium
```
## Install required tools
```
sudo apt install socat
sudo apt install minicom
```
## Set environment
```
sudo socat -d -d pty,link=$HOME/ttyS0,raw,echo=0 pty,link=$HOME/ttyS1,raw,echo=0
sudo chmod 777 $HOME/ttyS*
```
## Run emulator
```
cd python
python2 Iridium9602.py -d $HOME/ttyS0 -u <account1>@gmail.com -p <AppPassword> -i imap.gmail.com -o smtp.gmail.com -r <account2>@gmail.com -m EMAIL
minicom -D $HOME/ttyS1
```
### Note
`account1` has to enable 2-Step Verification in order to generate an App Password (https://support.google.com/accounts/answer/185833?visit_id=637975780298836300-4203556768&p=InvalidSecondFactor&rd=1).

## Send AT commands
In the shell running the `minicom`, type the AT command, e.g.:
```
at+gsn
300234060604220

OK
```
