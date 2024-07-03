# Unity Shader Graph Custom Functions (URP focused)
Notes on using Custom Function Nodes in Unity Shader graph 

(Unity 2022 LTS)

To see see a fullscreen Shader Graph effect to do URP outlines & using a custom function node - download the unity package here.

Custom Function Node Documentation: https://docs.unity3d.com/Packages/com.unity.shadergraph@14.0/manual/Custom-Function-Node.html

Documentation for writing the code is sparse! To find out what functions & variables you can use and how to read from the screen buffers, grab files like Functions.hlsl and ShaderVariables.hlsl from in Packages\Shader Graph\ShaderGraphLibrary. To see the actual code for say URP - view the ShaderLibrary folder under the Universal RP package.

# Fullscreen shader graphs 
https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@14.0/manual/post-processing/post-processing-custom-effect-low-code.html

You can sample Depth, Color and Normal if you have them enabled (Set the requirements in your FullScreenPassRendererFeature). Pass Screen Position into your custom function node from the graph. 

Reading from screen buffers:

SHADERGRAPH_SAMPLE_SCENE_DEPTH(uv);

But the depth is different under different graphics APIs so you should check out common.hlsl to handle it! An orthographic Camera just needs z values flipping #if defined(UNITY_REVERSED_Z)  A normal camera should convert depth to 'LinearEyeDepth'.

SHADERGRAPH_SAMPLE_SCENE_COLOR(uv); 

Currently this will only work if you have a Scene Color Node used in your graph!

SHADERGRAPH_SAMPLE_SCENE_NORMAL(uv);

If you need the texel size of the above textures you could use the available _ScreenParams (e.g. float2 texelSize = float2(1.0 / _ScreenParams.x, 1.0 / _ScreenParams.y);)
