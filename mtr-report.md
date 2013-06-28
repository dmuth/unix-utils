## MTR Report

This script is a wrapper that I wrote for the [mtr ping tool](http://en.wikipedia.org/wiki/MTR_(software\)).

It makes my life just a little easier by acting as a wrapper for MTR so I can easily 
get the status of a route in a long running loop, and logged to a file.


## Sample Usage

    ./mtr-report --num 3600 --log --loop google.com

The above pings Google and prints the results every hour, which would loop something like this:

    HOST: myMac                       Loss%   Snt   Last   Avg  Best  Wrst StDev
    [snip]
      6.|-- be-23-pe06.ashburn.va.ibo  0.0%  3600   16.1  16.8  12.3 1032.  18.0
      7.|-- 173.167.57.234             5.5%  3600   15.3  17.3  12.4 931.6  17.5
      8.|-- 216.239.46.248             3.3%  3600   14.9  17.8  12.6 830.6  15.1
      9.|-- 72.14.238.247              0.0%  3600   16.4  18.5  13.8 730.5  14.3
     10.|-- iad23s07-in-f4.1e100.net   0.1%  3600   15.9  17.7  13.2 629.5  11.8

This is useful when my Comcast connection starts acting up. :-)


## Syntax

    mtr-report [--loop] [-6] [--log] --num num hostname
          --loop Run in a loop
              -6 Use IPv6. IPv4 is the default.
           --log Log the results to mtr-report-log.txt
           --num How many pings to send out
        hostname Whom do you want to ping today?


## Author

Douglas T. Muth.  You can email me at doug.muth@gmail.com or 
[harass me in social media](http://www.dmuth.org/contact).


