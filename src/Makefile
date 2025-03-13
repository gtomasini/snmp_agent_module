#
#
# Makefile to generate sysInfoGroup.so
# 
# usage:
# "make" : generate library
# "make clean" : remove *.o , *.so
#

CC=gcc
LDFLAGS= `net-snmp-config --cflags`

PROG= sysTestGroup.so
SRCS= sysTestGroup.c
OBJS= $(SRCS:.c=.o)

# shared library flags (assumes gcc)
DLFLAGS=-fPIC -shared

all:$(PROG)
$(PROG): $(OBJS)
	$(CC) -Dall -o $@ $(OBJS) $(LDFLAGS) $(DLFLAGS)
.c.o:
	@if test "$(CC)" = "" ; then \
	echo "Environment variable CC must be set with compiler path" ; \
	exit 1 ; \
	fi
	$(CC) -o $@ -c $< -g $(LDFLAGS) $(DLFLAGS)

clean:
	rm -f $(OBJS) $(PROG) 
