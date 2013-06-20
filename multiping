#!/bin/bash

#
# Errors are fatal
#
set -e

HOSTS=""

while true
do
	ARG=$1
	if test ! "$1"
	then
		break

	elif test $ARG == "-h"
	then
		echo "Syntax: $0 hostname [hostname [hostname [...]]]"
		exit 1
		
	else
		HOSTS="${HOSTS} ${ARG}"

	fi

	shift
done


echo "Preparing to ping hosts: ${HOSTS}..."


#
# Kill both of our ping sessions
#
function _exit() {

	JOB=1
	for HOST in $HOSTS
	do
		kill -INT %${JOB}
		JOB=$(($JOB + 1))
	done

}

#
# Start pinging hosts
#
for HOST in $HOSTS
do

	#ping $HOST 2>&1 | sed -e s/"^"/"${HOST}: "/ &
# 64 bytes from 10.0.3.1:
		#| sed -e s/"64 bytes from [^:]+:"/"TEST"/ \
	ping $HOST 2>&1 \
		| sed \
		-e s/"64 bytes from[^:]*: "/""/ \
		-e s/"^"/"${HOST}: "/ \
		&
done


#
# Install our signal handler
#
trap _exit SIGINT SIGHUP SIGTERM 
#trap -p # Debugging

#
# Keep the script running for a very long time
#
sleep 86400

#
# If exit normally, clean up
#
echo "Script is over"
_exit


