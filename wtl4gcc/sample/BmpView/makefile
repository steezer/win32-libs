CPP       = g++.exe
CC        = gcc.exe
WINDRES   = windres.exe
GPROF     = gprof.exe
RM        = rm -f
LINK      = g++.exe

SRC       = BmpView.cpp
SRCH      = list.h mainfrm.h props.h resource.h stdafx.h view.h
OBJ       = $(SRC:.cpp=.o)
RC        = BmpView.rc
RES       = $(RC:.rc=.res)
BIN       = BmpView.exe
LINKOBJ   = $(OBJ) $(RES)
LIBS      = -mwindows -lkernel32 -luser32 -lcomctl32 -lgdi32 -lcomdlg32 -lole32 -lwinspool -s
INCS      = -I"../../atlport/include" -I"../../wtl/include/"
CXXFLAGS  = -fpermissive -w
CFLAGS    = 

.PHONY: all all-before all-after clean clean-custom
all: all-before $(BIN) all-after

clean: clean-custom
	$(RM) $(OBJ) $(BIN) $(RES)

$(BIN): $(OBJ) $(RES)
	$(LINK) $(LINKOBJ) -o $@ $(LIBS)

$(OBJ): $(GLOBALDEPS) $(SRC) $(SRCH)
	$(CPP) -c $(SRC) -o $(OBJ) $(CXXFLAGS) $(INCS)

$(RES): $(RC)
	$(WINDRES) --input-format=rc -o $@ $(INCS) $(RC) -O coff
