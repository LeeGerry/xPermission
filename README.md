# xPermission
1. Add maven "https://jitpack.io".
```
allprojects {
    repositories {
        google()
        mavenCentral()
        maven { url 'https://jitpack.io' }
    }
}
```
2. Include in the gradle file.
```
implementation 'com.github.LeeGerry:xPermission:v1.0.0'
```
3. Use it in your project
```
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        findViewById<Button>(R.id.button).setOnClickListener {
            XPermission.request(this, Manifest.permission.CALL_PHONE) { allGranted, deniedList ->
                if (allGranted) {
                    call()
                } else {
                    Toast.makeText(this, "You denied $deniedList", Toast.LENGTH_SHORT).show()
                }
            }
        }
    }

    private fun call() {
        startActivity(Intent(Intent.ACTION_CALL, Uri.parse("tel:4088210000")))
    }
}
```
