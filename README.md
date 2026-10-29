# libarchive - llm port

Original project: [libarchive](https://github.com/libarchive/libarchive), version 3.8.9.
Original authors: Tim Kientzle and the libarchive contributors. [Original repository](https://github.com/libarchive/libarchive).

The library is the work of its original authors, not a product of llm-build-system.
This repository only maintains its llm build integration and source subset.
It is not an official upstream release. Upstream source and header files are
unchanged. Build configuration files added by this port are kept separately.
Upstream build systems, command-line tools, tests and manuals are omitted.

The original license is preserved verbatim in [LICENSE](LICENSE).
[Upstream license](https://github.com/libarchive/libarchive/blob/v3.8.9/COPYING). Copyright and per-file license notices
remain in the original files.

Additional upstream copyright and license notices from the included source
files are reproduced verbatim in [NOTICE](NOTICE) for binary redistribution.
The original notices remain in the source files.

Build the static library with `llm build --release`. Consumers include
`<archive.h>` and `<archive_entry.h>`. Dependencies are pinned to OpenSSL 3.5.9,
zlib 1.3.2, bzip2 1.0.8, XZ 5.8.4, Zstandard 1.5.7 and Expat 2.9.0
in the [llm registry](https://github.com/llm-build-system/llm-registry).
XML parsing uses Expat and digests use OpenSSL on every platform.
Upstream libarchive internally selects Apple's built-in CommonCrypto for ZIP
cipher/HMAC operations on macOS.
That upstream platform implementation is retained without source patches.
Optional ACL/xattr, iconv, external regex, LZ4 and LZO integrations are
not enabled, matching the existing llm dependency feature profile.
Platform configuration profiles target the five native llm SDK targets.
