# Simple Makefile for QuestaSim with TB modes

# Variables
WORK      = work
# DUT_SRC   = ../dut/dut.sv
DUT_SRC   = ../dut/dut2.sv
TB_SRC    = ../tb/top_tb.sv
TOP_TB    = top_tb

VLOG      = vlog
VOPT      = vopt
VSIM      = vsim

# Default: compile → optimize → simulate
all: comp opt sim

# ---------- Compile ----------
comp:
	@echo "Compiling DUT and TB..."
	@if [ ! -d $(WORK) ]; then vlib $(WORK); fi
	$(VLOG) -work $(WORK) $(DUT_SRC) $(TB_SRC)

# ---------- Optimize ----------
opt:
	@echo "Optimizing design with +acc..."
	$(VOPT) $(WORK).$(TOP_TB) -o $(TOP_TB)_opt +acc

# ---------- Simulate ----------
sim:
	@echo "Running TB simulation..."
	$(VSIM) -c -do "run -all; quit" $(TOP_TB)_opt +UVM_TESTNAME=my_case0

# ---------- Clean ----------
clean:
	@echo "Cleaning up..."
	rm -rf $(WORK) transcript vsim.wlf vsim.db modelsim.ini *.log $(TOP_TB)_opt

.PHONY: all comp opt sim clean
