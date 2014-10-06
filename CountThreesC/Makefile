#!/usr/bin/make -f

SHELL=/bin/sh

.SUFFIXES:
.SUFFIXES: .c .o

# src directory contains .c and .h files
OBJDIR = src

TESTDIR = test

# object files
objects = countThrees.o readInt32BitLE.o

countThrees : prep $(objects)
	cc -o countThrees $(objects)
readInt32BitLE.o : $(OBJDIR)/readInt32BitLE.c $(OBJDIR)/readInt32BitLE.h
	cc -c $(OBJDIR)/readInt32BitLE.c
countThrees.o : $(OBJDIR)/countThrees.c $(OBJDIR)/readInt32BitLE.h
	cc -c $(OBJDIR)/countThrees.c

# prep
.PHONY : prep
prep :
	mkdir $(OBJDIR)
	unzip CountThreesC.zip -d $(OBJDIR)

# run compiled executable countThrees
.PHONY : test
test :
	-mkdir $(TESTDIR)
	-unzip threesData.zip -d $(TESTDIR)
	-mv countThrees $(TESTDIR)
	-cd $(TESTDIR) && ./countThrees

.PHONY : clean
clean : 
	-rm $(objects)
	-rm -rf $(OBJDIR) $(TESTDIR)
