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
   chmod +x compile.sh
   ```

   ```
   ./compile.sh
   ```
   
  
