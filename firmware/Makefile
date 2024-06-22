.PHONY: all build cmake clean format

BUILD_DIR := build
BUILD_TYPE ?= Debug

all: build

${BUILD_DIR}/Makefile:
	cmake \
		-B${BUILD_DIR} \
		-DCMAKE_BUILD_TYPE=${BUILD_TYPE} \
		-DCMAKE_EXPORT_COMPILE_COMMANDS=ON

cmake: ${BUILD_DIR}/Makefile

build: cmake
	$(MAKE) -C ${BUILD_DIR} --no-print-directory

flash:
	st-flash write build/MidiController_v3.bin 0x08000000

erase:
	st-flash erase

clean:
	rm -rf $(BUILD_DIR)
