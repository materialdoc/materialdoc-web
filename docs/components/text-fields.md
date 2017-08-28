## Text Fields

![](images/text-field-intro-v1.png)

?> From google material design [documentation](https://www.google.com/design/spec/components/text-fields.html).
<br>
<br>Text fields allow the user to input text, select text (cut, copy, paste), and lookup data via auto-completion.

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

![](images/text-field-style-v1.png)

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

### Compatibility issues

I. The height and vertical alignment of the `EditText` are different.

<div>
    <table>
        <tr>
            <td style="text-align:center; background-color: #FFFFFF;">
                Android 4.4
              </td>
            <td style="text-align:center; background-color: #FFFFFF;">
                Android 5.0
             </td>
            <td style="text-align:center; background-color: #FFFFFF;">
                Android 5.1
             </td>
        </tr>
        <tr>
        <td style="background-color: #FFFFFF;">
            <img src="images/4-4-small.png">
          </td>
        <td style="background-color: #FFFFFF;">
            <img src="images/5-0-small.png">
         </td>
        <td style="background-color: #FFFFFF;">
            <img src="images/5-1-small.png">
         </td>
        </tr>
    </table>
</div>

II. Line background is not transparent on Android 4.0 - 4.4 / 6.0 and is semi transparent on Android 5.0 / 5.1

## Single-line text field

?> From google material design [documentation](https://www.google.com/design/spec/components/text-fields.html#text-fields-single-line-text-field).
<br>
<br>Single-line fields automatically scroll their content to the left as the text input cursor reaches the right edge of the input field.

To make your `EditText` single line add `android:singleLine` attribute and set it's value to `true`.

```xml
<EditText
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:singleLine="true"
    android:hint="Hint text"/>
```

## Multi-line text field

?> From google material design [documentation](https://www.google.com/design/spec/components/text-fields.html#text-fields-multi-line-text-field).
<br>
<br>Multi-line text fields automatically break to a new line for overflow text and scroll vertically when the cursor reaches the lower edge.

To make your `EditText` multi-line add `android:inputType` attribute and set it's value to `textMultiLine`.

```xml
<EditText
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:inputType="textMultiLine"
    android:hint="Hint text"/>
```

## Full-width text field

![](images/Full-width-text-field-v2-1.png)

?> From google material design [documentation](https://www.google.com/design/spec/components/text-fields.html#text-fields-full-width-text-field).
<br>
<br>Full-width text fields are useful for more in-depth tasks.

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

![Floating labels](/images/floating-label.png)

?> From google material design [documentation](https://www.google.com/design/spec/components/text-fields.html#text-fields-floating-labels).
<br>
<br>When the user engages with the text input field, the floating inline labels move to float above the field.

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

?> Both widgets `TextInputLayout` and `EditText` have `android:hint` attribute, you can use any of them.

### How to style?

![Floating labels](/images/flaoting-label-styles.png)

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

![User input errors](/content/images/2015/11/error-label-1.png)

?> From google material design [documentation](http://www.google.com.ua/design/spec/patterns/errors.html#errors-user-input-errors).
<br>
<br>Help users fix input errors as soon as they are detected. Disable the submission of a form if errors are detected, and if detected only after form submission, clearly explain the error and how to fix it.

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

?> Declare `app:errorEnabled="true"` attribute inside `TextInputLayout` to reserve space for error label below `EditText`.

### How to style?

![User input errors](/images/error-label-styles-2-1.png)

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

![](/images/counter.gif)

?>From the Google Material Design [documentation](!https://www.google.com/design/spec/components/text-fields.html#text-fields-character-counter)
<br>
<br>Use a character counter in fields where a character restriction is in place.

### How to add?
I. Add the last version of the `appcompat` library to your  `build.gradle` file.
```
dependencies {  
    compile 'com.android.support:appcompat-v7:X.X.X'
    // where X.X.X is the last version available
}
```

II. Declare your `EditText` inside any `layout.xml` file and wrap it with `TextInputLayout`. Add `app:counterEnabled` attribute and set it value to `true`. To restrict maximum characters count set some integer value to `app:counterMaxLength` attribute.
```xml
<android.support.design.widget.TextInputLayout
        android:id="@+id/inputLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:counterEnabled="true"
        app:counterMaxLength="140" >

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="hint text" />

</android.support.design.widget.TextInputLayout>
```

### How to style?

![](/images/custom_counter.gif)
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
