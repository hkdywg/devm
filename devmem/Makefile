#
# Name:    Makefile
#
# Purpose: makefile of this project
#
# Copyright (C) 2014 wowotech
# Subject to the GNU Public License, version 2.

# Created By:         wowo<www.wowotech.net>
# Created Date:       2014-01-23
# 
# ChangeList:
# Created in 2014-01-23 by wowo;
#

#CC      = /opt/arm-2012.03/bin/arm-none-linux-gnueabi-gcc
CC      = /usr/local/linaro-aarch64-2018.08-gcc8.2/bin/aarch64-linux-gnu-gcc 
#CC      = gcc

CFLAGS  = -Wall -O3 -static
INCFLAGS=
LDFLAGS = -static

OBJS    = devmem.o
TARGETS = devmd devmset devmcpy devmload devmsave

DESTDIR=$(shell pwd)/release
OBJDIR=$(shell pwd)/obj
#DESTDIR=/tmp

.PHONY:all 
all:$(TARGETS)

devmd:$(OBJS) devmd.o
	$(CC) -o $@ $^ $(LDFLAGS)
	mv $@ $(DESTDIR)

devmset:$(OBJS) devmset.o
	$(CC) -o $@ $^ $(LDFLAGS)
	mv $@ $(DESTDIR)

devmcpy:$(OBJS) devmcpy.o
	$(CC) -o $@ $^ $(LDFLAGS)
	mv $@ $(DESTDIR)

devmload:$(OBJS) devmload.o
	$(CC) -o $@ $^ $(LDFLAGS)
	mv $@ $(DESTDIR)

devmsave:$(OBJS) devmsave.o
	$(CC) -o $@ $^ $(LDFLAGS)
	mv $@ $(DESTDIR)

%.o:%.c
	$(CC) -o $@ -c $< $(CFLAGS) $(INCFLAGS)

%.d:%.c
	@set -e; rm -f $@; $(CC) -MM $< $(INCFLAGS) > $@.$$$$; \
	sed 's,\($*\)\.o[ :]*,\1.o $@ : ,g' < $@.$$$$ > $@; \
	rm -f $@.$$$$

-include $(OBJS:.o=.d)

.PHONY:clean 
clean:
	rm -f $(TARGETS) *.exe *.o *.d *.d.*
