UNAME_S := $(shell uname)

ifeq ($(UNAME_S), Darwin)
	LDFLAGS = -Xlinker -framework,OpenGL -Xlinker -framework,GLUT
else
	LDFLAGS += -L/opt/cuda/samples/common/lib/linux/x86_64
	LDFLAGS += -lglut -lGL -lGLU -lGLEW
endif

NVCC = /opt/cuda/bin/nvcc
NVCC_FLAGS = -g -G -Xcompiler "-Wall -Wno-deprecated-declarations"
INC = -I/opt/cuda/samples/common/inc

all: main

main: main.o kernel.o
	$(NVCC) $^ -o $@ $(LDFLAGS)

main.o: main.cpp kernel.h interactions.h
	$(NVCC) $(NVCC_FLAGS) $(INC) -c $< -o $@

kernel.o: kernel.cu kernel.h
	$(NVCC) $(NVCC_FLAGS) -c $< -o $@

clean:
	rm -f *.o *.exe
