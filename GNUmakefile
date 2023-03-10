include config.mk

tarball   = emacs-$(VERSION).tar.$(EXTENSION)
signature = $(tarball).sig
sha256    = $(SHA256.$(EXTENSION))
root      = emacs-$(VERSION)

all: fetch verify $(root)

fetch: $(tarball) $(signature)

$(tarball):
	@echo Downloading $(tarball)
	wget $(MIRROR)/emacs/$(tarball) -O $(tarball)

$(signature):
	@echo Downloading $(signature)
	wget $(MIRROR)/emacs/$(signature) -O $(signature)

verify: gpgverify sha256verify

gpgverify: $(signature) $(tarball)
	@echo Verifying GPG signature
	gpg --verify $<

sha256verify: $(tarball)
	@echo Verifying verifysum
	printf "%s\t%s" $(sha256) $(tarball) | sha256sum -c -

$(root): $(tarball)
	@echo Extracting $< into $@
	mkdir $@
	tar -xf $< -C $@ --strip-components 1

.PHONY: all fetch verify gpgverify sha256verify
