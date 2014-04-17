
## Multiping

This is a wrapper for the `ping` program which pings several hosts at once.
I wrote this so I could ping several hosts at once so I could better 
troubleshoot what was going on with my Comcast connection at home.


### Installation

    git clone git@github.com:dmuth/unix-utils.git


### Syntax

    ./multiping host [ host [ host [...]]]


### How it works

Several instances of the "ping" utility


### Why not use mtr?

`mtr` is a nice tool, but I found if I ran it for long periods of time (hours), 
it would report packet losses that really weren't happening.  I'm not clear 
if it was an issue with mtr itself or something in OS/X, but I felt it 
would be safer to write a wrapper for ping instead.


### Sample output

    [Douglass-iMac:~/development/unix-utils ] $ ./multiping google.com comcast.com (my upstream) (my router) 10.0.3.1
    Preparing to ping hosts:  google.com comcast.com (my upstream) 10.0.3.1...
    10.0.3.1: PING 10.0.3.1 (10.0.3.1): 56 data bytes
    10.0.3.1: icmp_seq=0 ttl=64 time=0.776 ms
    (my upstream): PING (my upstream) (upstreams IP): 56 data bytes
    (my upstream): icmp_seq=0 ttl=254 time=13.397 ms
    google.com: PING google.com (74.125.228.64): 56 data bytes
    google.com: icmp_seq=0 ttl=55 time=19.772 ms
    comcast.com: PING comcast.com (76.96.111.23): 56 data bytes
    comcast.com: icmp_seq=0 ttl=245 time=62.312 ms
    10.0.3.1: icmp_seq=1 ttl=64 time=1.207 ms
    (my upstream): icmp_seq=1 ttl=254 time=11.080 ms
    google.com: icmp_seq=1 ttl=55 time=16.355 ms
    comcast.com: icmp_seq=1 ttl=245 time=60.557 ms
    10.0.3.1: icmp_seq=2 ttl=64 time=1.221 ms
    (my upstream): icmp_seq=2 ttl=254 time=14.437 ms
    google.com: icmp_seq=2 ttl=55 time=19.974 ms
    comcast.com: icmp_seq=2 ttl=245 time=64.255 ms
    10.0.3.1: icmp_seq=3 ttl=64 time=1.201 ms
    (my upstream): icmp_seq=3 ttl=254 time=10.843 ms
    google.com: icmp_seq=3 ttl=55 time=16.924 ms
    comcast.com: icmp_seq=3 ttl=245 time=62.551 ms
    ^C
    (my upstream): 
    (my upstream): --- (my upstream) ping statistics ---
    (my upstream): 4 packets transmitted, 4 packets received, 0.0% packet loss
    (my upstream): round-trip min/avg/max/stddev = 10.843/12.439/14.437/1.525 ms
    google.com: 
    google.com: --- google.com ping statistics ---
    google.com: 4 packets transmitted, 4 packets received, 0.0% packet loss
    google.com: round-trip min/avg/max/stddev = 16.355/18.256/19.974/1.631 ms
    10.0.3.1: 
    10.0.3.1: --- 10.0.3.1 ping statistics ---
    10.0.3.1: 4 packets transmitted, 4 packets received, 0.0% packet loss
    10.0.3.1: round-trip min/avg/max/stddev = 0.776/1.101/1.221/0.188 ms
    comcast.com: 
    comcast.com: --- comcast.com ping statistics ---
    comcast.com: 4 packets transmitted, 4 packets received, 0.0% packet loss
    comcast.com: round-trip min/avg/max/stddev = 60.557/62.419/64.255/1.310 ms


## Author

Douglas T. Muth.  You can email me at doug.muth@gmail.com or 
[harass me in social media](http://www.dmuth.org/contact).


## Shameless self-promotion

I like solving problems like these. If you need someone to 
solve problems like these, we should talk. :-)
Here's my resume:
[http://www.dmuth.org/resume](http://www.dmuth.org/resume)



