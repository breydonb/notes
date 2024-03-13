## Definition

Forward rendering is a rendering technique used in computer graphics, particularly in real-time rendering engines like those used in video games. It's a straightforward approach where each object in the scene is rendered individually, one after the other, with each object's contribution to the final image computed directly.
## How It Works
Here's how forward rendering typically works:
1. **Geometry Pass**: First, the scene's geometry is processed. This involves transforming each object's vertices into the camera's view space and performing any necessary transformations, such as scaling, rotation, and translation. The transformed geometry is then rasterized into fragments (pixels), which are passed on to subsequent stages.
2. **Per-Pixel Lighting**: For each fragment generated during the rasterization process, lighting calculations are performed. This typically involves computing the contribution of each light source in the scene to the fragment's final color. In forward rendering, this is usually done per pixel, meaning that for each pixel on the screen, the shader calculates the lighting contribution from all relevant light sources.
3. **Material Shading**: Once the lighting calculations are done, the fragment's final color is determined based on the material properties of the object being rendered. This includes factors like the object's color, reflectivity, transparency, and any other material properties defined by the shader.
4. **Rendering Passes**: After all the necessary calculations are complete for each fragment, the final image is assembled by combining all the rendered fragments together. This may involve blending fragments with alpha transparency, performing depth testing to determine which fragments are visible, and applying any post-processing effects such as anti-aliasing or depth of field.

In Forward Rendering, there are two types that URP handles applying light. Multi-Pass Forward which uses in the old built-in Renderer and Single-Pass Forward which uses URP. 

### Single-Pass Forward Rendering (SPFR)

In Single-Pass Forward Rendering, the renderer will calculate the object's appearance (lighting included) in one shot. This is known as a Draw Call, or the exact moment the Renderer asks the GPU to render the specific object. While more performant, the Draw Call can only handle a limited number of operations that the GPU can handle. 

### Multi-Pass Forward Rendering (MPFR)

In Multi-Pass Forward Rendering, the renderer will calculate the object's appearance and each light that affects the object. MPFR can apply any number of lights. With MPFR, you can use cheaper calculations on lower intensity lighting to save on resources. 


## Summary

Forward rendering is relatively simple and easy to implement, making it suitable for rendering scenes with a small to moderate number of light sources and objects. However, it can become inefficient when dealing with large numbers of lights or complex shader effects, as each object's shading calculations must be performed separately for each light source. This can lead to redundant computations and decreased performance compared to more advanced rendering techniques like deferred rendering or the Universal Render Pipeline in Unity, which optimize the rendering process by batching similar objects together and reducing the number of lighting calculations.