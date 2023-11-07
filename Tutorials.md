# Download and execute a shell script for the starter code

Use the following command to download and execute a shell script that retrieves 
   the starter code for this tutorial and places it into a subdirectory 
   called `cs1302-components`:

   ```
   $ curl -s -L https://git.io/fjfie | bash
   ```
# Directories (cs1302-components)
   ```
├── bin
│   └── cs1302
│       └── gui
│           ├── ImageApp.class
│           └── ImageDriver.class
├── components.md
├── doc
├── ScreenShot.png
├── src
│   └── cs1302
│       └── gui
│           ├── ImageApp.java
│           └── ImageDriver.java
└── TwoPaneScreenShot.png
   ```
# Hierachy
 Consider the following containment hierarchy:
   
   ```
                                                             --|
                         Stage                                 |
                           |                                   |
                         Scene                                 |
          |--              |                                   |
          |               HBox                                 |
          |                |\                                  |
          |                | \------------------\              |
          |                |                    |              |
          |               VBox                 VBox            | Overall
          |               / \                  / \             | Containment
   Scene  |              /   \                /   \            | Hierarchy
   Graph  |            HBox  ImageView      HBox  ImageView    |
          |            / \                  / \                |
          |           /   \                /   \               |
          |    TextField  Button    TextField  Button          |
          |--                                                --|
   ```
In this scenario, the root `HBox` of the scene graph contains two
separate, but identical, `VBox` objects. Building this app would
require the programmer to repeat the exact same code to create
these two `VBox` objects. Now, imagine that there are hundreds
of these in an app. Custom components allow us to avoid this type
of redundancy!

Consider the following scene graph where we replace the lower `VBox` 
sub-graphs with `ImageLoader`, a custom component that we will create 
in the next step. The resulting scene graph is much cleaner (kinda looks
like a giraffe, no?)!

   ```
                                                             --|
                         Stage                                 |
                           |                                   |
                         Scene                                 |
          |--              |                                   | Overall
          |               HBox                                 | Containment
   Scene  |                |\                                  | Hierarchy
   Graph  |                | \------------------\              |
          |                |                    |              |
          |           ImageLoader          ImageLoader         |
          |--                                                --|
   ```
Now consider the sub-graph for the `ImageLoader` component that we
will create. We want to avoid repeating this work by replacing this redundant
part of the original scene graph with a single `ImageLoader` component:

   ```
          |--
          |               VBox
          |               / \
   Sub-   |              /   \
   Graph  |            HBox  ImageView
          |            / \
          |           /   \
          |    TextField  Button
          |--
   ```
   
   Note that the root of this sub-graph is a `VBox`.

# Implement ImageLoader
Create a class called `ImageLoader` in the `cs1302.gui` package
that extends the `VBox` class (additional details are provided
below; please read them carefully). As this class extends `VBox`,
it "is-a" `VBox` and inherits all of the members of `VBox`
(although only `public` and `protected` members will be directly
visible).
   ```java
package cs1302.gui;

import javafx.scene.layout.VBox;

/**
 * This class is an extension of the VBox class to provide functionality
 * for loading and displaying images.
 */

public class ImageLoader extends VBox {

} //ImageLoader

   ```java
* The class should contain the `static` constants from the `ImageApp` class. They can be cut and paste directly from that class, perhaps changing them to `protected` visibility if you wish to do so. That way they can be accessedby the other classes in the package.
  ```
  protected static final String IMAGE_DIR = "path/to/images";
  protected static final String DEFAULT_IMAGE = "path/to/default/image.png";
  
  ```
* 
