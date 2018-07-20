# Kotlin Neshan Maps Sample
## A Kotlin sample application based on Neshan Maps Android SDK.

### Getting started with Neshan Maps SDK


#### 0) Get neshan.licence file  
To create a licence file you need :  
- Package Name : The packag name of the application you want to use SDK in.  
- SH1 fingerprint : SH1 fingerprints from your required apk sign keys. (Release key, debug key, etc)  

[REGISTER](https://developer.neshan.org)


#### 1) Installing SDK

Add maven repository to your project level `build.gradle`

```gradle
repositories {
    //add maven repo here
    maven { url "https://dl.bintray.com/neshan/neshan-android-sdk" }
}
```

Add to `build.gradle` module app

```gradle
dependencies {
    //Neshan sdk library
    implementation 'neshan-android-sdk:mobile-sdk:0.9.1'
}
```

#### 2) Define INTERNET permission for the app in your AndroidManifest.xml

```xml
<uses-permission android:name="android.permission.INTERNET"/>
```

#### 3) Create a `raw` Android resource directory and put your `neshan.licence` file there.

#### 4) Define your application layout

Define main layout as res/layout/activity_main.xml, so that it contains `org.neshan.ui.MapView` element:

```xml
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

<org.rajman.ui.MapView
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/map"/>

</android.support.constraint.ConstraintLayout>
```

#### 5) In your app code connect to the MapView object and add a basemap layer

Kotlin Code :
```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        //set map focus position
        map.setFocalPointPosition(LngLat(53.529929, 35.164676), 0f)
        //add basemap layer
        map.layers.add(NeshanServices.createBaseMap(NeshanMapStyle.STANDARD_DAY))
    }
}
```

Java Code :
```java 
public class MainActivity extends AppCompatActivity {
    private MapView map;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        map = findViewById(R.id.map);
        //set map focus position
        LngLat focalPoint = new LngLat(53.529929, 35.164676);
        map.setFocalPointPosition(focalPoint, 0f);
        //add basemap layer
        map.getLayers().add(NeshanServices.createBaseMap(NeshanMapStyle.STANDARD_DAY));
    }
}
```

#### 6) Run the Android app with smile :)




[logo]: https://github.com/NeshanMaps/kotlin-neshan-maps-sample/blob/master/app/src/main/res/drawable-xxxhdpi/ic_neshan_logo.png

