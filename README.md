# class-OpenGL
A simple class to create OpenGL-based C++ codes

## Compile a code that uses class-OpenGL
```
g++ empty-window.cc class-OpenGL.cc -o empty-window -framework OpenGL -framework GLUT -Wno-deprecated -DGL_SILENCE_DEPRECATION -lpng  -std=c++11
```

This class serves as a wrapper for OpenGL functions, significantly reducing the programmer's intervention. With this wrapper, all OpenGL functions are called by default, simplifying the initiation of an OpenGL project to the following:

### empty-window.cc using class-OpenGL
```cpp
#include "class-OpenGL.h"

int main(int argc, char** argv)
{
 OpenGL_Display::CallOpenGLMainFunctions(argc,argv);
 return 0;
}
```

rather than this:

### empty-window.cc without the class-OpenGL (self-contained OpenGL code)
```cpp
//
// This is a code that creates a simple window in OpenGL
//

#include<OpenGL/gl.h>
#include<OpenGL/glu.h>
#include<GLUT/glut.h>


void Draw(void)
{
 glClear(GL_COLOR_BUFFER_BIT); // Cleans the screen
 glFlush();                    // Sends the information to the screen (draws)
}

int main(int argc, char** argv)
{
 glutInit(&argc, argv);                        // Loads the internal data structure of GLUT.
 glutInitDisplayMode(GLUT_SINGLE | GLUT_RGBA); // Characteristics of the graphical card
 glutInitWindowSize(1000,500);                 // Window size
 glutInitWindowPosition(150, 150);             // Location (upper left)
 glutCreateWindow("My Window");                // Creates the window with 'My Window' as title
 glutDisplayFunc(Draw);                        // Calls the Draw function to draw the scene.
 glutMainLoop();                               // Infinite loop over the above glut functions.
 return 0;
}
```
