# Auto Pipeline
This is a project that attempts to automate the content asset importing for MonoGame projects.  

> [!NOTE]
> This is not a replacement for the MonoGame Content Builder (MGCB).  This is meant to replace the need for the MGCB Editor and the Contnet.mgcb file by automating it.

> [!WARNING]
> This project is in it's really early stages at the moment as I build it up.  Refer to the roadmap table below for what is implemented and what is planned.

## Usage
In the future this will be distributed via NuGets.  For now, if you want to try this out you can

1. Clone the source
```sh
git clone https://github.com/aristurtledev/autopipeline
```

2. Update your MonoGame .csproj file to reference the `AutoPipeline.targets` file

```xml
<Import Project="path/to/autopipeline/source/AutoPipeline/AutoPipeline.targets" />
```

3. Remove the `MonoGame.Content.Builder.Task` Nuget package from your project

4. (Optional) Delete the `Content.mgcb` file, it's no longer needed.  You can keep it for backup, but it's not used.

And that's it. When you do a `dotnet build` the content will be built and output to your project output directory.

## RoadMap
The following tables shows the planned features and what's been implemented so far

| Default Importer/Processors | Implemented |
| --------------------------- | ----------- |
| Effects                     | ✅           |
| Fbx                         | ✅           |
| SpriteFont                  | ✅           |
| H.264 Video                 | ✅           |
| Mp3                         | ✅           |
| Ogg                         | ✅           |
| Open Asset Import Library   | ❌           |
| Texture                     | ✅           |
| Wav                         | ❌           |
| Wmv                         | ❌           |
| X                           | ❌           |
| Xml                         | ❌           |

| Features                                              | Implemented |
| ----------------------------------------------------- | ----------- |
| Customize defaults for processors                     | ❌           |
| Easy integration with third party pipeline extensions | ❌           |

## Known Issues
The following are known issues that exist either due to a bug or because what's needed hasn't been implemented yet.  If you find an issue that isn't on this list, please open an [Issue](https://github.com/aristurtledev/autopipeline/issues) and let me know

| Known Issue                                                                                                           | Status |
| --------------------------------------------------------------------------------------------------------------------- | ------ |
| .xnb files are not cleaned when doing a `dotnet clean`                                                                | ❌      |
| If you remove an item from the content directory then do a `dotnet build`, the .xnb still remains in the build output | ❌      |

## Special Thanks
I would like to give a special thanks to [@MrGrak](https://github.com/mrgrak) for letting me use the name AutoPipeline even though he already has a lib for MonoGame called this.

## License
AutoPipeline is licensed under the MIT License. Please refer to the [LICENSE](LICENSE) file for full license text.
