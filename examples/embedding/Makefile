MPTOP = ../..
CROSS_COMPILE=nxdk #i686-windows
CC=nxdk-cc
CXX=nxdk-c++
CFLAGS=-std=c99 -I. -I$(MPTOP) -DNO_QSTR
LDFLAGS=-L.

hello-embed: hello-embed.o -lmicropython

-lmicropython:
	$(MAKE) -f $(MPTOP)/examples/embedding/Makefile.upylib MPTOP=$(MPTOP)
