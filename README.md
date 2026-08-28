# Ex.No:2B To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

1. Start the application.
2. Create a new Android project in Android Studio.
3. Design the first screen with:
4. One EditText to accept a number.
5. One Button labeled FACTORIAL.
6. Create a second activity to display the result.
7. In MainActivity, read the number entered by the user.
8. Create an Explicit Intent to open SecondActivity.
9. Pass the entered number to SecondActivity using putExtra().
10. In SecondActivity, receive the number using getIntent().getStringExtra().
11. Convert the received value into an integer.
12. Calculate the factorial of the number using a for loop.
13. Display the factorial result in a TextView.
14. Run the application.
15. Verify that the second screen displays the correct factorial.
16. Stop the application.



## PROGRAM:
```
Program to print the text “ExplicitIntent”.
Developed by: KAVIBHARATHI K
Registeration Number : 212224220045
```
## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="40dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Factorial Calculator"
        android:textSize="24sp"
        android:textStyle="bold"
        android:layout_marginBottom="25dp" />

    <EditText
        android:id="@+id/editNumber"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter a number"
        android:inputType="number"
        android:layout_marginBottom="20dp" />

    <Button
        android:id="@+id/btnCalculate"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Calculate" />

</LinearLayout>
```
## MainActivity.java
```
package com.aishwarya.explicitintent;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        EditText editNumber = findViewById(R.id.editNumber);
        Button btnCalculate = findViewById(R.id.btnCalculate);

        btnCalculate.setOnClickListener(view -> {

            String input = editNumber.getText().toString().trim();

            if (input.isEmpty()) {
                Toast.makeText(this, "Please enter a number", Toast.LENGTH_SHORT).show();
                return;
            }

            int number = Integer.parseInt(input);

            long factorial = 1;

            for (int i = 1; i <= number; i++) {
                factorial = factorial * i;
            }

            Intent intent = new Intent(MainActivity.this, SecondActivity.class);

            intent.putExtra("number", number);
            intent.putExtra("factorial", factorial);

            startActivity(intent);
        });
    }
}
```
## activity_second.xml
```
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="40dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Result"
        android:textSize="20sp"
        android:layout_marginBottom="10dp" />

    <TextView
        android:id="@+id/textResult"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Factorial Result"
        android:textSize="24sp"
        android:textStyle="bold"
        android:gravity="center"
        android:layout_marginBottom="25dp" />

    <Button
        android:id="@+id/btnBack"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Back to Home" />

</LinearLayout>
```
## SecondActivity.java
```
package com.aishwarya.explicitintent;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.widget.Button;
import android.widget.TextView;

public class SecondActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        TextView textResult = findViewById(R.id.textResult);
        Button btnBack = findViewById(R.id.btnBack);

        // Receive data from MainActivity
        int number = getIntent().getIntExtra("number", 0);
        long factorial = getIntent().getLongExtra("factorial", 1);

        // Display factorial result
        textResult.setText("Factorial of " + number + " is: " + factorial);

        // Return to first screen
        btnBack.setOnClickListener(view -> finish());
    }
}
```
## OUTPUT
<img width="1917" height="1198" alt="Screenshot 2026-07-30 090909" src="https://github.com/user-attachments/assets/5c41ebc5-9f31-45d4-8eed-f67204791ac1" />
<img width="1917" height="1198" alt="Screenshot 2026-07-30 091732" src="https://github.com/user-attachments/assets/61568c87-1ddc-4063-8f42-811c124141f5" />

## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


