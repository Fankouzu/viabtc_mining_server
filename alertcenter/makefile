TARGET  := alertcenter.exe
INCS = -I ../network -I ../utils
LIBS = -L ../utils -lutils -L ../network -lnetwork -Wl,-Bstatic -lev -lhiredis -ljansson -lcurl -lssl -lcrypto -Wl,-Bdynamic -lm
include ../makefile.inc
