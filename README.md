
# New Binary ! fping 4.2 (2019-02-19 released 3yrs ago)
======================
Can anyone reverse this so we can compile new version?
If you wish to see the V3 with gui then see inside folders ;)

Or else use the binary/cmd mode on the new 4.2


## Can anyone reverse the v3 so we can compile new GUI version?

fping 4.2 (2019-02-19)
======================

## New features

- New option -x / --reachable to check if the number of reachable hosts is >= a certain
  number. Useful for example to implement connectivity-checks (#138, thanks @deepak0004)

## Bugfixes and other changes

- Allow decimal numbers for '-t', '-i', '-p', and '-Q'
- Fix build with --disable-ipv6 (#134, thanks @Polynomial-C)
- Fix hang with '-6', with ipv6 kernel module, but not loaded (#140, thanks @abelbeck)
- Assume '-6' if the binary is named 'fping6' (this is mostly for special
  embedded-distro use cases, and not meant to be used generally in place of
  compiling IPv6-only binary or using '-6', see also the notes in #139, thanks
  abelbeck)
- Get rid of warning "timeout (-t) value larger than period (-p) produces unexpected results"
  (#142, thanks @MrDragon1122)
  

fping 4.1 (2018-09-17)
======================

## Bugfixes and other changes

- Fix problem when socket fd is 0 (#125, thanks Ram�n Novoa!)
- Fix running on servers with disabled IPv6 (#118, thanks Simon Matter)
- Allow running "fping -h" or "--help" even when raw socket can't be opened (#131, thanks @teto)
- Fix build issue with FreeBSD and IPv6 (#132, thanks @gsnw)

fping 4.0 (2017-04-23)
======================

## Incompatible Changes

##### fping and fping6 unification

fping and fping6 are now unified into one binary. It means that, for example,
doing 'fping google.com' is going to ping the IPv6 IP of google.com on
IPv6-enabled hosts.  

If you need exact compatibility with old versions, you can configure and
install fping twice: once for ipv4, and once for ipv6:

    ./configure --disable-ipv6; make clean install
    ./configure --disable-ipv4 --program-suffix=6; make clean install

##### Option -n, not the same as -d anymore

Option -n / --name is now doing a reverse-DNS lookups on host addresses,
only if they are given as IP address, but not for hostnames. For example,
if you write 'fping -n google.com', fping would previously do a
forward-DNS lookup on google.com, and then a reverse-DNS lookup on the
resolved IP address. Now, it is just going to keep the name 'google.com'.
That same behavior can be achieved with the option -d / --rdns (which was
previously an alias for -n).

                     fping<4.0              fping>=4.0
    fping -n NAME    NAME->IP->IPNAME       NAME
    fping -d NAME    NAME->IP->IPNAME       NAME->IP->IPNAME

##### Discarding of late packets

fping will now discard replies, if they arrive after the defined timeout
for reply packets, specified with -t. This change is relevant only for the
count and loop modes, where the measured times should be now more
consistent (see github issue [#32][i32] for details).

To prevent loosing reply packets because of this change, the default
timeout in count and loop modes is now automatically adjusted to the
period interval (up to 2000 ms), but it can be overriden with the -t
option. The default timeout for non-loop/count modes remains 500 ms.

##### No restrictions by default

fping will not enforce -i >= 1 and -p >= 10 anymore, except if you
'./configure --enable-safe-limits'.

The reasoning to removing the restrictions by default, is that users can
clog the network with other tools anyway, and these restrictions are
sometimes getting in the way (for example if you try to ping a lot of
hosts).

##### Default interval (-i) changed from 25ms to 10ms

The default minimum interval between ping probes has been changed from
25ms to 10ms. The reason is that 25ms is very high, considering today's
fast networks: it generates at most 31 kbps of traffic (for IPv4 and
default payload size).

## New features

- Unified 'fping' and 'fping6' into one binary ([#80][i80])
- Long option names for all options
- IPv6 enabled by default
- New option -4 to force IPv4
- New option -6 to force IPv6
- Keep original name if a hostname is given with -n/--name
- Option -d/--rdns now always does a rdns-lookup, even for names, as '-n' was doing until now
- Enforce -t timeout on reply packets, by discarding late packets ([#32][i32])
- Auto-adjust timeout for -c/-C/-l mode to value of -p

## Bugfixes and other changes

- -i/-p restrictions disabled by default (enable with --enable-safe-limits)
- Default interval -i changed from 25ms to 10ms
- Fix compatibility issue with GNU Hurd
- A C99 compiler is now required
- Option parsing with optparse (https://github.com/skeeto/optparse). Thanks Christopher Wellons!
- New changelog file format

[i32]: https://github.com/schweikert/fping/issues/32
[i80]: https://github.com/schweikert/fping/issues/80

(see doc/CHANGELOG.pre-v4 for older changes)






# fping-windows 3.00
Fping windows binary mirror
Acquired through Web Archive.

Pretty useful app.

Original source for available here : https://github.com/schweikert/fping

Binary/Port created by Wouter Dhondt from http://www.kwakkelflap.com


Fast pinger, version 3.00
(c) Copyright 2001 - 2012 Kwakkelflap
Written by Wouter Dhondt
Web: http://www.kwakkelflap.com
E-Mail: info@kwakkelflap.com

---------------------------------------------------------------------------------

Fping is a simple ping program, intended to be used instead of the
standard ping program that comes with windows. It was first made
to ping faster than once every second. Options have been added since
then and fping is now a very handy tool (at least I think it is).

PLATFORMS:
Windows 95, 98, NT 4.0, 2000, ME, XP, 2003 server, Vista, 7 and 2008 server

---------------------------------------------------------------------------------

Legal mumbo jumbo :

This program and the accompanying documentation are Copyright (C) 2001 - 2008
by Kwakkelflap.  You are allowed to redistribute it, provided that all 
the files in the original archive are distributed together and no changes
are made to any file in the distribution.  You can't charge for the 
program, only for distributing it.  You have to clearly identify me 
(Wouter Dhondt) as the author.

This program comes without any warranty either implied or expressed. In no
case shall the author be liable for any damage or unwanted behaviour of any
computer hardware and/or software.

The same things in English:

   - I own it.  It's mine.  Muahahaha!  (But I let you use it too.)

   - I can't guarantee that it works, or that it works correctly.

   - If it breaks, it's your fault.  But you do get to keep the pieces.

   - If it breaks something else, it's your fault too.

   - If you copy it, don't claim that you've made it yourself, or
     change it in any way; and copy both program and documentation.

   - You are free to offer the program on your web page.  All I ask for
     is that you give a link back to mine, and that you state that the
     program was made by Wouter Dhondt.

---------------------------------------------------------------------------------

Ping is one of the most useful network debugging tools available. The first ping 
program was written by Mike Muuss in December 1983 for use on Unix machines. Muuss 
named his program after the sonar sounds used for echolocation by submarines, 
although some say ping stands for "Packet InterNet Grouper". Ping sends a small 
packet of information containing an ICMP ECHO_REQUEST to a specified computer, 
which then sends an ECHO_REPLY packet in return. The ping program then evaluates 
this reply, and a report is shown. You can check several things with the ping 
program: can you reach another computer, how long does it take to bounce a packet 
off of another site, ... You can ping either a domain name, or an IP address. 
Functionality to show domain names when using IP addresses is supported. Even 
routing options are available, alas only 9 routes can be shown due to the 
structure of the IP header (RFC 792). Why did I write my own ping program? 
There are two main reasons: a) It wanted to know how the ping program worked. I 
found it really intriguing and was very curious and b) There was a need for a 
better ping program here at the lab where I work.

Usage:
fping <host(-list)> [-t time] [-w timeout] [-c] [-n count] [-s data_size]
       [-S size1/size2] [-R min/max] [-d ping_data] [-h TTL] [-v TOS]
       [-r routes] [-f] [-j] [-g host1/host2] [-H filename] [-a] [-A]
       [-p(x)] [-i] [-b(-)] [-T] [-D] [-l] [-o] [-L filename]

Options:
        -t : time between 2 pings in ms up to 1000000
        -w : timeout in ms to wait for each reply
        -c : continuous ping (higher priority than -n)
             to see statistics and continue - type Control-Break;
             to stop - type Control-C.
        -n : number of pings to send to each host
        -s : amount of data in bytes up to 65500
        -S : size sweep: ping with size1, size1 + 1, ..., size2 bytes
        -R : random length between min and max (disabled when using -S)
        -d : ping with specified data
        -h : number of hops (TTL: 1 to 128) + print hops
        -v : Type Of Service (0 to 255) (IPv4-only)
        -r : record route (1 to 9 routes) (IPv4-only)
        -f : set Don't Fragment flag in packet (IPv4-only)
        -j : print jitter with each reply (only when pinging one host)
        -g : ping IP range from host1 to host2 (IPv4-only)
        -H : get hosts from filename (comma delimited, filename with full path)
        -a : resolve addresses to hostnames
	-A : print addresses with each reply
        -p : use a thread pool to ping multiple hosts (enables ICMP dll)
             x is optional and allows you to choose the number of threads
             e.g. -p uses a thread for every host
                  -p5 uses a pool of 5 threads/core
        -i : use ICMP dll instead of raw socket (disables -r)
        -b : beep on every successful reply (-b- to beep on timeout)
        -T : print timestamp with each reply
        -D : print datestamp with each reply
        -l : limit the output to ping results and errors
        -o : limit the output to ping statistics
        -L : logging to a text file

fping uses raw sockets. This can be a problem for NT / 2000 / XP system
users without administrator rights. Raw socket creation will fail
due to a silly and useless socket protection. Fping will switch
to the ICMP dll if this happens (to ping the micro$oft way). To 
disable this protection (and take full advantage of fping) you can
do the following:
a) NT4 users should change / add the following registry variable
and set its value to DWORD 1:
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Afd\Parameters\DisableRawSecurity
b) 2000 / XP users should set the following registry variable to DWORD 1
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Tcpip\Parameters\AllowUserRawAccess

Also, if you want to change the TOS on 2000/XP systems, you need to add the
following value in the registry and set it to 0:
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\TCPip\Parameters\DisableUserTOSSetting

after you change the registry, you will need to reboot.
You can also run the reg file in accordance with your os.

Return Values:
Reply: 0
Reply timed out: 1
Host not found: 2
Packet size exceeds MTU: 3
Too few bytes: 4
Non-echo type: 5

Send questions (and bug reports) 2 support@kwakkelflap.com

---------------------------------------------------------------------------------

Known bugs: none

Possible future enhancements:
- loose and strict route ping options
- other ping options

---------------------------------------------------------------------------------

Revision History:

Version 3.00 (16/02/12)
- Changed the order of ping options
- Timestamp in milliseconds
- Datestamp option without timestamp, you can combine both
- Option to ping in different threads
- Option to print addresses instead of input
- Bugfix: crash when unable to resolve host in ICMP ping
- General cleanup

Version 2.22 (12/11/08)
- Fix for Win2K for the getaddrinfo() function (since version 2.19) (234)

Version 2.21 (31/10/08)
- Limit the output to statistics only (214)
- Use the real data size with -d option if not set with -s option (224)
- Removed the first 4 bytes of the RAW socket ping which had timing information (obsolete since 2.11) (224)
- Ping with random size and known data (225)
- Set the timer resolution to allow fast pings (231)

Version 2.20 (09/04/08)
- Calculate jitter when pinging one host (210)
- Print hops when using the TTL option for IPv4 (210)

Version 2.19 (07/04/08)
- Ping IPv6 address (189)

Version 2.18 (07/03/08)
- VS 2005 fix
- -g option bugfix
- Flush the output for each line
- x64 version

Version 2.17 (08/03/07)
- Fixed % sign with -i option
- Fixed recursive function block
- Display hostname when pinging multiple hosts
- Solved a problem with min time being max
- Fixed first ping time info
- Adjusted ICMP ping printout for parsing
- Average precision is the same as min and max

Version 2.16 (23/08/06)
- Log to file option
- Ping default with random data

Version 2.15 (10/04/06)
- Fixed a bug with the -d option

Version 2.14 (05/04/06)
- Use PC speaker instead of WAV for beep

Version 2.13 (13/02/06)
- Print the TOS with each ping
- Sequence check with RAW sockets
- Larger time between pings

Version 2.12 (09/06/05)
- g option added: host sweep

Version 2.11 (04/05/05)
- Use high precision timer
- datestamp option
- No need for comma's in host file, new line is also ok
- fixed a bug when there is only one host in the host file

Version 2.10 (23/02/05)
- Fix in the reply # indication in some cases (was always 1)
- Ping with random size

Version 2.09 (25/11/02)
- Bug fix: # of bytes with raw socket ping was incorrect

Version 2.08 (07/11/02)
- Fping size sweep
- Ping with specified data
- Retrieve hosts from comma delimited filename
- Removed self made linked list and using STL

Version 2.07 (25/06/02)
- Fping crashed in ICMP ping if no host was found with IP address
- Continue ping if host can't be found from IP address
- Space between return trip time and "ms" to allow better parsing
- Option to print timestamp with each reply

Version 2.06 (12/03/02)
- limit output option
- return values

Version 2.05 (16/10/01)
- ICMP WSAStartup & WSACleanup bug resolved.
- RAW Socket receive error time is now correct
- Usage programdir truncated
- Better invalid option parsing support
- Cleaned IP options struct (number of echo requests)
- Ping multiple hosts
- Reverse beep option

Version 2.04 (29/08/01)
- Zero ping statistics bug resolved
- ICMP dll option
- switch to ICMP dll if raw socket creation failed
- /? | -? gives usage info
- resolving addresses to hostnames (includes routing)
- internal IP options struct changed
- Don't Fragment flag can be set
- Option to beep on every successful reply

Version 2.03 (04/07/01)
- Routing

Version 2.02 (03/07/01)
- Generic error log messages instead of numbers as 10065
- Adjustable # of hops (TTL)
- Adjustable TOS
