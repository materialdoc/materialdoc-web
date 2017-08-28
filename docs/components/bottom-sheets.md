# Bottom Sheets

<img src="/images/expand.gif" width="480"/>

!!! note "From google material design [documentation](https://material.io/guidelines/components/bottom-sheets.html)."
    A bottom sheet is a sheet of material that slides up from the bottom edge of the screen.

    Bottom sheets are displayed only as a result of a user-initiated action, and can be swiped up to reveal additional content. A bottom sheet can be a temporary modal surface or a persistent structural element of an app.

### How to add?

I. In your `build.gradle` add latest `appcompat` and `design` libraries.

```
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
    compile 'com.android.support:design:X.X.X' // where X.X.X version
}
```

II. Set the `app:layout_behavior` attribute with the value  `@string/bottom_sheet_behavior` which will allow your view or viewgroup appear as a bottom sheet.

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="300dp"
    android:orientation="vertical"
    android:padding="16dp"
    app:layout_behavior="@string/bottom_sheet_behavior">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Dandelion Chocolate"
        android:textAppearance="@style/TextAppearance.AppCompat.Display1"
        android:textColor="@android:color/black"/>
</LinearLayout>
```

!!! note
    You can use the `behavior_peekHeight` attribute to set the default height of the bottom sheet.

III. Add your view which implements the bottom sheet behavior as a direct child of a `CoordinatorLayout`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<android.support.design.widget.CoordinatorLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity" >

    <android.support.design.widget.AppBarLayout
        android:id="@+id/appbarLayout"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar" >

        <android.support.v7.widget.Toolbar
            android:id="@+id/appbar"
            android:layout_height="?attr/actionBarSize"
            android:layout_width="match_parent"
            android:minHeight="?attr/actionBarSize"
            android:background="?attr/colorPrimary"
            app:elevation="4dp"
            android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar"
            app:popupTheme="@style/ThemeOverlay.AppCompat.Light" >

        </android.support.v7.widget.Toolbar>

    </android.support.design.widget.AppBarLayout>

    <!-- Your content -->
    <include layout="@layout/content_main" />

    <!-- Bottom Sheet -->
    <include layout="@layout/bottom_sheets_main" />
</android.support.design.widget.CoordinatorLayout>
```

!!! note
    You can wrap your views and viewgroups under `<include>` tags in order to keep clean your layouts.

IV. Get a reference of `BottomSheetBehavior` with a reference of  the view which has the bottom behavior set. Use the `from` method of `BottomSheetBehavior`.

```java
LinearLayout bottomSheetViewgroup = (LinearLayout) findViewById(R.id.bottom_sheet);
BottomSheetBehavior bottomSheetBehavior = BottomSheetBehavior.from(bottomSheetViewgroup);
```

VI. To expand your bottom sheet use `setState` method with `BottomSheetBehavior.STATE_EXPANDED` parameter.

```java
bottomSheetBehavior.setState(BottomSheetBehavior.STATE_EXPANDED);
```

You can handle these states via the `setState` method:

- `STATE_EXPANDED`: To completely expand the bottom sheet.
- `STATE_HIDE`: To completely hide the bottom sheet.
- `STATE_COLLAPSED`: To set the bottom sheet height with the value set on the `peekHeight` attribute.

## Modal bottom sheets

<img src="/images/modal.gif" width="480"/>

!!! note "From google material design [documentation](https://material.io/guidelines/components/bottom-sheets.html#bottom-sheets-modal-bottom-sheets)."
    Modal bottom sheets are alternatives to menus or simple dialogs. They can also present deep-linked content from other apps. They are primarily for mobile.

I. Create a class extending the `BottomSheetDialogFragment` inflated with a layout which will be used as the content of your modal bottom sheet.

```java
public class ModalBottomSheet extends BottomSheetDialogFragment {

    static BottomSheetDialogFragment newInstance() {
        return new BottomSheetDialogFragment();
    }

    @Override
    public View onCreateView(
       LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {

        View v = inflater.inflate(R.layout.bottom_sheet_modal, container, false);

        return v;
    }
}
```

II. Create an instance of your modal bottom sheet and show it with the `show` method with a `SupportFragmentManager` and a String as parameters.

```java
ModalBottomSheet modalBottomSheet = new ModalBottomSheet();
modalBottomSheet.show(getSupportFragmentManager(), "bottom sheet");
```

### How to anchor views?
<img src="/images/expand-2.gif" width="480"/>

I. Add the view that will be anchored to the bottom sheet as a direct child of the `CoordinatorLayout`

```xml
<android.support.design.widget.FloatingActionButton
    android:id="@+id/fab"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_margin="@dimen/fab_margin"
    android:src="@android:drawable/ic_dialog_email"
    />
```

II. Reference the id of the view wich has set the `BottomSheetBehavior` with the `layout_anchor` attribute.

```xml
<android.support.design.widget.FloatingActionButton
    android:id="@+id/fab"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_margin="@dimen/fab_margin"
    android:src="@android:drawable/ic_dialog_email"
    app:layout_anchor="@id/app_bar"
    />
```

III. Configure the `layout_anchorGravity` attribute with the desired gravity.

```xml
<android.support.design.widget.FloatingActionButton
    android:id="@+id/fab"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_margin="@dimen/fab_margin"
    android:src="@android:drawable/ic_dialog_email"
    app:layout_anchor="@id/app_bar"
    app:layout_anchorGravity="bottom|end"
    />
```
