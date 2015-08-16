+++
date = "2015-02-16T00:00:00+01:00"
draft = false
title = "Tools"
+++

# Existing Tools, Libraries, ...

## Game Engine integration

* [jme3_ext_remote_editor]() for [jMonkeyEngine](http://jmonkeyengine.org), allow to receive commands and datas over socket to modify the scene. It also include a Loader for '.xbuf'

## 3D Tools integration

## Protobuf tools

* a list of languages and utilities for protobuf is available at [Third-Party-Add-ons](https://github.com/google/protobuf/wiki/Third-Party-Add-ons)
* google, bing, ... ;-)

# Ideas for Tools

## Checker

* in a collection of datas (.xbuf) : verify that every ref points to existing id.
* in a collection of datas (.xbuf) : verify (+ correct) order of the ref in Relation.
* in a collection of datas (.xbuf) : verify that in parent-child relation child only have one parent (eg: TObject).
* in a datas (.xbuf) : verify that size of XxxBuffer is a multiple of its step.
* in a datas (.xbuf) : verify that every rpath points to existing file in assets' folder.

## Merge

* merge a collection of datas into a single datas + external assets

# Extractor

* from a collection of datas (.xbuf) : extract Node and related data + assets into its own datas
* from a collection of datas (.xbuf) : extract Material and related data + assets into its own datas
* from a collection of datas (.xbuf) : list all assets (rpath)

# Remapper

* in a collection of datas (.xbuf) : rename id (and ref) (via regexp or conversion table or a generator)
* in a collection of datas (.xbuf) : change rpath (and ref) (via regexp or conversion table)
