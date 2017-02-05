# Автоматически подгружаются ./sourse/*.cpp
SOURCES:= $(wildcard ./source/*.c??) $(wildcard ./include/*.c??)
# Автоматически подгружаются  ./include/*.h
INCLUDE:= -I./include/
EXE=writeanovell
# Автоматически выделяются .o
OBJECTS=$(SOURCES:.cpp=.o)
# переменная CC указывает компилятор, используемый для сборки
CC=g++
# в переменной CFLAGS лежат флаги, которые передаются компилятору
FL_FLAGS=$(shell fltk-config --cxxflags --ldflags --use-images)
#SQLite_FLAGS=(-lpthread -ldl)
#CFLAGS=-c
#CFLAGS=-c -Wall
CFLAGS=-c -std=c++11 -Wall -Werror -w -g
LDFLAGS=$(FL_FLAGS)
#LDFLAGS=
#

# По-умолчанию всегда срабатывает верхний вариант
main: $(SOURCES) $(EXE)

$(EXE): $(OBJECTS)
	$(CC) $(INCLUDE) $(OBJECTS) -o $@ $(LDFLAGS)
#	$(CC) $(LDFLAGS) $(INCLUDE) $(OBJECTS) -o $@

.cpp.o:
	$(CC) $< -o $@ $(CFLAGS)
#	$(CC) $(CFLAGS) $< -o $@

cxx:
	$(CC) $(SOURCES) -o $(EXE) $(LDFLAGS)
#	$(CC) $(SOURCES) -o $(EXE) `fltk-config --cxxflags --ldflags`

echo:
	echo $(SOURCES)
	echo $(OBJECTS)
	echo $(INCLUDE)

clear:
	rm $(EXE) $(OBJECTS)

clear-o:
	rm $(OBJECTS)
