![Box86 and Box64 logos](meta/box86box64.png)
# weilbyte/box
This docker image comes with box86/box64 for emulating i386/amd64 workloads on armv7/arm64v8. Default entry point is `box86`/`box64` (depending on architecture), which can be found at `/usr/local/bin/box86`/ `/usr/local/bin/box64`.

Images periodically rebuilds with box86/box64 `master` branch.

**The tag you should pull from is `debian-11` as it holds images for both `armv7` and `arm64v8`, HOWEVER `armv7` only comes with `box86`, while `arm64v8` comes with both**

**Tags**     
`latest`, **`debian-11`**, `armv7-debian-11`, `arm64v8-debian-11`

