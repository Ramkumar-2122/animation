# Ex.No: 11 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:
Start the application.
Create a new Android project in Android Studio
Design the user interface with an ImageView and buttons for Move, Blink, Fade, Clockwise, Zoom and Slide animations.
Load an image into the ImageView.
Initialize the required animation objects.
Set click listeners for all animation buttons.
Apply the corresponding animation when a button is clicked.
Display the selected animation effect on the ImageView.
Stop the application.


## PROGRAM:
```
Program to display animation operation”.
Developed by: Ramkumar S
Registeration Number :212223220085
```
MainActivity.java
```
package com.example.gallery;

import android.os.Bundle;
import android.view.View;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    // Declare variables for ImageView and Buttons
    private ImageView imageView;
    private Button blink, rotate, fade, move, slide, zoom, stop;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize ImageView and Buttons using their IDs
        imageView = findViewById(R.id.imageview);
        blink = findViewById(R.id.blink);
        rotate = findViewById(R.id.rotate);
        fade = findViewById(R.id.fade);
        move = findViewById(R.id.move);
        slide = findViewById(R.id.slide);
        zoom = findViewById(R.id.zoom);
        stop = findViewById(R.id.stop);

        // Set up click listeners for each button to start corresponding animations
        createAnimation(blink, R.anim.blink);
        createAnimation(rotate, R.anim.rotate);
        createAnimation(fade, R.anim.fade);
        createAnimation(move, R.anim.move);
        createAnimation(slide, R.anim.slide);
        createAnimation(zoom, R.anim.zoom);

        // Set up click listener for stop button to clear any ongoing animation
        stop.setOnClickListener(v -> imageView.clearAnimation());
    }

    // Function to set up an animation for a given view and animation resource ID
    private void createAnimation(View view, int animResId) {
        view.setOnClickListener(v -> {
            // Load the animation from the specified resource ID
            Animation animation = AnimationUtils.loadAnimation(MainActivity.this, animResId);
            // Start the animation on the ImageView
            imageView.startAnimation(animation);
        });
    }
}

```
activity_main.xml
```
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center_horizontal"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageview"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_marginTop="40dp"
        android:contentDescription="@string/app_name"
        android:src="@drawable/gfg_logo" />

    <LinearLayout
        android:id="@+id/linear1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="30dp"
        android:orientation="horizontal"
        android:weightSum="3">

        <!--To start the blink animation of the image-->
        <Button
            android:id="@+id/blink"
            style="@style/TextAppearance.MaterialComponents.Button"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_margin="10dp"
            android:layout_weight="1"
            android:padding="3dp"
            android:text="@string/blink"
            android:textColor="@color/white" />

        <!--To start the rotate animation of the image-->
        <Button
            android:id="@+id/rotate"
            style="@style/TextAppearance.MaterialComponents.Button"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_margin="10dp"
            android:layout_weight="1"
            android:padding="3dp"
            android:text="@string/clockwise"
            android:textColor="@color/white" />

        <!--To start the fading animation of the image-->
        <Button
            android:id="@+id/fade"
            style="@style/TextAppearance.MaterialComponents.Button"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_margin="10dp"
            android:layout_weight="1"
            android:padding="3dp"
            android:text="@string/fade"
            android:textColor="@color/white" />

    </LinearLayout>

    <LinearLayout
        android:id="@+id/linear2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="30dp"
        android:orientation="horizontal"
        android:weightSum="3">

        <!--To start the move animation of the image-->
        <Button
            android:id="@+id/move"
            style="@style/TextAppearance.MaterialComponents.Button"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_margin="10dp"
            android:layout_weight="1"
            android:padding="3dp"
            android:text="@string/move"
            android:textColor="@color/white" />

        <!--To start the slide animation of the image-->
        <Button
            android:id="@+id/slide"
            style="@style/TextAppearance.MaterialComponents.Button"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_margin="10dp"
            android:layout_weight="1"
            android:padding="3dp"
            android:text="@string/slide"
            android:textColor="@color/white" />

        <!--To start the zoom animation of the image-->
        <Button
            android:id="@+id/zoom"
            style="@style/TextAppearance.MaterialComponents.Button"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_margin="10dp"
            android:layout_weight="1"
            android:padding="3dp"
            android:text="@string/zoom"
            android:textColor="@color/white" />

    </LinearLayout>

    <!--To stop the animation of the image-->
    <Button
        android:id="@+id/stop"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="30dp"
        android:layout_marginTop="30dp"
        android:layout_marginRight="30dp"
        android:text="@string/stop_animation" />

</LinearLayout>
```
blink.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <alpha android:fromAlpha="0.0"
        android:toAlpha="1.0"
        android:interpolator="@android:anim/accelerate_interpolator"
        android:duration="500"
        android:repeatMode="reverse"
        android:repeatCount="infinite"/>
</set>
```
fade.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/accelerate_interpolator">

    <!-- duration is the time for which animation will work-->
    <alpha
        android:duration="1000"
        android:fromAlpha="0"
        android:toAlpha="1" />

    <alpha
        android:duration="1000"
        android:fromAlpha="1"
        android:startOffset="2000"
        android:toAlpha="0" />

</set>
```
move.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/linear_interpolator"
    android:fillAfter="true">

    <translate
        android:fromXDelta="0%p"
        android:toXDelta="75%p"
        android:duration="700" />
</set>
```
rotate.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android">
    <rotate
        android:duration="6000"
        android:fromDegrees="0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:toDegrees="360" />

    <rotate
        android:duration="6000"
        android:fromDegrees="360"
        android:pivotX="50%"
        android:pivotY="50%"
        android:startOffset="5000"
        android:toDegrees="0" />

</set>
```
slide.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true" >
    <scale
        android:duration="500"
        android:fromXScale="1.0"
        android:fromYScale="1.0"
        android:interpolator="@android:anim/linear_interpolator"
        android:toXScale="1.0"
        android:toYScale="0.0" />
</set>
```
zoom.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true" >

    <scale
        android:interpolator="@android:anim/linear_interpolator"
        android:duration = "1000"
        android:fromXScale = "1"
        android:fromYScale = "1"
        android:pivotX = "50%"
        android:pivotY = "50%"
        android:toXScale = "2"
        android:toYScale = "2"/>
</set>
```

## OUTPUT

<img width="1917" height="1095" alt="Screenshot 2026-11-18 104407" src="https://github.com/user-attachments/assets/7740604c-7e5c-4e6e-a4bd-2283a8f85f6b" />
<img width="1851" height="1198" alt="Screenshot 2026-11-18 104417" src="https://github.com/user-attachments/assets/9f884f18-88e4-4c69-ac39-43e1de3fff05" />
<img width="1886" height="1160" alt="Screenshot 2026-11-18 104430" src="https://github.com/user-attachments/assets/54ec179a-7cdc-4a81-889a-182324b6d48c" />
<img width="1917" height="1106" alt="Screenshot 2026-11-18 104458" src="https://github.com/user-attachments/assets/9586cf3c-6381-4064-a937-54b8b3802790" />
<img width="1907" height="1173" alt="Screenshot 2026-11-18 104502" src="https://github.com/user-attachments/assets/b6b53f41-62ee-44bf-962c-b4777dc0c4fb" />
<img width="1917" height="1085" alt="Screenshot 2026-11-18 104528" src="https://github.com/user-attachments/assets/59e384c0-4444-41c1-8a3c-a15da37fc38c" />




## RESULT
Thus an application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio is developed and executed successfully.



