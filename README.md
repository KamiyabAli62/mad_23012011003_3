Android Application: Implicit and Explicit Intent Demonstration

This project is an Android application developed to demonstrate the use of Explicit Intents (navigating to another Activity within the same application) and Implicit Intents (launching system apps such as dialer, email, browser, etc.).
This application is suitable for Mobile Application Development (MAD) practicals and academic submissions.

⸻

Objective

The main objectives of this application are:
	•	To demonstrate the use of Explicit Intent for opening another Activity.
	•	To demonstrate various Implicit Intents, such as:
	•	Opening the dialer
	•	Opening a browser
	•	Sending an email
	•	Sharing text
	•	To implement a simple and interactive user interface.

⸻

Features
	•	Explicit Intent to navigate from MainActivity to SecondActivity.
	•	Implicit Intent examples:
	•	Dial a number
	•	Open a website
	•	Send an email
	•	Share text with other apps
	•	Simple UI containing Buttons and EditText.
	•	Clean and easy-to-understand code structure.


Project Structure

app/
└── src/
    └── main/
        ├── java/com/example/intents/
        │   ├── MainActivity.kt
        │   └── SecondActivity.kt
        ├── res/
        │   ├── layout/activity_main.xml
        │   ├── layout/activity_second.xml
        │   └── values/strings.xml
        └── AndroidManifest.xml
README.md

Source Code

MainActivity.kt

package com.example.intents

import android.content.Intent
import android.net.Uri
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.EditText

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val navigateBtn = findViewById<Button>(R.id.navigateButton)
        val dialBtn = findViewById<Button>(R.id.dialButton)
        val browserBtn = findViewById<Button>(R.id.browserButton)
        val emailBtn = findViewById<Button>(R.id.emailButton)
        val shareBtn = findViewById<Button>(R.id.shareButton)
        val inputField = findViewById<EditText>(R.id.inputField)

        navigateBtn.setOnClickListener {
            val intent = Intent(this, SecondActivity::class.java)
            startActivity(intent)
        }

        dialBtn.setOnClickListener {
            val phone = "1234567890"
            val intent = Intent(Intent.ACTION_DIAL, Uri.parse("tel:$phone"))
            startActivity(intent)
        }

        browserBtn.setOnClickListener {
            val url = "https://www.google.com"
            val intent = Intent(Intent.ACTION_VIEW, Uri.parse(url))
            startActivity(intent)
        }

        emailBtn.setOnClickListener {
            val intent = Intent(Intent.ACTION_SENDTO).apply {
                data = Uri.parse("mailto:")
                putExtra(Intent.EXTRA_EMAIL, arrayOf("example@example.com"))
                putExtra(Intent.EXTRA_SUBJECT, "Test Email")
            }
            startActivity(intent)
        }

        shareBtn.setOnClickListener {
            val text = inputField.text.toString()
            val intent = Intent(Intent.ACTION_SEND)
            intent.type = "text/plain"
            intent.putExtra(Intent.EXTRA_TEXT, text)
            startActivity(Intent.createChooser(intent, "Share via"))
        }
    }
}


SecondActivity.kt

package com.example.intents

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle

class SecondActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_second)
    }
}

activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:padding="20dp">

        <EditText
            android:id="@+id/inputField"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Enter text to share" />

        <Button
            android:id="@+id/navigateButton"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Go to Second Activity"
            android:layout_marginTop="16dp" />

        <Button
            android:id="@+id/dialButton"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Dial Number"
            android:layout_marginTop="16dp" />

        <Button
            android:id="@+id/browserButton"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Open Browser"
            android:layout_marginTop="16dp" />

        <Button
            android:id="@+id/emailButton"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Send Email"
            android:layout_marginTop="16dp" />

        <Button
            android:id="@+id/shareButton"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Share Text"
            android:layout_marginTop="16dp" />

    </LinearLayout>
</ScrollView>

activity_second.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="This is the Second Activity"
        android:textSize="22sp" />

</LinearLayout>


How It Works

Explicit Intent

Used to open SecondActivity directly:

Intent(this, SecondActivity::class.java)

Implicit Intents

Used to request Android system components:
	•	Dialer: ACTION_DIAL
	•	Browser: ACTION_VIEW
	•	Email: ACTION_SENDTO
	•	Share text: ACTION_SEND

Each function demonstrates how Android chooses an appropriate app to handle the request.

⸻

How to Run
	1.	Install Android Studio.
	2.	Clone or download this repository.
	3.	Open the project in Android Studio.
	4.	Run the application on an emulator or device.

⸻

Requirements
	•	Android Studio Flamingo or later
	•	Minimum SDK: 21
	•	Kotlin support enabled

⸻

Purpose

This application is aimed at demonstrating Android Intents clearly and simply, making it suitable for university practicals, assignments, and reference material.
