CC=gcc
CPP=g++
TARGET_NAME=antispam

ifeq ($(OS),Windows_NT)
EXT=dll
CFLAGS=-m32 -Wall -O1 -g -mtune=core2
LFLAGS=-m32 -g -shared -static-libgcc -static-libstdc++ 
LIBS=-L.. -lcom_plugin
else
EXT=so
CFLAGS=-m32 -Wall -O1 -g -fPIC -fvisibility=hidden -mtune=core2
LFLAGS=-m32 -g -shared -Wl,-z,noexecstack -Wl,-z,notext
LIBS=
endif

all: antispam_plugin.cpp
	$(CPP) $(CFLAGS) -c *.cpp
	$(CPP) $(LFLAGS) -o $(TARGET_NAME).$(EXT) *.o $(LIBS)
		
clean:
ifeq ($(OS),Windows_NT)
	del *.o
else
	rm *.o
endif