# Buttons

## Raised Button

![](images/raised-button-intro-v2.png)

?> From google material design [documentation](http://www.google.com.ua/design/spec/components/buttons.html#buttons-flat-raised-buttons).
<br><br>A typically rectangular material button that lifts and displays ink reactions on press.

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
III. Declare your `Button` inside any `layout.xml` file

```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Button"/>
```

### How to style?

![](images/raised-button-style-v2.png)

I. Declare custom style in your `styles.xml` file.

```
<style name="MyButton" parent="Theme.AppCompat.Light">
    <item name="colorControlHighlight">@color/indigo</item>
    <item name="colorButtonNormal">@color/pink</item>
</style>
```

II. Apply this style to your `Button` via `android:theme` attribute.

```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Button"
    android:theme="@style/MyButton"/>
```

### Compatibility issues

!>  To change `Button` color of pressed state you can use `colorControlHighlight` theme attribute, however it will only affect Lollipop version.

!>  Android `elevation` attribute is only available on Lollipop devices therefore you will not see shadow around `Button` on pre Lollipop devices.

## Flat Button

![](images/flat-button-intro-v2.png)

?> From google material design [documentation](http://www.google.com.ua/design/spec/components/buttons.html#buttons-flat-raised-buttons).
<br><br>A button made of ink that displays ink reactions on press but does not lift.

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
III. Declare your `Button` inside any `layout.xml` file with `Borderless` style.

```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Button"
    style="@style/Widget.AppCompat.Button.Borderless"/>
```

### How to style?

![](images/flat-button-style-v2.png)

I. Declare custom style in your `styles.xml` file.

```
<style name="MyButton" parent="Theme.AppCompat.Light">
    <item name="colorControlHighlight">@color/pink</item>
</style>
```

III. Apply this style to your `Button` via `android:theme` attribute.

```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Button"
    android:theme="@style/MyButton"
    style="@style/Widget.AppCompat.Button.Borderless"/>
```
