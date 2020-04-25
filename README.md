# OpenGL Rendering Engine 

An OpenGL rendering engine written in C++. 
The engine is small and light. 
It implements things like shadow mapping, ambient occlusion, and shader application.
This engine is made open source through the MPL 2.0 license.

- This is a software rasterizer for OpenGL
- This does not use any existing graphics libraries

This is a proof-of-concept _and_ a learning tool for myself.
[Aquinas Games](https://aquinasgames.ca) was founded in April 2020.
Good game development necessitates a good understanding of graphics.
**Renderer based off the lessons in the [TinyRenderer Wiki](https://github.com/ssloy/tinyrenderer/wiki).**
I've made some changes, but this is very much a product of the lesson plan and coursework assigned in the TinyRenderer project.

---

## Lesson One: Wireframe Rendering

The first step to building a renderer was to render a file filled with 3D vectors (an `obj` file) by drawing lines on the screen. 
This was done by using the [Bresenham's Line Algorithm](https://en.wikipedia.org/wiki/Bresenham%27s_line_algorithm).
The final result was a wireframe image. The background is black and the lines are white.
To build off of this wireframe, we can fill in the triangles made by the wireframe model.

![Wireframe Render](/devlog/lesson-1-wireframe.png)

## Lesson Two: Fill Wireframe With Triangles

The next step was to fill and illuminate the space between wireframe lines.
We can assume all triangles drawn will be filled in. 
Then, we can illuminate our triangles by noticing that polygons that are parallel to the light vector won't be illuminated at all.
I.e. the intensity of illumination is equal to the scalar product of the light vector and the normal to the given triangle.
The result is that we can simulate light sources hitting our model from the front (where the camera is hypothetically facing).
Note that negative dot products mean that the light source is behind the polygon. 

![Triangles Filled In](/devlog/lesson-2-triangles.png)
