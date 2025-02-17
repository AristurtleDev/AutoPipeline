<h1 align="center">

<img src="https://github.com/AristurtleDev/AutoPipeline/blob/develop/images/banner.png?raw=true" alt="AutoPipeline" width="256"/>
<br/>
Automating the MonoGame Content Pipeline So You Don't Have To!
</h1>

<div align="center">

[![License: MIT](https://img.shields.io/badge/📃%20license-MIT-blue?style=flat)](LICENSE)


</div>

**AutoPipeline** is a project that automates the generation of your **Content.mgcb** file simply based on the files you have in your Content directory.  No need to open the MGCB Editor to add and remove content, just add and remove it directly from the `/Content` directory.

> [!WARNING]
> This project is in a really early stage at the moment and may change rapidly as I continue to finish it. Please refer to documentation below for using the version currently in the `develop` branch.

## Installation
You can install this in your MonoGame project either manually from source or via the NuGet package.

### NuGet Package Installation
Add the NuGet package to your MonoGame project

```
dotnet add package AutoPipeline --version 0.0.2
```

### Manual Installation
1. Download the [AutoPipeline.targets](/source/AutoPipeline/AutoPipeline.targets) file
2. Add it to the same directory as your MonoGame .csproj
3. Add the following import statement to your MonoGame .csproj:

```xml
<Import Project="AutoPipeline.targets" />
```

## Usage
This project is an MSBuild `.targets` file that contains a task that is configured to run before the `MonoGame.Content.Builder.Task` tasks run.  The task will generate the `Content.mgcb` file automatically for you based on the contents of the files in your `Content/` directory **each time you do a project build**.

For each type of asset, it will automatically configure it to be processed using the default processor settings.  You can find the properties of each one and the default values below:

### DirectX Model Files
These are model files with the extension `.x`.  

The Build Action type for these files is `MonoGameDirectXAsset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `XImporter` | - |
| Processor | string | `ModelProcessor` | - |
| ColorKeyColor | string | `255,255,255,255` | - |
| ColorKeyEnabled | bool | `True` | - |
| GenerateMipMaps | bool | `True` | - |
| GenerateTangentFrames | bool | `False` | - |
| PremultiplyTextureAlpha | bool | `True` | - |
| PremultiplyVertexColors | bool | `True` | - |
| ResizeTexturesToPowerOfTwo | bool | `False` | - |
| RotationX | number | `0` | - |
| RotationY | number | `0` | - |
| RotationZ | number | `0` | - |
| Scale | number | `1` | - |
| SwapWindingOrder | bool | `False` | - |
| TextureFormat | enum | `Color` | `AtcCompressed`, `Color`, `Color16Bit`, `Compressed`, `DxtCompressed`, `Etc1Compressed`, `NoChange` or `PvrCompressed` |

### Effect Files
These are shader effect files with the extension `.fx`

The Build Action type for these files is `MonoGameEffectAsset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `EffectImporter` | - |
| Processor | string | `EffectProcessor` | - |
| DebugMode | string | `Auto` | `Auto`, `Debug` or `Optimize` |
| Defines | string |  | - |

### FBX Model Files
These are model files that end with the `.fbx` extension

The Build Action type for these files is `MonoGameFbxAsset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `FbxImporter` | - |
| Processor | string | `ModelProcessor` | - |
| ColorKeyColor | string | `255,255,255,255` | - |
| ColorKeyEnabled | bool | `True` | - |
| GenerateMipMaps | bool | `True` | - |
| GenerateTangentFrames | bool | `False` | - |
| PremultiplyTextureAlpha | bool | `True` | - |
| PremultiplyVertexColors | bool | `True` | - |
| ResizeTexturesToPowerOfTwo | bool | `False` | - |
| RotationX | number | `0` | - |
| RotationY | number | `0` | - |
| RotationZ | number | `0` | - |
| Scale | number | `1` | - |
| SwapWindingOrder | bool | `False` | - |
| TextureFormat | enum | `Color` | `AtcCompressed`, `Color`, `Color16Bit`, `Compressed`, `DxtCompressed`, `Etc1Compressed`, `NoChange` or `PvrCompressed` |

### H.246 Video Files
These are video files that end with the `.mp4` extension.

The Build Action type for these files is `MonoGameH264Asset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `H264Importer` | - |
| Processor | string | `VideoProcessor` | - |

### Mp3 Audio Files
These are audio files that end with the `.mp3` extension.

The Build Action type for these files is `MonoGameMp3Asset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `Mp3Importer` | - |
| Processor | string | `SoundEffectProcessor` | - |
| Quality | enun | `Best` | `Best`, `Low`, or `Medium` |

### Ogg Audio Files
These are audio files that end with the `.ogg` extension.

The Build Action type for these files is `MonoGameOggAsset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `OggImporter` | - |
| Processor | string | `SoundEffectProcessor` | - |
| Quality | enun | `Best` | `Best`, `Low`, or `Medium` |

### Open Asset Library Model Files
These are model files that can be loaded with the Open Asset Import Library.  This includes files with following extensions: 

`.3d`, `.3ds`, `.ac`, `.ase`, `.b3d`, `.blend`,`.bvh`, `.cob`,`.csm`, `.dae`,`.dxf`, `.glb`, `.gltf`,`.hmp`, `.ifc`, `.irr`, `.irrmesh`, `.lwo`, `.lws`, `.lxo`, `.mdc`, `.mdl`, `.md2`, `.md3`, `.md5`, `.ms3d`, `.ndo`, `.nff`, `.obj`, `.off`, `.ogex`, `.pk3`, `.ply`, `.q3d`,`.q3s`, `.scn`, `.smd`,`.stl`, `.ter`, `.vta`, `.xgl`, `.zgl`

The Build Action type for these files is `MonoGameOpenAssetLibraryAsset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `OpenAssetImporter` | - |
| Processor | string | `ModelProcessor` | - |
| ColorKeyColor | string | `255,255,255,255` | - |
| ColorKeyEnabled | bool | `True` | - |
| GenerateMipMaps | bool | `True` | - |
| GenerateTangentFrames | bool | `False` | - |
| PremultiplyTextureAlpha | bool | `True` | - |
| PremultiplyVertexColors | bool | `True` | - |
| ResizeTexturesToPowerOfTwo | bool | `False` | - |
| RotationX | number | `0` | - |
| RotationY | number | `0` | - |
| RotationZ | number | `0` | - |
| Scale | number | `1` | - |
| SwapWindingOrder | bool | `False` | - |
| TextureFormat | enum | `Color` | `AtcCompressed`, `Color`, `Color16Bit`, `Compressed`, `DxtCompressed`, `Etc1Compressed`, `NoChange` or `PvrCompressed` |

### Image Files
These are images file that are loaded as textures. This includes files with the following extensions:

`.3fr`, `.ari`, `.arw`, `.bay`, `.bmp`, `.bw`, `.cap`, `.cr2`, `.crw`, `.cut`, `.dcr`, `.dcs`, `.dds`, `.dng`, `.drf`, `.eip`, `.erf`, `.fff`, `.g3`, `.gg`, `.gif`, `.hdp`, `.hdr`, `.ico`, `.iff`, `.iiq`, `.int`, `.inta`, `.j2k`, `.jbg`, `.jbig`, `.jfi`, `.jfif`, `.jif`, `.jng`, `.jp2`, `.jpe`, `.jpeg`, `.jpf`, `.jpg`, `.jpm`, `.jpx`, `.jxr`, `.k25`, `.kdc`, `.koa`, `.mdc`, `.mef`, `.mj2`, `.mng`, `.mos`, `.mrw`, `.nef`, `.nrw`, `.obm`, `.orf`, `.pbm`, `.pcd`, `.pct`, `.pcx`, `.pef`, `.pfm`, `.pgm`, `.pic`, `.pict`, `.png`, `.pnm`, `.ppm`, `.psd`, `.ptx`, `.pxn`, `.r3d`, `.raf`, `.ras`, `.raw`, `.rgba`, `.rwl`, `.rw2`, `.rwz`, `.sgi`, `.sr2`, `.srf`, `.srw`, `.sun`, `.tga`, `.tif`, `.tiff`, `.wbmp`, `.wdp`, `.webp`, `.xbm`, `.xpm`, `.x3f`

The Build Action type for these files is `MonoGameTextureAsset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `TextureImporter` | - |
| Processor | string | `TextureProcessor` | - |
| ColorKeyColor | string | 255,0,255,255 | - |
| ColorKeyEnabled | bool | `false` | - |
| GenerateMipMaps | bool | `false` | - |
| MakeSquare | bool | `false` | - |
| PremultiplyAlpha | bool | `false` | - |
| ResizeToPowerOfTwo | bool | `false` | - |
| TextureFormat | enum | `Color` | `AtcCompressed`, `Color`, `Color16Bit`, `Compressed`, `DxtCompressed`, `Etc1Compressed`, `NoChange` or `PvrCompressed` |

### SpriteFont Files
These are sprite fonts that end with the `.spritefont` extension.

The Build Action type for these files is `MonoGameSpriteFontAsset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `FontDescriptionImporter` | - |
| Processor | string | `FontDescriptionProcessor` | - |
| PremultiplyAlpha | bool | `True` | - |
| TextureFormat | enum | `Color` | `AtcCompressed`, `Color`, `Color16Bit`, `Compressed`, `DxtCompressed`, `Etc1Compressed`, `NoChange` or `PvrCompressed` |

### Wav Audio Files
These are audio files that end with the `.wav` extension.

The Build Action type for these files is `MonoGameWavAsset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `WavImporter` | - |
| Processor | string | `SoundEffectProcessor` | - |
| Quality | enun | `Best` | `Best`, `Low`, or `Medium` |

### Wma Audio Files
These are audio files that end with the `.wma` extension.

The Build Action type for these files is `MonoGameWmaAsset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `WmaImporter` | - |
| Processor | string | `SoundEffectProcessor` | - |
| Quality | enun | `Best` | `Best`, `Low`, or `Medium` |

### Wmv Videos Files
These are video files that end with the `.wmv` extension.

The Build Action type for these files is `MonoGameWmvAsset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `WmvImporter` | - |
| Processor | string | `VideoProcessor` | - |

### Xml Files
These are for eXtensible Markup Language files that end with the `.xml` extension.

The Build Action type for these files is `MonoGameXmlAsset`

| Property | Type | Default Value | Enum Values |
| --- | --- | --- | --- |
| Importer | string | `XmlImporter` | - |
| Processor | string | `PassThroughProcessor` | - |

## Customizing Parameters
All files in the content directory of a given Build Action type will use the defaults listed in the section above.  Though, there may be times when you need to adjust the processing parameters for a particular file.  

> ![Note]
> The overrides can be added directly inside your .csproj file, however I personally wouldn't recommend this as it can make your csproj file cluttered depending on the number of overrides you need to make.

To create overrides, first create a file called `ContentOverrides.targets` in the same directory as your csproj file.  Then add the following content to the file

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
	
</Project>
```

Next, open your csproj file and add the following import statement 

```xml
<Import Project="ContentOverrides.targets" />
```

Finally, in the `ContentOverrides.targets` file, add the overrides for each specific content file. For example, if you wanted to override the processing parameters for a texture your `ContentOverrides.targets` would contain the following

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
	<Target Name="AutoPipelineOverrides" AfterTargets="SetDefaultProperties">
		<ItemGroup>
			<MonoGameTextureAsset Update="Content\aristurtle.png">
				<ColorKeyEnabled>true</ColorKeyEnabled>
				<GenerateMipMaps>true</GenerateMipMaps>
			</MonoGameTextureAsset>
		</ItemGroup>
	</Target>
</Project>

```

1. A `<Target>` must be defined that executes `AfterTargets="SetDefaultProperties"`.
1. Overrides must be children inside the `<ItemGroup>` node.
2. Use the Build Action type, for instance `MonoGameTextureAsset` is used in the example.  See the sections under Usage above for the build action type of the various content files
3. The `Update` attribute must be used, and should point to the path of the content file relative from the root of the project directory

You can see an example of this in the examples directory of this repository.


## Known Limitations
Currently this only works for the default asset types that can be processed by the MonoGame Content Builder (mgcb).  This means this project **does not work if you use third-party content pipeline extensions**.  I do plan to support this, it is just not in there yet.


## Special Thanks
I would like to give a special thanks to [@MrGrak](https://github.com/mrgrak) for letting me use the name AutoPipeline even though he already has a lib for MonoGame called this.

## License
AutoPipeline is licensed under the MIT License. Please refer to the [LICENSE](LICENSE) file for full license text.
