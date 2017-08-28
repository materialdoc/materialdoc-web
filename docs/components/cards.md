# Cards

![](../images/cards.png)

!!! note "From Google material design [documentation](https://material.io/guidelines/components/cards.html)"
    A card is a piece of paper with unique related data that serves as an entry point to more detailed information. For example, a card could contain a photo, text, and a link about a single subject.

### How to add?

I. In your `build.gradle` include the `cardview` library:

```
dependencies {
  compile 'com.android.support:cardview-v7:X.X.X' // where X.X.X version
}
```

II. Declare your card inside any `layout.xml` file and insert views inside it.

```xml
<android.support.v7.widget.CardView
    android:layout_width="match_parent"
    android:layout_height="200dp">

    <TextView
        android:text="Hello World!"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>

</android.support.v7.widget.CardView>
```

!!! note
    Use `android:clipToPadding="false"` on the card parent allows you to prevent possible clips in the outer shadows of the card.

### How to style?

![](../images/cards-styled.png)

I. Declare your custom style in your `styles.xml` file.

```xml
<style name="MyCardViewStyle" parent="Theme.AppCompat.Light">
    <item name="cardCornerRadius">2dp</item>
    <item name="cardElevation">2dp</item>
    <item name="contentPaddingBottom">24dp</item>
    <item name="contentPaddingTop">24dp</item>
    <item name="contentPaddingLeft">16dp</item>
    <item name="contentPaddingRight">16dp</item>
    <item name="cardBackgroundColor">@color/indigo</item>
</style>
```

II. Apply this style to your card via `style` attribute.

```xml
<android.support.v7.widget.CardView
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    style="@style/MyCardViewStyle">
```
