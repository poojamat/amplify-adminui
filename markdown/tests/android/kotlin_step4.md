Amplify dependencies are installed through Gradle.

Under Gradle Scripts, open **build.gradle (Module: app)**.

```gradle
:::NO_COPY:::
android {

```
```gradle
    compileOptions {
        // Support for Java 8 features
        coreLibraryDesugaringEnabled true
        sourceCompatibility JavaVersion.VERSION_1_8
        targetCompatibility JavaVersion.VERSION_1_8
    }
```
```gradle
:::NO_COPY:::
}

dependencies {
```
```gradle
    // Amplify plugins
    implementation 'com.amplifyframework:core:1.17.4'
    implementation 'com.amplifyframework:aws-api:1.17.4'
    implementation 'com.amplifyframework:aws-datastore:1.17..4'

    // Support for Java 8 features
    coreLibraryDesugaring 'com.android.tools:desugar_jdk_libs:1.1.5'
```
```gradle
:::NO_COPY:::
}
```

Click on `Sync now`


Open your **MainActivity.kt** and add the following lines to initialize Amplify libraries:
```kt
:::NO_COPY:::
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
```
```kt
        try {
            //Amplify.addPlugin(AWSApiPlugin()) // UNCOMMENT this line once backend is deployed
            Amplify.addPlugin(AWSDataStorePlugin())
            Amplify.configure(applicationContext)
            Log.i("Amplify", "Initialized Amplify")
        } catch (e: AmplifyException) {
            Log.e("Amplify", "Could not initialize Amplify", e)
        }
```
```kt
:::NO_COPY:::
    }
}
```
