
noinst_LIBRARIES = libcommon.a

libcommon_a_SOURCES = connman-dbus.c connman-dbus.h \
				connman-client.h connman-client.c

BUILT_SOURCES = marshal.h marshal.c \
			connman-dbus-glue.h

nodist_libcommon_a_SOURCES = connman-dbus-glue.h

CLEANFILES = $(BUILT_SOURCES)

AM_CFLAGS = @DBUS_CFLAGS@ @GTK_CFLAGS@

EXTRA_DIST = marshal.list connman-dbus.xml

MAINTAINERCLEANFILES = Makefile.in

marshal.h: marshal.list
	$(GLIB_GENMARSHAL) --prefix=marshal $< --header > $@

marshal.c: marshal.list
	$(GLIB_GENMARSHAL) --prefix=marshal $< --body > $@

connman-dbus-glue.h: connman-dbus.xml
	$(DBUS_BINDING_TOOL) --prefix=connman --mode=glib-client --output=$@ $<
