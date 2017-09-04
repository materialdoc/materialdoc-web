## Notifications with text

![Material Style Notification](/images/notification-1.png)

!!! quote
    From Google material design [documentation](https://material.io/guidelines/patterns/notifications.html):

    Notifications inform your app’s users about relevant and timely events in your app. You can create notifications to draw attention to messages from friends, alert a commuter to traffic slowdowns, show the progress of a new app being installed, and more.

    Notifications should be synced to all of a user’s devices.

### How to add?

I. In your `build.gradle` file add the latest `appcompat` library.

```
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X'
    // X.X.X specify the version
}
```

II. Get an instance of the `NotificationCompat.Builder`.

```java
NotificationCompat.Builder builder =
    new NotificationCompat.Builder(context);
```

III. Create a `Notification` using `Notification.Builder`

```java
Notification notification = builder
    .setContentTitle("Title")
    .setContentText("This is a notification!")
    .setSmallIcon(R.drawable.ic_notifications_white_small)
    .build();
```

IV. Show the `Notification` with the method `notify` of  `NotificationManagerCompat` with an id of your choice.

```java
NotificationManagerCompat notificationManager =
    NotificationManagerCompat.from(context);

notificationManager.notify(0x1234, notification);
```

!!! note
    Title, text and small icon are mandatory in order to show the notification.


### How to style?

![](/images/notification-2.png)

Use the method `setColor(int color)` of `NotificationCompat.Builder` to set the color of the round background  your notification.

```java
Notification notification =
    new NotificationCompat.Builder(context)
        .setContentTitle("Title")
        .setContentText("This is a notification!")
        .setSmallIcon(R.drawable.ic_bell)
        .setColor(Color.parseColor("#4B8A08"))
        .build();
```

## Notifications with images

![Face styled notification](/images/notification-3.png)

Use the method `setLargeIcon(Bitmap)` of  `NotificationCompat.Builder` to use a big image next to the small icon.

```java
Notification notification =
    new NotificationCompat.Builder(context)
        .setContentTitle("Title")
        .setContentText("This is a notification!")
        .setSmallIcon(R.drawable.ic_bell)
        .setLargeIcon(profileImageBitmap) // Bitmap
        .setColor(Color.parseColor("#4B8A08"))
        .build();
```

## Vibrating notifications

Use the method `setVibrate` of `NotificationCompat.Builder` to create vibrate patterns accompanying the notification.

```java
long[] vibratePattern = new long[] {
   millisToWait, millisToVibrate,
   millisToWait, millisToVibrate
}

Notification notification =
    new NotificationCompat.Builder(context)
        .setContentTitle("Title")
        .setContentText("This is a notification!")
        .setSmallIcon(R.drawable.ic_bell)
        .setVibrate(vibratePattern)
        .build();
```

!!! note
    In order to use the vibration you will need to declare the `android.permission.VIBRATE` in your `AndroidManifest.xml` file.

## Notifications with lights

Use the method `setLights(int argb, int msOn, int msOff)` of `NotificationCompat.Builder` to customize the color and the LED pattern shown by the device.

```java
Notification notification =
   new NotificationCompat.Builder(context)
      .setContentTitle("Title")
      .setContentText("This is a notification!")
      .setSmallIcon(R.drawable.ic_bell)
      .setLights(Color.MAGENTA, onMillis, offMillis)
      .build();
```

## Tips and best practices

I. Notify the user about time-sensitive information directed specifically at them.

II. For notifications sent by another person, include that person's image.

III. When the user touches a notification, enable the user to take immediate action. This may open a detail view, such as a message, or a summary view for multiple notifications.

IV. The round cut is used by default when the `setLargeIcon` is not used and `setSmallIcon` method is used. When using the `setLargeIcon` the circular image has to be done manually.

![](/images/notification-4.png)
![](/images/notification-5.png)

## Expanded Notifications Layouts

![Big Notifications Title Notification](/images/big_notifications_title.png)

!!! quote
    From the Google Material Design [documentation](http://developer.android.com/intl/es/design/patterns/notifications.html)_

    You can choose how much detail your app's notifications should provide. They can show the first few lines of a message or show a larger image preview.

    The additional information provides the user with more context, and—in some cases—may allow the user to read a message in its entirety.

### How to use it?

I. Add the latest version of appcompat library on your `build.gradle`.

```
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X'
    // X.X.X especifica la versión
}
```

II. Retrieve an instance of `NotificationCompat.Builder`.

```java
NotificationCompat.Builder builder =
    new NotificationCompat.Builder(context);
```

III. Apply a style to the `NotificationCompat.Builder`

```java
NotificationCompat.BigTextStyle style = new NotificationCompat.BigTextStyle(builder);
```

IV. You have several styles available.

```java
// Big Text Style
NotificationCompat.BigTextStyle style
    = new NotificationCompat.BigTextStyle(builder);
```

```java
// Big Picture Style
NotificationCompat.BigPictureStyle style
    = new NotificationCompat.BigPictureStyle(builder);
```

```java
// Inbox Style
NotificationCompat.InboxStyle style
    = new NotificationCompat.InboxStyle(builder);
```

V. Build a `Notification` using the `NotificationCompat.Builder`

```java
Notification notification = builder
    .setContentTitle("Title")
    .setContentText("This is a notification!")
    .setSmallIcon(R.drawable.ic_notifications_white_small)
    .build();
```

VI. Pass along the `Notification` object via `notify` method from  `NotificationManagerCompat` and assign an ID of your choice.

```java
NotificationManagerCompat notificationManager =
    NotificationManagerCompat.from(context);

notificationManager.notify(0x1234, notification);
```

!!! note
    Title, text and small icon are mandatory so the notification can be displayed.

### Big Text Style

![](/images/big_text_expanded.png)

![Big Text Style Compressed Notification](/images/big_text_compressed.png)

Big Text Style is used to show large quantities of text. The notification body can hold around `450` characters. The rest of the text will be trimmed **without** the use of an ellipsis.

I. Apply the style by passing the builder to a `NotificationCompat.BigTextStyle`
instance.

```java
NotificationCompat.BigTextStyle style =
    new NotificationCompat.BigTextStyle(builder);
```

II. Set the long text you want to display on the expanded mode.

```java
style.bigText("The path of..." /* long text goes here */ );
```

!!! note
    For the compressed layout, the text set via `setContentText` of `NotificationCompat.Builder` will be shown.

III. Use the method `setBigContentTitle` of `NotificationCompat.BigTextStyle` if you want a different title for the expanded layout form.

```java
style.bigText("The path of..." /* long text goes here */)
     .setBigContentTitle("Expanded title");
```

!!! note
    If you do not call this method the title will fallback to the value you set on `setContentTitle` from `NotificationCompat.Builder`.

IV. Add if you like an additional summary to the expanded layout form.

```java
style.bigText("The path of..." /* long text goes here */ )
     .setBigContentTitle("Expanded title")
     .setSummaryText("Summary text");
```

### Big Picture Style

![Big Picture Style Expanded](/images/big_picture_expanded-1.png)

!!! note
    Big Picture Style is used to show image-rich content. The image limits will be phone screen length by `256dp` height. On Tablets, the image is 2:1 ratio. The rest of the image will be cropped with a `ScaleType.CROP_CENTER`.

I. Create a new instance of `NotificationCompat.BigPictureStyle` which will accept a `NotificationCompat.Builder` instance.

```java
NotificationCompat.BigPictureStyle style
    = new NotificationCompat.BigPictureStyle(builder);
```

!!! note
    Check how `NotificationCompat.Builder` are managed on the [basic notifications](http://www.materialdoc.com/notifications/) article.

II. Add the image you want to display by using `BigPictureStyle.bigPicture` method. The format of the image must be a `Bitmap`.

```java
Bitmap picture = BitmapFactory.decodeResource(getResources(), R.drawable.conga);
style.bigPicture(picture);
```

III. Add a new `LargeIcon` if you want to change it. In other case it will default to `NotificationCompat.Builder.setLargeIcon(Bitmap)`.

```java
Bitmap largeExpandedAvatar = BitmapFactory.decodeResource(
             getResources(), R.drawable.koala_avatar)  

style.bigPicture(picture)
     .bigLargeIcon(largeExpandedAvatar);
```

IV. Add a new title for the expanded layout form.

```java
Bitmap picture = BitmapFactory.decodeResource(getResources(), R.drawable.conga);
Bitmap largeExpandedAvatar = BitmapFactory.decodeResource(
             getResources(), R.drawable.koala_avatar)  

style.bigPicture(picture)
     .bigLargeIcon(largeExpandedAvatar);
     .setBigContentTitle("Expanded title")
```

V. Add a summary which sums up the notification content.
```java
Bitmap picture = BitmapFactory.decodeResource(getResources(), R.drawable.conga);
Bitmap largeExpandedAvatar = BitmapFactory.decodeResource(
             getResources(), R.drawable.koala_avatar)  

style.bigPicture(picture)
     .bigLargeIcon(largeExpandedAvatar);
     .setBigContentTitle("Expanded title")
     .setSummaryText("Summary text");
```

### Inbox Style

![Inbox Expanded Style](/images/inbox_style_expanded-1.png)

!!! quote
    Inbox Style allows a notification made of several independent lines of short text, as in the normal notifications. This style accepts up to `7` lines. Any number above the notification will ellipsize further lines by adding a "...".

I. Apply the style by creating a new `NotificationCompat.BigPictureStyle` instance.

```java
NotificationCompat.InboxStyle style =
    new NotificationCompat.InboxStyle(builder);
```

II. Add as many lines as you wish.
```java
style.addLine("This is line #" + i);
```
III. Add a different title if you want by using `setBigContentTitle`.
```java
style.addLine("This is line #" + i)
    .setBigContentTitle("Expanded title");
```

IV. Optionally add a summary to the notification.

```java
style.addLine("This is line #" + i)
    .setBigContentTitle("Expanded title")
    .setSummaryText("Summary text");
```

### Tricks and good practices

I. Guidelines insist that every app should display a single notification at all times in order to keep the notification list clean. Use `InboxStyle` to join several notifications in one while providing a history of the last ones.

II. Expanded layouts will be automatically displayed when the notification list have enough space, while compressing them otherwise. Play with different titles, `LargeIcon` and summaries to pick the interest of your user in both cases. If your notification is related to an image content, make it more attractive by using `BigPictureStyle`.

III. If your notification does not require images and there is only one, using by default `BigTextStyle` will not hurt. In this way, you will ensure that you can accomodate as much text as possible and giving the user the maximum context available.
