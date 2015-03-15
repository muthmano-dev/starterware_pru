CC = clpru
DEVICE=am335x
CFLAGS = --silicon_version=3 -o1 -D$(DEVICE)
HEXBIN = hexpru

PRU_C_DIR = -I/usr/share/ti/cgt-pru/lib \
	    -I/usr/share/ti/cgt-pru/include \
	    -I../../AM335X_StarterWare_02_00_01_01/include \
	    -I../../AM335X_StarterWare_02_00_01_01/include/arm7a \
	    -I../../AM335X_StarterWare_02_00_01_01/include/hw \
	    -I../../AM335X_StarterWare_02_00_01_01/platform/beaglebone

DRIVER_DIR = ../../AM335X_StarterWare_02_00_01_01/drivers
SRC = $(wildcard ${DRIVER_DIR}/*.c) blinkled.c
OUT = blinkled.out
CMD = ./lnk.cmd
BUILD_DIR = build

$(BUILD_DIR)/$(OUT):$(SRC)
	mkdir -p $(BUILD_DIR)
	$(CC) $(CFLAGS) $(PRU_C_DIR) $^ -z $(CMD) -o $@ -m $(OUT).map
	rm -rf *.out *.map *.obj
	$(HEXBIN) ./bin.cmd $@
	cp *.bin $(BUILD_DIR)
	rm -rf *.bin
clean:
	rm -r build/
