# Basic-Dice-Roller

The basic version of a dice roller android app First android app, these are the key points of this
exercise

- Setup Android Studio
- Setup Device and Emulator
- Basic app Structure
- Layouts, Activities and inflation
    - Activities
        - `MainActivity` is a subclass of `AppCompatActivity`, which in turn is a subclass
          of `Activity`. An `Activity` is a core Android class that is responsible for drawing an
          Android app UI and receiving input events.
        - All activities have an associated layout file, which is an XML file in the app's
          resources. The layout file is named for the activity, for example `activity_main.xml`.
        - The `setContentView()` method in MainActivity associates the layout with the activity, and
          inflates that layout when the activity is created.
        - Layout inflation is a process where the views defined in the XML layout files are turned
          into (or "inflated" into) Kotlin view objects in memory. Once layout inflation happens,
          the `Activity` can draw these objects to the screen and dynamically modify them.
    - Views
        - All UI elements in the app layout are subclasses of the `View` class and are called views.
          `TextView` and `Button` are examples of views.
        - `View` elements can be grouped inside a `ViewGroup`. A view group acts as a container for
          the views, or other view groups, within it. `LinearLayout` is an example of a view group
          that arranges its views linearly.
    - View attributes
        - The `android:layout_width` and `android:layout_height` attributes indicate the width and
          height of a view. The `match_parent` value stretches the view to its parent's width or
          height. The `wrap_content` value shrinks the view to fit the view's contents.
        - The `android:text` attribute indicates the text that a view should display (if that view
          displays text.) For buttons, `android:text` is the button label.
        - The `android:orientation` attribute in a `LinearLayout` view group arranges the view
          elements it contains. A value of `horizontal` arranges views left to right. A value
          of `vertical`
          arranges the views top to bottom.
        - The `android:layout_gravity` attribute determines the placement of a view and all that
          view's children.
        - The `android:textSize` attribute defines the size of the text in a text view. Text sizes
          are specified in sp units (scalable pixels). By using sp units, you can size text
          independently of the device's display quality.
    - Strings
        - Instead of hardcoding strings in the layout, it's a best practice to use string resources.
        - String resources are contained in the `res/values/string.xml` file.
        - To extract strings, use `Alt+Enter`. Select `Extract string resources` from the popup
          menu.
- Interactions
    - Using Views
        - To connect your Kotlin code to a view that you defined in the layout, you need to get a
          reference to the view object after the view has been inflated. Assign an ID (`android:id`)
          to the view in the layout, then use the `findViewById()` method to get the associated view
          object.
        - When you create an ID for a view in the XML layout file, Android Studio creates an integer
          constant with that ID's name in the generated `R` class. You can then use that `R.id`
          reference in the `findViewById()` method.
        - You can set the attributes of a view object in your Kotlin code directly by property name.
          For example, the text in a text view is defined by the `android:text` attribute in the
          XML, and it is defined by the `text` property in Kotlin.
        - A *click handler* is a method that is invoked when the user clicks or taps on a UI
          element. To attach a click-handler method to a view such as a button, use
          the `setOnClickListener()`
          method.
    - Using Toasts    
      A toast is a view that shows the user a simple message in a small popup window.   
      To create a toast, call the `makeText()` factory method on the `Toast` class with three
      arguments:
        1. The context of the app `Activity`
        2. The message to display, for example a string resource
        3. A duration, for example `Toast.LENGTH_SHORT`
           To display the toast, call `show()`.
- Images
    - The `drawable` resources folder is where you should put all the image resources for your app.
    - Vector drawables are images described in XML format. Vector drawables are more flexible than
      bitmap images (such as PNG files) because they can be scaled to any size or resolution.
    - To add a drawable to your app's layout, use an `<ImageView>` element. The source of the image
      is in the `android:src` attribute. To refer to the drawable resource folder, use `@drawable`,
      for example `@drawable/image_name`.
    - Use the `ImageView` view in your `Activity` code for the image. You can
      use `setImageResource()`
      to change the view's image to a different resource. Use `R.drawable` to refer to specific
      drawables, for example `setImageResource(R.drawable.image_name)`.
    - Minimize the calls to `findViewById()` in your code by declaring fields to hold those views,
      and initializing the fields in `onCreate()`. Use the `lateinit` keyword for the field to avoid
      needing to declare it nullable.
    - Use the `tools:src` attribute in the `<ImageView>` element in your layout to display an image
      in only Android Studio's preview or design editor. You can then use an empty image
      for `android:
      src` for the final app.
- Compatibility on Android
    - API levels
        - Each Android OS has an official version number and name (for example Android 9.0, "Pie")
          and an API level (API 28). Use the API levels in your app's Gradle files to indicate the
          versions of Android your app supports.
        - The `compileSdkVersion` parameter in the `build.gradle` file specifies the Android API
          level that Gradle should use to compile your app.
        - The `targetSdkVersion` parameter specifies the most recent API level that you have tested
          your app against. In many cases this parameter has the same value as `compileSdkVersion`.
        - The `minSdkVersion` parameter specifies the oldest API level your app can run on.
    - Android Jetpack
        - Android Jetpack is a collection of libraries, developed by Google, that offers
          backward-compatible classes and helpful functions for supporting older versions of
          Android. Jetpack replaces and expands on the set of libraries formerly known as the
          Android Support Library.
        - Classes imported from the `androidx` package refer to the Jetpack libraries. Dependencies
          to Jetpack in your `build.gradle` file also start with `androidx`.
    - Vector Drawables
        - Vector drawables are only natively supported in versions of Android higher than API 21. In
          older versions, Gradle generates PNG images for those drawables when your app is built.
        - You can specify that the Android Support Library should be used for vector drawables in
          older API versions with the `vectorDrawables.useSupportLibrary = true` configuration
          parameter in the `build.gradle` file.
        - Once you've enabled the support library for vector drawables, use the `app:srcCompat`
          attribute in the `<ImageView>` element (instead of `android:src`) to specify the vector
          drawable source for that image.
        - The `app` namespace in your XML layout file is for attributes that come from either your
          custom code or from libraries, not from the core Android framework.
