# Android Wrapper for Streamlit Applications

This project is a lightweight Android wrapper for running any public [Streamlit](https://streamlit.io) app inside a native Android WebView.

It allows you to:
- Wrap your Streamlit app in an Android interface
- Generate an `.apk` or `.aab`
- Publish it to the Google Play Store

> 📱 Ideal for data scientists, developers, educators or researchers who want to make their web-based apps available as native Android apps — without rewriting them in Java/Kotlin.

---

## ✅ Features

- Minimal native code (just a WebView)
- Compatible with Streamlit’s full interactivity
- Supports file uploads, plots, input widgets, etc.
- Works on Android 5.0+ (`minSdk 21`)
- Small app size (~5 MB)

---

## 🚀 How to Use

### 1. Clone the repo

```bash
git clone https://github.com/luiscunhacsc/androidwrapper4streamlit.git
cd androidwrapper4streamlit
```

### 2. Open in Android Studio

- Launch **Android Studio**
- Open the project directory
- Let it sync Gradle files

---

## 🔄 Customize the App

### 3. Set your Streamlit app URL

Open `MainActivity.java` and set your URL:

```java
private String streamlitUrl = "https://yourusername-yourappname.streamlit.app";
```

Ensure the URL is **publicly accessible**.

---

### 4. Rename the Package

To be accepted on Google Play, **you must use a unique package name** — never use `com.example`.

Update the following to your own reverse domain name:

#### Example:

```java
package com.joanasilva.myfinanceapp;
```

Update the same in:
- `build.gradle`:
  ```groovy
  namespace 'com.joanasilva.myfinanceapp'
  applicationId "com.joanasilva.myfinanceapp"
  ```
- Rename folder structure:
  ```
  app/src/main/java/com/joanasilva/myfinanceapp/MainActivity.java
  ```

---

### ❗ Common issue: “Cannot resolve symbol R”

This is caused by a mismatch in package names or errors in `res` files.

#### How to fix:

1. Match package name everywhere (`MainActivity`, `build.gradle`, folder)
2. `File > Sync Project with Gradle Files`
3. `Build > Clean Project`, then `Build > Rebuild`
4. Check for errors in XML files (e.g., `activity_main.xml`)
5. If needed: `File > Invalidate Caches / Restart`

---

## 📦 Generate the App Bundle (.aab)

Google Play requires `.aab` files for new apps.

In Android Studio:

```bash
Build > Build Bundle(s) / APK(s) > Build Bundle (AAB)
```

Output is in:

```
app/build/outputs/bundle/release/app-release.aab
```

---

## 🛡️ Google Play Store Requirements

To publish your app, the **Play Console** requires:

| Requirement | Description | Suggestions |
|------------|-------------|-------------|
| ✅ **Unique package name** | Must not be `com.example` | Use a reverse domain: `com.nome.aplicacao` |
| 📸 **Screenshots** | At least 2 screenshots (1080x1920) | Use Android Emulator + `Shift+Cmd+S` or [`Screenly](https://app.screenly.io/) |
| 🖼️ **App icon** | 512x512 PNG | Use [Canva](https://www.canva.com/) or [IconKitchen](https://icon.kitchen/) |
| 📜 **Privacy policy URL** | Public link is required | Use [Notion](https://notion.so), [Google Docs](https://docs.google.com), or [GitHub Pages](https://pages.github.com) |
| 📋 **Content Rating** | Fill in Google's questionnaire | Done inside Play Console |
| 🌍 **Countries & Pricing** | Choose target countries | Usually set as “Free” |
| 🔒 **Data safety form** | Describe data collection (usually none) | Mark as: no data collected, no shared data |
| 📲 **Target API level** | Must be recent (e.g. 34) | Already set in `build.gradle` |

---

## 🧠 Tips for Better Mobile Experience

- In your Streamlit app, add:
```python
st.set_page_config(layout="wide")
```

- Use `st.button`, `st.radio`, `st.selectbox`, etc., instead of complex drag/drop widgets
- Keep pages light to reduce load time on mobile networks

---

## 📄 License

MIT License — feel free to use and adapt.

---

## 🙌 Credits

Created by [Luís Cunha](https://github.com/luiscunhacsc) to make Streamlit apps more accessible via the Android ecosystem.
