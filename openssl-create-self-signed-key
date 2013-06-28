#!/bin/sh
#
# This is a wrapper script for making self-signed certificates
#

#
# Make errors be fatal.
#
set -e

if test ! "$1"
then
	echo "Syntax: $0 basename"
	exit 1
fi

BASENAME=$1

#
# Our secret key
#
KEY="${BASENAME}.key"

#
# Our certificate signing request (we won't need this)
#
CSR="${BASENAME}.csr"

#
# Our self-signed certificate
#
CERTIFICATE="${BASENAME}.crt"


#
# Don't worry about the password here.  The assumption 
# is that only yourself and root will have access to this key.
#
echo "#"
echo "#"
echo "# About to generate private key"
echo "#"
echo "#"
openssl genrsa -des3 -passout pass:12345 -out ${KEY} 2048


echo "#"
echo "#"
echo "# About to create certificate signing request"
echo "# For these questions, if the key is being used for AWS or anywhere BUT a public server, you can just mash the enter key." 
echo "#"
echo "#"
openssl req -new -passin pass:12345 -key ${KEY} -out ${CSR}

#
# This will remove the passphrase from the key
#
cp ${KEY} ${KEY}.orig
openssl rsa -passin pass:12345 -in ${KEY}.orig -out ${KEY}
rm -f ${KEY}.orig


echo "#"
echo "#"
echo "# Creating the self-signed certificate."
echo "#"
echo "#"
openssl x509 -req -days 365 -in ${CSR} -signkey ${KEY} -out ${CERTIFICATE}

#
# We don't need our signing request anymore.
#
rm -f ${CSR}

echo "#"
echo "#"
echo "# All done!  Here are your files:"
echo "# Private key: ${KEY}"
echo "# Certificate: ${CERTIFICATE}"
echo "#"
echo "#"


