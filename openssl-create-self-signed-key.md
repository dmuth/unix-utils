
## What's this?

This is a quick and dirty script that I wrote which creates an SSL key 
and a self-signed certificate, without littering up your filesystem
with intermediate files.


## Why would I want to use this?

Let's say you're running a webserver on your personal machine and 
don't need a properly signed key.  I got tired of having to look up the syntax
for the `openssl` **every single time**, hence this script.


## Syntax

    ./openssl-create-self-signed-key basename
        basename The base name for the key and self-signed public certificate


## Sample run

    #
    #
    # About to generate private key
    #
    #
    Generating RSA private key, 2048 bit long modulus
    .............................+++
    .............................+++
    e is 65537 (0x10001)
    #
    #
    # About to create certificate signing request
    # For these questions, if the key is being used for AWS or anywhere BUT a public server, you can just mash the enter key.
    #
    #
    You are about to be asked to enter information that will be incorporated
    into your certificate request.
    What you are about to enter is what is called a Distinguished Name or a DN.
    There are quite a few fields but you can leave some blank
    For some fields there will be a default value,
    If you enter '.', the field will be left blank.
    -----
    Country Name (2 letter code) [AU]:
    State or Province Name (full name) [Some-State]:
    Locality Name (eg, city) []:
    Organization Name (eg, company) [Internet Widgits Pty Ltd]:
    Organizational Unit Name (eg, section) []:
    Common Name (eg, YOUR name) []:
    Email Address []:
    
    Please enter the following 'extra' attributes
    to be sent with your certificate request
    A challenge password []:
    An optional company name []:
    writing RSA key
    #
    #
    # Creating the self-signed certificate.
    #
    #
    Signature ok
    subject=/C=AU/ST=Some-State/O=Internet Widgits Pty Ltd
    Getting Private key
    #
    #
    # All done!  Here are your files:
    # Private key: foobar.key
    # Certificate: foobar.crt
    #
    #


## Author

Douglas T. Muth.  You can email me at doug.muth@gmail.com or (harass me in social media)[http://www.dmuth.org/contact].


