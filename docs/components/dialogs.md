# Dialogs

## Alerts

![](../images/dialog_alert_simple.png)

!!! quote "From Google material design [documentation](https://material.io/guidelines/components/dialogs.html#dialogs-alerts)"
    Alerts are urgent interruptions, requiring acknowledgement, that inform the user about a situation.

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

III. To create your dialog use  `android.support.v7.app.AlertDialog.Builder`.

```java
private void showLocationDialog() {
    AlertDialog.Builder builder = new AlertDialog.Builder(MainActivity.this);
    builder.setTitle(getString(R.string.dialog_title));
    builder.setMessage(getString(R.string.dialog_message));

    String positiveText = getString(android.R.string.ok);
    builder.setPositiveButton(positiveText,
            new DialogInterface.OnClickListener() {
        @Override
        public void onClick(DialogInterface dialog, int which) {
            // positive button logic
        }
    });

    String negativeText = getString(android.R.string.cancel);
    builder.setNegativeButton(negativeText,
            new DialogInterface.OnClickListener() {
        @Override
        public void onClick(DialogInterface dialog, int which) {
            // negative button logic
        }
    });

    AlertDialog dialog = builder.create();
    // display dialog
    dialog.show();
}
```

### How to style?

![](../images/dialog_alert_styled.png)

I. Declare custom `drawable.xml` for dialog background.

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
    <!--buttons color-->
    <item name="colorAccent">@color/pink</item>
    <!--title and message color-->
    <item name="android:textColorPrimary">@android:color/white</item>
    <!--dialog background-->
    <item name="android:windowBackground">@drawable/background_dialog</item>
</style>
```

III. Create your dialog and use `style` as parameter in `AlertDialog.Builder`.

```java
AlertDialog.Builder builder = 
        new AlertDialog.Builder(this, R.style.MyDialogTheme);
...
AlertDialog dialog = builder.create();
// display dialog
dialog.show();
```

!!! note 
        You can also style dialog in your activity theme via `alertDialogTheme` attribute.




