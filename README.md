# Android File Templates

Android Studio provides you with file templates to help speed up your development. You can use the pre-defined templates or create your own.

## What's in this repo?

Sample file templates:

- Compose Screen
- Unit Test

## Getting Started

### Use a file template

1. Right click on the package where you want to create your file
2. Select `New` from the dropdown
3. Select the file template for the type of file you want to create

### Create a file template

1. **Open File and Code Template menu**
  
   This can be accessed through either:  
   a. `Preferences` > `File and Code Templates`, or   
   b. Right click on a package in Project tab > `New` > `Edit file templates`
   
     <img width="400" alt="select default of project schema" src="https://user-images.githubusercontent.com/7950697/231135862-2c958e87-74a8-4931-a304-a71e4c0933ad.png">

2. Click on `+` under the `Files` tab
   
     <img width="600" alt="image" src="https://user-images.githubusercontent.com/7950697/231136740-88cca559-676c-414c-8bf6-43f5508067a3.png">
     
3. **Select Scheme**  
   **Default**: File template available for entire application (all projects). Use for personal templates.  
   **Project**: File template for the current project. Use if you want it to be available to everyone working on project. Stored in `.idea/fileTemplates`.

     <img width="600" alt="image" src="https://user-images.githubusercontent.com/7950697/231137753-c84f0a37-9f1c-488d-9061-e562b606bea8.png">

4. Add a _name_, _file extension_ and _filename_.  
  If you want the filename to contain the name you can use the `${NAME}` variable in the filename field.  
5. Add the code snippet you want included in the file template. 
    Below is a sample code snippet for a Compose Screen that includes a preview  

    ```kt
    #if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")
    package ${PACKAGE_NAME}
    #end

    import androidx.compose.material.Text
    import androidx.compose.runtime.Composable
    import androidx.compose.ui.tooling.preview.Preview
   
    @Composable
    fun ${NAME}() {
        Text("${NAME} Composable")
    }
   
    @Preview
    @Composable
    private fun ${NAME}Preview() {
        ${NAME}()
    }
   ```
     <img width="600" alt="image" src="https://user-images.githubusercontent.com/7950697/231136888-8f1d9aa3-2a15-4717-96f0-08e7838fbfec.png">

5. If you want to use [live templates](https://www.jetbrains.com/help/idea/using-live-templates.html) or a [set it so code generated based on the template conforms to a style](https://www.jetbrains.com/help/idea/code-style.html) in the file template then you can toggle those options to on
6. Click `OK` 
7. Start using your new file template

## Template Variables

To help with your file template creation you can use template variables. There are [pre-defined ones](https://www.jetbrains.com/help/idea/2022.1/file-template-variables.html) or you can create your own.
In the Compose template `NAME` is an example of a pre-defined variable.

### Custom template variable

   1. Use the custom variable in your file template by surrounding it with `${}` e.g. `${customParameter}`
      
   ```kt
   #if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")
   package ${PACKAGE_NAME}
   #end
   
   import androidx.compose.material.Text
   import androidx.compose.runtime.Composable
   import androidx.compose.ui.tooling.preview.Preview
   
   @Composable
   fun ${NAME}(${customParameter}: String) {
       Text("${customParameter}")
   }
   
   @Preview
   @Composable
   private fun ${NAME}Preview() {
       ${NAME}(${customParameter} = "${customParameter}")
   }
   ```

   2. Create a file using the file template
   3. Enter the name of the variable when prompted by Android Studio
   <img width="600" alt="image" src="https://user-images.githubusercontent.com/7950697/231141781-05cb5a6d-efba-4278-a156-14247e0397ea.png">

  Generated code when `customParameter` = `banana`:
  
  ```kt
  package com.nimisaya.filetemplates.ui.theme

  import androidx.compose.material.Text
  import androidx.compose.runtime.Composable
  import androidx.compose.ui.tooling.preview.Preview

  @Composable
  fun UseCustomVariable(banana: String) {
      Text(banana)
  }

  @Preview
  @Composable
  private fun UseCustomVariablePreview() {
      UseCustomVariable(banana = "Banana")
  }
  ```
## Directives

File templates use the Velocity Template Langauge (VTL). As well as using variables and plain text, you can also use directives such as `#if`, `#set` and `#foreach`.

```kt
println("Are you a Banana?")

#if ($NAME == "Banana")
println("Yes, hungry?") 
#else 
println("No, please don't eat me!")
#end

#set( $items = ["One", "Two", "Three"] )
#foreach( $item in $items)
println("$item")
#end

```
In this example if the file name is `Banana` the generated code will be:

```kt
println("Are you a Banana?")

println("Yes, hungry?") 

println("One")
println("Two")
println("Three")
```

### Next steps

Explore child templates and live templates.

### Resources

1. [Jetbrains File and Code Templates](https://www.jetbrains.com/help/idea/settings-file-and-code-templates.html)
2. [Templates with multiple files](https://www.jetbrains.com/help/idea/2022.1/templates-with-multiple-files.html)
3. [File template variables](https://www.jetbrains.com/help/idea/2022.1/file-template-variables.html)
4. [Velocity - VTL Guide (Template Directives)](https://velocity.apache.org/engine/2.0/vtl-reference.html)
