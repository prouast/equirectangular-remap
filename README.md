# 360fly-remap

Generate maps for conversions from spherical to equirectangular video in [ffmpeg](http://ffmpeg.org).

Works for videos which represent a half sphere - tested with [360fly](http://www.360fly.com).

Adapted from the example given for ffmpeg's [`RemapFilter`](https://trac.ffmpeg.org/wiki/RemapFilter).

## Guide

### Building

1. Install ffmpeg
2. Checkout the source of this repository
3. Build: `$ gcc projection.c -Wall -o project -lm`

### Running

Create maps `example_x.pgm` and `example_y.pgm` for dimensions `400 x 400`:

```
$ ./project -x example_x.pgm -y example_y.pgm -h 400 -w 400 -r 400 -c 400 -m equirectangular --verbose
```

Apply the maps to the image `example.jpg`:

```
$ ffmpeg -i example.jpg -i example_x.pgm -i example_y.pgm -lavfi remap result.png
```

### Result

**Example spherical image**

![Example](https://github.com/prouast/equirectangular-remap/blob/master/example.jpg?style=centerme)

**Equirectangular result**

![Result](https://github.com/prouast/equirectangular-remap/blob/master/result.png?style=centerme)