AM_CFLAGS = $(libirecovery_CFLAGS) $(libimobiledevice_CFLAGS) $(libusbmuxd_CFLAGS) $(openssl_CFLAGS)
AM_LDFLAGS = $(libirecovery_LIBS) $(libimobiledevice_LIBS) $(libusbmuxd_LIBS) $(openssl_LIBS)

bin_PROGRAMS = igetnonce
igetnonce_CFLAGS = $(AM_CFLAGS)
igetnonce_LDADD = $(AM_LDFLAGS)

if WIN32
igetnonce_LDFLAGS = -all-static -static-libgcc -static-libstdc++ $(AM_LDFLAGS)
endif

igetnonce_SOURCES = common.c dfu.c idevicerestore.c normal.c recovery.c main.c

