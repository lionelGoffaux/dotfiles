CXX = g++
SRCDIR = src
LIBDIR = lib
INCDIR = include
EXECDIR = bin
CXXFLAGS = -O3 -Wextra -Wall -std=c++17 -I $(INCDIR)
LDFLAGS = -L $(LIBDIR)
SRC = $(wildcard $(SRCDIR)/*.cpp)
OBJ = $(SRC:.cpp=.o)
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
	$(CXX) -o $@ $^ $(LDFLAGS)

$(SRCDIR)/%.o : $(SRCDIR)%.cpp
	$(CXX) -o $@ -c $<

clean :          ## Clean all object files
	rm -rf $(SRCDIR)/*.o

mrproper : clean ## Clean all object and exe files
	rm -rf $(EXECDIR)