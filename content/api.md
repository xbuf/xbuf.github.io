+++
date = "2015-02-15T00:00:00+01:00"
draft = false
title = "API"
+++

> It's a generated api from <a href="https://github.com/davidB/pgex/tree/master/src/main/proto">*.proto</a>.
> IMHO, the files *.proto are more readable. And always more uptodate.

# Protocol Documentation
<a name="top"/>

## Table of Contents
* [animations_kf.proto](#animations_kf.proto)
 * [AnimationKF](#xbuf_ext.AnimationKF)
 * [BezierParams](#xbuf_ext.BezierParams)
 * [Clip](#xbuf_ext.Clip)
 * [ColorKF](#xbuf_ext.ColorKF)
 * [KeyPoints](#xbuf_ext.KeyPoints)
 * [QuaternionKF](#xbuf_ext.QuaternionKF)
 * [TransformKF](#xbuf_ext.TransformKF)
 * [Vec3KF](#xbuf_ext.Vec3KF)
 * [KeyPoints.InterpolationFct](#xbuf_ext.KeyPoints.InterpolationFct)
* [custom_params.proto](#custom_params.proto)
 * [CustomParam](#xbuf_ext.CustomParam)
 * [CustomParamList](#xbuf_ext.CustomParamList)
* [cmds.proto](#cmds.proto)
 * [ChangeAssetFolders](#xbuf.ChangeAssetFolders)
 * [Cmd](#xbuf.Cmd)
 * [DeleteData](#xbuf.DeleteData)
 * [SetEye](#xbuf.SetEye)
 * [SetEye.ProjMode](#xbuf.SetEye.ProjMode)
* [datas.proto](#datas.proto)
 * [Attenuation](#xbuf.Attenuation)
 * [AttenuationInverse](#xbuf.AttenuationInverse)
 * [AttenuationInverseSquare](#xbuf.AttenuationInverseSquare)
 * [AttenuationLinear](#xbuf.AttenuationLinear)
 * [AttenuationSmooth](#xbuf.AttenuationSmooth)
 * [Bone](#xbuf.Bone)
 * [Color](#xbuf.Color)
 * [Data](#xbuf.Data)
 * [FloatBuffer](#xbuf.FloatBuffer)
 * [Geometry](#xbuf.Geometry)
 * [IndexArray](#xbuf.IndexArray)
 * [Light](#xbuf.Light)
 * [Mat4](#xbuf.Mat4)
 * [Material](#xbuf.Material)
 * [Mesh](#xbuf.Mesh)
 * [Quaternion](#xbuf.Quaternion)
 * [Relation](#xbuf.Relation)
 * [Skeleton](#xbuf.Skeleton)
 * [TObject](#xbuf.TObject)
 * [Texture](#xbuf.Texture)
 * [Texture2DInline](#xbuf.Texture2DInline)
 * [Transform](#xbuf.Transform)
 * [UintBuffer](#xbuf.UintBuffer)
 * [Vec2](#xbuf.Vec2)
 * [Vec3](#xbuf.Vec3)
 * [Vec4](#xbuf.Vec4)
 * [VertexArray](#xbuf.VertexArray)
 * [Light.Kind](#xbuf.Light.Kind)
 * [Mesh.Primitive](#xbuf.Mesh.Primitive)
 * [Texture2DInline.Format](#xbuf.Texture2DInline.Format)
 * [VertexArray.Attrib](#xbuf.VertexArray.Attrib)
* [Scalar Value Types](#scalar-value-types)

<a name="animations_kf.proto"/>
<p align="right"><a href="#top">Top</a></p>

## animations_kf.proto

<a name="xbuf_ext.AnimationKF"/>
### AnimationKF


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | string | required | @check identifier (id) should be unique and invariant over a set of datas (eg: use uuid) and over time. |
| name | string | optional | display name |
| duration | float | optional |  |
| clips | Clip | repeated |  |

<a name="xbuf_ext.BezierParams"/>
### BezierParams
Bezier Params for a curve between P0(0, yp0)  and P1(1, yp1)
/ y are in the same range that value of KeyPoints

| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| h0_x | float | optional | x of handle of P0 in range [0,1] |
| h0_y | float | optional |  |
| h1_x | float | optional | x of handle of P1 in range [0,1] |
| h1_y | float | optional |  |

<a name="xbuf_ext.Clip"/>
### Clip


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| transforms | TransformKF | optional |  |
| colors | ColorKF | optional |  |

<a name="xbuf_ext.ColorKF"/>
### ColorKF


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| r | KeyPoints | optional |  |
| g | KeyPoints | optional |  |
| b | KeyPoints | optional |  |
| a | KeyPoints | optional |  |

<a name="xbuf_ext.KeyPoints"/>
### KeyPoints


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| duration_ratio | float | repeated |  |
| value | float | repeated |  |
| interpolation | KeyPoints.InterpolationFct | repeated |  |
| bezier_params | BezierParams | repeated |  |

<a name="xbuf_ext.QuaternionKF"/>
### QuaternionKF


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| x | KeyPoints | optional |  |
| y | KeyPoints | optional |  |
| z | KeyPoints | optional |  |
| w | KeyPoints | optional |  |

<a name="xbuf_ext.TransformKF"/>
### TransformKF


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| translation | Vec3KF | optional |  |
| rotation | QuaternionKF | optional |  |
| scale | Vec3KF | optional |  |

<a name="xbuf_ext.Vec3KF"/>
### Vec3KF


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| x | KeyPoints | optional |  |
| y | KeyPoints | optional |  |
| z | KeyPoints | optional |  |


<a name="xbuf_ext.KeyPoints.InterpolationFct"/>
### KeyPoints.InterpolationFct


| Name | Number | Description |
| ---- | ------ | ----------- |
| constant | 1 |  |
| linear | 2 |  |
| bezier | 3 |  |

<a name="custom_params.proto"/>
<p align="right"><a href="#top">Top</a></p>

## custom_params.proto

<a name="xbuf_ext.CustomParam"/>
### CustomParam


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | string | required |  |
| vbool | bool | optional |  |
| vstring | string | optional |  |
| vfloat | float | optional |  |
| vint | int32 | optional |  |
| vvec2 | Vec2 | optional |  |
| vvec3 | Vec3 | optional |  |
| vvec4 | Vec4 | optional |  |
| vquat | Quaternion | optional |  |
| vmat4 | Mat4 | optional |  |
| vtexture | Texture | optional |  |
| vcolor | Color | optional |  |

<a name="xbuf_ext.CustomParamList"/>
### CustomParamList


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | string | required |  |
| params | CustomParam | repeated |  |


<a name="cmds.proto"/>
<p align="right"><a href="#top">Top</a></p>

## cmds.proto

<a name="xbuf.ChangeAssetFolders"/>
### ChangeAssetFolders


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| path | string | repeated | a list of local folder path |
| register | bool | optional | true =&gt; register path as a root folder for assets, false =&gt; unregister/remove path as a root folder |
| unregisterOther | bool | optional | should try to unregister every other root folders for assets ? |

<a name="xbuf.Cmd"/>
### Cmd


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| setEye | SetEye | optional | use to define eye (the virtual camera used to render viewport) |
| setData | Data | optional | use to set (add/update/merge) data into the scene, model, animation, ... |
| deleteData | DeleteData | optional | use to delete data from a scene, model, animation, ... |
| changeAssetFolders | ChangeAssetFolders | optional | use to delete data from a scene, model, animation, ... |

<a name="xbuf.DeleteData"/>
### DeleteData


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| refs | string | repeated | the list of id of object to delete, including relation where the object is part of. |
| relations | Relation | repeated | the list relation to delete, the object part of the relation can continue to exist. |
| all | bool | optional | set to true to remove all Data |

<a name="xbuf.SetEye"/>
### SetEye


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| location | Vec3 | required |  |
| rotation | Quaternion | required |  |
| projection | Mat4 | optional |  |
| near | float | optional |  |
| far | float | optional |  |
| projMode | SetEye.ProjMode | optional |  |


<a name="xbuf.SetEye.ProjMode"/>
### SetEye.ProjMode


| Name | Number | Description |
| ---- | ------ | ----------- |
| perspective | 1 |  |
| orthographic | 2 |  |

<a name="datas.proto"/>
<p align="right"><a href="#top">Top</a></p>

## datas.proto

<a name="xbuf.Attenuation"/>
### Attenuation


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| max | float | required | for a distance max is in meter, for an angle attenuation max is in radian. |
| linear | AttenuationLinear | optional |  |
| smooth | AttenuationSmooth | optional |  |
| inverse | AttenuationInverse | optional |  |
| inverse_square | AttenuationInverseSquare | optional |  |

<a name="xbuf.AttenuationInverse"/>
### AttenuationInverse


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| scale | float | optional |  |
| offset | float | optional |  |
| constant | float | optional |  |
| linear | float | optional |  |

<a name="xbuf.AttenuationInverseSquare"/>
### AttenuationInverseSquare


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| scale | float | optional |  |
| offset | float | optional |  |
| constant | float | optional |  |
| linear | float | optional |  |
| quadratic | float | optional |  |

<a name="xbuf.AttenuationLinear"/>
### AttenuationLinear


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| begin | float | optional |  |
| end | float | optional |  |

<a name="xbuf.AttenuationSmooth"/>
### AttenuationSmooth


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| begin | float | optional |  |
| end | float | optional |  |

<a name="xbuf.Bone"/>
### Bone


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | string | required | @check identifier (id) should be unique and invariant over a set of datas (eg: use uuid) and over time. |
| transform | Transform | required |  |
| name | string | optional | display name |

<a name="xbuf.Color"/>
### Color


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| r | float | required |  |
| g | float | required |  |
| b | float | required |  |
| a | float | required |  |

<a name="xbuf.Data"/>
### Data


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| version | uint32 | optional | version of the protocol / data format. readonly !! (== the major of the xbuf project version) |
| relations | Relation | repeated |  |
| tobjects | TObject | repeated |  |
| geometries | Geometry | repeated |  |
| materials | Material | repeated |  |
| lights | Light | repeated |  |
| skeletons | Skeleton | repeated |  |

<a name="xbuf.FloatBuffer"/>
### FloatBuffer


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | float | repeated |  |
| step | uint32 | required | number of float per group/entry (eg 3 for vec3, 2 for texcoord,...). the length of values should be a multiple of step |

<a name="xbuf.Geometry"/>
### Geometry


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | string | required | @check identifier (id) should be unique and invariant over a set of datas (eg: use uuid) and over time. |
| meshes | Mesh | repeated |  |
| name | string | optional | display name |

<a name="xbuf.IndexArray"/>
### IndexArray


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ints | UintBuffer | optional |  |

<a name="xbuf.Light"/>
### Light
the direction of the light need by directional and spot is Z (forward like regular Node).
/ To use an other direction add relation to a Node and change the rotation of the Node (idem for translation).

| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | string | required | @check identifier (id) should be unique and invariant over a set of datas (eg: use uuid) and over time. |
| kind | Light.Kind | optional |  |
| color | Color | optional |  |
| intensity | float | optional |  |
| cast_shadow | bool | optional |  |
| radial_distance | Attenuation | optional | attenuation from the radial distance of light source (for spot and point) |
| spot_angle | Attenuation | optional | attenuation of the angle forme between the forward axis (z) and the direction of the point./ eg: for a linear attenuation linear.begin is the end of inner cone, linear.end is the end of outer cone : linear define the penumbra |
| name | string | optional | display name |

<a name="xbuf.Mat4"/>
### Mat4


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| c00 | float | required |  |
| c10 | float | required |  |
| c20 | float | required |  |
| c30 | float | required |  |
| c01 | float | required |  |
| c11 | float | required |  |
| c21 | float | required |  |
| c31 | float | required |  |
| c02 | float | required |  |
| c12 | float | required |  |
| c22 | float | required |  |
| c32 | float | required |  |
| c03 | float | required |  |
| c13 | float | required |  |
| c23 | float | required |  |
| c33 | float | required |  |

<a name="xbuf.Material"/>
### Material


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | string | required | @check identifier (id) should be unique and invariant over a set of datas (eg: use uuid) and over time. |
| family | string | optional |  |
| name | string | optional | display name |
| shadeless | bool | optional |  |
| color | Color | optional |  |
| color_map | Texture | optional |  |
| opacity | float | optional | @check range(0.0, 1.0) |
| opacity_map | Texture | optional |  |
| normal | Vec3 | optional |  |
| normal_map | Texture | optional |  |
| roughness | float | optional | @check range(0.0, 1.0) |
| roughness_map | Texture | optional |  |
| metalness | float | optional | @check range(0.0, 1.0) |
| metalness_map | Texture | optional |  |
| specular | Color | optional |  |
| specular_map | Texture | optional |  |
| specular_power | float | optional |  |
| specular_power_map | Texture | optional |  |
| emission | Color | optional |  |
| emission_map | Texture | optional |  |

<a name="xbuf.Mesh"/>
### Mesh


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | string | required | @check identifier (id) should be unique and invariant over a set of datas (eg: use uuid) and over time. |
| primitive | Mesh.Primitive | required |  |
| lod | uint32 | optional |  |
| vertexArrays | VertexArray | repeated | @check every vertexArray should have the same number of elements (size / step) |
| indexArrays | IndexArray | repeated | @check max value of every indexArray should be &lt; number of elements of vertexArrays |
| name | string | optional | display name |

<a name="xbuf.Quaternion"/>
### Quaternion
Quaternion should be normalized

| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| x | float | required |  |
| y | float | required |  |
| z | float | required |  |
| w | float | required |  |

<a name="xbuf.Relation"/>
### Relation
Define a Relation (edge, link) between two objects with an id
/ rules:
/ * typename of obj with id == ref1 &lt; typename of obj with id == ref2
/ * if typename of both obj is the same the relation if ref1 is the parent, ref2 is the child

| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ref1 | string | required | reference the id of object 1/@check ref1 != ref2 |
| ref2 | string | required | reference the id of object 1 |
| label | string | optional | mainly for description but often useless |

<a name="xbuf.Skeleton"/>
### Skeleton


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | string | required | @check identifier (id) should be unique and invariant over a set of datas (eg: use uuid) and over time. |
| name | string | optional | display name |
| bones | Bone | repeated |  |
| bones_graph | Relation | repeated |  |

<a name="xbuf.TObject"/>
### TObject


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | string | required | @check identifier (id) should be unique and invariant over a set of datas (eg: use uuid) and over time. |
| transform | Transform | required |  |
| name | string | optional | display name |

<a name="xbuf.Texture"/>
### Texture


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | string | required |  |
| name | string | optional |  |
| rpath | string | optional | path of the texture relative to asset root folder (use '/' as folder separator) |
| tex2d | Texture2DInline | optional |  |

<a name="xbuf.Texture2DInline"/>
### Texture2DInline


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| format | Texture2DInline.Format | required |  |
| width | uint32 | required |  |
| height | uint32 | required |  |
| data | bytes | required |  |

<a name="xbuf.Transform"/>
### Transform


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| translation | Vec3 | required |  |
| rotation | Quaternion | required |  |
| scale | Vec3 | required |  |

<a name="xbuf.UintBuffer"/>
### UintBuffer


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | uint32 | repeated |  |
| step | uint32 | required | number of float per group/entry (eg 3 for vec3, 2 for texcoord,...). the length of values should be a multiple of step |

<a name="xbuf.Vec2"/>
### Vec2


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| x | float | required |  |
| y | float | required |  |

<a name="xbuf.Vec3"/>
### Vec3


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| x | float | required |  |
| y | float | required |  |
| z | float | required |  |

<a name="xbuf.Vec4"/>
### Vec4


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| x | float | required |  |
| y | float | required |  |
| z | float | required |  |
| w | float | required |  |

<a name="xbuf.VertexArray"/>
### VertexArray


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| attrib | VertexArray.Attrib | required |  |
| morph | uint32 | optional |  |
| floats | FloatBuffer | optional |  |


<a name="xbuf.Light.Kind"/>
### Light.Kind


| Name | Number | Description |
| ---- | ------ | ----------- |
| ambient | 1 |  |
| directional | 2 |  |
| point | 3 |  |
| spot | 4 |  |

<a name="xbuf.Mesh.Primitive"/>
### Mesh.Primitive


| Name | Number | Description |
| ---- | ------ | ----------- |
| points | 1 | &quot;points&quot; The mesh is composed of a set of independent points. The number of points is n, and point i is given by vertex i. |
| lines | 2 | &quot;lines&quot; The mesh is composed of a set of independent lines. The number of lines is n / 2 , and line i is composed of vertices 2i and 2i+1 . |
| line_strip | 3 | &quot;line_strip&quot; The mesh is composed of one or more line strips. The number of lines is  n - 1 , and line i is composed of vertices i and i + 1 . |
| triangles | 4 | &quot;triangles&quot; The mesh is composed of a set of independent triangles. The number of triangles is n/3 , and triangle i is composed of vertices 3i , 3i + 1 , and 3i + 2. |
| triangle_strip | 5 | &quot;triangle_strip&quot; The mesh is composed of one or more triangle strips. The number of triangles is n - 2 , and triangle i is composed of vertices i, i + 1 , and i + 2 when i is even or vertices i, i + 2 , and i + 1 when i is odd, in the orders listed. |

<a name="xbuf.Texture2DInline.Format"/>
### Texture2DInline.Format


| Name | Number | Description |
| ---- | ------ | ----------- |
| rgb8 | 1 |  |
| rgba8 | 2 |  |
| bgra8 | 3 |  |

<a name="xbuf.VertexArray.Attrib"/>
### VertexArray.Attrib


| Name | Number | Description |
| ---- | ------ | ----------- |
| position | 1 |  |
| normal | 2 |  |
| tangent | 3 |  |
| bitangent | 4 |  |
| color | 5 |  |
| texcoord | 6 |  |
| texcoord2 | 7 |  |
| texcoord3 | 8 |  |
| texcoord4 | 9 |  |
| texcoord5 | 10 |  |
| texcoord6 | 11 |  |
| texcoord7 | 12 |  |
| texcoord8 | 13 |  |
| texcoord9 | 14 |  |


<a name="scalar-value-types"/>
## Scalar Value Types

| .proto Type | Notes | C++ Type | Java Type | Python Type |
| ----------- | ----- | -------- | --------- | ----------- |
| double |  | double | double | float |
| float |  | float | float | float |
| int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int |
| int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long |
| uint32 | Uses variable-length encoding. | uint32 | int | int/long |
| uint64 | Uses variable-length encoding. | uint64 | long | int/long |
| sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int |
| sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long |
| fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int |
| fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long |
| sfixed32 | Always four bytes. | int32 | int | int |
| sfixed64 | Always eight bytes. | int64 | long | int/long |
| bool |  | bool | boolean | boolean |
| string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode |
| bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str |
