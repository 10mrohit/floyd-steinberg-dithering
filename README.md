#Floyd-Steinberg Dithering#

Floyd–Steinberg dithering is an image dithering algorithm first published in 1976 by Robert W. Floyd and Louis Steinberg. It is commonly used by image manipulation software, for example when an image is converted into GIF format that is restricted to a maximum of 256 colors.

The algorithm achieves dithering using error diffusion, meaning it pushes (adds) the residual quantization error of a pixel onto its neighboring pixels, to be dealt with later.


#Pseudocode as on *Wikipedia*:#
        for each y from top to bottom
            for each x from left to right
              oldpixel  := pixel[x][y]
              newpixel  := find_closest_palette_color(oldpixel)
              pixel[x][y]  := newpixel
              quant_error  := oldpixel - newpixel
              pixel[x + 1][y    ] := pixel[x + 1][y    ] + quant_error * 7 / 16
              pixel[x - 1][y + 1] := pixel[x - 1][y + 1] + quant_error * 3 / 16
              pixel[x    ][y + 1] := pixel[x    ][y + 1] + quant_error * 5 / 16
              pixel[x + 1][y + 1] := pixel[x + 1][y + 1] + quant_error * 1 / 16
