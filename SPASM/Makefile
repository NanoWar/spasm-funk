CC = $(CROSS_COMPILE)g++
LD = $(CROSS_COMPILE)ld

CXXFLAGS += -I. -DUSE_REUSABLES -DUSE_GMP -DUNIXVER -DUSE_BUILTIN_FCREATE -std=c++11
LDFLAGS += -lc -lgmp -lm -lcrypto

# Suffix Rules

.SUFFIXES: .cpp

.cpp.o:
	$(CC) $(CXXFLAGS) -c $<

.cpp:
	$(CC) $(CXXFLAGS) $< -o $@

SRC = main.cpp opcodes.cpp pass_one.cpp pass_two.cpp utils.cpp export.cpp preop.cpp directive.cpp console.cpp \
      expand_buf.cpp hash.cpp list.cpp parser.cpp storage.cpp errors.cpp bitmap.cpp modp_ascii.cpp opcodes_ez80.cpp

OBJ = $(addsuffix .o, $(basename $(SRC)))

OBJ_FILES = $(addsuffix .o, $(basename $(notdir $(SRC))))

spasm: $(OBJ) Makefile
	$(CC) -o spasm $(OBJ_FILES) $(LDFLAGS)

clean:
	rm $(OBJ)

release32:
	cp spasm ../bin/spasm-linux32

release64:
	cp spasm ../bin/spasm-linux64

install: spasm /usr/bin/spasm
