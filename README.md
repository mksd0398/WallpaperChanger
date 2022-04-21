# WallpaperChanger

## MainActivity.kt

package com.parta.wallpaperchanger

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.os.Handler
import android.os.Looper
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        actionBar?.title = "Changing Wallpaper App";
        supportActionBar?.title = "Changing Wallpaper App";

        val images = arrayOf(R.drawable.w1, R.drawable.w2,R.drawable.w3,R.drawable.w4)

        button.setOnClickListener {
            button.isEnabled = false
            val mainHandler = Handler(Looper.getMainLooper())

            mainHandler.post(object : Runnable {
                override fun run() {

                    imageView.setImageResource(images[(Math.random() * images.size).toInt()])
                    mainHandler.postDelayed(this, 3000) //3 second delay for demo can increase or decrease

                }
            })
        }
    }
}
