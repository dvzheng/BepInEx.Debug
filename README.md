# BepInEx Debugging Tools
Tools and resources useful for developing and debugging BepInEx plugins.

You need to have at least [BepInEx 5,x](https://github.com/BepInEx/BepInEx) installed for most of the tools to work.

## Tools in this repo

### DemystifyExceptions
Turns exceptions into a more readable format. Resolves enumerators, lambdas and other complex structures.  
Based on [Apkd.UnityDemystifier](https://github.com/apkd/Apkd.UnityDemystifier).

**How to use:** This is a preloader patcher. Put the compiled DLL into `BepInEx/patchers`. Requires BepInEx 5 (or BepInEx 4 with MonoMod.RuntimeDetour).

### Simple Mono Profiler
A simple profiler that can be used in any Unity player build as long as it can run BepInEx 5.x. It can generate a .csv file with profiling results from an arbitrary length of time.

**How to use:** To install simply extract the release archive into the game root directory (folder structure is important, MonoProfiler.dll needs to be right next to the game .exe and other dlls need to be inside BepInEx subfolders).

Check the config file or use ConfigurationManager to change the hotkey used to dump the collected profiler data (KeyCode.BackQuote by default). Dumps only include information that was captured since the last time a dump was triggered.

**Warning:** The profiler always runs and will noticeably slow down the game. To turn the profiler off you have to close the game and rename `MonoProfiler.dll` to something else like `_MonoProfiler.dll`.

### ScriptEngine
Loads and reloads BepInEx plugins from the `BepInEx\scripts` folder. User can reload all of these plugins by pressing the keyboard shortcut defined in the config. Shortcut is F6 by default.  
Very useful for quickly developing plugins as you don't have to keep reopening the game to see your changes.

Remember to clean up after the old plugin version in case you need to. Things like harmony patches or loose GameObjects/MonoBehaviours remain after the plugin gets destroyed. Loose gameobjects and monobehaviours in this case are objects that are not attached to the parent scriptengine gameobject.

**How to use:** This is a plugin. Put the compiled DLL into `BepInEx/plugins`.

### Startup Profiler
Log and report the time spent in the `Start`, `Awake`, `Main`, `.ctor` and `.cctor` methods of each plugin.  
Also reports the total time spent in all plugins during these methods and the total time spent in chainloader so any performance improvements done through multithreading can be analyzed better.

**How to use:** This is a preloader patcher. Put the compiled DLL into `BepInEx/patchers`. Requires BepInEx 5 (or BepInEx 4 with MonoMod.RuntimeDetour).


## External tools and resources

### How use dnSpy debugger
You can debug already built Unity players even if you don't have its source project.
https://github.com/risk-of-thunder/R2Wiki/wiki/Debugging-Your-Mods-With-dnSpy

### Runtime Unity Editor
In-game inspector, editor and interactive console for applications made with Unity3D game engine. It's designed for debugging and modding Unity games.  
https://github.com/ManlyMarco/RuntimeUnityEditor#readme
