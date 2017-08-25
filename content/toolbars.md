# Toolbars

![](images/anglerMMB29Msaulmm12282015010055.png)


?> From the google material design [documentation](https://material.io/guidelines/components/toolbars.html#)
<br>
<br>Toolbars appear a step above the sheet of paper affected by their actions. When sheets scroll underneath toolbars, they are clipped and cannot pass through to the opposite side.


## How to add?

I. In your `build.gradle` add latest `appcompat` library.

```
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X'
    // where X.X.X version
}
```

II. Make your activity extend `android.support.v7.app.AppCompatActivity`.

```java
public class MyActivity extends AppCompatActivity {
   ...
}
```

III. Declare your `Toolbar` inside any `layout.xml` file.


```xml
<android.support.v7.widget.Toolbar
    android:layout_width="fill_parent"
    android:layout_height="?attr/actionBarSize"
    android:background="?colorPrimary"
    app:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar"
    />
```

!> In order to use the method `setSupportActionBar` make sure that your Activity uses the `Theme.AppCompat.NoActionBar` theme.

## How to style?

![](images/anglerMMB29Msaulmm12292015005810.png)

I. Declare custom styles in your `style.xml` file.

```xml
<style name="ToolbarTextAppearance">
    <item name="android:fontFamily">sans-serif-condensed</item>
    <item name="android:textColor">@android:color/white</item>
    <item name="android:shadowDx">1</item>
    <item name="android:shadowDy">1</item>
    <item name="android:shadowRadius">2</item>
    <item name="android:shadowColor">?colorAccent</item>
</style>

<style name="ToolbarTextAppearance.Title">
    <item name="android:textSize">20sp</item>
</style>

<style name="ToolbarTextAppearance.Subtitle">
    <item name="android:textSize">14sp</item>
</style>

<style name="MyToolbar">
    <item name="theme">@style/ThemeOverlay.AppCompat.Dark</item>
    <item name="android:background">?colorPrimary</item>
    <item name="android:elevation">4dp</item>
</style>
```

II. Apply these styles to your `Toolbar` via `style`, `tittleTextAppearance` and `subtittleTextAppearance` attributes.

```xml
<android.support.v7.widget.Toolbar
    android:id="@+id/toolbar"
    android:layout_width="match_parent"
    android:layout_height="?actionBarSize"
    app:title="Toolbar"
    app:subtitle="Toolbars are amazing"
    app:titleTextAppearance="@style/ToolbarTextAppearance.Title"
    app:subtitleTextAppearance="@style/ToolbarTextAppearance.Subtitle"
    style="@style/MyToolbar"
    />
```

## Toolbar with menu icons

![](images/anglerMMB29Msaulmm12282015180321.png)


I. Create items for every action.


```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android"
      xmlns:app="http://schemas.android.com/apk/res-auto"
      xmlns:tools="http://schemas.android.com/tools">

    <item
        android:id="@+id/action_favorite"
        android:icon="@drawable/ic_favorite"
        app:showAsAction="always"/>

    <item
        android:id="@+id/action_search"
        android:icon="@drawable/ic_search"
        app:showAsAction="always"/>

    <item
        android:id="@+id/action_settings"
        android:orderInCategory="100"
        android:title="@string/action_settings"
        app:showAsAction="never"/>
</menu>

```

II. Inflate your menu via `inflateMenu` method

```java
Toolbar toolbar = (Toolbar) findViewById(R.id.toolbar);
toolbar.inflateMenu(R.menu.main);
```

II. Make your activity implement `Toolbar.OnMenuItemClickListener`.

```java
public class MyActivity extends AppCompatActivity
    implements Toolbar.OnMenuItemClickListener {
```

III. Reference your activity which implements the listener in your toolbar.

```prettyprint
toolbar.setOnMenuItemClickListener(this);
```


IV. Implement your actions inside the `onMenuItemClick` method.

```java
@Override
public boolean onMenuItemClick(MenuItem item) {
    switch (item.getItemId()) {
        case R.id.action_favorite:
            Toast.makeText(this, "Favorite", Toast.LENGTH_SHORT).show();
            return true;

        case R.id.action_search:
            Toast.makeText(this, "Search", Toast.LENGTH_SHORT).show();
            return true;
    }

    return true;
}
```

## Toolbar with navigation back icon

![](images/anglerMMB29Msaulmm12282015180702.png)

I. Declare custom style in your `styles.xml` file.

```xml
<style name="MyToolbar">
    <item name="theme">@style/ThemeOverlay.AppCompat.Dark</item>
    <item name="navigationIcon">@drawable/abc_ic_ab_back_mtrl_am_alpha</item>
    <item name="android:background">?colorPrimary</item>
    <item name="android:elevation">4dp</item>
</style>
```

II. Apply this style to your `Toolbar` via style attribute.


````xml
<android.support.v7.widget.Toolbar
    android:id="@+id/toolbar"
    android:layout_width="match_parent"
    android:layout_height="?actionBarSize"
    app:title="Toolbar"
    app:subtitle="Toolbars are amazing"
    style="@style/MyToolbar"
    />
```

III. Reference a listener to handle the navigation back action.

```java
toolbar.setNavigationOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        onBackPressed();
    }
});
```

## Toolbar with blank space

![](images/anglerMMB29Msaulmm12282015180943.png)

I. Declare custom style in your `styles.xml` file.

```xml
<style name="MyToolbar">
    <item name="theme">@style/ThemeOverlay.AppCompat.Dark</item>
    <item name="navigationIcon">@drawable/abc_ic_ab_back_mtrl_am_alpha</item>
    <item name="titleMarginTop">?actionBarSize</item>
    <item name="android:background">?colorPrimary</item>
    <item name="android:elevation">4dp</item>
</style>
```

II. Apply this style to your `Toolbar` via `style` attribute.


````xml
<android.support.v7.widget.Toolbar
    android:id="@+id/toolbar"
    android:layout_width="match_parent"
    android:layout_height="112dp"
    app:title="Toolbar"
    app:subtitle="Toolbars are really cool"
    style="@style/MyToolbar"
    />
```
