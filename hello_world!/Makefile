NVCC = /opt/cuda/bin/nvcc
NVCC_FLAGS = -g -G -Xcompiler -Wall
main : hello_world.cu
	$(NVCC) $(NVCC_FLAGS) $< -o $@
