# Ex.No:6 Design an android application Send SMS using Intent.


## AIM:

To create and design an android application Send SMS using Intent using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as smsintent and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Send SMS and Display details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
~~~
Program to create and design an android application Send SMS using Intent.
Developed by: DIVYASHREE B S
Registeration Number : 212221040044
~~~

## Android Manifest File:
~~~
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:tools="http://schemas.android.com/tools">
<uses-permission android:name="android.permission.SEND_SMS" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />

<application
    android:allowBackup="true"
    android:dataExtractionRules="@xml/data_extraction_rules"
    android:fullBackupContent="@xml/backup_rules"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:supportsRtl="true"
    android:theme="@style/Theme.Smsintent"
    tools:targetApi="31">
    <activity
        android:name=".MainActivity"
        android:exported="true">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />

            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
    </activity>
</application>

</manifest>
~~~

## Activity_xml File:
~~~
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".MainActivity">

<EditText
    android:id="@+id/number"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginTop="192dp"
    android:ems="10"
    android:inputType="textPersonName"
    android:text=""
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.497"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent" />

<EditText
    android:id="@+id/text"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginStart="88dp"
    android:layout_marginTop="140dp"
    android:ems="10"
    android:inputType="textPersonName"
    android:text=""
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/number" />

<Button
    android:id="@+id/send"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginTop="56dp"
    android:backgroundTint="#4CAF50"
    android:text="SEND"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.498"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/text" />

<TextView
    android:id="@+id/textView"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginStart="16dp"
    android:layout_marginBottom="23dp"
    android:text="Enter Number:"
    android:textColor="#F44336"
    android:textSize="36dp"
    app:layout_constraintBottom_toTopOf="@+id/number"
    app:layout_constraintStart_toStartOf="parent" />

<TextView
    android:id="@+id/textView2"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginStart="16dp"
    android:layout_marginTop="46dp"
    android:text="Enter Message:"
    android:textColor="#673AB7"
    android:textSize="36dp"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/number" />
</androidx.constraintlayout.widget.ConstraintLayout>
~~~

## MainActivity.java File:
~~~
package com.example.smsintent;

import androidx.appcompat.app.AppCompatActivity;

import android.Manifest;
import android.annotation.SuppressLint;
import android.content.pm.PackageManager;
import android.os.Build;
import android.os.Bundle;
import android.telephony.SmsManager;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
private EditText number,message;
private Button send;
@SuppressLint("MissingInflatedId")
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    number = findViewById(R.id.number);
    message = findViewById(R.id.text);
    send = findViewById(R.id.send);

    send.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View view) {
            if (Build.VERSION.SDK_INT>=Build.VERSION_CODES.M){
                if (checkSelfPermission(Manifest.permission.SEND_SMS) == PackageManager.PERMISSION_GRANTED){
                    sendSMS();
                }else {
                    requestPermissions(new String[]{Manifest.permission.SEND_SMS},1);
                }
            }
        }
    });
}
private void sendSMS(){
    String phoneNo = number.getText().toString().trim();
    String SMS = message.getText().toString().trim();

    try{
        SmsManager smsManager = SmsManager.getDefault();
        smsManager.sendTextMessage(phoneNo,null,SMS,null,null);
        Toast.makeText(this,"Message is sent",Toast.LENGTH_SHORT).show();
    } catch (Exception e){
        e.printStackTrace();
        Toast.makeText(this,"Failed to send message",Toast.LENGTH_SHORT).show();
    }
}
}
~~~

## OUTPUT

![image](https://github.com/divvisha/MAD-EXP-6/assets/127508123/dbdd687e-f5d1-49ea-9595-da29eb1e34e3)

![image](https://github.com/divvisha/MAD-EXP-6/assets/127508123/a2a1eb36-f942-46b6-9a05-67dee8eb1ad8)

![image](https://github.com/divvisha/MAD-EXP-6/assets/127508123/4c770e23-03d1-4c82-b588-8aae73602060)

![image](https://github.com/divvisha/MAD-EXP-6/assets/127508123/ef1a7a08-28b3-417d-a99b-607f733f1647)

![image](https://github.com/divvisha/MAD-EXP-6/assets/127508123/8e31cb77-17f7-4f6e-938e-ac1bf88d3ad5)

![image](https://github.com/divvisha/MAD-EXP-6/assets/127508123/f1e8f511-7754-4175-8c93-907267fe523a)

![image](https://github.com/divvisha/MAD-EXP-6/assets/127508123/0b366a73-c21c-4013-867e-936b89b3d880)

## RESULT
Thus a Simple Android Application create and design an android application Send SMS using Intent using Android Studio is developed and executed successfully.
