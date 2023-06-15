EXE=simsyn
CC=cc
CFILES=$(wildcard src/*.c)
OBJS=$(patsubst src/%.c, bin/linux/%.o, $(CFILES))
DEPS=$(patsubst src/%.c, bin/linux/%.d, $(CFILES))
FLAGS=-Wall -Wextra -Werror -I./include/

.PHONY: all run clean

all: bin/linux/$(EXE)

bin/linux/$(EXE): $(OBJS)
	$(CC) $(FLAGS) -o bin/linux/$(EXE) $(OBJS)
	cp bin/linux/$(EXE) ../linux/

-include $(DEPS)

bin/linux/%.o: src/%.c
	$(CC) $(FLAGS) -MMD -c $< -o $@

run:
	../linux/$(EXE)

clean:
	rm bin/linux/*
