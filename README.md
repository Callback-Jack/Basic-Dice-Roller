# Basic-Dice-Roller
The basic version of a dice roller android app
First android app, these are the key points of this exercise
- Setup Android Studio
- Setup Device and Emulator
- Basic app Structure
- Layouts, Activities and inflation
- Interaction via button
- Gradle and Compatibility on Android
    For vector drawables' backward compatibility: 
  1. add `vectorDrawables.useSupportLibrary = true` in `build.gradle` in the module
  2. add namespace: `xmlns:app="http://schemas.android.com/apk/res-auto` in layout
  3. use `app:srcCompat=` for the drawable source