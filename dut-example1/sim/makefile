# Simple Makefile for QuestaSim with TB and TLM modes

# Variables
WORK      = work
DUT_SRC   = ../dut/dut.sv
TB_SRC    = ../tb/top_tb.sv
TLM_SRC   = ../tlm/top_tb.sv
TOP_TB    = top_tb
TOP_TLM   = top_tb

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
	$(VSIM) -c -do "run -all; quit" $(WORK).$(TOP_TB)

# ---------- TLM ----------
comp_tlm:
	@echo "Compiling DUT and TLM..."
	@if [ ! -d $(WORK) ]; then vlib $(WORK); fi
	$(VLOG) -work $(WORK) $(DUT_SRC) $(TLM_SRC)

sim_tlm:
	@echo "Running TLM simulation..."
	$(VSIM) -c -do "run -all; quit" $(WORK).$(TOP_TLM)

# ---------- Clean ----------
clean:
	@echo "Cleaning up..."
	rm -rf $(WORK) transcript vsim.wlf vsim.db modelsim.ini *.log

.PHONY: all comp sim comp_tlm sim_tlm clean
