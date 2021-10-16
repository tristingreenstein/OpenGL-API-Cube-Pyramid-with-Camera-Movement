# OpenGL-API-Cube-Pyramid-with-Camera-Movement

# OpenGL Cubes and Camera Movement
Now that you have the basics of OpenGL out of the way, we can start working on something more interesting. For this assignment, you will be using OpenGL to define a Cube Primitive. We are going to use the definition of the Cube Primitive to create a mini-level using our building block, the cube.

To complete this assignment, you will need to perform some key tasks. First and foremost, you can use your previous OpenGL assignment as a starting point, as you have created the basics of Windowing and Rendering already. You will be expanding this code base to implement the new requirements.

# Requirements
Cube Primitive Definition using a set of vertices.
Create a shader class that will be used for future projects.
Texture Mapping Cube Surface using the provided texture.
Generating the Pyramid shape dynamically by using Cube Primitive Definition.
Create a camera class that will be used for future projects.
Keyboard Input for camera movement.
Mouse Input for camera rotation.
Cube Primitive
Given the knowledge you have from the previous assignment as well as reading and learning more about OpenGL, you know already that you need a set of vertices to represent geometric shapes. The cube primitives can be represented by the following floating point array list:

float vertices[] = {
-0.5f, -0.5f, -0.5f, 0.0f, 0.0f,
0.5f, -0.5f, -0.5f, 1.0f, 0.0f,
0.5f, 0.5f, -0.5f, 1.0f, 1.0f,
0.5f, 0.5f, -0.5f, 1.0f, 1.0f,
-0.5f, 0.5f, -0.5f, 0.0f, 1.0f,
-0.5f, -0.5f, -0.5f, 0.0f, 0.0f,

-0.5f, -0.5f, 0.5f, 0.0f, 0.0f,
0.5f, -0.5f, 0.5f, 1.0f, 0.0f,
0.5f, 0.5f, 0.5f, 1.0f, 1.0f,
0.5f, 0.5f, 0.5f, 1.0f, 1.0f,
-0.5f, 0.5f, 0.5f, 0.0f, 1.0f,
-0.5f, -0.5f, 0.5f, 0.0f, 0.0f,

-0.5f, 0.5f, 0.5f, 1.0f, 0.0f,
-0.5f, 0.5f, -0.5f, 1.0f, 1.0f,
-0.5f, -0.5f, -0.5f, 0.0f, 1.0f,
-0.5f, -0.5f, -0.5f, 0.0f, 1.0f,
-0.5f, -0.5f, 0.5f, 0.0f, 0.0f,
-0.5f, 0.5f, 0.5f, 1.0f, 0.0f,

0.5f, 0.5f, 0.5f, 1.0f, 0.0f,
0.5f, 0.5f, -0.5f, 1.0f, 1.0f,
0.5f, -0.5f, -0.5f, 0.0f, 1.0f,
0.5f, -0.5f, -0.5f, 0.0f, 1.0f,
0.5f, -0.5f, 0.5f, 0.0f, 0.0f,
0.5f, 0.5f, 0.5f, 1.0f, 0.0f,

-0.5f, -0.5f, -0.5f, 0.0f, 1.0f,
0.5f, -0.5f, -0.5f, 1.0f, 1.0f,
0.5f, -0.5f, 0.5f, 1.0f, 0.0f,
0.5f, -0.5f, 0.5f, 1.0f, 0.0f,
-0.5f, -0.5f, 0.5f, 0.0f, 0.0f,
-0.5f, -0.5f, -0.5f, 0.0f, 1.0f,

-0.5f, 0.5f, -0.5f, 0.0f, 1.0f,
0.5f, 0.5f, -0.5f, 1.0f, 1.0f,
0.5f, 0.5f, 0.5f, 1.0f, 0.0f,
0.5f, 0.5f, 0.5f, 1.0f, 0.0f,
-0.5f, 0.5f, 0.5f, 0.0f, 0.0f,
-0.5f, 0.5f, -0.5f, 0.0f, 1.0f
};

# Texture
In order to use textures, you will need to be able to load images. As you may already have figured out, OpenGL is just a graphics API, and it does not provide anything more then what you need to draw a pixel on the screen. Which means, you will need to somehow load these image files in memory before you can use them. Lucky for you, there is a library that provides you with most of the features you will need! 

stb_image.h is a great library that you can use for loading most popular image formats.


# Classes to be Defined
You will also create two classes for this project. The first one will be for loading shader files, and the second one will be for the camera control. Reading the sections assigned, will help you with the class definition and creation.

You will name your classes as such:

MyShaderLoader.h
MyCamera.h
As always, the key is attention to details while you read your reading assignments.

# Creating the Pyramid
The pyramid has a base of 10 x 10 cubes! It also has a height of 10. Each level is one less then the previous, i.e., the lowest level is composed of 100 cubes, the next level is composed of 81 cubes, the next 64 and etc... you will need to create a position vector dynamically to represent each one of the cubes, in total there are going to be 385 cubes that represent the Pyramid! 

The ultimate cube, the one on the top, will be rotating on all of its axis. 

NOTE: Last cube is scaled to (0.6, 0.6, 0.6)

# Camera and Keyboard Input
For this project, we would also want to program some input control from the keyboard and from the mouse. These features will be also outside the OpenGL library. You guessed it, we are going to be using GLFW to handle the keyboard and mouse inputs.

# Keyboard Mappings:
Esc key, will close and exit the application.
W key, will move the camera forward
Z key, will move the camera backward
A key, will move the camera to the left
S key, will move the camera to the right
Up Arrow key, will move the camera up
Down Arrow key, will move the camera down
Mouse Input:
To capture the mouse events, you will need to define two functions.

void mouse_callback(GLFWwindow* window, double xpos, double ypos);
void scroll_callback(GLFWwindow* window, double xoffset, double yoffset);
The mouse will control the yaw and the pitch of the camera. In other words, it will dictate there the front of the camera will be pointing in the world space.

# Camera Setup:
The camera setup is really simple for this assignment. You will just need to define a few vectors that will represent:

Camera Position Vector
Camera Front Vector
Camera Up Vector
You will also need to define a few variables for:

Yaw
Pitch
Previous Mouse Position
Field of View
You will also need to introduce the concept of timing in the program. This will be the time between current frame and last frame. These will be defined by deltaTime and lastFrame variables of float type.


Hints
The key to completing this assignment is the ability to pay attention to details and performing the samples provided in the book. You will also be introduced to a math library which will need to be downloaded and configured to make the matrix computation easier.

GLM: http://glm.g-truc.net/ 
STB_IMAGE: stb_image.h  that you can use for loading most popular image formats.
