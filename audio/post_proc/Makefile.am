AM_CFLAGS = -I ${WORKSPACE}/external/tinyalsa/include \
            -I ${WORKSPACE}/system/media/audio_effects/include

c_sources = bundle.c \
            equalizer.c \
            bass_boost.c \
            virtualizer.c \
            reverb.c \
            effect_api.c \
            effect_util.c

if AFE_PROXY
AM_CFLAGS += -DAFE_PROXY_ENABLED
endif

if HW_ACC_EFFECT
AM_CFLAGS += -DHW_ACCELERATED_EFFECTS
c_sources += hw_accelerator.c
endif

if AUDIOSPHERE
AM_CFLAGS += -DAUDIOSPHERE_ENABLED
c_sources += asphere.c
endif

library_include_HEADERS = $(h_sources)
library_includedir = $(includedir)

lib_LTLIBRARIES = libqcompostprocbundle.la
libqcompostprocbundle_la_SOURCES = $(c_sources)
libqcompostprocbundle_la_LIBADD = $(GLIB_LIBS) -llog -lcutils -ltinyalsa -ldl
libqcompostprocbundle_la_CFLAGS = $(AM_CFLAGS) $(GLIB_CFLAGS)
libqcompostprocbundle_la_CFLAGS += -D__unused=__attribute__\(\(__unused__\)\)
libqcompostprocbundle_la_LDFLAGS = -module -shared -avoid-version
