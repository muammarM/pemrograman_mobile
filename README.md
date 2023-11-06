Nama : M Muammar <br>
NIM  : 312210663 <br>
Kelas : TI.22.B1 <br>
Mata Kuliah : Pemrograman Mobile


## tugas mengenai Toast Fibonaci
[Tutorial silahkan cek Youtube saya](https://youtu.be/6Ru16B67IPo)

<br>



<br>

toast activity sintax sbb:<br>
``` xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:gravity="center"
        android:background="#eeeeee"
        android:orientation="vertical"
        android:paddingLeft="40dp"
        android:paddingRight="40dp">

        <TextView
            android:id="@+id/textView2"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="Increment"
            android:textAlignment="center"
            android:textSize="24sp" />

        <TextView
            android:id="@+id/textViewNumber"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="0"
            android:textAlignment="center"
            android:textSize="24sp" />

        <TextView
            android:id="@+id/textView"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="Fibonnaci"
            android:textAlignment="center"
            android:textSize="24sp" />

        <TextView
            android:id="@+id/textViewNumberFibo"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="0"
            android:textFontWeight="600"
            android:textColor="@color/black"
            android:textAlignment="center"
            android:textSize="24sp" />
    </LinearLayout>

    <Button
        android:id="@+id/button_toast"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentLeft="true"
        style="@style/Widget.AppCompat.Button"
        android:text="Toast" />
    <Button
        android:id="@+id/button_reset"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Reset"
        android:layout_margin="10dp"
        android:backgroundTint="@color/red"
        android:textColor="@color/white"
        android:textAlignment="center" />
    <Button
        android:id="@+id/button_hitung"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentRight="true"
        android:backgroundTint="@color/teal_700"
        android:layout_marginRight="10dp"
        android:textColor="@color/white"
        android:text="Hitung" />

</RelativeLayout>
```



Main aktivity sbb:<br>

``` java
 package com.example.toastfibonancci;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;
import android.widget.Toast;

 public class MainActivity extends AppCompatActivity {
    private int mCount = 0;
    private int mCountFibo = 0;
    private TextView mShowCount;
    private TextView mShowCountFibo;
    private Button buttonToast;
    private Button buttonHitung;
    private Button buttonReset;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.toast_activity);
        mShowCount = (TextView) findViewById(R.id.textViewNumber);
        mShowCountFibo = (TextView) findViewById(R.id.textViewNumberFibo);
        buttonToast = (Button) findViewById(R.id.button_toast);
        buttonHitung = (Button) findViewById(R.id.button_hitung);
        buttonReset = (Button) findViewById(R.id.button_reset);

        buttonHitung.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                hitungIncrement(view);
            }
        });
        buttonToast.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                showToast(view);
            }
        });
        buttonReset.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                resetCountDanFibbo(view);
            }
        });

    }
     public void showToast(View view){
         Toast toast = Toast.makeText(this, R.string.toast_pesan, Toast.LENGTH_SHORT);
         toast.show();
     }

     public void hitungIncrement(View view){
         mCount++;
         int fibo = hitungFibonacci(mCount);
         mCountFibo = fibo;
         if(mShowCount != null && mShowCountFibo != null){
             mShowCount.setText(Integer.toString(mCount));
             mShowCountFibo.setText(Integer.toString(mCountFibo));
         }
     }

     public int hitungFibonacci(int n){
         if(n <= 1){
             return n;
         }
         int prev = 0;
         int current = 1;
         for(int i = 2; i <= n; i++){
             int next = prev + current;
             prev = current;
             current = next;
         }
         return current;
     }

     public  void resetCountDanFibbo(View view){
         mCount = 0;
         mCountFibo = 0;
         mShowCount.setText(Integer.toString(mCount));
         mShowCountFibo.setText(Integer.toString(mCountFibo));
     }
 }
```






``` xml
<resources>
    <string name="app_name">Toast fibonancci</string>
    <string name="button_label_toast">Toast</string>
    <string name="botton_label_hitung">Hitung</string>
    <string name="hitung_initial_value">0</string>
    <string name="toast_pesan">Halo, Saya M Muammar</string>
</resources>
```

``` xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="purple_200">#FFBB86FC</color>
    <color name="purple_500">#FF6200EE</color>
    <color name="purple_700">#FF3700B3</color>
    <color name="teal_200">#FF03DAC5</color>
    <color name="teal_700">#FF018786</color>
    <color name="red">#D10000</color>

</resources>
```
