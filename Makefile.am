flatpak_DATA = metadata.current deploy.current metadata.distro deploy.distro
flatpakdir   = ${datadir}/@PACKAGE@
service_DATA = flatpak-current-runtime.service flatpak-distro-runtime.service
servicedir   = ${systemd_unitdir}/system

ORG            = @_ORG_@
ARCH           = @_ARCH_@
CURRENT        = @_CURRENT_@
DISTRO_VERSION = @_DISTRO_VERSION_@
IMAGE_VERSION  = @_IMAGE_VERSION_@
BUILD_VERSION  = @_BUILD_VERSION_@
SHA1           = 1234567890abcdeffedcba09876543211234567890abcdeffedcba0987654321
REMOTE         = refkit

if IMAGE_RUNTIME
flatpak_DATA += metadata.image deploy.image
service_DATA += flatpak-image-runtime.service
endif

if BUILD_RUNTIME
flatpak_DATA += metadata.build deploy.build
service_DATA += flatpak-build-runtime.service
endif


COMMON_SUBST   = sed "s/@FPREM@/$(REMOTE)/g;s/@FPSHA1@/$(SHA1)/g" | \
	         sed "s/@FPORG@/$(ORG)/g;s/@FPARCH@/$(ARCH)/g"

CURRENT_SUBST  = sed "s/@FPVER@/$(CURRENT)/g;s/@FPTYPE@/$(CURRENT)/g"
DISTRO_SUBST   = sed "s/@FPVER@/$(DISTRO_VERSION)/g;s/@FPTYPE@/distro/g"
IMAGE_SUBST    = sed "s/@FPVER@/$(IMAGE_VERSION)/g;s/@FPTYPE@/image/g"
BUILD_SUBST    = sed "s/@FPVER@/$(BUILD_VERSION)/g;s/@FPTYPE@/build/g"

%.current: %.in
	cat $< | $(COMMON_SUBST) | $(CURRENT_SUBST) > $@

flatpak-current-runtime.service: flatpak-runtime.service.in
	cat $< | $(COMMON_SUBST) | $(CURRENT_SUBST) > $@


%.distro: %.in
	cat $< | $(COMMON_SUBST) | $(DISTRO_SUBST) > $@

flatpak-distro-runtime.service: flatpak-runtime.service.in
	cat $< | $(COMMON_SUBST) | $(DISTRO_SUBST) > $@


%.image: %.in
	cat $< | $(COMMON_SUBST) | $(IMAGE_SUBST) > $@

flatpak-image-runtime.service: flatpak-runtime.service.in
	cat $< | $(COMMON_SUBST) | $(IMAGE_SUBST) > $@


%.build: %.in
	cat $< | $(COMMON_SUBST) | $(BUILD_SUBST) > $@

flatpak-build-runtime.service: flatpak-runtime.service.in
	cat $< | $(COMMON_SUBST) | $(BUILD_SUBST) > $@

all:

clean:
	rm -f *.current *-current-*.service *.distro *-distro-*.service
	rm -f  *.image *-image-*.service *.build *-build-*.service

