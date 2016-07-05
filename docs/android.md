# Android

Android Architecture [^1]

<img src="http://www.developer.com/imagesvr_ce/1638/CloudAndroid0_r1_c1.jpg" alt="" />

### Folder Structure

A well-structured app [^2]

* Make it easy and efficient to get things done.
* Keep related things together, and unrelated things seperate.
* Actively manages complexity through consistent navigation

### Android Development Patterns

* [Multiple Tasks with Concurrent Documents (Android Development Patterns)](https://www.youtube.com/watch?v=4Y3JMvbcxQE)

### Resources

* [(Doc) Android Developer Training](http://developer.android.com/training/index.html)

### Courses

* (★★★★★) [Programming Mobile Applications for Android Handheld Systems: Part 1](https://www.coursera.org/learn/android-programming/home/assignments)

[^1]: http://www.developer.com/ws/android/programming/guide-to-porting-android-applications-to-windows-8.html
[^2]: [Google I/O 2013 - Structure in Android App Design](https://www.youtube.com/watch?v=XpqyiBR0lJ4)

# Android: Layout

[#37 Android Layout Weight - Android Tutorial for Beginners [HD 1080p]](https://www.youtube.com/watch?v=rMksRBvYG28)

# Android: Saving Data

http://ormlite.com/sqlite_java_android_orm.shtml

Use `ormlite` (for ORM) and `sqliteassethelper` (for shipping with a database [^1])

Step 1: Add library to `grandle`

[code]
dependencies {
    compile 'com.j256.ormlite:ormlite-core:4.47'
    compile 'com.j256.ormlite:ormlite-android:4.47'

    compile 'com.readystatesoftware.sqliteasset:sqliteassethelper:2.0.1'
}
[/code]

Step 2: Create sqlite database

1. Create new folders `assets/databases` in your `src/main` folder
2. Create your database and save to `databases` folder

Step 3: Create pojo in `YourPojo.java`

Step 4: Create `OrmDbHelper.java`

Step 5: Connect to your database in `MainActivity.java`

[Sample project: Life](https://github.com/rain1024/Life/tree/0.2)

[^1]: [How to ship an Android application with a database?](http://stackoverflow.com/questions/513084/how-to-ship-an-android-application-with-a-database)

# Android: Sharing

https://developers.facebook.com/quickstarts/573926429447471/?platform=android

# Android: View

### Button

Floating Button

[https://github.com/makovkastar/FloatingActionButton](https://github.com/makovkastar/FloatingActionButton)

### Tools

[App Icon Generator](https://romannurik.github.io/AndroidAssetStudio/icons-launcher.html#foreground.type=text&foreground.space.trim=0&foreground.space.pad=0.05&foreground.text.text=L&foreground.text.font=Roboto&foreColor=fff%2C0&crop=0&backgroundShape=square&backColor=f44336%2C100&effects=score)



