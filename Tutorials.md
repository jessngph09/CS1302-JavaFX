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

# Implement ImageLoader.java
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

   ```
* The class should contain the `static` constants from the `ImageApp` class. They can be cut and paste directly from that class, perhaps changing them to `protected` visibility if you wish to do so. That way they can be accessedby the other classes in the package.
  
  ```java
  
  protected static final String IMAGE_DIR = "path/to/images";
  protected static final String DEFAULT_IMAGE = "path/to/default/image.png";
  
  ```
* Your `ImageLoader` class should contain instance variables for the nodes in the sub-graph above (`HBox`, `TextField`, `Button`, and `ImageView`).You do not need an instance variable for `VBox` because the `ImageLoader` itself is a `VBox`! For the most part, the required instance variables can be cut and paste from the `ImageApp` class. Any instance variables that you move into the `ImageLoader` class can be removed from `ImageApp`. You can also remove any imports that are no longer needed in `ImageApp`.

   ```java
   
    private HBox hbox;
    private TextField textField;
    private Button button;
    private ImageView imageView;
   
   ```
* In `ImageLoader`, add a default constructor that explicitly calls `super()`. After the call to `super`, the constructor should instantiate the other nodes in the `ImageLoader` sub-graph (`HBox`, `ImageView`, `TextField`, and `Button`). Since  `ImageLoader` extends `VBox`, it is-a `VBox`. Therefore, you can call any `VBox` methods using `this` as the calling object. Use this knowledge to add your newly created nodes to the sub-graph rooted at `this` similar to how they are added to the `VBox` node in the `ImageApp` class.  Your code will likely look something like the code below with additional statements to instantiate the components and connect them:
  
  ```java
  
      public ImageLoader() {
         super();
         // instantiate objects for the component's sub-graph, then
         // add them to the ImageLoader (i.e., this)...
         this.getChildren().addAll(urlLayer, imgView);
         // Add TextField and Button to the HBox
         hbox.getChildren().addAll(textField, button);
      } // ImageLoader
  
 ```
  
