# Swipe to refresh

<img src="/images/normal_swipe.gif" width="480"/>

!!! note "From the Google Material Design [documentation](https://material.io/guidelines/patterns/swipe-to-refresh.html#)"
    Swipe to refresh manually refreshes screen content with a user action or gesture.

### How to add?
I. Add the last version of the `support-v4` library to your  `build.gradle` file.
```
dependencies {  
    compile 'com.android.support:support-v4:X.X.X'
    // where X.X.X is the last version available
}
```

II. Create your layout file and declare `SwipeRefreshLayout`inside. This view is usually along with lists, but you can use it with any view that fits your design.

```xml
<android.support.v4.widget.SwipeRefreshLayout
    android:id="@+id/swipe_refresh_layout"
    android:layout_width="match_parent"
    android:layout_height="wrap_content">

    <ListView
        android:id="@+id/listview"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>

</android.support.v4.widget.SwipeRefreshLayout>
```

III. Proceed with the refresh listening the events in the Activity using a `SwipeRefreshLayout.OnRefreshListener` instance.

```java
SwipeRefreshLayout swipeRefreshLayout =
        (SwipeRefreshLayout) findViewById(R.id.activity_main_swipe_refresh_layout);
swipeRefreshLayout.setOnRefreshListener(new SwipeRefreshLayout.OnRefreshListener() {
        @Override
        public void onRefresh() {
            refreshData();
        }
});
```

IV. To cancel the progress animation use `setRefreshing` method.

```java
swipeRefreshLayout.setRefreshing(false);
```
### How to style?

<img src="/images/custom_swipe.gif" width="480"/>

To define your own color scheme for the loading icon.

I. Define the colors you want to use it.
```xml
<resources>
    <color name="pink">#FF4081</color>
    <color name="indigo">#3F51B5</color>
    <color name="lime">#CDDC39</color>
</resources>
```

II. Assign the colors to the view with the `setColorSchemeResources` method.
```java
swipeRefreshLayout.setColorSchemeResources(R.color.pink, R.color.indigo, R.color.lime);
```
