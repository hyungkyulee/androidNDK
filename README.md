# androidNDK
Android Native Programming

## NDK Development evironment
Android Studio -> SDK manager -> SDK Tools Tab -> check the LLDB, CMake, NDK tools
 - LLDB : Tools to debug the code written C/C++ 
 - CMake : build tool according to each operating system
 - NDK : a set of library and headers for C/C++ Android programming
 
## The First NDK Project
1) File -> New -> New Project (or + Start a new Android Project)
2) Choose 'Native C++' Project
3) Config the project
4) Select 'default Toolchain'
5) Run the application by 'Ctrl + r' on Mac (or 'Ctrl+F5' on Windows)

## Programme details
### MainActivity.kt

- 'external fun' keyword for an external c/c++ liberary ( 'native' keyword on Java )
- native library load(```System.loadLibrary("native-lib"```) prior to using a native method 
- use 'companion object {}' keyword to have a static variable and function inside a class (Java can do this by 'static{}' keyword)

```
package com.example.helloandroid

import androidx.appcompat.app.AppCompatAct (ivity
import android.os.Bundle
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Example of a call to a native method
        sample_text.text = stringFromJNI()
    }

    /**
     * A native method that is implemented by the 'native-lib' native library,
     * which is packaged with this application.
     */
    external fun stringFromJNI(): String

    companion object {

        // Used to load the 'native-lib' library on application startup.
        init {
            System.loadLibrary("native-lib")
        }
    }
}
```
