# Launch screens

<img src="/images/splash.gif" width="360"/>

!!! note "From google material design [documentation](https://material.io/guidelines/patterns/launch-screens.html)."
    The launch screen is a user’s first experience of your application.

    Because launching your app while displaying a blank canvas increases its perceived loading time, consider using a placeholder UI or a branded launch screen.

### How to add?

I. Declare custom `drawable.xml` file with `items` for launch screen background.

```xml
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:drawable="@color/blue"/>

    <item>
        <bitmap
            android:gravity="center"
            android:src="@drawable/logo"/>
    </item>
</layer-list>
```

II. Declare custom style in your `styles.xml` using the new `drawable` as background.

```xml
<style name="SplashTheme" parent="Theme.AppCompat.NoActionBar">
    <item name="android:windowBackground">@drawable/background_splash</item>
</style>
```
!!! note
    If your API Level is greater than v19, you can make Status Bar and Navigation Bar translucent setting attributes `android:windowTranslucentStatus` and `android:windowTranslucentNavigation` to `true`.

III. Apply this style to your splash activity via `android:theme` attribute in your `AndroidManifest.xml` file.

```xml
<activity
    android:name=".SplashActivity"
    android:theme="@style/SplashTheme">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />

        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```
