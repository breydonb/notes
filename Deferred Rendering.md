## Definition

Deferred rendering is a rendering technique used in computer graphics, particularly in real-time rendering engines like those used in video games. It's an advanced approach that aims to improve performance by separating the rendering process into multiple stages, allowing for more efficient handling of complex scenes with numerous lights and materials. Deferred Rendering uses High Definition Render Pipeline.
## How It Works
Here's how deferred rendering typically works:

1. **Geometry Pass**: In the first stage, known as the geometry pass, the scene's geometry is processed similarly to forward rendering. Each object's vertices are transformed into the camera's view space, and the transformed geometry is rasterized into fragments (pixels). However, unlike forward rendering, lighting calculations are deferred until later stages.
    
2. **G-Buffer Generation**: Instead of immediately calculating lighting contributions during the geometry pass, deferred rendering stores information about each fragment's material properties and position in a set of buffers called the G-Buffer (Geometry Buffer). These buffers typically include information such as the fragment's position, normal, albedo color, specular properties, and any other material attributes needed for shading.
    
3. **Lighting Pass**: Once the G-Buffer has been generated, a separate lighting pass is performed to calculate the contributions of each light source in the scene to the final image. For each light source, the shader retrieves the relevant information from the G-Buffer (such as the fragment's position and material properties) and computes the lighting contribution. This is done per pixel, allowing for accurate lighting calculations without the need to re-render geometry.
    
4. **Composite Pass**: After all the lighting contributions have been calculated, the final image is assembled by combining the results of the lighting pass with the information stored in the G-Buffer. This typically involves blending together the diffuse and specular lighting contributions for each fragment, applying any post-processing effects, and outputting the final color values to the screen.
    
## Pros and Cons Using Deferred Rendering Over [[Forward Rendering]]
Deferred rendering offers several advantages over [[forward rendering]], including:

- **Efficient handling of multiple lights**: Because lighting calculations are deferred until after the geometry pass, deferred rendering can handle scenes with a large number of dynamic lights more efficiently than forward rendering.
- **Flexibility**: Deferred rendering separates the rendering process into distinct stages, allowing developers to apply different shader effects and post-processing techniques more easily.
- **Reduced overdraw**: By storing material properties in the G-Buffer, deferred rendering can reduce overdraw and redundant pixel shader executions, leading to improved performance on modern graphics hardware.

However, deferred rendering also has some drawbacks, such as increased memory usage due to the need to store additional information in the G-Buffer and limitations when it comes to transparent or complex surface materials. Despite these limitations, deferred rendering remains a popular choice for rendering complex scenes in real-time applications.

