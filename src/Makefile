PROG_NAME=hello

CC=gcc

CFLAGS=-std=c89 -Wall -Wextra -Wpedantic -Werror

DEBUGFLAG=-g
STRIPFLAG=--strip-debug --strip-unneeded

.PHONEY : clean clean_obj clean_bin all Makefile strip strip.o $(PROG_NAME) $(PROG_NAME)_obj $(PROG_NAME)_debug $(PROG_NAME)_obj_debug

BIN_DIR=../bin
$(shell test -d $(BIN_DIR) && true || mkdir $(BIN_DIR))

OBJ_DIR=../obj
$(shell test -d $(OBJ_DIR) && true || mkdir $(OBJ_DIR))

all: $(PROG_NAME)

strip:
	strip $(STRIPGLAG) $(BIN_DIR)/$(PROG_NAME)

strip.o:
	strip $(STRIPFLAG) $(OBJ_DIR)/*.o

clean: clean_obj clean_bin

clean_bin:
	rm -rf $(BIN_DIR)

clean_obj: 
	rm -rf $(OBJ_DIR)

$(PROG_NAME)_obj:
	$(CC) $(CFLAGS) -o $(OBJ_DIR)/$(PROG_NAME).o -c $(PROG_NAME).c

$(PROG_NAME)_obj_debug:
	$(CC) $(CFLAGS) $(DEBUGFLAG) -o $(OBJ_DIR)/$(PROG_NAME).o -c $(PROG_NAME).c

$(PROG_NAME)_only:
	$(CC) $(CFLAGS) $(OBJ_DIR)/$(PROG_NAME).o -o $(BIN_DIR)/$(PROG_NAME)
	strip $(STRIPFLAG) $(BIN_DIR)/$(PROG_NAME)

$(PROG_NAME): $(PROG_NAME)_obj
	$(CC) $(CFLAGS) $(OBJ_DIR)/$(PROG_NAME).o -o $(BIN_DIR)/$(PROG_NAME)
	strip $(STRIPFLAG) $(BIN_DIR)/$(PROG_NAME)

$(PROG_NAME)_debug: $(PROG_NAME)_obj_debug
	$(CC) $(CFLAGS) $(DEBUGFLAG) $(OBJ_DIR)/$(PROG_NAME).o -o $(BIN_DIR)/$(PROG_NAME)




