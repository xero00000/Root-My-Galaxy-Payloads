# pa3q-S938USQSBCZF5

Galaxy S25 Ultra `SM-S938U1` / internal kernel build `S938USQSBCZF5`
(display `S938U1UESBCZF5`, CHA).

## Status

**Offline build-verified only. Not device-tested.**

- Target headers and P0 fingerprints derived from the official CZF5 firmware
  package and recovered `vmlinux`/`BTF`.
- App release payload built with Android NDK r29 (`API=35`), size-gated to
  104128 bytes.
- KernelSU currently reuses the shared PA3Q `android15-6.6` / `ksud-s25u-kdp`
  artifacts. Exact vermagic rebuild for
  `6.6.98-android15-8-pd6ff1cd-abogkiS938USQSBCZF5-4k` has not been produced on
  this workstation. Treat KernelSU late-load as unproven for this build.

Full derivation record:
[`docs/SM-S938U1-S938U1UESBCZF5.md`](../../../docs/SM-S938U1-S938U1UESBCZF5.md).

## Build

```sh
make TARGET=pa3q-S938USQSBCZF5 ANDROID_NDK_HOME=/path/to/android-ndk-r29 release
cp build/pa3q-S938USQSBCZF5/cve-2026-43499-app.release.so \
   artifacts/pa3q-S938USQSBCZF5/cve-2026-43499-app.so
```

## Diff vs June PA3Q CZF1

- `SLIDE_NFULNL_LOGGER_NAME_OFF`: `0x0175e2af` (CZF1 S938N was `0x0175e2a1`)
- All 32 P0 fingerprint rows
- Build identity / kernel release / fingerprint

Provisional (same as other PA3Q, not ABL-decoded here):

- `P0_KERNEL_PHYS_LOAD = 0xa8000000`
- `SLIDE_PSELECT_WORD_SHIFT = 0`
