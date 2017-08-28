# Pickers

## Date Picker

<img src="/images/date-picker-1.png" width="360"/>

!!! note "From the Google Material Design [documentation](https://material.io/guidelines/components/pickers.html#pickers-date-pickers)"
    A dialog picker is used to select a single date on mobile_.

    The selected day is indicated by a filled circle. The current day is indicated by a different color and type weight.

### How to add?

I. In your `build.gradle` add latest `appcompat` library.

```
dependencies {  
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. Make your activity extend `android.support.v7.app.AppCompatActivity` and implement the  `DatePickerDialog.OnDateSetListener` interface.

```java
public class MainActivity extends AppCompatActivity
    implements DatePickerDialog.OnDateSetListener {
      ...
    }
```

III. Create your `DatePickerDialog` setting a context, the implementation of the listener and the start year, month and day of the date picker.

```java
DatePickerDialog datePickerDialog =
    new DatePickerDialog(context, listener, startYear, starthMonth, startDay);
```

IV. Show your dialog with the method `show` of `DatePickerDialog`

```java
datePickerDialog.show();
```

### How to style?

<img src="/images/date-picker-2.png" width="360"/>

I. Declare custom `drawable.xml` for the dialog background.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- From: support/v7/appcompat/res/drawable/abc_dialog_material_background_light.xml -->
<inset xmlns:android="http://schemas.android.com/apk/res/android"
    android:insetLeft="16dp"
    android:insetTop="16dp"
    android:insetRight="16dp"
    android:insetBottom="16dp">

    <shape android:shape="rectangle">
        <corners android:radius="2dp" />
        <solid android:color="@color/indigo" />
    </shape>

</inset>
```

II. Declare custom styles in your `styles.xml` file.

```xml
<style name="MyDialogTheme" parent="Theme.AppCompat.Light.Dialog.Alert">
    <item name="colorControlNormal">@android:color/white</item>
    <item name="colorControlActivated">@color/pink</item>
    <item name="textColorAlertDialogListItem">@android:color/white</item>
    <item name="colorAccent">@color/pink</item>
    <item name="android:textColorPrimary">@android:color/white</item>
    <item name="android:windowBackground">@drawable/background_dialog</item>
</style>
```

III. Set your custom style as a parameter of the `DatePickerDialog`.

```java
DatePickerDialog datePickerDialog =
    new DatePickerDialog(this, R.style.MyDialogTheme, listener, 2016, 21, 3);
```

IV. Show your `DatePickerDialog` with the `show` method.

```java
datePickerDialog.show();
```

## Time Picker

<img src="/images/time-picker-1.png" width="360"/>

!!! note "From de Google Material Design [documentation](https://material.io/guidelines/components/pickers.html#pickers-time-pickers)"
    A time picker adjusts to a user’s preferred time setting, i.e. the 12-hour or 24-hour format.

    A dialog picker is used to select a single time (hours:minutes) on mobile.

### How to add?

I. In your `build.gradle` add latest `appcompat` library.

```
dependencies {  
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. Make your activity extend `android.support.v7.app.AppCompatActivity` and implement the  `TimePickerDialog.OnTimeSetListener` interface.

```java
public class MainActivity extends AppCompatActivity
    implements TimePickerDialog.OnTimeSetListener {
      ...
    }
```

III. Create your `TimePickerDialog` setting a context, the implementation of the listener, the start hour of the day, minute and a `boolean` indicating if the dialog should show a 24h. format or not.

```java
TimePickerDialog timePickerDialog =
    new TimePickerDialog(context, listener, startHour, startMinute, is24HourFormat);
```

IV. Show your dialog with the method `show` of `TimePickerDialog`.

```java
timePickerDialog.show();
```

### How to style?

<img src="/images/time-picker-2.png" width="360"/>

I. Declare custom `drawable.xml` for the dialog background.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- From: support/v7/appcompat/res/drawable/abc_dialog_material_background_light.xml -->
<inset xmlns:android="http://schemas.android.com/apk/res/android"
    android:insetLeft="16dp"
    android:insetTop="16dp"
    android:insetRight="16dp"
    android:insetBottom="16dp">

    <shape android:shape="rectangle">
        <corners android:radius="2dp" />
        <solid android:color="@color/indigo" />
    </shape>

</inset>
```

II. Declare a custom styles in your `styles.xml` file.

```xml
    <style name="MyDialogTheme" parent="Theme.AppCompat.Light.Dialog.Alert">
        <item name="colorControlNormal">@color/indigo</item>
        <item name="colorControlActivated">@color/pink</item>
        <item name="textColorAlertDialogListItem">@color/indigo</item>
        <item name="colorAccent">@color/pink</item>
        <item name="android:textColorPrimary">@color/indigo</item>
        <item name="android:windowBackground">@drawable/background_dialog</item>
    </style>
```

III. Set your custom style as a parameter of the `DatePickerDialog`.

```java
TimePickerDialog timePickerDialog = new TimePickerDialog(
    context, R.style.MyDialogTheme, listener,
    startHour, startMinute, is24HourFormat);
```

IV. Show your `TimePickerDialog` with the `show` method.

```java
timePickerDialog.show();
```

### Dark theme

<img src="/images/time-picker-3.png" width="360"/>

I. Use `R.style.Theme_AppCompat_Dialog_Alert`theme for the style parameter in the `TimePickerDialog` constructor.

```java
TimePickerDialog dialog = new TimePickerDialog(
    context, R.style.Theme_AppCompat_Dialog_Alert,
    listener, startingHour, startingMinute, is24HourFormat);
```

!!! note
    You can use your custom style setting its parent with the `Theme.AppCompat.Light.Dialog.Alert` value

## Color Picker

<img src="/images/color-picker-1.png" width="480"/>

!!! note "From Google material design [documentation](https://www.google.com/design/spec/components/pickers.html)."
    Pickers provide a simple way to select a single value from a pre-determined set.

### How to add?

I. Clone the color picker project from the [Google open source repository](https://android.googlesource.com/platform/frameworks/opt/colorpicker/).

```
git clone https://android.googlesource.com/platform/frameworks/opt/colorpicker
```

II. Import a new module in android studio with the **New/Import module** menu, choosing the path where the project was cloned.

III. Compile the new module as a dependency of your android project

```
dependencies {
    compile project(':colorpicker')
}
```

IV. Declare some colors in your resources file `colors.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="red">#F6402C</color>
    <color name="pink">#EB1460</color>
    <color name="purple">#9C1AB1</color>
    <color name="deep_purple">#6633B9</color>
    <color name="indigo">#3D4DB7</color>
    <color name="blue">#1093F5</color>
    <color name="light_blue">#00A6F6</color>
    <color name="cyan">#00BBD5</color>
    <color name="teal">#009687</color>
    <color name="green">#46AF4A</color>
    <color name="light_green">#88C440</color>
    <color name="lime">#CCDD1E</color>
    <color name="yellow">#FFEC16</color>
    <color name="amber">#FFC100</color>
    <color name="orange">#FF9800</color>
    <color name="deep_orange">#FF5505</color>
    <color name="brown">#7A5547</color>
    <color name="grey">#9D9D9D</color>
    <color name="blue_grey">#5E7C8B</color>
</resources>
```

V. Init your `ColorPickerDialog` with a title, an array of colors, the default selected color, the number of columns and the size of the shown colors.

```java
ColorPickerDialog colorPickerDialog = new ColorPickerDialog();
colorPickerDialog.initialize(
    R.string.title, colors, selectedColor, numColumns, colors.length);
```

VI. Since `ColorPickerDialog` extends from a `DialogFragment` show it with the `show` method setting it with a `FragmentManager` and a tag.

```java
colorPickerDialog.show(getFragmentManager(), tag);
```

### How to style?

<img src="/images/color-picker-2.png" width="480"/>

I. Create a `ColorPickerPalette` in a layout file.

```xml
<com.android.colorpicker.ColorPickerPalette
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/palette"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_gravity="center"
    android:gravity="center"
    android:padding="16dp"
    />
```

!!! note
    The `ColorPickerPalette` extends from the `TableLayout` class, you can use the `TableLayout` view group parameters to  style it.

II. Declare a dark style for the dialog which will contain the `ColorPickerPalette`.

```xml
<style name="MyDialogTheme" parent="Theme.AppCompat.Dialog.Alert">
    <item name="colorAccent">@color/teal_light</item>
    <item name="android:textColorPrimary">@android:color/white</item>
</style>
```

III. Inflate your `ColorPickerPalette` in a view object.

```java
LayoutInflater layoutInflater = LayoutInflater.from(context);
ColorPickerPalette colorPickerPalette =
    (ColorPickerPalette) layoutInflater.inflate(R.layout.custom_picker, null);
```

IV. Configure the `ColorPickerPalette` with a number of colors and a listener.

```java
colorPickerPalette.init(colors.length, columns, mOnColorSelectedListener);
```

V. Call the `colorPickerPalette` method of `ColorPickerPalette` with an array of your colors and the selected default color.

```java
colorPickerPalette.drawPalette(colors, selectedColor);
```

VI. Create your dialog via `AlertDialog.Builder` with your dark theme and your view as the content.

```java
AlertDialog alert = new AlertDialog.Builder(this, R.style.MyDialogTheme)
    .setTitle(R.string.title_color_picker)
    .setPositiveButton(android.R.string.ok, mOnClickListener)
    .setNegativeButton(android.R.string.no, mOnClickListener)
    .setView(colorPickerPalette)
    .create();
```

VII. Show your dialog

```java
alert.show();
```
