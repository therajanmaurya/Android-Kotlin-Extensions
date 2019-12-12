# Android-Kotlin-Extensions

This is the collection of Koltin Extensions that I use in daily basis. Just trying to make collection so others might learn and contribute back.

### Context Extensions

```
fun Context.getColorCompat(@ColorRes colorRes: Int) = ContextCompat.getColor(this, colorRes)
fun Context.getFontCompat(@FontRes fontRes: Int) = ResourcesCompat.getFont(this, fontRes)
```

