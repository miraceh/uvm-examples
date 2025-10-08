# Simple Makefile for QuestaSim

# Variables
WORK      = work
DUT_SRC   = ../dut/dut.sv
TB_SRC    = ../tb/top_tb.sv
TOP       = top_tb

VLOG      = vlog
VSIM      = vsim

# Default target: compile and simulate
all: comp sim

# Compile DUT and TB
comp:
	@echo "Compiling DUT and Testbench..."
	@if [ ! -d $(WORK) ]; then vlib $(WORK); fi
	$(VLOG) -work $(WORK) $(DUT_SRC) $(TB_SRC)

# Run simulation
sim:
	@echo "Running simulation..."
	$(VSIM) -c -do "run -all; quit" $(WORK).$(TOP)

# Clean generated files
clean:
	@echo "Cleaning up..."
	rm -rf $(WORK) transcript vsim.wlf vsim.db modelsim.ini *.log

.PHONY: all comp sim clean
