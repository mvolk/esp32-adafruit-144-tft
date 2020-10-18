# Adafruit 1.44" TFT Prototyping Library for ESP32 & ESP-IDF

This library supports quick-start interfacing support
with an Adafruit 1.44" 128x128 pixel TFT LCD screen via
SPI on an Espressif ESP32 system using the ESP-IDF
development platform.

A breakout board with the TFT hardware is available from
[Adafruit](https://www.adafruit.com/product/2088).

## For Prototyping

This library does not emphasize performance, memory
efficiency, testing or configurability.

This library is particularly useful for getting up
and running rapidly with the 1.44" TFT using ESP-IDF,
and as a jumping-off point for learning how to
configure and utilize this peice of hardware.

This library is licensed under the permissive MIT
license. You are encouraged to fork it, modify it,
and mould it to fit your needs. It aspires only to
be your starting point.

## Supported Ecosystem

This library aims to support the following... and only the following:

* **Microcontroller:** Espressif [ESP32 modules](https://www.espressif.com/en/products/modules/esp32)
* **TFT Controller:** Sitronix [ST7735R](https://cdn-shop.adafruit.com/datasheets/ST7735R_V0.2.pdf) rev 0.2
* **Interface:** SPI 4-wire sans MISO, with an
  additional line for data/command signaling, and
  optionally with lines for hardware reset and backlight control
* **Display Panel:** [Adafruit 1.44" TFT LCD](https://www.adafruit.com/product/2088)
* **Development Platform:** [ESP-IDF v4.1+](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/index.html),
  Espressif's freeRTOS-based platform for ESP32 development

## Dependencies

This library depends on the
[esp32-st7335r](https://github.com/mvolk/esp32-st7735r)
library.

## Boundaries

* **SPI Bus:** this library relies on the
  [esp32-st7335r](https://github.com/mvolk/esp32-st7735r)
  library to interface with the driver IC over SPI. This
  library does not itself directly exercise any SPI bus
  features.
* **Display Panel:** this library does not provide support
  for any display panel other than the 1.44" Adafruit TFT
* **GFX:** this library does not provide features to draw
  geometries, text, images, etc.
* **Peripherals:** this library provides no support for the
  SD card reader included in the Adafruit 1.44" TFT breakout
  board, but its use is expected to be compatible with use
  of the SD card reader on the same SPI bus via a different
  library or user code.

## Installation

Using the modern ESP-IDF with CMake, Git and the recommended
project structure (with a `components` folder), the easiest
way to install this library is to add it to the `components`
folder as a Git submodule:

```shell
cd ${YOUR_PROJECT_ROOT}/components
git submodule add https://github.com/mvolk/esp32-adafruit-144-tft.git
git commit -m "Add esp32_adafruit_144_tft component"

```

## API

There's not much to this high-level library. The
heavy lifting has been delegated to the
[esp32-st7335r](https://github.com/mvolk/esp32-st7735r)
library, leaving this "developer interface" quite
simple!

* `adafruit_144_tft_init(...)` initializes the panel
* `adafruit_144_tft_rgb565(...)` creates RGB/565 color codes
  corrected for the ESP32's little endian memory layout
* `adafruit_144_tft_paint(...)` "prints" a rectangular pixel
  buffer to the panel

See detailed durocumentation in
[adafruit-144-tft.h](./include/adafruit-144-tft.h))

## Technical Notes

* This library is set up so that the origin (0, 0) is
  at the bottom left of the screen, and so that the origin
  closest to the "lite" pin and the x-axis extends from
  the origin towards the ribbon cable opposite the pinouts.

* This library is a thin wrapper around the
  [esp32-st7335r](https://github.com/mvolk/esp32-st7735r)
  library. There are a number of important technical
  notes in that library's README that are well worth
  reading.

## Support

Technical support is not available.

## Contributing

### Bug Reports

Please feel free to report bugs by
[opening a new issue via Github](https://github.com/mvolk/esp32-adafruit-144-tft/issues/new).

Please do not use Github issues to request technical support.

### Pull Requests

Pull requests that further the goals of this library are welcome.

The [issues list](https://github.com/mvolk/esp32-adafruit_144_tft/issues)
is a good place to look for ideas if you would like to contribute but
don't have a specific contribution in mind.

If you would like to extend support to additional panels, MCUs or
development platforms, please consider forking this library.

## Credits

This library is not quite a derivative of the [Adafruit-ST7735-Library](Adafruit-ST7735-Library)
for the Arduino platform, but it draws so heavily on the configuration
examples provided in that library that the Adafruit license and copyright
are reproduced as part of this library's licensing.

Espressif's [ESP-IDF Programming Guide](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/index.html)
was invaluable.

A Sitronix [ST7735R datasheet](https://cdn-shop.adafruit.com/datasheets/ST7735R_V0.2.pdf)
and TFT breakout board sourced from [Adafruit](https://www.adafruit.com/)
made this library possible.

## License & Copyright

See [LICENSE.txt](./LICENSE.txt) for license details.

## Liability Notice

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED
TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL
THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF
CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
DEALINGS IN THE SOFTWARE.
