ROOT_DIR:=../../../../..
include $(ROOT_DIR)/system.mk

# include Faraday memory compiler
MEMAKER_SRC:=source /opt/ic_tools/init/init-memaker-20100111-130LL

# memory compilation flags
BOOTROM_WORDS:=$(shell echo '2^($(BOOTROM_ADDR_W)-2)' | bc)
MEM_FLAGS:=-s fsc0l_d -type sp -words $(BOOTROM_WORDS) -bits 32 -mux 1 -rformat hex -romcode $(BOOT_DIR)/boot.hex -ds -lib -ver -lef

# run memory compiler
run:
	$(MEMAKER_SRC) && memaker $(MEM_FLAGS)
	sed  -i 's/ME\([0-9]\)/metal\1/g' *.lef

clean:
	@find . -type f -not -name Makefile -delete

.PHONY: all clean 
