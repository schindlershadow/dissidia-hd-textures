# Dissidia 012 HD textures

Upscaled replacement textures for [Dissidia Recomp](https://github.com/schindlershadow/dissidia): 3,366 PNGs named by the
recomp's texture-pack id (`textures/<id>.png`). The installer downloads them when "HD textures" is selected, next to the community
D012FFRT pack (which is not included here). They need the player's own copy of the game; nothing here runs without it.

- 3,030 textures are ones that D012FFRT does not cover (`"kind": "new"` in `manifest.json`): costume and DLC textures, stage textures,
  menu and theater art, boot logos.
- 336 textures replace entries of D012FFRT that are only the original with every pixel repeated 2x or 4x
  (`"kind": "replaces-pixel-repeated"`, mainly item icons and UI art). The runtime looks these id-named files up first.
- Textures are the PSP originals read from the disc image, upscaled 4x (2x above 256 px) with Real-ESRGAN
  (`realesrgan-x4plus-anime` for UI art, `realesrgan-x4plus` for stage textures), and then fixed up by
  `games/dissidia/tools/texpack_upscale.py` in the main repository: flat art gets a plain Lanczos upscale, small cut-out art is blended
  with Lanczos so faces are not redrawn, the original colour is kept under transparent pixels, and tiny text is not left to the model.
  The title screen's copyright strip is upscaled with `texpack_crisp.py`. About a third are palette PNGs (lossless where used, quantized
  only when the measured error stays under 42 dB PSNR).
- The EU release has the same textures (same ids), so one set serves both.

Real-ESRGAN: Xintao Wang et al., BSD-3-Clause, https://github.com/xinntao/Real-ESRGAN. The artwork belongs to Square Enix; this is an
unofficial fan project, not affiliated with or endorsed by Square Enix.

`manifest.json`: `{id: {w, h, kind}}` with the original size of each texture.
