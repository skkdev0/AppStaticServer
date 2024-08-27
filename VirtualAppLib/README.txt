package com.skkapp.virtual;

import android.app.Activity;
import android.graphics.Color;
import android.os.Bundle;
import android.os.Handler;
import android.os.Looper;
import android.widget.LinearLayout;
import android.widget.TextView;

import java.io.File;
import android.widget.Toast;

public class MainActivity extends Activity 
{
    
   
    public static TextView textview1;
	private static Activity aaa;
    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
		aaa = MainActivity.this;
		
		
		// Create a new LinearLayout
        LinearLayout linearLayout = new LinearLayout(this);
        linearLayout.setLayoutParams(new LinearLayout.LayoutParams(
										 LinearLayout.LayoutParams.MATCH_PARENT,
										 LinearLayout.LayoutParams.MATCH_PARENT
									 ));
        linearLayout.setGravity(android.view.Gravity.CENTER);
        linearLayout.setBackgroundColor(Color.BLACK);

        // Create a new TextView
         textview1 = new TextView(this);
        textview1.setText("Loading......");
        textview1.setLayoutParams(new LinearLayout.LayoutParams(
									 LinearLayout.LayoutParams.WRAP_CONTENT,
									 LinearLayout.LayoutParams.WRAP_CONTENT
								 ));
        textview1.setTextColor(Color.WHITE);
        textview1.setTextIsSelectable(true);
        textview1.setTextSize(20);
        linearLayout.addView(textview1);
        setContentView(linearLayout);
		
		if(App.isRun)aa();	
	  }
	
	public static void aa(){
		
					File myPlug = new File(App.DataPath);
					try {
						new dalvik.system.DexClassLoader("/filepath/classes.dex", "/tmp", null, aaa.getClass().getClassLoader()).loadClass("androidx.pluginmgr.PluginManager").getConstructor(new Class[]{Activity.class,File.class}).newInstance(new Object[]{aaa, myPlug});
						

						aaa.finish();
						App.isRun = false;
					} catch (Exception e) {
						Toast.makeText(aaa,"Please Wait..."+e.toString(),Toast.LENGTH_LONG).show();
						aaa.finish();
					}
				
	
		
    }
	
}
