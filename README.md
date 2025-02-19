# Android SliderView Sample App

<img src="banner/AndroidSliderViews%20Banner%202.jpg" width="100%" />

This is a sample Android project to demonstrate how to use <a href="https://github.com/sung2063/AndroidSliderViewsLibrary">Android Slider Views library</a> created by sung2063.<br/>
The sample app includes using of <b>Horizontal and Vertical CarouselViews</b> and <b>SlideshowView</b>.

## 💖 Sponsor

Android Slider Views library updates regularly. Your valuable sponsorship helps me contributing more features and maintaining the library. Support me for building more interesting projects! 💜

<div>
<a href="https://github.com/sponsors/sung2063"><img src="https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=#white" style="float: left" /></a>
<a href="https://www.paypal.com/donate?business=sunghyunb1991%40gmail.com&item_name=GitHub+Open+Source+Project+Sponsorship&currency_code=USD"><img src="https://img.shields.io/badge/PayPal-00457C?style=for-the-badge&logo=paypal&logoColor=white" /></a>
</div>
  
 ## 🎬 GIF Images

<center>
  <table>
    <tr style="border-collapse: collapse;">
      <td><img src="gifs/horizontal_carousel.gif" width="250" /></td>
      <td><img src="gifs/horizontal_carousel%232.gif" width="250" /></td>
      <td><img src="gifs/vertical_carousel.gif" width="250" /></td>
    </tr>
    <tr>
      <td>Horizontal Carousel</td>
      <td>Carousel w/ Custom Indicator</td>
      <td>Vertical Carousel</td>
    </tr>ttt
   </table>
 </center>


## 🔢 Instruction

1) Clone the AndroidSliderViewSample repository to your local computer
2) Open the project on Android Studio
3) Run the program either on Android virtual device or your Android device 

## 📖 How To Use Slider Views

<b>1. Setup your Android project setting</b>

Minimum SDK Version: 21 or greater (Update in your <i>app level</i> `build.gradle`)<br/>
Supported Programming Language: Java
Add following snippet code in your <i>project level</i> `build.gradle`.
```gradle
android {
    compileOptions {
        sourceCompatibility JavaVersion.VERSION_1_8
        targetCompatibility JavaVersion.VERSION_1_8
    }
}
```

<b>2. Add required library</b>

First, include following jitpack url inside maven block in your <i>project level</i> `build.gradle`.
```gradle
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```

Next, add the SliderViews and required libraries in <i>app level</i> `build.gradle` and sync the gradle file. 
```gradle
implementation 'com.github.sung2063:AndroidSliderViewsLibrary:1.7'
implementation 'com.google.android.material:material:1.1.0'
```

Now you are ready to use SliderView Library. You can start creating CarouselView and SlideshowView.<br/>

<hr/>

### <i>CarouselView</i>

CarouselView can be used for your application intro and show multiple images or videos in one layout with scrolling. CarouselView by Sliders library supports both horizontal and vertical scrolls.

First, create a CarouselView in your xml file.
```xml
<com.sung2063.sliders.carousel.CarouselView
        android:id="@+id/carousel_view"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:showIndicator="true"
        app:scrollDirection="horizontal"
        app:showSlideNumber="true" />
```
Set `scrollDirection` attribution to `horizontal` for creating horizontal carousel and `vertical` for vertical carousel.

In your `onCreate()` method in Activity, create your own custom layouts, add layouts to List<ViewGroup>, and start the carousel. You can add up to 10 layouts in the CarouselView. 

From <i>version 1.6</i>, you can also include sub-title of each slides. In that case, you need to make DescriptiveSlideModel objects that holds slide layout and sub-title and add to ``List<DescriptiveSlideModel>``. Also, do not forget to add <b>app:showSubTitle="true"</b> into your CarouselView in xml. The default is false.

```java
CarouselView carouselView = findViewById(R.id.carousel_view);

// Create your own layouts...
// Create List<ViewGroup> object or List<DescriptiveSlideModel>...
// Add your layouts to list object...

carouselView.setSlideList(layoutList);
carouselView.launch();
```

Your CarouselView is now displayed on your app! 👏<br/>

<hr/>

### <i>SlideshowView</i>

SlideshowView can be used to show the multiple layouts by certain period of time. You can set how much time you want to show each layout to the user.

First, create a SlideshowView in your xml file.
```xml
<com.sung2063.sliders.slideshow.SlideshowView
        android:id="@+id/slideshow_view"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:showIndicator="true"
        app:delayTimePeriod="5"
        app:showSlideNumber="true" />
```

In your `onCreate()` method in Activity, create your own custom layouts, add layouts to List<ViewGroup>, and start the slideshow. You can add up to 10 layouts in the SlideshowView.

From <i>version 1.6</i>, you can also include sub-title of each slides. In that case, you need to make DescriptiveSlideModel objects that holds slide layout and sub-title and add to ``List<DescriptiveSlideModel>``. Also, do not forget to add <b>app:showSubTitle="true"</b> into your SlideshowView in xml. The default is false.

```java
SlideshowView slideshowView = findViewById(R.id.slideshow_view);

// Create your own layouts...
// Create List<ViewGroup> object or List<DescriptiveSlideModel>...
// Add your layouts to list object...

slideshowView.setSlideList(layoutList);
slideshowView.launch();
```

Your SlideshowView is now displayed on your app! 👏<br/>

<hr/>

### Add Callback Action

You can also get callback from slider when it is clicked. On your Activity, create a SliderListener object with implementing own action and pass this object to the view by calling `setSliderListener`. Here is the snippet code how to implement the callback: 

```java
// Create a callback interface
SliderListener sliderListener = position -> {
     // TODO: Do something when slide is clicked
};

// Set callback object to the View
carouselView.setSliderListener(sliderListener);    // If you are using Carousel
slideshowView.setSliderListener(sliderListener);   // If you are using Slideshow
```

<br/>

## 🎨 Attributions

Here are available attributions you can use to modify your slider views.

### CarouselView

<center>
  <table>
    <tr>
      <th>Attribution</th>
      <th>Value</th>
      <th>Description</th>
    </tr>
    <tr>
      <td rowspan="2">scrollDirection</td>
      <td>horizontal</td>
      <td>Display the carousel horizontally. <i>Field value is 0.</i></td>
    </tr>
    <tr>
      <td>vertical</td>
      <td>Display the carousel vertically. <i>Field value is 1.</i></td>
    </tr>
    <tr>
      <td>showIndicator</td>
      <td>boolean</td>
      <td>Show the dot indicator on the slide if the value true, otherwise do not show.</td>
    </tr>
    <tr>
      <td>indicatorScale</td>
      <td>float</td>
      <td>Used for resize the indicator scale from 0.5 - 1.5.</td>
    </tr>
    <tr>
      <td>indicatorSelectedIcon</td>
      <td>integer</td>
      <td>Selected indicator icon drawable id.</td>
    </tr>
    <tr>
      <td>indicatorUnselectedIcon</td>
      <td>integer</td>
      <td>Unselected indicator icon drawable id.</td>
    </tr>
    <tr>
      <td>showSlideNumber</td>
      <td>boolean</td>
      <td>Show the slide number text if the value is true, otherwise do not show.</td>
    </tr>
    <tr>
      <td>slideNumberTextSize</td>
      <td>int</td>
      <td>Set the slide number text size in px.</td>
    </tr>
    <tr>
      <td>showSubTitle</td>
      <td>boolean</td>
      <td>Show the sub-title if the value is true, otherwise do not show.</td>
    </tr>
   </table>
 </center>

### SlideshowView

<center>
  <table>
    <tr>
      <th>Attribution</th>
      <th>Value</th>
      <th>Description</th>
    </tr>
    <tr>
      <td>showIndicator</td>
      <td>boolean</td>
      <td>Show the dot indicator on the slide if the value true, otherwise do not show.</td>
    </tr>
    <tr>
      <td>indicatorScale</td>
      <td>float</td>
      <td>Used for resize the indicator scale from 0.5 - 1.5.</td>
    </tr>
    <tr>
      <td>indicatorSelectedIcon</td>
      <td>integer</td>
      <td>Selected indicator icon drawable id.</td>
    </tr>
    <tr>
      <td>indicatorUnselectedIcon</td>
      <td>integer</td>
      <td>Unselected indicator icon drawable id.</td>
    </tr>
    <tr>
      <td>showSlideNumber</td>
      <td>boolean</td>
      <td>Show the slide number text if the value is true, otherwise do not show.</td>
    </tr>
    <tr>
      <td>slideNumberTextSize</td>
      <td>int</td>
      <td>Set the slide number text size in px.</td>
    </tr>
    <tr>
      <td>delayTimePeriod</td>
      <td>int</td>
      <td>The slide delay time in second. Default is 5 seconds.</td>
    </tr>
    <tr>
      <td>showSubTitle</td>
      <td>boolean</td>
      <td>Show the sub-title if the value is true, otherwise do not show.</td>
    </tr>
   </table>
 </center>

 ## 📚 Library
 
 <a href="https://github.com/sung2063/AndroidSliderViewsLibrary">AndroidSlidersView library</a> by @sung2063

 ## 🌟 Contributor
 
 Sung Hyun Back (@sung2063)
