+++
date = "2015-10-18T00:00:00+01:00"
draft = false
title = "Setup Blender"
tags = ["blender", "tutorial"]
+++

The quickest way to give a try : blender_io_xbuf

# jme3_xbuf_viewer

Install a pre-configured application ready to connect to blender.

1. install java 8
2. download [jme3_xbuf_viewer-201510171736.tgz](https://github.com/xbuf/jme3_xbuf/releases/download/0.7.2/jme3_xbuf_viewer-201510171736.tgz) + unarchive + run ./launch (or launch.exe)

# On Blender 2.74+

1. click the **[Download ZIP](https://github.com/xbuf/blender_io_xbuf/archive/master.zip)** button on [blender_io_xbuf](https://github.com/xbuf/blender_io_xbuf)
2. install add-on into blender
  * `File > User Preferences ... > Addons > Install from file ...` select the downloaded zip file
  * enable the plugin **Import-Export: Xbuf Exporter & Render Engine** (check the checkbox)
3. open or create a model
4. select `Xbuf Render` in the render engine combobox (top)
5. check the render properties (eg: `Xbuf > assets_path` the directory where to export images, ...)
6. in the 3D view select `viewport shading > rendered` could take/freeze a moment to transfer the initial data.
7. You should see your model rendered by jme3_xbuf_viewer inside blender viewport, play with the camera, lights, ... (animation should store in a strip on NLA Editor, click on the strip)
