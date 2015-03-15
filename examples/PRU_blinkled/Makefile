CC = clpru
DEVICE=am335x
CFLAGS = --silicon_version=3 -o1 -D$(DEVICE)
HEXBIN = hexpru

SWDIR = ../../

PRU_C_DIR = -I/usr/share/ti/cgt-pru/lib \
	    -I/usr/share/ti/cgt-pru/include \
	    -I${SWDIR}/include \
	    -I${SWDIR}/include/arm7a \
	    -I$SWDIR}/include/hw \
	    -I${SWDIR}/platform/beaglebone

DRIVER_DIR = ${SWDIR}/drivers
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
