ifndef CFLAGS
	CFLAGS = -O2 -pipe
endif

ifndef LDFLAGS
	LDFLAGS = 
endif

ifndef OUTPUT
	OUTPUT = saedit
endif

LDFLAGS += -export-dynamic

CFLAGS += `pkg-config --cflags gtk+-3.0 gtksourceview-3.0`

LDFLAGS += `pkg-config --libs gtk+-3.0 gtksourceview-3.0`

all:main.o search.o config.o xml.o sae.o compile clean
compile: main.o search.o config.o xml.o
	gcc ${CFLAGS} -o '${OUTPUT}' main.o search.o config.o xml.o sae.o ${LDFLAGS}
main.o: main.c main.h search.h config.h common.h xml.h
	gcc ${CFLAGS}-c -o main.o main.c
search.o: search.c search.h common.h
	gcc ${CFLAGS} -c -o search.o search.c
xml.o: xml.c xml.h common.h
	gcc ${CFLAGS} -c -o xml.o xml.c
config.o: config.c config.h common.h
	gcc ${CFLAGS} -c -o config.o config.c
sae.o: sae.c sae.h common.h
	gcc ${CFLAGS} -c -o sae.o sae.c
clean:
	rm -rfv *.o *~
