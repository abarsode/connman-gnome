
EXTRA_DIST = 
CLEANFILES =

lib_LTLIBRARIES = libgnome-connman.la

# will be scanned for introspection annotation, but won't be installed
libgnome_connman_c_sources =		\
	connman-client.c		\
	connman-client-glue.c

libgnome_connman_private_headers =	\
	connman-client-glue.h

# public headers don't need to be listed, are handled by _HEADERS
libgnome_connman_la_SOURCES =			\
	$(libgnome_connman_private_headers)	\
	$(libgnome_connman_c_sources)

libgnome_connman_la_LIBADD = $(LIBGNOME_LIBS)

libgnome_connman_la_LDFLAGS =				\
	-no-undefined					\
	$(AM_LDFLAGS)

AM_CFLAGS =						\
	-I$(srcdir)					\
	$(LIBGNOME_CFLAGS)				\
	$(WARN_CFLAGS)					\
	$(DISABLE_DEPRECATED)				\
	-DG_LOG_DOMAIN=\"Connman\"

BUILT_SOURCES = connman-client-glue.h \
		connman-client-glue.c

CLEANFILES += $(BUILT_SOURCES)

EXTRA_DIST += connman-client.xml

MAINTAINERCLEANFILES = Makefile.in

connman-client-glue.c: connman-client-glue.h

connman-client-glue.h: connman-client.xml
	$(AM_V_GEN) $(GDBUS_CODEGEN) --c-namespace= --generate-c-code=connman-client-glue --interface-prefix=net.connman $<
