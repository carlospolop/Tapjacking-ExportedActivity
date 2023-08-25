# Tapjacking with Exported Activity

## Tapjacking

A Tapjacking attack is like a **Clickjacking but for an Android applications**. It is a type of attack where the user is tricked into **clicking something different from what the user perceives they are clicking on**, thus potentially revealing confidential information or taking control of their device while clicking on seemingly innocuous objects.

This is achieved by putting on the foreground a malicious application that will be changing what the user is looking at while the user is actually interacting with the malicious application (in some cases the user won't even notice that this malicious application is running).

You can find **more info in https://book.hacktricks.xyz/mobile-pentesting/android-app-pentesting/tapjacking**

## Exported Activities

An exported activity not properly protected can be **launched by any application**.

## Combinig both

This project is an Android application that will **start by launching the indicated exported application** and then it will put on the foreground a malicious application that will be **changing what the user is looking at** while the user is actually interacting with the malicious application.

## Compiling

1. Use Android studio to open this folder.
2. Go to `app/src/main/java/com/tapjacking/demo` and change `[PACKAGE NAME]` for the package name vulenrable activity and `[ACTIVITY NAME]` for the name of the exported activity you want to launch.
3. Compile & launch the application.

## Protections against Tapjacking

### Android 12 (API 31,32) and higer

[According to this source](https://www.geeksforgeeks.org/tapjacking-in-android/) tapjacking attacks are automatically prevented by Android from Android 12 (API 31 & 30) and higer. So, even if the application is vulnerable you won't be able to exploit it.

### `setFilterTouchesWhenObscured`

The attribute setFilterTouchesWhenObscured set to true can also prevent the exploitation of this vulnerability if the Android version is lower.
If set to true, for example, a button can be automatically disabled if it is obscured:
<Button android:text="Button"
android:id="@+id/button1"
android:layout_width="wrap_content"
android:layout_height="wrap_content" 
android:filterTouchesWhenObscured="true">
</Button>