# Android-Kotlin-Extensions-Collections

This is the collection of Koltin Extensions that I use in daily basis. Just trying to make collection so others might learn and contribute back.

### Context Extensions

```kotlin
fun Context.getColorCompat(@ColorRes colorRes: Int) = ContextCompat.getColor(this, colorRes)
fun Context.getFontCompat(@FontRes fontRes: Int) = ResourcesCompat.getFont(this, fontRes)
fun Context.getLocationService() = this.getSystemService(Context.LOCATION_SERVICE)
fun Context.getNotificationService() = this.getSystemService(Context.NOTIFICATION_SERVICE)
```

### EditText Extensions

```kotlin
fun EditText.afterTextChanged(afterTextChanged: (String) -> Unit) {
    this.addTextChangedListener(object : TextWatcher {
        override fun beforeTextChanged(p0: CharSequence?, p1: Int, p2: Int, p3: Int) {}
        override fun onTextChanged(p0: CharSequence?, p1: Int, p2: Int, p3: Int) {}
        override fun afterTextChanged(editable: Editable?) {
            afterTextChanged.invoke(editable.toString())
        }
    })
}

fun EditText.trim(): EditText = this.apply { setText(this.text.trim()) }

```

### Spinner Extensions

```kotlin
fun Spinner.onItemSelected(onItemSelected: (Int) -> Unit) {
    this.onItemSelectedListener = object : AdapterView.OnItemSelectedListener {
        override fun onNothingSelected(parent: AdapterView<*>?) {}
        override fun onItemSelected(parent: AdapterView<*>?, view: View?, position: Int, id: Long) {
            onItemSelected.invoke(position)
        }
    }
}
```

### ViewPager Extensions

```kotlin
fun ViewPager.onPageChangeListener(onPageSelected: (Int) -> Unit){
    this.addOnPageChangeListener(object: ViewPager.OnPageChangeListener{
        override fun onPageScrollStateChanged(state: Int) {}
        override fun onPageScrolled(position: Int, positionOffset: Float, positionOffsetPixels: Int) {}
        override fun onPageSelected(position: Int) {
            onPageSelected.invoke(position)
        }
    })
}
```

### Decimal Extensions

```kotlin
fun Double.roundOff(): Double {
    val df = DecimalFormat("#.#")
    df.roundingMode = RoundingMode.FLOOR
    return df.format(this).toDouble()
}
```
