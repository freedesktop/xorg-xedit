# 
#  Copyright 2005  Red Hat, Inc.
# 
#  Permission to use, copy, modify, distribute, and sell this software and its
#  documentation for any purpose is hereby granted without fee, provided that
#  the above copyright notice appear in all copies and that both that
#  copyright notice and this permission notice appear in supporting
#  documentation, and that the name of Red Hat not be used in
#  advertising or publicity pertaining to distribution of the software without
#  specific, written prior permission.  Red Hat makes no
#  representations about the suitability of this software for any purpose.  It
#  is provided "as is" without express or implied warranty.
# 
#  RED HAT DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE,
#  INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS, IN NO
#  EVENT SHALL RED HAT BE LIABLE FOR ANY SPECIAL, INDIRECT OR
#  CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE,
#  DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER
#  TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR
#  PERFORMANCE OF THIS SOFTWARE.

bin_PROGRAMS = xedit
noinst_LIBRARIES = liblisp.a libre.a libmp.a

#
#    libmp.a
#

libmp_a_CFLAGS =
libmp_a_SOURCES = \
	lisp/mp/mp.c	\
	lisp/mp/mp.h	\
	lisp/mp/mpi.c	\
	lisp/mp/mpr.c

#
#    liblisp.a
#

liblisp_a_CFLAGS = -I$(top_srcdir)/lisp/re -I$(top_srcdir)/lisp/mp -DLISP -DLISPDIR=\"$(libdir)/X11/xedit/lisp\"
liblisp_a_LIBADD = libmp.a
liblisp_a_SOURCES = \
	lisp/bytecode.c \
	lisp/bytecode.h \
	lisp/core.c \
	lisp/core.h \
	lisp/debugger.c \
	lisp/debugger.h \
	lisp/format.c \
	lisp/format.h \
	lisp/hash.c \
	lisp/hash.h \
	lisp/helper.c \
	lisp/helper.h \
	lisp/internal.h \
	lisp/io.c \
	lisp/io.h \
	lisp/lisp.c \
	lisp/lisp.h \
	lisp/lsp.c \
	lisp/math.c \
	lisp/math.h \
	lisp/package.c \
	lisp/package.h \
	lisp/pathname.c \
	lisp/pathname.h \
	lisp/private.h \
	lisp/read.c \
	lisp/read.h \
	lisp/regex.c \
	lisp/regex.h \
	lisp/require.c \
	lisp/require.h \
	lisp/stream.c \
	lisp/stream.h \
	lisp/string.c \
	lisp/string.h \
	lisp/struct.c \
	lisp/struct.h \
	lisp/time.c \
	lisp/time.h \
	lisp/write.c \
	lisp/write.h \
	lisp/xedit.c \
	lisp/xedit.h

#
#     libre.a
#

libre_a_CFLAGS = 
libre_a_SOURCES = \
	lisp/re/re.c \
	lisp/re/rec.c \
	lisp/re/re.h \
	lisp/re/reo.c \
	lisp/re/rep.h \
	lisp/re/tests.c

#
#     xedit
#   

xedit_CFLAGS = $(XEDIT_CFLAGS) -I$(top_srcdir)/lisp/re -D_BSD_SOURCE -DXEDIT -DINCLUDE_XPRINT_SUPPORT
xedit_LDADD = $(XEDIT_LIBS) libre.a liblisp.a libmp.a -lm

xedit_SOURCES =	\
        commands.c \
        hook.c \
        ispell.c \
        lisp.c \
        options.c \
        realpath.c \
        strcasecmp.c \
        util.c \
        xedit.c \
	xedit.h

if XAW_USE_XPRINT
xedit_CFLAGS += -DINCLUDE_XPRINT_SUPPORT

xedit_SOURCES += \
        print.c \
        printdialog.c \
        printdialog.h \
        printdialogprivates.h \
        print.h
endif

# App default files  (*.ad)

appdefaultdir = $(sysconfdir)/X11/app-defaults


APPDEFAULTFILES = \
        Xedit-color \
	Xedit

if XAW_USE_XPRINT
Xedit.ad: 
	cp $(top_srcdir)/Xedit-xprint.ad Xedit.ad
else
Xedit.ad:
	cp $(top_srcdir)/Xedit-noxprint.ad Xedit.ad
endif

$(APPDEFAULTFILES): %: %.ad
	cp $< $@

appdefault_DATA = $(APPDEFAULTFILES)

EXTRA_DIST = lisp/compile.c Xedit-color.ad				\
		Xedit-xprint.ad Xedit-noxprint.ad			\
		./lisp/env.c						\
	 	lisp/mathimp.c



CLEANFILES = $(APPDEFAULTFILES) Xedit.ad


