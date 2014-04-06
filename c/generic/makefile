# Generic C Makefile
# Travis Lane
# A generic makefile for small C projects
# 
# All C source files should be in src. 
# This makefile is not recursive and does not handle subdirectories.
# src/*.c
# obj/*.o
# bin/target
#
# Also note, I don't track your .h files.
# If you modify a .h file you'll have to rebuild.

CC=gcc
CFLAGS=-Wall -std=c99
LIBS=

SRC_EXTENSION=.c
OBJ_EXTENSION=.o
DEBUG_OBJ_EXTENSION=_debug$(OBJ_EXTENSION)
RELEASE_OBJ_EXTENSION=_release$(OBJ_EXTENSION)

#Where your source is
SRC_DIR=src
SOURCES=$(wildcard $(SRC_DIR)/*$(SRC_EXTENSION))

# Where the objects will be
OBJ_DIR=obj
RELEASE_OBJECTS=$(patsubst $(SRC_DIR)/%$(SRC_EXTENSION),$(OBJ_DIR)/%$(RELEASE_OBJ_EXTENSION),$(SOURCES))
DEBUG_OBJECTS=$(patsubst $(SRC_DIR)/%$(SRC_EXTENSION),$(OBJ_DIR)/%$(DEBUG_OBJ_EXTENSION),$(SOURCES))

# This is the name of your binary.
RELEASE_BIN=example
DEBUG_BIN=example_debug

# Where the binary is being put
BIN_DIR=bin
RELEASE_TARGET=$(BIN_DIR)/$(RELEASE_BIN)
DEBUG_TARGET=$(BIN_DIR)/$(DEBUG_BIN)

# Flags for debug vs release
DEBUG_FLAGS=-O0 -g -DDEBUG
RELEASE_FLAGS=-O3 -DNDEBUG

# Default make 
.PHONY: all
all: dir debug

# Make directory structure
.PHONY: dir
dir:
	test -d $(BIN_DIR) || mkdir $(BIN_DIR)
	test -d $(OBJ_DIR) || mkdir $(OBJ_DIR)
 
# Clean objects
.PHONY: clean
clean:
	rm -f $(DEBUG_TARGET) $(RELEASE_TARGET)
	rm -f $(DEBUG_OBJECTS)
	rm -f $(RELEASE_OBJECTS)
 
# Build debug
.PHONY: debug
debug: CFLAGS += $(DEBUG_FLAGS)
debug: $(DEBUG_OBJECTS)
	$(CC) -o $(DEBUG_TARGET) $^ $(LIBS)
 
# Build Release
.PHONY: release
release: CFLAGS += $(RELEASE_FLAGS)
release: $(RELEASE_OBJECTS)
	$(CC) -o $(RELEASE_TARGET) $^ $(LIBS)
 
# Build Object Files
# Debug
$(OBJ_DIR)/%$(DEBUG_OBJ_EXTENSION): $(SRC_DIR)/%$(SRC_EXTENSION)
	$(CC) $(CFLAGS) $(LIBS) -o $@ -c $<
# Release
$(OBJ_DIR)/%$(RELEASE_OBJ_EXTENSION): $(SRC_DIR)/%$(SRC_EXTENSION)
	$(CC) $(CFLAGS) $(LIBS) -o $@ -c $<
