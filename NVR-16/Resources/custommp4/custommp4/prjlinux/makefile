#CCARCH := arm_v5t_le-
#CCARCH := powerpc-linux-
#CCARCH := arm-hismall-linux-
#CCARCH := arm-hisiv100nptl-linux-

include  ../../../../Makefile.param

CCILINUX_eti_CC    := $(CCARCH)gcc
CCILINUX_eti_CPP   := $(CCARCH)g++
CCILINUX_eti_LD    := $(CCARCH)ld
CCILINUX_eti_AR    := $(CCARCH)ar
CCILINUX_eti_STRIP := $(CCARCH)strip

INC_DIR := ../include ../../Common/inc/mod
SRC_DIR := ../source

LIB_TARGET := libcustommp4.a
#INSTALL_LIB_PATH := ../../common/lib/debug
INSTALL_LIB_PATH := ../../../../Common/lib

#CFLAGS += -fpack-struct

#CFLAGS += -O2 -Wall -fno-strict-aliasing #-march=armv5t
CFLAGS += -g -Wall -fno-strict-aliasing

#CFLAGS += -Wall -fno-strict-aliasing -march=armv5t -mabi=apcs-gnu

#CFLAGS += -D__DEBUG

#LINUXKERNEL_INSTALL_DIR=/home/user/workdir/lsp/ti-davinci		
#LINUXKERNEL_INSTALL_DIR=/opt/mtwk/usr/local/powerpc-linux/gcc-3.4.3-glibc-2.3.3/powerpc-linux
INC_PATH += $(INC_DIR) ../../common/include# $(LINUXKERNEL_INSTALL_DIR)/include

CFLAGS += $(foreach dir,$(INC_PATH),-I$(dir))

OBJS :=$(SRC_DIR)/debug/custommp4					\
				$(SRC_DIR)/debug/util							\
				$(SRC_DIR)/debug/partitionindex		\
				$(SRC_DIR)/debug/diskmanage				\

OBJS := $(foreach obj,$(OBJS),$(obj).o)

$(SRC_DIR)/debug/%.o: $(SRC_DIR)/%.c
	$(CCILINUX_eti_CC) $(CFLAGS) -c $< -o $@  
$(SRC_DIR)/debug/%.o: $(SRC_DIR)/%.cpp
	$(CCILINUX_eti_CPP) $(CFLAGS) -c $< -o $@
	
all:$(LIB_TARGET)
$(LIB_TARGET) : $(OBJS)
	$(CCILINUX_eti_AR) crus $(LIB_TARGET) $(OBJS)
	install -D -m 644 $(LIB_TARGET) $(INSTALL_LIB_PATH)/$(LIB_TARGET)
#	cp $(LIB_TARGET) /home/user/dvevm_1_00_00_32/codec_engine_1_00/examples/apps/mpeg4/dualcpu/lib/
#	install -D -m 644 $(LIB_TARGET) /root/src/9108/common/lib/debug/$(LIB_TARGET)
#	cp $(LIB_TARGET) /home/chen/prj/prj1-hs3511/app/common/lib/debug -f
	
clean:
	rm -f $(OBJS) *.pdb *.map
	rm -f $(LIB_TARGET)


