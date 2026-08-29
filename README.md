# Scoop bucket for Ansel nightly builds

```powershell
scoop bucket add ansel https://github.com/aurelienpierreeng/scoop-ansel
scoop install ansel-nightly
scoop update ansel-nightly            # or just: scoop update *
```

`bucket/ansel-nightly.json` is **generated** — rewritten after every nightly by the
`Nightly manifest` workflow in [aurelienpierreeng/ansel](https://github.com/aurelienpierreeng/ansel)
(`tools/nightly_manifest.py`), from the same manifest that drives the ansel.photos
download buttons. Do not edit it by hand; a fix belongs in the generator.

There is deliberately no `autoupdate` block: Ansel's own CI bumps the manifest every
night, so Scoop's bucket-side auto-bump would only fight it. `checkver` is kept so
`scoop status` can report a newer nightly.

Nightly builds are **not code-signed**; SmartScreen will warn on first launch. See
`doc/nightly-distribution.md` in the ansel repository for what signing would take.