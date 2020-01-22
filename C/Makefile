CC = gcc
SRCDIR = src
LIBDIR = lib
INCDIR = include
EXECDIR = bin
CFLAGS = -O3 -std=c18 -Wextra -Wall -I $(INCDIR)
LDFLAGS = -L $(LIBDIR)
SRC = $(wildcard $(SRCDIR)/*.c)
OBJ = $(SRC:.c=.o)
EXEC = prog

.PHONY: run all clean mrproper layout
.DEFAULT_GOAL = all

run : all
	./$(EXECDIR)/$(EXEC)

layout : $(INCDIR) $(SRCDIR) $(LIBDIR)

all : $(EXECDIR)/$(EXEC)

$(LIBDIR) :
	mkdir -p $(LIBDIR)

$(INCDIR) :
	mkdir -p $(INCDIR)

$(SRCDIR) :
	mkdir -p $(SRCDIR)

$(EXECDIR)/$(EXEC) : $(OBJ)
	mkdir -p $(EXECDIR)
	$(CC) -o $@ $^ $(LDFLAGS)

$(SRCDIR)/%.o : $(SRCDIR)%.cpp
	$(CC) -o $@ -c $<

clean :          ## Clean all object files
	rm -rf $(SRCDIR)/*.o

mrproper : clean ## Clean all object and exe files
	rm -rf $(EXECDIR)
