meta-lts-mixins - wrynose/connectivity
=======================================

"Mixin" layer for adding latest Linux connectivity tools into the Yocto Project LTS.

Wrynose intentionally keeps an LTS baseline, while some users need newer
versions for selected connectivity components. This branch provides mixin
recipes to upgrade hostapd and wpa-supplicant with the latest versions,
overriding the oe-core/meta-openembedded versions when explicitly selected.
The upgrade enables newer features (including EHT/IEEE 802.11be/Wi-Fi 7) and
includes interoperability and security robustness fixes.

In order to make this layer Yocto Project Compatible, the layer should not
provide new versions of packages by default. Because of this, the recipe
provided in this layer will not be used unless that is explicitly stated.
To use the provided linux-firmware recipe, the following can be done:

```
# please use 'DEFAULT_PREFERENCE:layer-lts-connectivity-mixin:your_override = ""' to keep Yocto Project Compatible
echo 'DEFAULT_PREFERENCE:layer-lts-connectivity-mixin = ""' >> recipes-kernel/wpa-supplicant/wpa-supplicant_%.bbappend
echo 'DEFAULT_PREFERENCE:layer-lts-connectivity-mixin = ""' >> recipes-kernel/hostapd/hostapd_%.bbappend
```

Dependencies
------------

This layer depends on:

- URI: https://github.com/openembedded/openembedded-core
  layers: meta
    branch: wrynose

Backporting
-----------

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

Contributing
------------

Please submit any patches against the meta-qcom-3rdparty layer by using the GitHub pull-request feature.
Fork the repo, create a branch, do the work, rebase from upstream, and create the pull request.

Maintenance
-----------

Layer maintainers:
* Jose Quaresma jose.quaresma@oss.qualcomm.com
* Miaoqing Pan miaoqing.pan@oss.qualcomm.com
