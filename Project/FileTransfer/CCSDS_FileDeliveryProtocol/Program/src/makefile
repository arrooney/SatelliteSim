
PROJDIR = $(CURDIR)/..
INCLUDE += -I$(PROJDIR)/include



#---------------------------FOR FREE RTOS INTEGRATION---------------------------
#path to source includes
INCLUDE += -I$(PROJDIR)/../../../../Source/include

#path to compiler includes (portmacro.h)
INCLUDE += -I$(PROJDIR)/../../../../Source/portable/GCC/POSIX/

#path to FreeRTOSconfig
INCLUDE += -I$(PROJDIR)/../../../../Project/

#-------------------------------------------------------------------------------

CC = gcc 

#---------------------------File Names---------------------------
CFILES += port.c 
CFILES += utils.c
CFILES += server.c  #used for poxix port
CFILES += protocol_handler.c
CFILES += mib.c
CFILES += filesystem_funcs.c
CFILES += requests.c
CFILES += tasks.c
CFILES += file_delivery_app.c
CFILES += list.c
CFILES += packet.c
#----------------------------test files-------------------------

#entrypoint
MAIN = main

#---------------------------Compiler Warnings---------------------------
CWARNS += -W
CWARNS += -Wall
#CWARNS += -Werror
CWARNS += -Wextra
CWARNS += -Wformat
CWARNS += -Wmissing-braces
CWARNS += -Wno-cast-align
CWARNS += -Wparentheses
CWARNS += -Wshadow
CWARNS += -Wno-sign-compare
CWARNS += -Wswitch
CWARNS += -Wuninitialized
CWARNS += -Wunknown-pragmas
CWARNS += -Wunused-function
CWARNS += -Wunused-label
#CWARNS += -Wunused-parameter
CWARNS += -Wno-unused-parameter

CWARNS += -Wunused-value
CWARNS += -Wunused-variable
CWARNS += -Wmissing-prototypes

#---------------------------Libs---------------------------
LINKFLAGS = 
LIBS = -pthread

#---------------------------Compiler flags---------------------------

#32 bit machines, leave this out if your machine is 64 bit
CFLAGS += -m32
CFLAGS += -g -UUSE_STDIO -D__GCC_POSIX__=1
CFLAGS += -pthread
CFLAGS += -DDEBUG=1

# MAX_NUMBER_OF_TASKS = max pthreads used in the POSIX port. 
# Default value is 64 (_POSIX_THREAD_THREADS_MAX), the minimum number required by POSIX.
CFLAGS += -DMAX_NUMBER_OF_TASKS=300
CFLAGS += $(INCLUDE) $(CWARNS)

#---------------------------Build---------------------------
OBJS_FILES = $(patsubst %.c, %.o, $(CFILES))



all: $(MAIN) 

.PHONY: clean lib

$(MAIN): $(OBJS_FILES)

lib:  $(OBJS_FILES)
	ar -rsc file_delivery_app.a $(OBJS_FILES)

clean: 
	rm -f *.o $(MAIN)


