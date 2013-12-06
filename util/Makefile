SRCDIR = .
TOPDIR = $(SRCDIR)/..

include $(TOPDIR)/Make.defaults

all : $(patsubst %.in, %, $(wildcard *.in))

$(patsubst %.in,%,$(wildcard *.in)) :: % : %.in

clean :
	@rm -vf $(patsubst %.in, %, $(wildcard *.in))

install :
	@$(INSTALL) -m 755 -d $(DESTDIR)$(LIBDIR)/kernel/install.d/
	@for x in $(patsubst %.in,%,$(wildcard *.in)) ; do \
		case $$x in \
			*_$(ARCH)*) \
				$(INSTALL) -v -m 755 $$x $(DESTDIR)$(LIBDIR)/kernel/install.d/$$x ; \
				;; \
		esac ; \
	done

.PHONY : all clean install

include $(TOPDIR)/Make.rules
