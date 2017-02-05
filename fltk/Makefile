# Автоматически подгружаются ./sourse/*.cpp
SOURCES_OBJ_CPP:= $(wildcard ./source/*.cpp) $(wildcard ./include/*.cpp)
SOURCES_OBJ_C:= $(wildcard ./source/*.c) $(wildcard ./include/*.c)
SOURCES:=$(SOURCES_OBJ_CPP) $(SOURCES_OBJ_C)
# Автоматически подгружаются  ./include/*.h
INCLUDE:= -I./include/
# Название файла программы
EXE=writeanovell
# Автоматически выделяются .o
OBJECTS=$(SOURCES_OBJ_CPP:.cpp=.o) $(SOURCES_OBJ_C:.c=.o)
# переменная CC указывает компилятор, используемый для сборки
CC=g++
CC_C=gcc
# в переменной CFLAGS лежат флаги, которые передаются компилятору
FL_FLAGS=$(shell fltk-config --cxxflags --ldflags --use-images)
SQLite_FLAGS= -lpthread -ldl 
#CFLAGS=-c
#CFLAGS=-c -Wall 
CFLAGS=-c -std=c++11 -Wall -Werror -w -g
CFLAGS_C=-c -Wall -Werror -w -g
LDFLAGS=$(SQLite_FLAGS) $(FL_FLAGS)
#LDFLAGS=
#

# По-умолчанию всегда срабатывает верхний вариант
main: $(SOURCES) $(EXE)

#.c:
#	$(CC_C) $< -o $@ $(CFLAGS) -o $@
#	$(CC_C) $(INCLUDE) $(SOURCES_OBJ_C) -o $@ $(SQLite_FLAGS)

$(EXE): $(OBJECTS)
	@echo "\tEXE start:\t" $@ "\t"
	$(CC) $(INCLUDE) $(OBJECTS) -o $@ $(LDFLAGS)
#	$(CC) $(LDFLAGS) $(INCLUDE) $(OBJECTS) -o $@
	@echo "\tEXE end.\t"

.cpp.o:
	@echo "\t.cpp.o start:\t" $@ "\t"
	$(CC) $< -o $@ $(CFLAGS)
#	$(CC) $(CFLAGS) $< -o $@
	@echo "\t.cpp.o end\t"

.c.o:
	@echo "\t.c start:\t" $@ "\t"
	$(CC_C) $< -o $@ $(CFLAGS_C)
	@echo "\t.c end\t"

# Дополнительно, для тестирования
cxx:
	$(CC) $(SOURCES) -o $(EXE) $(LDFLAGS)
#	$(CC) $(SOURCES) -o $(EXE) `fltk-config --cxxflags --ldflags`

help:
	@echo "List of options"
	@echo "\tSOURCES:\t$(SOURCES)\n\tOBJECTS:\t$(OBJECTS)\n\tINCLUDE:\t$(INCLUDE)\n\tCompiler_C:\t$(CC_C)\n\tCFLAGS: \t$(CFLAGS_C)\n\tCompiler:\t$(CC)\n\tCFLAGS: \t$(CFLAGS)\n\tLDFLAGS: \t$(LDFLAGS)\n"

clear:
	rm $(EXE) $(OBJECTS)

clear-o:
	rm $(OBJECTS)
