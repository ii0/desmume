TARGETS  = http_test net_ifinfo

LIBRETRO_COMM_DIR := ../..

INCFLAGS = -I$(LIBRETRO_COMM_DIR)/include

ifeq ($(DEBUG),1)
CFLAGS += -O0 -g
else
CFLAGS += -O2
endif
CFLAGS += -Wall -pedantic -std=gnu99

HTTP_TEST_C = \
				  $(LIBRETRO_COMM_DIR)/net/net_http.c \
				  net_http_test.c \
				  $(LIBRETRO_COMM_DIR)/net/net_compat.c \
				  $(LIBRETRO_COMM_DIR)/compat/compat_strl.c

HTTP_TEST_OBJS := $(HTTP_TEST_C:.c=.o)

NET_IFINFO_C = \
					$(LIBRETRO_COMM_DIR)/net/net_ifinfo.c \
					net_ifinfo_test.c

NET_IFINFO_OBJS := $(NET_IFINFO_C:.c=.o)

.PHONY: all clean

all: $(TARGETS)

%.o: %.c
	$(CC) $(INCFLAGS) $< -c $(CFLAGS) -o $@

http_test: $(HTTP_TEST_OBJS)
	$(CC) $(INCFLAGS) $(HTTP_TEST_OBJS) $(CFLAGS) -o $@

net_ifinfo: $(NET_IFINFO_OBJS)
	$(CC) $(INCFLAGS) $(NET_IFINFO_OBJS) $(CFLAGS) -o $@

clean:
	rm -rf $(TARGETS) $(HTTP_TEST_OBJS) $(NET_IFINFO_OBJS)
