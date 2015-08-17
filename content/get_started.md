+++
date = "2015-07-20T00:00:00+01:00"
draft = false
title = "Get started"
+++
# Level 1

The quickest way to give a try to jme3_xbuf : blender_io_xbuf + jme3_xbuf_viewer.

## jme3_xbuf_viewer

Install a pre-configured application ready to connect to blender.

1. install java 8
2. download [jme3_xbuf_viewer-201507192026.tar.gz](https://github.com/xbuf/jme3_xbuf/releases/download/0.4.0/jme3_xbuf_viewer-201507192026.tar.gz) + unarchive + run ./launch (or launch.exe)

## On [blender 2.73+](http://www.blender.org/)

1. click the **[Download ZIP](https://github.com/xbuf/blender_io_xbuf/archive/master.zip)** button on [blender_io_xbuf](https://github.com/xbuf/blender_io_xbuf)
2. install add-on into blender
  * `File > User Preferences ... > Addons > Install from file ...` select the downloaded zip file
  * enable the plugin **Import-Export: Xbuf Exporter & Render Engine** (check the checkbox)
3. Open or create a model
4. select "xbuf" in the render engine combobox (top)
5. check the render properties (eg: the directory where to export images,...)
6. in the 3D view select "viewport shading : rendered" could take/freeze a moment to trandfert the initial data.
7. You should see your model rendered via jme inside blender viewport, play with the camera, lights, ... (animation should store in a strip on NLA Editor, click on the strip)

# Level 2

Export your data from blender via `File > Export > xbuf`, external assets like images are stored into the directory define in the Render property panel (when xbuf renderer is selected).

Load your xbuf data into your jme app : 
```
import jme3_ext_xbuf.XbufLoader;
...
assetManager.registerLoader(XbufLoader.class, "xbuf");
Spatial s = assetManager.loadModel("Models/xxxxx.xbuf");
```

dependencies setup : 
```
repositories {
	mavenLocal()
	jcenter()
	maven { url "http://updates.jmonkeyengine.org/maven/"}
	maven { url "https://jitpack.io" }
}

dependencies {
  compile 'org.xbuf.jme3_xbuf:jme3_xbuf_loader:213c6a499d'
...
```

see [samples/xbuf_jaime](https://github.com/xbuf/jme3_xbuf/tree/master/samples/xbuf_jaime) for a runnable sample.
