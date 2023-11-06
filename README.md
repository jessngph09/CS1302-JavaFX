# CS1302-JavaFX
JavaFX is a library for creating and delivering applications with graphical user interfaces (GUIs)
in Java.

# Log in to JavaFX
Log in to Odin using the `ssh` command along with the `-XY` option
   ```
   ssh -XY username@odin.cs.uga.edu
   ```
Also, the `-X` and `-Y` options can be used individually with or without each other. 

# How to compile source code
Compile the source code using the command below:
   ```
   javac -d bin -p $JAVAFX_HOME/lib --add-modules javafx.controls src/cs1302/gui/*.java
   ```
There are a few new command-line arguments to `javac` that you haven't seen before:

 * `-p $JAVAFX_HOME/lib`: tells the java compiler where to find the JavaFX library files (`.class` files)
        on Odin.
 * `--add-modules javafx.controls`: JavaFX is organized into 7 different modules. This option
        tells `javac` which modules to include. A list of the modules in JavaFX 17 can be found 
	[here](https://openjfx.io/javadoc/17/).
 
 # How to run the compiled code
 Run the compiled code using the command below:
 Ex: Run the compiled ExampleDriver.java in cs1302/gui
   ```
   java -cp bin -Dprism.order=sw -p $JAVAFX_HOME/lib --add-modules javafx.controls cs1302.gui.ExampleDriver
   ```
Notice the use of the `-p` and `add-modules` command line arguments as shown in the previous step. 


