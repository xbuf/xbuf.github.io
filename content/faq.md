+++
date = "2015-02-18T00:00:00+01:00"
draft = false
title = "FAQ"
+++

# What ...

## What are the units, coordinate system ?

* Coordinate system : Right Handled
  * object : Y up, Z forward, X left
  * camera : Y up, Z lookAt direction, X left
  * orthogonal-axes
  * uniform axis unit
  * front face: CCW (counter-clock-wise), back face: CW
* Distance unit : meter (float)
* Time unit : millisecond (int32)
* Angle unit : radian (float)

I try to collect same data for game engine, tools, to help create importer/exporter. Help me to complete the [table](https://docs.google.com/spreadsheets/d/19FscoJzidZKF6Iqs1bqELv57Ds-t_dAbMD_XflrIUuk/edit?usp=sharing)

## What is the file extension ?

```
.xbuf
```

## What is the future of the format ?

I don't know ;-)

But there some ideas :

* Integrate some community' suggestions
* Ingrate compression  like [glTF: Open 3D Graphics Compression](https://github.com/KhronosGroup/glTF/wiki/Open-3D-Graphics-Compression)
* Define an archive format to store complementary data : textures, shaders, ...

# How ...

## How can I protect my content ?

1. Change the file extension
2. Modify the file content, example of modifications (can be combined) :
  * wrap into your own proto Message
  * add an header at the begin of the file (a fixed or variable size of useless bytes, some license info)
  * encrypt : rot13, pgp, ...
  * wrap into an archive (but without the reguler extension): tar, zip,...
  * compress (but without the reguler extension) : snappy, gzip, bzip, lzma,...

# Why ...

## Why not [OpenGEX](http://opengex.org/) ?

* Rxcept if you use [OpenGEX Import Template](http://opengex.org/OpenGex-Import.zip) (C++ only), it requires to write parser and low level writer, and writing good parser is hard.
* Text based, not optimal for network and realtime update
* Importer should support several metrics, several orientations (Z up, Y up,...)

## Why not [glTF](https://github.com/KhronosGroup/glTF) ?

* Moving and heavy spec ;-)
* Json based format requires to write "semantic" parser, converter.

## Why no configurable metrics (like in OpenGEX) ?

* To simplify the loader (less composition to implement loader, less confusion) : *"convention over configuration"*
* To ease share and merge of data (eg: merge multiples xbuf file)
* It's the responsability of the exporter to write shareable data (from internal format to xbuf)

##  Why no configurable up ?

* See *Why no configurable metrics (like in OpenGEX) ?* (above).
* To avoid branch in loader code like in this [response on unity forum](http://answers.unity3d.com/questions/46589/zup-yup-xup-handedness-space-conversion.html).

see discussion [glTF : unify scenes axis-up](https://github.com/KhronosGroup/glTF/issues/22).

## Why no transform matrix, variant of Rotation, Scale ?

* See *Why no configurable metrics (like in OpenGEX) ?* (above).
* I don't want too freedom (simple loader, more work on exporter), so I have to choose between matrix or translation / rotation / scale
* Extracting translation / rotation / scale from a 4×4 matrix is harder than creating a 4×4 matrix from translation / rotation / scale.
* Quaternion is often more animation friendly.
