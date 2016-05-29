+++
date = "2015-08-21T00:00:00+01:00"
draft = false
title = "Get started"
+++

In the tutoriel bellow I use jME3 as render engine, but xbuf is not limited to jME3. It's just the first target engine I work on.

# Level 1

The quickest way to give a try : blender_io_xbuf + jme3_xbuf_viewer.

## jme3_xbuf_viewer

Install a pre-configured application ready to connect to blender.

1. install java 8
2. download [jme3_xbuf_viewer-201510171736.tgz](https://github.com/xbuf/jme3_xbuf/releases/download/0.7.2/jme3_xbuf_viewer-201510171736.tgz) + unarchive + run ./launch (or launch.exe)

## On Blender 2.74+

1. click the **[Download ZIP](https://github.com/xbuf/blender_io_xbuf/archive/master.zip)** button on [blender_io_xbuf](https://github.com/xbuf/blender_io_xbuf)
2. install add-on into blender
  * `File > User Preferences ... > Addons > Install from file ...` select the downloaded zip file
  * enable the plugin **Import-Export: Xbuf Exporter & Render Engine** (check the checkbox)
3. open or create a model
4. select `Xbuf Render` in the render engine combobox (top)
5. check the render properties (eg: `Xbuf > assets_path` the directory where to export images, ...)
6. in the 3D view select `viewport shading > rendered` could take/freeze a moment to transfer the initial data.
7. You should see your model rendered by jme3_xbuf_viewer inside blender viewport, play with the camera, lights, ... (animation should store in a strip on NLA Editor, click on the strip)

# Level 2

## On Blender

1. repeat steps 1 - 4 from Level 1 / On Blender
2. in the `Render Property Panel > Xbuf > assets_path` set your target assets directory (eg: `myproject/assets` or `myproject/src/main/resources`)
3. export your data from Blender via `File > Export > xbuf`, tips : choose the same directory or a subdirectory of `assets_path`

## On your project (myproject)

1. add jme3_xbuf_loader as a depencencies, eg for gradle :
~~~groovy
repositories {
	mavenLocal()
	jcenter()
	maven { url "http://updates.jmonkeyengine.org/maven/"}
	maven { url "https://jitpack.io" }
}

def jme3_xbuf_version = '213c6a499d'

dependencies {
  compile 'org.xbuf.jme3_xbuf:jme3_xbuf_loader:${jme3_xbuf_version}'
...
~~~
2. load your xbuf data into your jME app :
~~~java
import jme3_ext_xbuf.XbufLoader;
...
assetManager.registerLoader(XbufLoader.class, "xbuf");
Spatial s = assetManager.loadModel("Models/xxxxx.xbuf");
~~~
3. run

See :

* [samples/simple](https://github.com/xbuf/jme3_xbuf/tree/master/samples/simple) for a simplest code to load your model (model not include in this project).
* [samples/xbuf_jaime](https://github.com/xbuf/jme3_xbuf/tree/master/samples/xbuf_jaime) for a runnable sample with Jaime, the jME's mascot.

# Level 3

Use your jME3 application (with all your scene, post-process, UI, ...) to render data from/to Blender.

## On your project (myproject)

1. add jme3_xbuf_loader as a depencencies, eg for gradle :
~~~groovy
repositories {
	mavenLocal()
	jcenter()
	maven { url "http://updates.jmonkeyengine.org/maven/"}
	maven { url "https://jitpack.io" }
}

def jme3_xbuf_version = '213c6a499d'

dependencies {
  compile 'org.xbuf.jme3_xbuf:jme3_xbuf_loader:${jme3_xbuf_version}'
  compile 'org.xbuf.jme3_xbuf:jme3_xbuf_remote:${jme3_xbuf_version}'
...
~~~
2. load your xbuf data into your jME app :
~~~java
import jme3_ext_remote_editor.AppState4RemoteCommand;
import jme3_ext_xbuf.Xbuf;
...
app.setPauseOnLostFocus(false); //<-- Required else remote application will not receive image (eg: blender freeze)
app.getStateManager().attach(new AppState4RemoteCommand(4242, new Xbuf(app.getAssetManager())));
~~~
3. run

## On Blender

see Level 1 / On Blender
