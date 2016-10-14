ACLOCAL_AMFLAGS = -I m4
AM_CFLAGS =

light_guid = 51227ac4-2790-7100-5668-b88074d8c578
darker_guid = a77018e0-a472-234a-e838-24422a2f1a7a
dark_guid = 152de52c-209a-4084-9e18-9830ac9d9a5a

lighttempdir = $(top_builddir)/solarc-firefox-theme-light
darkertempdir = $(top_builddir)/solarc-firefox-theme-darker
darktempdir = $(top_builddir)/solarc-firefox-theme-darker

extensiondir = $(DESTDIR)/$(libdir)/firefox/browser/extensions


EXTRA_DIST = ${top_srcdir}/README.md \
	     ${top_srcdir}/LICENSE \
	     ${top_srcdir}/solarc-firefox-theme \
	     $(top_srcdir)/autogen.sh
NULL =


mkxpi:
if ENABLE_LIGHT
	cp -R $(top_srcdir)/solarc-firefox-theme $(lighttempdir)

	cp $(lighttempdir)/chrome/browser/sass/browser-light.css $(lighttempdir)/chrome/browser/browser.css
	rm -rf $(lighttempdir)/chrome/browser/sass
	rm $(lighttempdir)/chrome/overrides.sh

	cd $(lighttempdir) && \
		/usr/bin/zip -FS -r ../solarc-firefox-theme-$(VERSION).xpi *

	rm -rf $(lighttempdir)
endif # ENABLE_LIGHT

if ENABLE_DARKER
	cp -R $(top_srcdir)/solarc-firefox-theme $(darkertempdir)

	cp $(darkertempdir)/chrome/browser/sass/browser-darker.css $(darkertempdir)/chrome/browser/browser.css
	rm -rf $(darkertempdir)/chrome/browser/sass
	rm $(darkertempdir)/chrome/overrides.sh

	sed -i 's/solarc-theme/solarc-darker-theme/' $(darkertempdir)/chrome.manifest
	sed -i 's/solarc-theme/solarc-darker-theme/' $(darkertempdir)/install.rdf
	sed -i 's/SolArc /SolArc Darker /' $(darkertempdir)/install.rdf

	sed -i "s/$(light_guid)/$(darker_guid)/" $(darkertempdir)/install.rdf

	cd $(darkertempdir) && \
		/usr/bin/zip -FS -r ../solarc-darker-firefox-theme-$(VERSION).xpi *

	rm -rf $(darkertempdir)
endif # ENABLE_LIGHT

if ENABLE_DARK
	cp -R $(top_srcdir)/solarc-firefox-theme $(darktempdir)

	cp $(darktempdir)/chrome/browser/sass/browser-dark.css $(darktempdir)/chrome/browser/browser.css
	rm -rf $(darktempdir)/chrome/browser/sass
	rm $(darktempdir)/chrome/overrides.sh

	sed -i 's/solarc-theme/solarc-dark-theme/' $(darktempdir)/chrome.manifest
	sed -i 's/solarc-theme/solarc-dark-theme/' $(darktempdir)/install.rdf
	sed -i 's/SolArc /SolArc Dark /' $(darktempdir)/install.rdf

	sed -i "s/$(light_guid)/$(dark_guid)/" $(darktempdir)/install.rdf

	cd $(darktempdir) && \
		/usr/bin/zip -FS -r ../solarc-dark-firefox-theme-$(VERSION).xpi *

	rm -rf $(darktempdir)
endif # ENABLE_DARK

install-data-local: mkxpi

	$(MKDIR_P) $(extensiondir)

if ENABLE_LIGHT
	/usr/bin/unzip -d $(extensiondir)/\{$(light_guid)\} $(top_builddir)/solarc-firefox-theme-$(VERSION).xpi
endif # ENABLE_LIGHT

if ENABLE_DARKER
	/usr/bin/unzip -d $(extensiondir)/\{$(darker_guid)\} $(top_builddir)/solarc-darker-firefox-theme-$(VERSION).xpi
endif # ENABLE_LIGHT

if ENABLE_DARK
	/usr/bin/unzip -d $(extensiondir)/\{$(dark_guid)\} $(top_builddir)/solarc-dark-firefox-theme-$(VERSION).xpi
endif # ENABLE_LIGHT


uninstall:
if ENABLE_LIGHT
	rm -rf $(extensiondir)/\{$(light_guid)\}
endif # ENABLE_LIGHT

if ENABLE_DARKER
	rm -rf $(extensiondir)/\{$(darker_guid)\}
endif # ENABLE_DARKER

if ENABLE_DARK
	rm -rf $(extensiondir)/\{$(dark_guid)\}
endif # ENABLE_DARK

CLEANFILES = \
	solarc-firefox-theme-$(VERSION).xpi \
	solarc-darker-firefox-theme-$(VERSION).xpi \
	solarc-dark-firefox-theme-$(VERSION).xpi
