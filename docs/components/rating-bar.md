# Rating Bar

![](images/rating-bar-1.png)

?> From google [documentation](http://developer.android.com/reference/android/widget/RatingBar.html).
A RatingBar is an extension of SeekBar and ProgressBar that shows a rating in stars. The user can touch/drag or use arrow keys to set the rating when using the default size RatingBar. The smaller RatingBar style ([ratingBarStyleSmall](http://developer.android.com/reference/android/R.attr.html#ratingBarStyleSmall)) and the larger indicator-only style ([ratingBarStyleIndicator](http://developer.android.com/reference/android/R.attr.html#ratingBarStyleIndicator)) do not support user interaction and should only be used as indicators.

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

III. Declare your `RatingBar` inside any `layout.xml` file.

```
<RatingBar
    android:rating="3.5"
    android:stepSize="0.5"
    android:numStars="5"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"/>
```

### How to style?

![](images/rating-bar-2.png)

I. Declare custom style in your `styles.xml` file.

```
<style name="RatingBar" parent="Theme.AppCompat">
    <item name="colorControlNormal">@color/indigo</item>
    <item name="colorControlActivated">@color/pink</item>
</style>
```

II. Apply this style to your `RatingBar` via `android:theme` attribute.

```
<RatingBar
    android:theme="@style/RatingBar"
    android:rating="3"
    android:stepSize="0.5"
    android:numStars="5"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"/>
```
