# react-native-inapp-update

Here is the all steps to achieve in-app update in React Native

### How to use ?

1. Open `android` folder in your react-native project with `Android Studio` and add `implementation "com.google.android.material:material:1.1.0"` and `implementation 'com.google.android.play:core:1.7.3'` at the end of dependencies section of the `build.gradle(app)` file. Like below,

```
dependencies {
    implementation fileTree(dir: "libs", include: ["*.jar"])

    implementation "com.facebook.react:react-native:+"  // From node_modules


    .......
    implementation "com.google.android.material:material:1.1.0"
    implementation 'com.google.android.play:core:1.7.3' //  at the end
}

```

Cick sync after adding the dependency.

2. Download `InAppUpdateModule.java` and `InAppUpdatePackage.java` files and place in them in the same directory of `MainActivity.java`(`android/app/src/main/java/<package>/`)
3. Change the package names in both `InAppUpdateModule.java` and `InAppUpdatePackage.java` to your project package name.
4. Now Open `MainApplication.java` and add our `InAppUpdatePackage` into `getPackages` method like below,

```
         @Override
        protected List<ReactPackage> getPackages() {
          @SuppressWarnings("UnnecessaryLocalVariable")
          List<ReactPackage> packages = new PackageList(this).getPackages();
          // Packages that cannot be autolinked yet can be added manually here, for example:
          // packages.add(new MyReactNativePackage());

           packages.add(new InAppUpdatePackage());
          return packages;
        }
```

5. Download `InAppUpdate.js` and place it into your `react-native` project.
6. Import the `InAppUpdate.js` in any `js` file, wherever you want to use. And use it like below.

```
 useEffect(() => {
    InAppUpdate.checkUpdate() // this is how you check for update
  }, []);

```

7. That's it.

### For testing you can use internal app sharing

    Here is the full desciption where you can go through and see how it works and how we can test this feature.
        ->https://developer.android.com/guide/playcore/in-app-updates#internal-app-sharing

        ->https://stackoverflow.com/questions/56087064/how-can-i-test-in-app-updates-in-android
