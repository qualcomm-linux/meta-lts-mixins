meta-lts-mixins - wrynose/connectivity
=======================================

"Mixin" layer for adding latest Linux connectivity tools into the Yocto Project LTS.

Wrynose intentionally keeps an LTS baseline, while some users need newer
versions for selected connectivity components. This branch provides mixin
recipes to upgrade hostapd and wpa-supplicant with the latest versions,
overriding the oe-core/meta-openembedded versions when explicitly selected.
The upgrade enables newer features (including EHT/IEEE 802.11be/Wi-Fi 7) and
includes interoperability and security robustness fixes.

Dependencies
------------

This layer depends on:

- URI: https://github.com/openembedded/openembedded-core
  layers: meta
    branch: wrynose

Contributing
------------

The patches can be backported from openembedded-core with:

```
 git -C ../openembedded-core format-patch --stdout -1 \
   origin/master meta/recipes-connectivity/wpa-supplicant \
  git am --signoff -p4 --directory=recipes-connectivity/wpa-supplicant
```
or

```
 git -C ../meta-openembedded format-patch --stdout -1 \
   origin/master meta-oe/recipes-connectivity/hostapd \
  git am --signoff -p4 --directory=recipes-connectivity/hostapd
```

  The yocto-patches mailinglist (yocto-patches@lists.yoctoproject.org) is used
  for questions, comments and patch review. It is subscriber only, so please
  register before posting.

  Send pull requests to yocto-patches@lists.yoctoproject.org with
  '[meta-lts-mixins][wrynose/connectivity]' in the subject.

  When sending single patches, please use something like:

```
  git send-email -M origin/wrynose/connectivity \
   --to=yocto-patches@lists.yoctoproject.org \
   --subject-prefix='meta-lts-mixins][wrynose/connectivity][PATCH'
```

Maintenance
-----------

Layer maintainers:
* Jose Quaresma jose.quaresma@oss.qualcomm.com
* Miaoqing Pan miaoqing.pan@oss.qualcomm.com
