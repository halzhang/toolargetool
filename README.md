# toolargetool

A tool for debugging `TransactionTooLargeException` on Android.

## Usage

1. Include `toolargetool` as a dependency, you can remove it again once you've debugged your crash:

       maven { url 'https://jitpack.io' } // in project build.gradle
       implementation 'com.github.halzhang:toolargetool:v0.1.6' // in module build.gradle

2. Add code to start logging during app start, for example in your `Application.onCreate` method:

       TooLargeTool.startLogging(this);

3. Monitor logcat output to see which components are writing substantial data to the transaction
   buffer and when:

       $ adb logcat -s TooLargeTool

   Example logcat output (TODO: improve this example):

       D/TooLargeTool: MainActivity.onSaveInstanceState wrote: Bundle@200090398 contains 1 keys and measures 0.6 KB when serialized as a Parcel
                                                                               * android:viewHierarchyState = 0.6 KB

