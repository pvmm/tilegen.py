tilegen.py
==========

Splits big image into smaller tiles, checks MD5 signature for repeated images, and deletes them if found. After the purge, a new smaller tileset is created according to specified dimensions. **Requires ImageMagick and Python 3.10 to work.** Usage is best explained by example:

``` 
./tilegen.py ./sample/maniac.png 16x16 result/tile 256x192
```

will create `result` directory and, inside it, tiles from `tile0000.png` to `tilennnn.png` where `nnnn` is the number of times a 16x16 tile fits inside `sample/maniac.png`. Identical tiles are removed if found, so the actual number of tiles may be smaller than that. A list of removed tiles called `removed.txt` will be created inside `result` along with a *Tiled*-compatible `map.json` and a new tileset image called `tileset256x192.png`.

![Tiled with generated sample map](/docs/tiled.png "Tiled with generated sample map")

TODO
----

Some features I may write some day:

* Create separated tilebanks when tilesets are bigger than 256 and use the screen region to decide which tilebank to use;
* Detection of near-identical tiles; 
* Detection of color-swapped tiles;
