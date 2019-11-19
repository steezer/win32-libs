CPP       = g++.exe
CC        = gcc.exe
WINDRES   = windres.exe
GPROF     = gprof.exe
RM        = rm -f
LINK      = g++.exe

SRC       = WTLExplorer.cpp MainFrm.cpp ShellMgr.cpp 
SRCH      = mainfrm.h resource.h stdafx.h ExplorerCombo.h ShellMgr.h
OBJ       = $(SRC:.cpp=.o)
RC        = WTLExplorer.rc
RES       = $(RC:.rc=.res)
BIN       = WTLExplorer.exe
LINKOBJ   = $(OBJ) $(RES)
LIBS      = -mwindows -lkernel32 -luser32 -lgdi32 -lcomdlg32 -lole32 -lwinspool -lshlwapi -lcomctl32 -Wl,--allow-multiple-definition
INCS      = -I"../../atlport/include" -I"../../wtl/include/"
CXXFLAGS  = -fpermissive -w
CFLAGS    = 

.PHONY: all all-before all-after clean clean-custom
all: all-before $(BIN) all-after

clean: clean-custom
	$(RM) $(OBJ) $(BIN) $(RES)

$(BIN): $(OBJ) $(RES)
	$(LINK) $(LINKOBJ) -o $@ $(LIBS) -s

$(OBJ): $(GLOBALDEPS) $(SRC) $(SRCH)
	$(CPP) -c $(SRC) $(CXXFLAGS) $(INCS) 

$(RES): $(RC)
	$(WINDRES) --input-format=rc -o $@ $(INCS) $(RC) -O coff
