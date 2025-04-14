---
title: "Build Beautiful UIs with Jetpack Compose Material Toolkit"
seoTitle: "Craft Stunning UIs with Jetpack Compose"
seoDescription: "Learn how to use Jetpack Compose's Material toolkit to style your app, structure layouts, and apply modifiers to build rich and responsive user interfaces."
datePublished: Mon Apr 14 2025 14:23:22 GMT+0000 (Coordinated Universal Time)
cuid: cm9h5ywk3000408l80yq9hmcu
slug: build-beautiful-uis-with-jetpack-compose-material-toolkit
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/cZr2sgaxy3Q/upload/f1cb3a33a0295afd9a54f3ef0e11cb91.jpeg
tags: material-design, layout, jetpack-compose, android-ui, modifiers

---

> In this post, you'll explore how Jetpack Compose makes it incredibly easy to build stylish, functional UIs using Material Design principles, composable layouts, and powerful modifiers.

## ✨ Jetpack Compose UI Toolkit: A Quick Recap

So far, you've seen how to create composable functions and use basic components like `Row`, `Text`, and `RadioButton`. But Jetpack Compose offers **so much more** out of the box.

Jetpack Compose ships with a **robust Material Design toolkit**, allowing you to:

* Style your entire app consistently
    
* Create polished layouts with intuitive structures
    
* Customize every element with modifiers
    

Let’s dive deeper by building a survey screen UI from the `jetsurvey` sample app.

---

## 🎨 Styling with Material Design

Jetpack Compose includes **Material Design 2 and 3** support. Material 3, aka Material You, aligns with the design language of Android 12+, offering dynamic theming and modern components.

### Define a Custom Theme

The `jetsurvey` app defines a custom `JetsurveyTheme` composable. This includes:

* **Colors** for dark and light themes
    
* **Typography** for fonts, sizes, weights
    
* **Shapes** for rounded corners and design consistency
    

```kotlin
@Composable
fun JetsurveyTheme(content: @Composable () -> Unit) {
    MaterialTheme(
        colorScheme = if (isSystemInDarkTheme()) DarkColors else LightColors,
        typography = AppTypography,
        shapes = AppShapes,
        content = content
    )
}
```

Use your theme as the outermost layer via `setContent` in your activity or fragment. This ensures all components follow the defined design system.

---

## 🧱 Structure with Scaffold & Surface

### Use `Scaffold` for Layouts

A **Scaffold** provides a structure for screens with:

* Top app bar
    
* Content area
    
* Bottom bar (e.g., buttons)
    

Example from `SurveyQuestionsScreen`:

```kotlin
Scaffold(
    topBar = { SurveyTopAppBar(progress) },
    bottomBar = { SurveyBottomBar(onNext, onPrevious) }
) { padding ->
    SurveyContent(currentQuestion, modifier = Modifier.padding(padding))
}
```

### Use `Surface` to Add Depth

A **Surface** represents a container for your content, allowing you to define:

* Background color
    
* Border and shape
    
* Elevation (shadow and layering)
    

You can wrap UI components inside a `Surface` to apply a unified style or add visual hierarchy.

---

## 📐 Compose Layouts: Row, Column, and Box

Jetpack Compose provides 3 powerful layout composables:

| Layout | Purpose |
| --- | --- |
| `Row` | Arrange items **horizontally** |
| `Column` | Arrange items **vertically** |
| `Box` | **Stack** items on top of each other |

### Example: Centering Items in a Row

```kotlin
Row(
    verticalAlignment = Alignment.CenterVertically,
    horizontalArrangement = Arrangement.SpaceBetween,
    modifier = Modifier.fillMaxWidth()
) {
    Text("Option 1")
    RadioButton(selected = true, onClick = {})
}
```

---

## 🛠️ Modifiers: Your Customization Tool

**Modifiers** help you decorate and customize composables. They can:

* Set padding, size, or background
    
* Add interactivity (e.g., click)
    
* Align elements inside layouts
    

### Modifier Example

```kotlin
Row(
    modifier = Modifier
        .fillMaxWidth()
        .padding(16.dp)
) {
    Text("Your Answer")
}
```

### Wrap in a Surface for Styling

```kotlin
Surface(
    shape = MaterialTheme.shapes.small,
    border = BorderStroke(1.dp, Color.Gray),
    modifier = Modifier.fillMaxWidth()
) {
    Row(modifier = Modifier.padding(16.dp)) {
        Text("Answer Text")
    }
}
```

---

## 📚 Learn More

Jetpack Compose's material toolkit gives you full control to build adaptive, beautiful UIs. There’s so much more to explore:

* [Material 3 Guidelines](https://m3.material.io/)
    
* [Jetpack Compose Material Docs](https://developer.android.com/jetpack/compose/design)
    

Next up, we’ll explore how **tooling in Jetpack Compose** speeds up your development and debugging.

> Don’t forget to subscribe so you don’t miss it! 🚀