include config.mk

tarball   = emacs-$(VERSION).tar.$(EXTENSION)
signature = $(tarball).sig

all: fetch

fetch: $(tarball) $(signature)

$(tarball):
	@echo Downloading $(tarball)
	wget $(MIRROR)/emacs/$(tarball) -O $(tarball)

$(signature):
	@echo Downloading $(signature)
	wget $(MIRROR)/emacs/$(signature) -O $(signature)

.PHONY: all fetch
