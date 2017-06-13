flatpak_DATA = metadata.image deploy.image
flatpakdir   = ${datadir}/@PACKAGE@
service_DATA = flatpak-image-runtime.service
servicedir   = ${systemd_unitdir}/system

REMOTE      = @_REMOTE_@
DOMAIN      = @_DOMAIN_@
ARCH        = @_ARCH_@
BRANCH      = @_BRANCH_@
SHA1        = 1234567890abcdeffedcba09876543211234567890abcdeffedcba0987654321

IMAGE_SUBST = sed "s:@REMOTE@:$(REMOTE):g;s:@SHA1@:$(SHA1):g" | \
		sed "s:@DOMAIN@:$(DOMAIN):g;s:@MACHINE@:$(ARCH):g" | \
		sed "s:@BRANCH@:$(BRANCH):g"

%.image: %.in
	cat $< | $(IMAGE_SUBST) > $@

flatpak-image-runtime.service: flatpak-runtime.service.in
	cat $< | $(IMAGE_SUBST) > $@

all:

clean:
	rm -f *.image flatpak-image-runtime.service
