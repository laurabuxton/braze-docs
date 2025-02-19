Braze requires an external image library to display animated GIFs with {{ include.channel }}.

### Custom Image Library Integration {#gifs-delegate-integration}

Braze offers the ability to use a custom image library to display animated GIFs with {{ include.channel }}.

__Note:__ Although the example below uses [Glide][gifs-67], any image library that supports GIFs is compatible.

#### Step 1: Creating the Image Loader Delegate

The Image Loader delegate must implement the following methods:

* [`renderUrlIntoView()`][gifs-69]
* [`getBitmapFromUrl()`][gifs-68]
* [`setOffline()`][gifs-70]

The integration example below is taken from the [Glide Integration Sample App][gifs-65] included with the Braze Android SDK.

{% tabs %}
{% tab JAVA %}

```java
public class GlideAppboyImageLoader implements IAppboyImageLoader {
  private static final String TAG = GlideAppboyImageLoader.class.getName();
  private RequestOptions mRequestOptions = new RequestOptions();

  @Override
  public void renderUrlIntoView(Context context, String imageUrl, ImageView imageView, AppboyViewBounds viewBounds) {
    Glide.with(context)
        .load(imageUrl)
        .apply(mRequestOptions)
        .into(imageView);
  }

  @Override
  public Bitmap getBitmapFromUrl(Context context, String imageUrl, AppboyViewBounds viewBounds) {
    try {
      return Glide.with(context)
          .asBitmap()
          .apply(mRequestOptions)
          .load(imageUrl).submit().get();
    } catch (Exception e) {
      Log.e(TAG, "Failed to retrieve bitmap at url: " + imageUrl, e);
    }
    return null;
  }

  @Override
  public void setOffline(boolean isOffline) {
    // If the loader is offline, then we should only be retrieving from the cache
    mRequestOptions = mRequestOptions.onlyRetrieveFromCache(isOffline);
  }
}
```

{% endtab %}
{% tab KOTLIN %}

```kotlin
class GlideAppboyImageLoader : IAppboyImageLoader {
  companion object {
    private val TAG = GlideAppboyImageLoader::class.qualifiedName
  }

  private var mRequestOptions = RequestOptions()

  override fun renderUrlIntoView(context: Context, imageUrl: String, imageView: ImageView, viewBounds: AppboyViewBounds) {
    Glide.with(context)
        .load(imageUrl)
        .apply(mRequestOptions)
        .into(imageView)
  }

  override fun getBitmapFromUrl(context: Context, imageUrl: String, viewBounds: AppboyViewBounds): Bitmap? {
    try {
      return Glide.with(context)
          .asBitmap()
          .apply(mRequestOptions)
          .load(imageUrl).submit().get()
    } catch (e: Exception) {
      Log.e(TAG, "Failed to retrieve bitmap at url: $imageUrl", e)
    }

    return null
  }

  override fun setOffline(isOffline: Boolean) {
    // If the loader is offline, then we should only be retrieving from the cache
    mRequestOptions = mRequestOptions.onlyRetrieveFromCache(isOffline)
  }
}
```

{% endtab %}
{% endtabs %}

#### Step 2: Setting the Image Loader Delegate

The Braze SDK will use any custom image loader set with [setAppboyImageLoader][gifs-66]. Note that we recommend setting the custom image loader in a custom application subclass.

{% tabs %}
{% tab JAVA %}

```java
public class GlideIntegrationApplication extends Application {
  @Override
  public void onCreate() {
    super.onCreate();
    Appboy.getInstance(this).setAppboyImageLoader(new GlideAppboyImageLoader());
  }
}
```

{% endtab %}
{% tab KOTLIN %}

```kotlin
class GlideIntegrationApplication : Application() {
  override fun onCreate() {
    super.onCreate()
    Appboy.getInstance(this).appboyImageLoader = GlideAppboyImageLoader()
  }
}
```

{% endtab %}
{% endtabs %}

### Fresco Migration {#gifs-integration}
Fresco is no longer supported as a GIF loading library in version 3.0.0 of the Braze Android SDK. A custom image loader, such as [Glide][gifs-67], must be used in order to display GIFs.

_The usage of Fresco with `IAppboyImageLoader` is not supported since Fresco requires Drawee views to work._

[gifs-56]: http://developer.android.com/reference/android/app/Application.html
[gifs-57]: https://github.com/Appboy/appboy-android-sdk/blob/master/droidboy/src/main/java/com/appboy/sample/DroidboyApplication.java
[gifs-58]: https://github.com/Appboy/appboy-android-sdk/blob/master/droidboy/src/main/AndroidManifest.xml
[gifs-59]: https://github.com/Appboy/appboy-android-sdk#version-support
[gifs-60]: http://developer.android.com/guide/topics/manifest/application-element.html#nm
[gifs-61]: https://github.com/Appboy/appboy-android-sdk/tree/master/droidboy
[gifs-64]: https://github.com/Appboy/appboy-android-sdk/tree/master/droidboy
[gifs-65]: https://github.com/Appboy/appboy-android-sdk/tree/master/samples/glide-image-integration
[gifs-66]: https://appboy.github.io/appboy-android-sdk/javadocs/com/appboy/Appboy.html#setAppboyImageLoader-com.appboy.IAppboyImageLoader-
[gifs-67]: https://bumptech.github.io/glide/
[gifs-68]: https://appboy.github.io/appboy-android-sdk/javadocs/com/appboy/IAppboyImageLoader.html#getBitmapFromUrl-android.content.Context-java.lang.String-com.appboy.enums.AppboyViewBounds-
[gifs-69]: https://appboy.github.io/appboy-android-sdk/javadocs/com/appboy/IAppboyImageLoader.html#renderUrlIntoView-android.content.Context-java.lang.String-android.widget.ImageView-com.appboy.enums.AppboyViewBounds-
[gifs-70]: https://appboy.github.io/appboy-android-sdk/javadocs/com/appboy/IAppboyImageLoader.html#setOffline-boolean-
