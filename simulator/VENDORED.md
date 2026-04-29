# Vendored simulator dependencies

This standalone repository vendors LVGL and FreeRTOS under `simulator/` so the
host simulator can be built without fetching submodules from the original
monorepo layout.

The upstream licenses remain in the vendored directories:

- `simulator/lvgl/LICENCE.txt`
- `simulator/FreeRTOS/LICENSE.md`
