## Text Fields

![](../images/text-field-intro-v1.png)

!!! quote "From google material design [documentation](https://material.io/guidelines/components/text-fields.html)."
    Text fields allow the user to input text, select text (cut, copy, paste), and lookup data via auto-completion.

### How to add?

I. In your `build.gradle` add latest `appcompat` library.

```
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```
II. Make your activity extend `android.support.v7.app.AppCompatActivity`.

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```
III. Declare your `EditText` inside any `layout.xml` file.

```xml
<EditText
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Hint text"/>
```

### How to style?

![](../images/text-field-style-v1.png)

I. Declare custom style in your `styles.xml` file.

```xml
<style name="MyEditText" parent="Theme.AppCompat.Light">
    <item name="colorControlNormal">@color/indigo</item>
    <item name="colorControlActivated">@color/pink</item>
</style>
```

II. Apply this style to your `EditText` via `android:theme` attribute.

```xml
<EditText
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Hint text"
    android:theme="@style/MyEditText"/>
```

## Single-line text field

!!! note "From google material design [documentation](https://material.io/guidelines/components/text-fields.html)."
    Single-line fields automatically scroll their content to the left as the text input cursor reaches the right edge of the input field.

To make your `EditText` single line add `android:inputType` attribute and set it's value to `text`.

```xml
<EditText
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:inputType="text"
    android:hint="Hint text"/>
```

## Multi-line text field

!!! note "From google material design [documentation](https://material.io/guidelines/components/text-fields.html)."
    Multi-line text fields automatically break to a new line for overflow text and scroll vertically when the cursor reaches the lower edge.

To make your `EditText` multi-line add `android:inputType` attribute and set it's value to `textMultiLine`.

```xml
<EditText
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:inputType="textMultiLine"
    android:hint="Hint text"/>
```

## Full-width text field

![](../images/Full-width-text-field-v2-1.png)

!!! note "From google material design [documentation](https://material.io/guidelines/components/text-fields.html)."
    Full-width text fields are useful for more in-depth tasks.

I. Declare custom style in your `styles.xml` file.

```xml
<style name="FullWidthEditText" parent="Widget.AppCompat.EditText">
    <item name="android:padding">20dp</item>
    <item name="android:background">@null</item>
    <item name="android:textSize">@dimen/abc_text_size_subhead_material</item>
</style>
```

II. Apply this style to your `EditText` via `style` attribute.

```xml
<EditText
    style="@style/FullWidthEditText"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Subject"/>
```

## Floating labels

![Floating labels](../images/floating-label.png)

!!! note "From google material design [documentation](https://material.io/guidelines/components/text-fields.html)."
    When the user engages with the text input field, the floating inline labels move to float above the field.

### How to add?

I. In your `build.gradle` add latest `appcompat` and `design` libraries.

```
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
    compile 'com.android.support:design:X.X.X' // where X.X.X version
}
```
II. Make your activity extend `android.support.v7.app.AppCompatActivity`.

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```
III. Declare your `EditText` inside any `layout.xml` file and wrap it with `TextInputLayout`.

```xml
<android.support.design.widget.TextInputLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content">

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/Title" />

</android.support.design.widget.TextInputLayout>
```

!!! note
    Both widgets `TextInputLayout` and `EditText` have `android:hint` attribute, you can use any of them. If your app supports landscape mode, replace `EditText` with `TextInputEditText` in order for the hint to display correctly.

### How to style?

![Floating labels](../images/flaoting-label-styles.png)

I. Declare custom styles in your `styles.xml` file.

```xml
<!--Floating label text style-->
<style name="MyHintText" parent="TextAppearance.AppCompat.Small">
    <item name="android:textColor">@color/pink</item>
</style>

<!--Input field style-->
<style name="MyEditText" parent="Theme.AppCompat.Light">
    <item name="colorControlNormal">@color/indigo</item>
    <item name="colorControlActivated">@color/pink</item>
</style>
```

II. Apply this styles to your `TextInputLayout` via `app:hintTextAppearance` attribute and to `EditText` via `android:theme` attribute.

```xml
<android.support.design.widget.TextInputLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:hintTextAppearance="@style/MyHintText">

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/Title"
        android:theme="@style/MyEditText" />

</android.support.design.widget.TextInputLayout>
```

## User input errors

![User input errors](../content/images/2015/11/error-label-1.png)

!!! note "From google material design [documentation](https://material.io/guidelines/components/text-fields.html)."
    Help users fix input errors as soon as they are detected. Disable the submission of a form if errors are detected, and if detected only after form submission, clearly explain the error and how to fix it.

### How to add?

I. In your `build.gradle` add latest `appcompat` and `design` libraries.

```
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
    compile 'com.android.support:design:X.X.X' // where X.X.X version
}
```
II. Make your activity extend `android.support.v7.app.AppCompatActivity`.

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```
III. Declare your `EditText` inside any `layout.xml` file and wrap it with `TextInputLayout`.

```xml
<android.support.design.widget.TextInputLayout
    android:id="@+id/inputLayout"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:errorEnabled="true">

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/First_name" />

</android.support.design.widget.TextInputLayout>
```

IV. To show/hide error use `TextInputLayout#setError`.

```java
TextInputLayout inputLayout = (TextInputLayout) findViewById(R.id.inputLayout);
inputLayout.setError("First name is required"); // show error
inputLayout.setError(null); // hide error
```

!!! note
    Declare `app:errorEnabled="true"` attribute inside `TextInputLayout` to reserve space for error label below `EditText`.

### How to style?

![User input errors](../images/error-label-styles-2-1.png)

I. Declare custom styles in your `styles.xml` file.

```xml
<!--Error label text style-->
<style name="MyErrorText" parent="TextAppearance.AppCompat.Small">
    <item name="android:textColor">@color/pink</item>
</style>

<!--Input field style-->
<style name="MyEditText" parent="Theme.AppCompat.Light">
    <item name="colorControlNormal">@color/indigo</item>
    <item name="colorControlActivated">@color/pink</item>
</style>
```

II. Apply this styles to your `TextInputLayout` via `app:errorTextAppearance` attribute and to `EditText` via `android:theme` attribute.

```xml
<android.support.design.widget.TextInputLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:errorTextAppearance="@style/MyErrorText"
    app:errorEnabled="true">

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/Title"
        android:theme="@style/MyEditText" />

</android.support.design.widget.TextInputLayout>
```

## Character counter

![](../images/counter.gif)

!!! note "From google material design [documentation](https://material.io/guidelines/components/text-fields.html)."
    Use a character counter in fields where a character restriction is in place.

### How to add?
I. In your `build.gradle` add latest `appcompat` and `design` libraries.
```
dependencies {  
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
    compile 'com.android.support:design:X.X.X' // where X.X.X version
}
```

II. Make your activity extend `android.support.v7.app.AppCompatActivity`.

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. Declare your `EditText` inside any `layout.xml` file and wrap it with `TextInputLayout`. Add `app:counterEnabled` attribute and set its value to `true`. To restrict maximum characters count set some integer value to `app:counterMaxLength` attribute.
```xml
<android.support.design.widget.TextInputLayout
        android:id="@+id/inputLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:counterEnabled="true"
        app:counterMaxLength="140">

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="hint text" />

</android.support.design.widget.TextInputLayout>
```

### How to style?

![](../images/custom_counter.gif)
To define a custom style for the overflow.

I. Define the text style.
```xml
<!--Overflow label text style-->
<style name="MyOverflowText" parent="TextAppearance.AppCompat.Small">
    <item name="android:textColor">@color/deep_orange</item>
</style>
```

II. Apply this styles to your `TextInputLayout` via `app:counterOverflowTextAppearance` attribute.
```xml
app:counterOverflowTextAppearance="@style/MyOverflowText"
```

## Password toggle

![](../images/password_toggle.gif)

!!! note "From google material design [documentation](https://material.io/guidelines/components/text-fields.html)."
    When the visibility icon is displayed with a text field, it indicates whether or not that field’s input is visible. A text field’s visibility may be toggled on or off using the icon.

### How to add?

I. In your `build.gradle` add latest `appcompat` and `design` libraries.

```
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
    compile 'com.android.support:design:X.X.X' // where X.X.X version
}
```

II. Make your activity extend `android.support.v7.app.AppCompatActivity`.

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. Declare your `EditText` inside any `layout.xml` file and wrap it with `TextInputLayout`. Add `app:passwordToggleEnabled` and set its value to `true`.
```xml
<android.support.design.widget.TextInputLayout
        android:id="@+id/inputLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:passwordToggleEnabled="true">

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:inputType="textPassword"
        android:hint="Password" />

</android.support.design.widget.TextInputLayout>
```

!!! note
    Declare `app:passwordToggleContentDescription` attribute inside `TextInputLayout` for accessibility purposes.

### How to style?

![](../images/password_toggle_color.png)

To change the color of the password toggle icon, use the `app:passwordToggleTint` attribute:
```xml
<android.support.design.widget.TextInputLayout
        android:id="@+id/inputLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:passwordToggleEnabled="true"
        app:passwordToggleTint="@color/colorAccent">

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Password" />

</android.support.design.widget.TextInputLayout>
```

Moreover, you can specify the blending mode with the `app:passwordToggleTintMode` attribute.

### Icon

![](../images/password_toggle_icon.png)

To change the password toggle icon, use the `app:passwordToggleDrawable` attribute:
```xml
<android.support.design.widget.TextInputLayout
        android:id="@+id/inputLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:passwordToggleEnabled="true"
        app:passwordToggleDrawable="@drawable/ic_lock">

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Password" />

</android.support.design.widget.TextInputLayout>
```

Use a [StateListDrawable](https://developer.android.com/reference/android/graphics/drawable/StateListDrawable.html) with the `android:state_checked` attribute to use separate drawables for each toggle state. Moreover, choose an [AnimatedStateListDrawable](https://developer.android.com/reference/android/graphics/drawable/AnimatedStateListDrawable.html) to animate the drawables between states.
