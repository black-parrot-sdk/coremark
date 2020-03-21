#Coremark makefile for BP

RISCV_GCC = $(CROSS_COMPILE)gcc -mabi=lp64 -march=rv64ia -mcmodel=medany -fno-builtin-printf

RISCV_LINK = -O0 -static -nostdlib -nostartfiles -lm -lgcc -T test.ld -L../

RISCV_TESTS_DIR = ../../riscv-tests/benchmarks

COMMON_FILES = -I$(RISCV_TESTS_DIR)/../env -I$(RISCV_TESTS_DIR)/common -I../ -I./
COMMON_FILES += $(RISCV_TESTS_DIR)/common/crt.S $(RISCV_TESTS_DIR)/common/syscalls.c

#Number of iterations coremark runs for
ITER_NUM = 2
#indicates whether or not BP has float support
BP_HAS_FLOAT = 0

.PHONY: riscv

riscv:
	$(RISCV_GCC) $(COMMON_FILES) -o coremark.riscv $(wildcard *.c) $(wildcard ../*.c) -DITERATIONS=$(ITER_NUM) \
	-DHAS_FLOAT=$(BP_HAS_FLOAT) $(RISCV_LINK)

clean:
	rm -f *.riscv
