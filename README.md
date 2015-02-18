# android-issue-1

This sample application demonstrates an issue with resource merging. The issue prevents `@id/text_view` from being defined which results in this runtime failure:

```
02-18 12:43:42.692  20024-20024/com.example.jameswald.android_issue_1 E/AndroidRuntime﹕ FATAL EXCEPTION: main
    Process: com.example.jameswald.android_issue_1, PID: 20024
    java.lang.NoSuchFieldError: No static field text_view of type I in class Lcom/example/jameswald/android_issue_1/lib/R$id; or its superclasses (declaration of 'com.example.jameswald.android_issue_1.lib.R$id' appears in /data/app/com.example.jameswald.android_issue_1-1/base.apk)
            at com.example.jameswald.android_issue_1.lib.MainActivity.onCreate(MainActivity.java:14)
            at android.app.Activity.performCreate(Activity.java:5933)
            at android.app.Instrumentation.callActivityOnCreate(Instrumentation.java:1105)
            at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:2251)
            at android.app.ActivityThread.handleLaunchActivity(ActivityThread.java:2360)
            at android.app.ActivityThread.access$800(ActivityThread.java:144)
            at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1278)
            at android.os.Handler.dispatchMessage(Handler.java:102)
            at android.os.Looper.loop(Looper.java:135)
            at android.app.ActivityThread.main(ActivityThread.java:5221)
            at java.lang.reflect.Method.invoke(Native Method)
            at java.lang.reflect.Method.invoke(Method.java:372)
            at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:899)
            at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:694)
```

The expected result would be a `NullPointerException` because `@id/text_view` is defined but the view does not exist.
