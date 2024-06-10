# Unity Shader Graph Custom Functions
Notes on using Custom Functions Nodes in Unity Shader graph
(Unity 2022 LTS)

Documentation is sparse! To find out what functions & variables you can use and how to read from the screen buffers, grab files like Functions.hlsl and ShaderVariables.hlsl from in Packages\Shader Graph\ShaderGraphLibrary.

You can sample Depth, Color and Normal if you have them enabled (pass Screen Position into your function from the graph). 

SHADERGRAPH_SAMPLE_SCENE_DEPTH(uv);

SHADERGRAPH_SAMPLE_SCENE_COLOR(uv);

SHADERGRAPH_SAMPLE_SCENE_NORMAL(uv);

If you need the texel size of the above textures you could use the available _ScreenParams (e.g. float2 texelSize = float2(1.0 / _ScreenParams.x, 1.0 / _ScreenParams.y);)
