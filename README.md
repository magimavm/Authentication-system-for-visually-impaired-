# Authentication-system-for-visually-impaired-
Fingerprint Authentication
Main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:id="@+id/main_layout"
android:visibility="gone"
tools:context=".MainActivity">

<TextView
android:layout_width="167dp"
android:layout_height="56dp"
android:text="Login"
android:textColor="@color/black"
android:textSize="50dp"
app:layout_constraintBottom_toBottomOf="parent"
app:layout_constraintEnd_toEndOf="parent"
app:layout_constraintStart_toStartOf="parent"
app:layout_constraintTop_toTopOf="parent"
app:layout_constraintVertical_bias="0.477" />

</androidx.constraintlayout.widget.ConstraintLayout>
Java
public class MainActivity extends AppCompatActivity {

private static final int REQUEST_CODE =10101 ;
BiometricPrompt biometricPrompt;
BiometricPrompt promptInfo;
ConstraintLayout mMain_Layout;
@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
mMain_Layout.findViewById(R.id.main_layout);

BiometricManager biometricManager = this.(BiometricManager);
switch (biometricManager.canAuthenticate(BIOMETRIC_STRONG | DEVICE_CREDENTIAL)) {
case BIOMETRIC_SUCCESS:
                Log.d("MY_APP_TAG", "App can authenticate using biometrics.");
break;
case BIOMETRIC_ERROR_NO_HARDWARE:
                Log.e("MY_APP_TAG", "No biometric features available on this device.");
break;
case BIOMETRIC_ERROR_HW_UNAVAILABLE:
                Log.e("MY_APP_TAG", "Biometric features are currently unavailable.");
break;
case BIOMETRIC_ERROR_NONE_ENROLLED:
// Prompts the user to create credentials that your app accepts.
final Intent enrollIntent = new Intent(Settings.ACTION_BIOMETRIC_ENROLL);
                enrollIntent.putExtra(Settings.EXTRA_BIOMETRIC_AUTHENTICATORS_ALLOWED,
                        BIOMETRIC_STRONG | DEVICE_CREDENTIAL);
                startActivityForResult(enrollIntent, REQUEST_CODE);
break;
        }
    }
}
Login and signup
Main activity.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
xmlns:card_view="http://schemas.android.com/apk/res-auto"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:orientation="vertical"
android:gravity="center"
android:background="@drawable/pagebkg"
tools:context=".MainActivity">

<androidx.cardview.widget.CardView
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_margin="30dp"
app:cardCornerRadius="30dp"
app:cardElevation="20dp"
android:background="@drawable/customedittext">
<LinearLayout
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:orientation="vertical"
android:layout_gravity="center_horizontal"
android:padding="24dp">
<TextView
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:text="Login"
android:id="@+id/loginText"
android:textSize="36sp"
android:textAlignment="center"
android:textStyle="bold"
android:textColor="@color/purple"/>
<EditText
android:layout_width="match_parent"
android:layout_height="50dp"
android:id="@+id/username"
android:background="@drawable/customedittext"
android:drawableLeft="@drawable/baseline_person_24"
android:drawablePadding="8dp"
android:hint="Username"
android:padding="8dp"
android:textColor="@color/black"
android:textColorHighlight="@color/cardview_dark_background"
android:layout_marginTop="40dp"/>
<EditText
android:layout_width="match_parent"
android:layout_height="50dp"
android:id="@+id/password"
android:background="@drawable/customedittext"
android:drawableLeft="@drawable/baseline_lock_24"
android:drawablePadding="8dp"
android:hint="Password"
android:padding="8dp"
android:inputType="textPassword"
android:textColor="@color/black"
android:textColorHighlight="@color/cardview_dark_background"
android:layout_marginTop="20dp"/>

<TextView
android:id="@+id/textView2"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_marginTop="20dp"
android:background="#8682f7"
android:text="Forgot Password?"
android:textColor="#fff"
android:textStyle="bold" />

<Button
android:id="@+id/loginButton"
android:layout_width="match_parent"
android:layout_height="60dp"
android:layout_marginTop="30dp"
android:backgroundTint="@color/purple"
android:text="Login"
android:textSize="18sp"
app:cornerRadius="20dp" />
</LinearLayout>
</androidx.cardview.widget.CardView>

<TextView
android:id="@+id/signupText"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_marginBottom="10dp"
android:padding="8dp"

android:text="Not yet registered? SignUp Now"
android:textAlignment="center"
android:textColor="#000"
android:textSize="14sp"
android:textStyle="bold" />
</LinearLayout>
Register .xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
xmlns:card_view="http://schemas.android.com/apk/res-auto"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:orientation="vertical"
android:gravity="center"
android:background="@drawable/pagebkg"
tools:context=".MainActivity">

<androidx.cardview.widget.CardView
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_margin="30dp"
app:cardCornerRadius="30dp"
app:cardElevation="20dp"
android:background="@drawable/customedittext">
<LinearLayout
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:orientation="vertical"
android:layout_gravity="center_horizontal"
android:padding="24dp">
<TextView
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:text="Register"
android:id="@+id/loginText"
android:textSize="36sp"
android:textAlignment="center"
android:textStyle="bold"
android:textColor="@color/purple"/>
<EditText
android:layout_width="match_parent"
android:layout_height="50dp"
android:id="@+id/username"
android:background="@drawable/customedittext"
android:drawableLeft="@drawable/baseline_person_24"
android:drawablePadding="8dp"
android:hint="Username"
android:padding="8dp"
android:textColor="@color/black"
android:textColorHighlight="@color/cardview_dark_background"
android:layout_marginTop="40dp"/>
<EditText
android:layout_width="match_parent"
android:layout_height="50dp"
android:id="@+id/password"
android:background="@drawable/customedittext"
android:drawableLeft="@drawable/baseline_lock_24"
android:drawablePadding="8dp"
android:hint="Password"
android:padding="8dp"
android:inputType="textPassword"
android:textColor="@color/black"
android:textColorHighlight="@color/cardview_dark_background"
android:layout_marginTop="20dp"/>
<EditText
android:layout_width="match_parent"
android:layout_height="50dp"
android:id="@+id/password1"
android:background="@drawable/customedittext"
android:drawableLeft="@drawable/baseline_lock_24"
android:drawablePadding="8dp"
android:hint="Conform Password"
android:padding="8dp"
android:inputType="textPassword"
android:textColor="@color/black"
android:textColorHighlight="@color/cardview_dark_background"
android:layout_marginTop="20dp"/>


<Button
android:id="@+id/RegisterButton"
android:layout_width="match_parent"
android:layout_height="60dp"
android:layout_marginTop="30dp"
android:backgroundTint="@color/purple"
android:text="Register account"
android:textSize="18sp"
app:cornerRadius="20dp" />
</LinearLayout>
</androidx.cardview.widget.CardView>

<TextView
android:id="@+id/signupText"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_marginBottom="10dp"
android:padding="8dp"

android:text="Aldready have an account?"
android:textAlignment="center"
android:textColor="#000"
android:textSize="24sp"
android:textStyle="bold" />

<Button
android:id="@+id/loginButton1"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_marginTop="30dp"
android:backgroundTint="@color/purple"
android:text="Login"
android:textSize="18sp"
app:cornerRadius="20dp" />

</LinearLayout>

Main activity.java
package com.example.myloginapp;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

Button b1,b2;
TextView t1,t2;
EditText e1,e2;


@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

b1=(Button)findViewById(R.id.loginButton);
t2=(TextView)findViewById(R.id.textView2);
e1=(EditText)findViewById(R.id.username);
e2=(EditText)findViewById(R.id.password);
b1.setOnClickListener(new View.OnClickListener() {
@Override
public void onClick(View view) {
Intent i =new Intent(getApplicationContext(),RegisterActivity.class);
                startActivity(i);
Toast.makeText(getApplicationContext(),"Login Successful",Toast.LENGTH_LONG).show();
            }
        });
    }
}

register acitivity.java
package com.example.myloginapp;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

public class RegisterActivity extends AppCompatActivity {

Button bk1;


@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_register);

bk1=(Button)findViewById(R.id.loginButton1);
bk1.setOnClickListener(new View.OnClickListener() {
@Override
public void onClick(View view) {
Intent intent =new Intent(getApplicationContext(),MainActivity.class);
                startActivity(intent);
            }
        });


    }
}
voice
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:orientation="vertical"
tools:context=".MainActivity">
<!--this button will convert voice to text-->
<Button
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:text="Convert voice to text"
android:id="@+id/btn_convert"/>

<!--Textview will show the text message which come from your voice message-->
<TextView
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:id="@+id/tv_message"/>


</LinearLayout>

Java
package com.example.voice;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.speech.RecognizerIntent;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

import java.util.ArrayList;
import java.util.Locale;

public class MainActivity extends AppCompatActivity {
Button btn_convert;
TextView tv_message;


@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
btn_convert = findViewById(R.id.btn_convert);
tv_message = findViewById(R.id.tv_message);
btn_convert.setOnClickListener(new View.OnClickListener() {
@Override
public void onClick(View v) {
Intent intent = new Intent(RecognizerIntent.ACTION_RECOGNIZE_SPEECH);
intent.putExtra(RecognizerIntent.EXTRA_LANGUAGE_MODEL,
RecognizerIntent.LANGUAGE_MODEL_FREE_FORM);
intent.putExtra(RecognizerIntent.EXTRA_LANGUAGE,
Locale.getDefault());
intent.putExtra(RecognizerIntent.EXTRA_PROMPT,
"Speak Now....");
                startActivityForResult(intent, 1);

            }
        });
//to recieve the output of startActivity for result Intent
}

@Override
protected void onActivityResult(int requestCode,int resultCode, Intent data) {
super.onActivityResult(requestCode,resultCode, data);
if(requestCode==1 && resultCode==RESULT_OK && data !=null)
        {
ArrayList<String>arrayList=data.getStringArrayListExtra(RecognizerIntent.EXTRA_RESULTS);
//set the message into textview
tv_message.setText(arrayList.get(0).toString());

        }
    }
}
morse code
activity_main.xml:
=======================================================================


<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/activity_main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="com.ssaurel.mc.MainActivity">

    <EditText
        android:id="@+id/txt"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="70dp"
        android:layout_centerHorizontal="true"/>

    <LinearLayout
        android:id="@+id/ctrls"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:layout_below="@id/txt"
        android:layout_marginTop="30dp"
        android:orientation="horizontal">

        <Button
            android:id="@+id/toAlphaBtn"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="To Alpha"
            android:layout_marginRight="15dp"/>

        <Button
            android:id="@+id/toMorseBtn"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="To Morse"/>

    </LinearLayout>

    <TextView
        android:id="@+id/result"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:textSize="18sp"
        android:layout_below="@id/ctrls"
        android:layout_marginTop="50dp"
        />

</RelativeLayout>

Java
package com.ssaurel.mc;
import java.util.HashMap;
public class MorseCode {
    static String[] ALPHA = { "a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r",
            "s", "t", "u", "v", "w", "x", "y", "z", "1", "2", "3", "4", "5", "6", "7", "8", "9", "0"};
    static String[] MORSE = { ".-", "-...", "-.-.", "-..", ".", "..-.", "--.", "....", "..", ".---", "-.-", ".-..",
            "--", "-.", "---", ".--.", "--.-", ".-.", "...", "-", "..-", "...-", ".--", "-..-", "-.--", "--..", ".----",
            "..---", "...--", "....-", ".....", "-....", "--...", "---..", "----.", "-----"};
    public static HashMap<String, String> ALPHA_TO_MORSE = new HashMap<>();
    public static HashMap<String, String> MORSE_TO_ALPHA = new HashMap<>();
    static {
        for (int i = 0; i < ALPHA.length  &&  i < MORSE.length; i++) {
            ALPHA_TO_MORSE.put(ALPHA[i], MORSE[i]);
            MORSE_TO_ALPHA.put(MORSE[i], ALPHA[i]);
        }
    }

    public static String morseToAlpha(String morseCode) {
        StringBuilder builder = new StringBuilder();
        String[] words = morseCode.trim().split("   ");

        for (String word : words) {
            for (String letter : word.split(" ")) {
                String alpha = MORSE_TO_ALPHA.get(letter);
                builder.append(alpha);
            }

            builder.append(" ");
        }

        return builder.toString().toUpperCase();
    }

    public static String alphaToMorse(String englishCode) {
        StringBuilder builder = new StringBuilder();
        String[] words = englishCode.trim().split(" ");

        for (String word : words) {
            for (int i = 0; i < word.length(); i++) {
                String morse = ALPHA_TO_MORSE.get(word.substring(i, i + 1).toLowerCase());
                builder.append(morse).append(" ");
            }

            builder.append("  ");
        }

        return builder.toString();
    }

}
OCR
Xml
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout
android:id="@+id/activity_main"
xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context="com.truiton.mobile.vision.ocr.MainActivity">
<ImageView
android:id="@+id/imageView"
android:layout_width="200dp"
android:layout_height="200dp"
android:layout_marginTop="16dp"
app:layout_constraintLeft_toLeftOf="parent"
app:layout_constraintRight_toRightOf="parent"
app:layout_constraintTop_toTopOf="parent"
app:srcCompat="@mipmap/truiton"
tools:layout_constraintLeft_creator="1"
tools:layout_constraintRight_creator="1"/>
<Button
android:id="@+id/button"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_marginBottom="8dp"
android:text="Scan Text"
app:layout_constraintBottom_toBottomOf="parent"
app:layout_constraintLeft_toLeftOf="parent"
app:layout_constraintRight_toRightOf="parent"
tools:layout_constraintLeft_creator="1"
tools:layout_constraintRight_creator="1"
/>
<TextView
android:id="@+id/textView"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_marginTop="40dp"
android:text="Scan Results:"
android:textAllCaps="false"
android:textStyle="normal|bold"
app:layout_constraintLeft_toLeftOf="parent"
app:layout_constraintRight_toRightOf="parent"
app:layout_constraintTop_toBottomOf="@+id/imageView"
tools:layout_constraintLeft_creator="1"
tools:layout_constraintRight_creator="1"/>
<ScrollView
android:layout_width="0dp"
android:layout_height="0dp"
android:layout_marginTop="8dp"
android:paddingLeft="5dp"
android:paddingRight="5dp"
app:layout_constraintBottom_toBottomOf="parent"
app:layout_constraintHorizontal_bias="1.0"
app:layout_constraintLeft_toLeftOf="parent"
app:layout_constraintRight_toRightOf="parent"
app:layout_constraintTop_toBottomOf="@+id/textView"
tools:layout_constraintTop_creator="1"
tools:layout_constraintRight_creator="1"
tools:layout_constraintBottom_creator="1"
tools:layout_constraintLeft_creator="1">
<LinearLayout
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:orientation="vertical">
<TextView
android:id="@+id/results"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_marginTop="8dp"
app:layout_constraintLeft_toLeftOf="parent"
app:layout_constraintRight_toRightOf="parent"
tools:layout_constraintLeft_creator="1"
tools:layout_constraintRight_creator="1"
tools:layout_constraintTop_creator="1"/>
</LinearLayout>
</ScrollView>
</android.support.constraint.ConstraintLayout>

Java
package com.truiton.mobile.vision.ocr;
import android.Manifest;
import android.content.Context;
import android.content.Intent;
import android.content.pm.PackageManager;
import android.graphics.Bitmap;
import android.graphics.BitmapFactory;
import android.net.Uri;
import android.os.Bundle;
import android.os.Environment;
import android.provider.MediaStore;
import android.support.annotation.NonNull;
import android.support.v4.app.ActivityCompat;
import android.support.v4.content.FileProvider;
import android.support.v7.app.AppCompatActivity;
import android.util.Log;
import android.util.SparseArray;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;
import android.widget.Toast;
import com.google.android.gms.vision.Frame;
import com.google.android.gms.vision.text.Text;
import com.google.android.gms.vision.text.TextBlock;
import com.google.android.gms.vision.text.TextRecognizer;
import java.io.File;
import java.io.FileNotFoundException;
public class MainActivity extends AppCompatActivity {
private static final String LOG_TAG = "Text API";
private static final int PHOTO_REQUEST = 10;
private TextView scanResults;
private Uri imageUri;
private TextRecognizer detector;
private static final int REQUEST_WRITE_PERMISSION = 20;
private static final String SAVED_INSTANCE_URI = "uri";
private static final String SAVED_INSTANCE_RESULT = "result";
@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);
Button button = (Button) findViewById(R.id.button);
scanResults = (TextView) findViewById(R.id.results);
if (savedInstanceState != null) {
imageUri = Uri.parse(savedInstanceState.getString(SAVED_INSTANCE_URI));
scanResults.setText(savedInstanceState.getString(SAVED_INSTANCE_RESULT));
}
detector = new TextRecognizer.Builder(getApplicationContext()).build();
button.setOnClickListener(new View.OnClickListener() {
@Override
public void onClick(View view) {
ActivityCompat.requestPermissions(MainActivity.this, new
String[]{Manifest.permission.WRITE_EXTERNAL_STORAGE}, REQUEST_WRITE_PERMISSION);
}
});
}
@Override
public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions, @NonNull int[] grantResults) {
super.onRequestPermissionsResult(requestCode, permissions, grantResults);
switch (requestCode) {
case REQUEST_WRITE_PERMISSION:
if (grantResults.length > 0 && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
takePicture();
} else {
Toast.makeText(MainActivity.this, "Permission Denied!", Toast.LENGTH_SHORT).show();
}
}
}
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
if (requestCode == PHOTO_REQUEST && resultCode == RESULT_OK) {
launchMediaScanIntent();
try {
Bitmap bitmap = decodeBitmapUri(this, imageUri);
if (detector.isOperational() && bitmap != null) {
Frame frame = new Frame.Builder().setBitmap(bitmap).build();
SparseArray<TextBlock> textBlocks = detector.detect(frame);
String blocks = "";
String lines = "";
String words = "";
for (int index = 0; index < textBlocks.size(); index++) {
//extract scanned text blocks here
TextBlock tBlock = textBlocks.valueAt(index);
blocks = blocks + tBlock.getValue() + "\n" + "\n";
for (Text line : tBlock.getComponents()) {
//extract scanned text lines here
lines = lines + line.getValue() + "\n";
for (Text element : line.getComponents()) {
//extract scanned text words here
words = words + element.getValue() + ", ";
}
}
}
if (textBlocks.size() == 0) {
scanResults.setText("Scan Failed: Found nothing to scan");
} else {
scanResults.setText(scanResults.getText() + "Blocks: " + "\n");
scanResults.setText(scanResults.getText() + blocks + "\n");
scanResults.setText(scanResults.getText() + "---------" + "\n");
scanResults.setText(scanResults.getText() + "Lines: " + "\n");
scanResults.setText(scanResults.getText() + lines + "\n");
scanResults.setText(scanResults.getText() + "---------" + "\n");
scanResults.setText(scanResults.getText() + "Words: " + "\n");
scanResults.setText(scanResults.getText() + words + "\n");
scanResults.setText(scanResults.getText() + "---------" + "\n");
}
} else {
scanResults.setText("Could not set up the detector!");
}
} catch (Exception e) {
Toast.makeText(this, "Failed to load Image", Toast.LENGTH_SHORT)
.show();
Log.e(LOG_TAG, e.toString());
}
}
}
private void takePicture() {
Intent intent = new Intent(MediaStore.ACTION_IMAGE_CAPTURE);
File photo = new File(Environment.getExternalStorageDirectory(), "picture.jpg");
imageUri = FileProvider.getUriForFile(MainActivity.this,
BuildConfig.APPLICATION_ID + ".provider", photo);
intent.putExtra(MediaStore.EXTRA_OUTPUT, imageUri);
startActivityForResult(intent, PHOTO_REQUEST);
}
@Override
protected void onSaveInstanceState(Bundle outState) {
if (imageUri != null) {
outState.putString(SAVED_INSTANCE_URI, imageUri.toString());
outState.putString(SAVED_INSTANCE_RESULT, scanResults.getText().toString());
}
super.onSaveInstanceState(outState);
}
private void launchMediaScanIntent() {
Intent mediaScanIntent = new Intent(Intent.ACTION_MEDIA_SCANNER_SCAN_FILE);
mediaScanIntent.setData(imageUri);
this.sendBroadcast(mediaScanIntent);
}
private Bitmap decodeBitmapUri(Context ctx, Uri uri) throws FileNotFoundException {
int targetW = 600;
int targetH = 600;
BitmapFactory.Options bmOptions = new BitmapFactory.Options();
bmOptions.inJustDecodeBounds = true;
BitmapFactory.decodeStream(ctx.getContentResolver().openInputStream(uri), null, bmOptions);
int photoW = bmOptions.outWidth;
int photoH = bmOptions.outHeight;
int scaleFactor = Math.min(photoW / targetW, photoH / targetH);
bmOptions.inJustDecodeBounds = false;
bmOptions.inSampleSize = scaleFactor;
return BitmapFactory.decodeStream(ctx.getContentResolver()
.openInputStream(uri), null, bmOptions);
}
}

