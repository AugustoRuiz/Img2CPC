# img2cpc
Tool to convert images in a lot of formats to data that can be used in Amstrad CPC software

img2cpc - (c) 2007-2015 Retroworks.

## Usage
```img2cpc [OPTIONS] fileNames

## Options
`--help`
Help. Show usage.

`-bn, --baseName ARG` 
Tile base name. If not set, the filename will be used.

`-f`
Create a flipped values look-up table for the current palette and mode.

`-fwp, --firmwarePalette ARG1[,ARGn]`
Palette specified in firmware values.

`-g, --generatePNG`
Generates PNG images, one per tile and one per mask (if transparency is set).

`-h, --tileHeight ARG`
Tile height. If not set, the image height is used.

`-hwp, --hardwarePalette ARG1[,ARGn]`
Palette specified in hardware values.

`-im, --interlacedMasks`
Interlaced masks. Mask values will be interlaced with pixel values.

`-m, --mode ARG`
Specifies the CPC Mode to generate data for. Valid values are 0 (default), 1 or 2.

`-map, --tilemap`
Generate tile map

`-o, --outputFileName ARG`
Output file name. Default value is gfx. img2cpc will append the proper extension based on format.

`-of, --outputFormat ARG`
Output format. If not set, data will be generated in assembly format.

`-opfw`
Output palette (firmware values)

`-ophw`
Output palette (hardware values)

`-p, --palette ARG`
Specifies input palette file.

`-rgbp, --rgbPalette ARG1[,ARGn]`
Palette specified in RGB values. RGB values must be specified as `0xRRGGBB`, where `RR`, `GG` and `BB` are hexadecimal, or as an int value.
                                      
Examples: `0x1122FF`, `255`

`-s, --scanlineOrder ARG1[,ARGn]`
Scanline order. Default value is `0,1,2,3,4,5,6,7`

`-t, --transparentColor ARG`
Specifies transparent color (as index in palette).

`-w, --tileWidth ARG`
Tile width. If not set, the image width is used.

`-z, --zigzag`
Zigzag. Generate data in zigzag order.

## Examples

img2cpc -w 8 -h 8 --outputFormat asm -bn tile -m 0 tiles.png

Paleta en src/config_rgb.json, salida en formato C, mode 0, fichero de salida gfx.c, generar PNGs, nombre base: tile, tiles de 32x32.
```img2cpc -p src/config_rgb.json -of c -m 0 -o gfx.c -g -bn tile -h 32 -w 32 bee.png

Paleta en src/config_rgb.json, el color transparente es el 0, salida en formato C, mode 0, fichero de salida gfx.c, generar PNGs, nombre base: tile, tiles de 32x32.
```img2cpc -p src/config_rgb.json -t 0 -of c -m 0 -o gfx.c -g -bn tile -h 32 -w 32 bee.png

Paleta en src/config_rgb.json, el color transparente es el 12, salida en formato ASM, mode 0, fichero de salida gfx.s, 1 unico tile.
```img2cpc -p src/config_rgb.json -t 12 -of asm -m 0 -o gfx.s RYU_STAND_0.png

Paleta en src/config_rgb.json, el color transparente es el 12, salida en formato ASM, mode 0, fichero de salida gfx.s, datos en zigzag, 1 unico tile.
```img2cpc -p src/config_rgb.json -t 12 -of asm -m 0 -o gfx.s -z RYU_STAND_0.png

Paleta en src/config_rgb.json, el color transparente es el 12, salida en formato ASM, mode 0, fichero de salida gfx.s, datos en zigzag, orden de scanlines: 0,1,2,3,7,6,5,4, 1 unico tile.
```img2cpc -p src/config_rgb.json -t 12 -of asm -m 0 -o gfx.s -z -s 0,1,2,3,7,6,5,4 RYU_STAND_0.png

If you liked this program, drop an email at: `augusto.ruiz@gmail.com`
