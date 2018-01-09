# Android 

Notes of components used, problems faced etc... when working on an Android project. (might be useful for reference for future projects). 

Most of the explanations are taken from [here](https://developer.android.com/guide/index.html). Reference original site for detailed explanation.

*Not 100% reliable, please google.


Integrating libraries into project
- edit `build.gradle (Module:)`
    > dependencies: implementation ''

OR

- edit `build.gradle (Project:)`
    > repository {}

[Android Activity Life Cycle](https://developer.android.com/guide/components/activities/activity-lifecycle.html)


[Android activity launchMode](https://developer.android.com/guide/topics/manifest/activity-element.html#lmode)

An instruction on how the activity should be launched. There are four modes that work in conjunction with activity flags in Intent objects to determine what should happen when the activity is called upon to handle an intent.

They are:
- standard
- singleTop
- singleTask
- singleInstance

*read link

More explanation
- [here]((https://inthecheesefactory.com/blog/understand-android-activity-launchmode/en))

## Android Components


### [Linear Layout](https://developer.android.com/guide/topics/ui/layout/linear.html)
LinearLayout is a view group that aligns all children in a single direction, vertically or horizontally. The layout direction can be specified with the `android:orientation` attribute.

Commonly use attribute?

`android:weightSum`
- Defines the maximum weight sum. Sum is computed by adding layout_weight of all of the children. This can be used for instance to give a single child 50% of the total available space by giving it a layout_weight of 0.5 and setting te weightSum to 1.0.

### [Relative Layout](https://developer.android.com/guide/topics/ui/layout/relative.html)
RelativeLayout lets child views specify their position relative to the parent view or to each other. By default, all child views are drawn at the top-left of the layout, so you must define the position of each view using various layout properties available from `RelativeLayout.LayoutParams`.


### [WebView](https://developer.android.com/reference/android/webkit/WebView.html)
A View that displays web pages. This class is the basics upon which you can roll your own web browser or simple display some online content within your Activity. It uses WebKit rendering engine to display web pages and includes methods to navigate forward and backward through a history, zoom in and out, perform searches and more.

In order for your Activity to access the Internet and load web pages in a WebView, you must add `INTERNET` permission to your Android Manifest file:
> `<uses-permission android:name="android.permission.INTERNET" />`

Common usage:

Loading the webpage
```
webView.loadUrl("");
```

Going back pages
```
if (webView.canGoBack()) { 
    webView.goBack(); 
}
```

To load the links the user clicks in the WebView, create your own `WebViewClient` that overrides the `shouldOverrideUrlLoading()` method. For Example:

```
private class MyWebViewClient extends WebViewClient {
    @Override
    public boolean shouldOverrideUrlLoading(WebView view, String url) {
        if (Uri.parse(url).getHost().equals("www.example.com")) {
            // This is my web site, so do not override; let my WebView load the page
            return false;
        }
        // Otherwise, the link is not for a page on my site, so launch another Activity that handles URLs
        Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(url));
        startActivity(intent);
        return true;
    }
}
```

create an instance of this new `WebViewCient for the `WebView`
```
WebView myWebView = (WebView) findViewById(R.id.webview);
myWebView.setWebViewClient(new MyWebViewClient());
```

### [ProgressBar](https://developer.android.com/reference/android/widget/ProgressBar.html)
A user interface element that indicates the progress of an operation. Progress bar supports 2 modes to represent progress: determinate and indeterminate

### Determinate Progress
Use determinate mode for progress bar when you want to show a specific quantity of progress has occured. To indicate determinate progress, set the style of the progress bar to `Widget_ProgressBar_Horizontal`. The following example shows a determinate progress bar that is 25% complete:
```
<ProgressBar
      android:id="@+id/determinateBar"
      style="@android:style/Widget.ProgressBar.Horizontal"
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
      android:progress="25"/>
```

### Indeterminate Progress
Use indeterminate mode for progress bar when you do not know how long an operation will take. Indeterminate mode is the default for progress bar and shows a cyclic animation without specific amount of progress indicated. The following example shows an indeterminate progress bar:
```
<ProgressBar
      android:id="@+id/indeterminateBar"
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
      />
```
The following example show a horizontal indeterminate progress bar:
```
<ProgressBar
    style="@style/Widget.AppCompat.ProgressBar.Horizontal"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:indeterminate="true" />
```
Note - Use with webview when loading pages

### [ViewFlipper](https://developer.android.com/reference/android/widget/ViewFlipper.html)
Simple ViewAnimator that will animate between 2 or more views that have been added to it. Only one child is shown at a time. If requested, can automatically flip between each child at a regular interval.

[Gesture and Touch Event example](https://stackoverflow.com/questions/7089015/viewflipper-doesnt-receive-touch-events)

Note - Use for image/photo galleries

### [ViewPager](https://developer.android.com/reference/android/support/v4/view/ViewPager.html)
Layout manager that allows user to flip left and right through pages of data. You supply an implementation of a `PagerAdapter` to generate the pages that view shows.

ViewPager is most often used in conjunction with `Fragment`, which is a convenient way to supply and manage th lifecycle of each page. 

There are standard adapters implemented for using fragments with the ViewPager which are `FragmentPagerAdapter` and `FragmentStatePagerAdapter`. The key difference between the 2 are that `FragmentPagerAdapter` will load all the pages while `FragmentStatePagerAdapter` load like a recycle view and is ideal for use when the amount of pages is not known.

Note - ViewFlipper will be easier for automatic flips

### [Sqlite](https://www.tutorialspoint.com/android/android_sqlite_database.htm)

## Android Libraries

### [Piccasso](https://github.com/square/picasso)

A powerful image downloading and caching library for Android

Detailed Usage: http://square.github.io/picasso/


### [android-async-http](https://github.com/loopj/android-async-http)

HTTP Client for Android (smaller usecase)

Detailed Usage: https://loopj.com/android-async-http/

[retrofit](https://github.com/square/retrofit)

HTTP Client for Android (bigger usecase)

Detailed Usage: http://square.github.io/retrofit/

### [Google Map Android](https://developers.google.com/maps/documentation/android-api/start)

## Others

### Fullscreen mode
To enabled full screen mode for activity, add the following link to the activity in the Android Manifest file:
```
android:theme="@android:style/Theme.NoTitleBar.Fullscreen"
```
### [Passing objects via intent in android](http://www.techjini.com/blog/passing-objects-via-intent-in-android/)
Whenever you want to pass an object, you can either make your objects Parcelable or Serializable. Below is an example of how you will make your class Serializable.

```
public class ClassName implements Serializable {
}
```

### [Background Timer Example](https://stackoverflow.com/questions/5883635/how-to-remove-all-callbacks-from-a-handler)

### [Hex Opacity Values](https://stackoverflow.com/questions/5445085/understanding-colors-on-android-six-characters/11019879#11019879)

Add the Hex Value infront of hex value

Example of the color black (000000) with an opacity value of 20% (33):
> `<color name="black20%visible">#33000000</color>`

