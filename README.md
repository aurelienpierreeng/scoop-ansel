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
## Installing an older nightly, or staying on one

Every night's manifest is a commit in this bucket, and Scoop reads that history natively:

```powershell
scoop install ansel-nightly@0.0.0+4791.gf3a0c27035   # any version that ever appeared here
scoop reset ansel-nightly@0.0.0+4791.gf3a0c27035     # switch between installed versions
scoop hold ansel-nightly                              # keep it there through `scoop update`
scoop unhold ansel-nightly
```

Installed versions sit side by side under `apps\ansel-nightly\<version>\`, so switching
back is instant. The version string is the one in the package name
(`0.0.0+<commits>.g<hash>`): higher `<commits>` is newer.

## Stable releases

A separate `ansel` manifest will appear here with the first tagged release, so the stable
and nightly channels can be installed side by side.
