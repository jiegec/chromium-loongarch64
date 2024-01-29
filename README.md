# chromium-loongarch64

Port chromium (also chromium-based qt6-webengine) to loongarch64.

Whole diff: `chromium/chromium-VER.diff`.

Partial diff: `chromium/chromium-VER.*.diff`, they are extracted from the whole diff.

Also maintained at [AOSC-Tracking/chromium](https://github.com/AOSC-Tracking/chromium).

Caveat: you need to build compiler-rt and rustc with `-mcmodel=medium`, otherwise it may fail to link due to relocation truncation.

Based on:

- [loongson/electron](https://github.com/loongson/electron/)
- [prcups/qt6-webengine-loongarchlinux](https://github.com/prcups/qt6-webengine-loongarchlinux/)
- various patches from linux distributions for building chromium with gcc/clang, e.g. [Fedora](https://src.fedoraproject.org/rpms/chromium/tree/rawhide) and [Debian](https://salsa.debian.org/chromium-team/chromium/-/tree/master/debian/patches?ref_type=heads)
- llvm 16 files are generated by running `third_party/swiftshader/third_party/llvm-16.0/scripts/update.py`
- ffmpeg config files are generated by running configure with the arguments recorded in `FFMPEG_CONFIGURATION` (Chrome branding has aac and h264 enabled `--enable-decoder='aac,h264' --enable-demuxer=aac --enable-parser='aac,h264'`, while Chromium does not) and copying the generated files

See also:

- [Chromium port to riscv64](https://github.com/felixonmars/archriscv-packages/tree/master/chromium)
- [Chromium port to ppc64le](https://gitlab.com/chromium-ppc64le/chromium-ppc64le) [Debian's patches for ppc64le](https://salsa.debian.org/chromium-team/chromium/-/tree/master/debian/patches/ppc64le?ref_type=heads)
