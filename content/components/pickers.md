# Pickers

## Date Pickers

<img src="images/date-picker-1.png" width="360"/>

?> From the Google Material Design [documentation](https://material.io/guidelines/components/pickers.html#pickers-date-pickers)
<br>
<br>A dialog picker is used to select a single date on mobile_.
<br>
<br>The selected day is indicated by a filled circle. The current day is indicated by a different color and type weight.

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

<img src="images/date-picker-2.png" width="360"/>

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

## Time Pickers

<img src="/images/time-picker-1.png" width="360"/>

?> From de Google Material Design [documentation](https://material.io/guidelines/components/pickers.html#pickers-time-pickers)
<br>
<br>A time picker adjusts to a user’s preferred time setting, i.e. the 12-hour or 24-hour format.
<br>
<br>A dialog picker is used to select a single time (hours:minutes) on mobile.

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

### Time Picker with dark theme

<img src="/images/time-picker-3.png" width="360"/>

I. Use `R.style.Theme_AppCompat_Dialog_Alert`theme for the style parameter in the `TimePickerDialog` constructor.

```java
TimePickerDialog dialog = new TimePickerDialog(
    context, R.style.Theme_AppCompat_Dialog_Alert,
    listener, startingHour, startingMinute, is24HourFormat);
```

?> You can use your custom style setting its parent with the `Theme.AppCompat.Light.Dialog.Alert` value
