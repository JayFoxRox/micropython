include ../../py/mkenv.mk

# qstr definitions (must come before including py.mk)
QSTR_DEFS = qstrdefsport.h

# include py core make definitions
include $(TOP)/py/py.mk

#CROSS_COMPILE = arm-none-eabi-

INC += -I.
INC += -I$(TOP)
INC += -I$(BUILD)

CFLAGS := $(INC) -Wall

#Debugging/Optimization
#ifeq ($(DEBUG), 1)
#CFLAGS += -O0 -ggdb
#else
#CFLAGS += -Os -DNDEBUG
#endif

#LDFLAGS = -nostdlib -T stm32f405.ld -Map=$@.map --cref

SRC_C = \
	main.c

#SRC_S = \
#	startup_stm32f40xx.s \
#	gchelper.s \

OBJ += $(PY_CORE_O) $(addprefix $(BUILD)/, $(SRC_C:.c=.o) $(SRC_S:.s=.o))

# Add stuff to nxdk target
main.exe: $(OBJ)

XBE_TITLE = micropython

#FIXME: Remove path
NXDK_DIR=/home/fox/Data/Projects/XboxDev/nxdk
include $(NXDK_DIR)/Makefile

#FIXME: This is a cruel hack because uPython sucks a bit (unistd.h)
CFLAGS := $(NXDK_CFLAGS) -Dssize_t=int -DSEEK_SET=0 -DSEEK_CUR=1 -DSEEK_END=2
CXXFLAGS := $(NXDK_CXXFLAGS)
ASFLAGS := $(NXDK_ASFLAGS)
LDFLAGS := $(NXDK_LDFLAGS)

include $(TOP)/py/mkrules.mk
