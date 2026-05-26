## What is this?
This is documentation on how to mod Glue3DCE, this will introduce you into how many Glue3D elements work, how to do certain stuff, and some added features

## Modding basics
1. **Extensions**\
  Glue3DCE comes with many extensions to make certain features possible, here are all of them (by v1.2) and what they do
    * **text** for string manipulation, very useful for data-related moments like parsing
    * **JSON** for handeling data in packets, useful for files and storing constants or simply just data
    * **pen** used for rendering everything
    * **Advanced clipboard** custom made extension by Droplets21 for clipboard controls, this one is used in particular since other clipboard extensions typically ask for access every time they're prompted, this is only once
    * **Files** for importing and downloading files, useful for opening files like .g3dp and more
    * **Lily's toolbox** is an extension with a lot of very useful features, whatever you need will most likley be in there, but make sure to check "legacy" blocks too
    * **Asset manager** can be used to manipulate the engines internal code, it can be used to import and delete sprites, add and remove assets; like sounds and costumes, and more
>   [!WARNING]\
>   the **Asset manager** extensions is **very** powerful, please be careful with how you use it\
* Continuing... these extensions are very useful, now when modding Glue3DCE you may be tempted to add more extensions, but I recommend you stick to the ones Glue3DCE already has, like don't get an extension to open websites when **Lily's toolbox** already has that features, and don't get extensions for something that can easilly and quickly be done by vanilla-code

2. **Functions**\
   Glue3DCE comes with many functions (custom blocks) that can do many things, for example the `clamp(in, min, max)` function-operator, which can be used to clamp a value! *(it was made before any extension with the clamp was installed)* and I recommend you make        some too whenever you mod, as it speeds things up and can seperate stuff to be more orginized. Base Glue3D has many useful functions, many of them similar to g3dscript lines. I'll talk about more of them when they come in-handy for each specific chapter but here\
   are some miscelanius functions that are very useful
     * **decode** can be used to seperate a string into many sections using one or more "flags" or seperator characters, this is very useful even with the string manipulation extension
     * **edit data in object** is used to read, write, sum, and multiply local varaiables, one of it's biggest use-cases is setting `data_return`
     * **terminal.print** can be used to send messages in the terminal, this can be used to log, warn, and push error messages, please make sure if you're making a custom category or adding block-defenitions to add error detection ***AND*** push error messages to           ensure that developers aren't confused
  
3. **Rendering**\
   If you're making a mod that's anything more advanced than a simple block-category you might want to get learning on how to render stuff to the screen. First of all, you'll need to worry about layering, or where in the render pipeline you render something, I\
   recommend finding a function that does something similar/close enough to what your rendering for, or directly rendering on a major-render-function, like `Editor.screen`, `Editor.dragscreen`, or one of the major elements, like `Element: mainbar` or `Element: sidebar`. Once you've done that you'll need to know the functions that are used to render elements onto the screen, here are some of the major ones
     * **Render2D** renders a costume, with many inputs like position, size, direction, `GBC`, and even if it's interactive
     * **Render box** renders a box using two 2Dvectors, with inputs like `GBC` and it's type (idk what this input does, so just set it to `1` for default)
     * **Text** draws a string, with many inputs like position, size, if it's centered, `GBC`, and even if it shows a cursor for when editing
     * **Gui element** renders certain ui-elements using instructions, this one is a bit harder to use since you're setting up the instructions in a list-before calling the function, but I recommend you find and see how the engine uses them to find out how the work
