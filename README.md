# SpinnerDialog
Android Spinner Dialog Library, Use for single or multi selection of choice

[![](https://jitpack.io/v/hamzaahmedkhan/SpinnerDialog.svg)](https://jitpack.io/#hamzaahmedkhan/SpinnerDialog)

[ ![Download](https://api.bintray.com/packages/hamzaahmedkhan/SpinnerDialog/SpinnerDialog/images/download.svg?version=v1.0) ](https://bintray.com/hamzaahmedkhan/SpinnerDialog/SpinnerDialog/v1.0/link)



## Android UI

<img src='demo/home.png' height=480 width=240 />


<img src='demo/list_0.png' height=480 width=240 />


<img src='demo/list_1.png' height=480 width=240 />


## Download

To include `SpinnerDialog` in your project, add the following to your dependencies:

**app/build.gradle**
```groovy
dependencies {
        implementation 'com.github.hamzaahmedkhan:SpinnerDialog:v1.0'
}
```

## Usage
The following snippet shows how you can use Spinner Dialog in your project.


**In Java**

```java
public class MainActivity extends Activity {
    
    
    //... other variables
    
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        
            // Set Data
            
           ArrayList<SpinnerModel> arrSpinners = new ArrayList<>();
        
           for (int i = 0; i < 5; i++) {
               arrSpinners.add(new SpinnerModel("Number " + i));
           }
        
           // Init Fragment
           SpinnerDialogFragment spinnerDialogFragment = SpinnerDialogFragment.Companion.newInstance("Demo", arrSpinners, (data, selectedPosition) -> UIHelper.showToast(getContext(), data.getText()), 0);
           
           // Show Fragment
           spinnerDialogFragment.show(getActivity().getSupportFragmentManager(), "spinnerDialog");

    }
}
```



**In Kotlin**

```kotlin
class MainActivity : AppCompatActivity() {


    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)


        val arraySpinnerModel: ArrayList<SpinnerModel> = ArrayList()

        for (i in 1..9) {
            arraySpinnerModel.add(SpinnerModel("Number $i"))
        }


        // Init Fragment
        val spinnerDialogFragment =
            SpinnerDialogFragment.newInstance(
                "Spinner Dialog", arraySpinnerModel,
                object : OnSpinnerOKPressedListener {
                    override fun onItemSelect(data: SpinnerModel, selectedPosition: Int) {
                        Toast.makeText(applicationContext, data.text, Toast.LENGTH_LONG).show()
                    }

                }, 0
            )


        txtShowSingleChoiceSpinner.setOnClickListener { spinnerDialogFragment.show(supportFragmentManager, "SpinnerDialogFragment") }
        txtShowMultiChoiceSpinner.setOnClickListener { Toast.makeText(applicationContext, "In Progress", Toast.LENGTH_LONG).show() }
    }
}
```



**EXTRA ATTRIBUTES**
```kotlin

        // Using optional features
        spinnerDialogFragment.buttonText = "SAVE"
        spinnerDialogFragment.themeColorResId = resources.getColor(R.color.material_pink500)

```


**FUTURE PLANS**

-> Multi check options
-> Searh bar
