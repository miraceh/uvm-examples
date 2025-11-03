# Simple Makefile for QuestaSim with TB modes

# Variables
WORK      = work
# DUT_SRC   = ../dut/dut.sv
DUT_SRC   = ../dut/dut2.sv
TB_SRC    = ../tb/top_tb.sv
TOP_TB    = top_tb

VLOG      = vlog
VSIM      = vsim

# Default: compile & run TB
all: comp sim

# ---------- TB ----------
comp:
	@echo "Compiling DUT and TB..."
	@if [ ! -d $(WORK) ]; then vlib $(WORK); fi
	$(VLOG) -work $(WORK) $(DUT_SRC) $(TB_SRC)

sim:
	@echo "Running TB simulation..."
	$(VSIM) -c -do "run -all; quit" $(WORK).$(TOP_TB) +UVM_TESTNAME=my_case0

# ---------- Clean ----------
clean:
	@echo "Cleaning up..."
	rm -rf $(WORK) transcript vsim.wlf vsim.db modelsim.ini *.log

.PHONY: all comp sim clean
