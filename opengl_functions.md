
## Setup functions

#### Function::glfwPollEvents
Function checks if any events are triggered (like keyboard input or
mouse movement events) and calls the corresponding functions (which we can set via callback
methods). We usually call event processing functions at the start of a loop iteration.

#### Function::glfwSwapBuffers
Function will swap the color buffer (a large buffer that contains color values
for each pixel in GLFW’s window) that has been used to draw in during this iteration and show it
as output to the screen.

#### Double Buffer approach
When an application draws in a single buffer the resulting image might display flickering
issues. This is because the resulting output image is not drawn in an instant, but drawn
pixel by pixel and usually from left to right and top to bottom. Because these images are
not displayed at an instant to the user, but rather via a step by step generation the result
may contain quite a few artifacts. To circumvent these issues, windowing applications
apply a double buffer for rendering. The front buffer contains the final output image
that is shown at the screen, while all the rendering commands draw to the back buffer.
As soon as all the rendering commands are finished we swap the back buffer to the front
buffer so the image is instantly displayed to the user, removing all the aforementioned
artifacts.


## Render functions

>There is a difference between a 2D coordinate and a pixel. A 2D coordinate is a
very precise representation of where a point is in 2D space, while a 2D pixel is an
approximation of that point limited by the resolution of your screen/window.

#### Function::glClearColor
We can clear the screen’s color buffer using the glClear function where
we pass in buffer bits to specify which buffer we would like to clear. The possible bits we can set are
> GL_COLOR_BUFFER_BIT, GL_DEPTH_BUFFER_BIT and GL_STENCIL_BUFFER_BIT.

```cpp
glClearColor(0.2f, 0.3f, 0.3f, 1.0f);
glClear(GL_COLOR_BUFFER_BIT);
```
