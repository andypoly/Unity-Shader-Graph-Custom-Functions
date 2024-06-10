# UnityShaderGraphCustomFunctions
Notes on using Custom Functions Nodes in Unity Shader graph
(Unity 2022 LTS)

Documentation is sparse! To find out what functions you can use and how to read from the screen buffers, grab the Functions.hlsl file from in Packages\Shader Graph\ShaderGraphLibrary.

You can sample Depth, Color and Normal if you have them enabled (pass Screen Position into your function from the graph). 
SHADERGRAPH_SAMPLE_SCENE_DEPTH(uv);
SHADERGRAPH_SAMPLE_SCENE_COLOR(uv);
SHADERGRAPH_SAMPLE_SCENE_NORMAL(uv);
