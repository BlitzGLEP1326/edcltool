AM_CFLAGS= -D 'LUAEXT_PREFIX="@datadir@/edcltool/lib"' 

lib_LTLIBRARIES = libedcl-1.0.la
libedcl_1_0_la_SOURCES = edcl.c platform-linux.c chips.c
libedcl_1_0_la_includedir=$(includedir)/edcl-1.0/
libedcl_1_0_la_include_HEADERS = edcl.h

bin_cflags = $(AMCFLAGS)
bin_ldadd = -lpthread libedcl-1.0.la

bin_PROGRAMS=

if BUILD_EDCLTOOL
bin_PROGRAMS += edcltool
edcltool_LDADD = $(bin_ldadd) $(LUA_LIBS) 
edcltool_CPPFLAGS = $(bin_cflags) $(LUA_CFLAGS) 
edcltool_SOURCES = edcltool.c

if BUILD_ELFLOAD
edcltool_SOURCES  += elf.c
edcltool_CPPFLAGS += -DENABLE_ELFLOAD $(LIBELF_CFLAGS)
edcltool_LDADD += $(LIBELF_LIBS) 
endif

endif


bin_PROGRAMS += edcl_write
edcl_write_LDADD = $(bin_ldadd)
edcl_write_CPPFLAGS = $(bin_cflags)
edcl_write_SOURCES = edcl_write.c

bin_PROGRAMS += edcl_dump
edcl_dump_LDADD = $(bin_ldadd)
edcl_dump_CPPFLAGS = $(bin_cflags)
edcl_dump_SOURCES = edcl_dump.c

bin_PROGRAMS += edcl_test
edcl_test_LDADD = $(bin_ldadd)
edcl_test_CPPFLAGS = $(bin_cflags)
edcl_test_SOURCES = edcl_test.c

EXTRA_DIST=toolhelpers.h

install-exec-hook:
	@echo    "#### Setting SUID for edcltool. ####"
	@ls -l $(DESTDIR)$(bindir)/edcltool
	@chmod 4755 $(DESTDIR)$(bindir)/edcltool
	@ls -l $(DESTDIR)$(bindir)/edcltool
	@echo    "####-------------------------------####"
