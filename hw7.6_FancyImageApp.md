# HW 7.6 Fancy Image App

This class exercise continues the development of a GUI app using the JavaFX library.

## Outcomes
* **LO2.e:** (Partial) Utilize existing generic methods, interfaces, and classes in a software solution.
* **LO7.a:** (Partial) Design and implement a graphical user interface in a software project.

## References and Prerequisites
* [CSCI 1302 JavaFX Tutorial](https://github.com/cs1302uga/cs1302-tutorials/blob/alsi/javafx/javafx.md)
* [JavaFX Bookmarks](https://github.com/cs1302uga/cs1302-tutorials/blob/master/javafx/javafx-bookmarks.md)
* [JavaFX API Documentation](https://openjfx.io/javadoc/17/)

## Questions

Answer the following questions in your notes. These instructions assume that you are 
logged into the Odin server. 

**NOTE:** If a step requires you to enter a command, please provide in your notes the full 
command that you typed to make the related action happen. If context is necessary (e.g., the 
command depends on your present working directory), then please note that context as well.

### Getting Started

1. Use Git to clone the repository for this exercise onto Odin into a subdirectory called `cs1302-hw7.6`:

   ```
   $ git clone --depth 1 https://github.com/cs1302uga/cs1302-hw7.6.git
   ```

## Exercise Steps

### Checkpoint 1 Steps

1. Execute `tree src` from within the `cs1302-hw7.6` directory you created to see the provided source files. Then, take a few
   minutes to look through the code and understand what you were given.
   
1. Compile and run the code using the provided compile script (`compile.sh`).

  ```java
  #!/bin/bash -ex

  # Compile the app
  javac -d bin -p $JAVAFX_HOME/lib --add-modules javafx.controls src/cs1302/gui/ImageApp.java
  javac -d bin -cp bin -p $JAVAFX_HOME/lib --add-modules javafx.controls src/cs1302/gui/ImageDriver.java

   # Run the app
  java -cp bin -Dprism.order=sw -p $JAVAFX_HOME/lib --add-modules javafx.controls cs1302.gui.ImageDriver

  ```
#### Run your `compile.sh`

   ```
   $ chmod +x compile.sh
   ```

   ```
   $ ./compile.sh
   ```

1. Enter an invalid URL into the `TextField` and click the load button. The starter code includes a method called `alertError`
   that displays an error message within an `Alert` window. Take a minute to look over the code in that method.

1. Consider the following screenshot and associated containment hierarchy:

   <table>
   <tr>
      <td><img src="resources/exampleNewIcons.png" width="382"></td>
      <td><pre><code>            Stage
                 |
               Scene
                 |
               VBox
                 |
               /---\---------\
              /     \         \
            HBox  ImageView  HBox
            / \               |
           /   \            /---\-----\
    TextField  Button      /     \     \
                      Button Button Button
                      /      /           \
                 ImageView ImageView ImageView</code></pre></td>
   </tr>
   </table>
   
   Each node corresponds to an object of some class under the 
   [`javafx`](https://openjfx.io/javadoc/17/)
   package. The diagram for the scene graph assumes that child nodes
   are added to their parents in a left-to-right order.
   Here are some additional notes:

   * All images will be loaded into the application with a width and height of `300`. Even if the original image
     is not perfectly square, it will show up that way in the app. This is expected behavior and this functionality
     is already built into the starter code. You can see this in the call to the `Image` constructor.
     
   * The text field is expected to grow with its parent `HBox`.
   
   * The three buttons at the bottom should grow to fill their enclosing `HBox`. Buttons require an
     extra step that was not needed with text fields. To get this to work, make sure you read and 
     understand all of the starter code in the 
     [`Hbox` Documentation](https://openjfx.io/javadoc/17/javafx.graphics/javafx/scene/layout/HBox.html)
   
   * The three `ImageView` objects associated with the `Button` objects 
      via each `Button` object's `graphic` property. 

   * The icons for the associated images are contained in the `resources` directory 
     provided with this exercise. To use these local files in your `ImageView`, you
     can use a relative `file:` URL, e.g., `file:resources/image.png` -- this will only work
     if resources is in the present working directory when the app is run. There is an example
     of this in the `init` method in the starter code. There, we initialize the default image
     from the `resources` directory.
   
  
