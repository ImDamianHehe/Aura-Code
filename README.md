# AuraSK

**AuraSK is a GUI-first programming language for building modern desktop applications.**

AuraSK is designed around a simple idea:

> **Describe what your application does. Let AuraSK handle the GUI machinery.**

Instead of writing large amounts of Swing boilerplate, AuraSK lets you create windows, buttons, labels, inputs, and events using a compact syntax.

```text
new.mainWindow = Window
mainWindow.title: "Hello AuraSK"
mainWindow.size: "500, 300"

new.helloButton = Button
helloButton.label: "Click Me"

helloButton.onClick: {
    console.print: "Hello from AuraSK!"
}
```

AuraSK currently compiles to Java internally and uses Swing as its desktop GUI backend.

---

## ✨ Features

* 🖥️ GUI-first programming model
* 🟣 Simple component-based syntax
* 🎯 Name your components however you want
* 📐 Automatic GUI organization and vertical stacking
* 🎨 Built-in modern styling
* 🖱️ GUI events such as `onClick`
* ⏱️ `timerWait()` support
* 📝 Component properties
* 🎛️ Built-in GUI components
* 🧪 AuraSK-specific compiler errors
* 💻 Standalone `aurask` command-line tool
* 🛠️ AuraSK Studio IDE
* ☕ Java/Swing used internally, without exposing generated Java to the developer

---

# 🚀 Getting Started

## Requirements

AuraSK currently requires:

* Java JDK 25 or newer
* Linux for the current installer workflow
* A terminal for using the CLI

Check your Java version:

```bash
java --version
```

Check that the Java compiler is available:

```bash
javac --version
```

---

# 📦 Installing AuraSK

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/AuraSK.git
cd AuraSK
```

Build and install the CLI:

```bash
chmod +x sk.sh
./sk.sh
```

The installer places the AuraSK runtime in:

```text
~/.local/aurask/
```

and the executable in:

```text
~/.local/bin/
```

Make sure `~/.local/bin` is in your `PATH`.

Then test the installation:

```bash
aurask --version
```

You should see something similar to:

```text
AuraSK 0.1.0
```

---

# ▶️ Running an AuraSK Program

Create a file ending in `.aurask`.

For example:

```text
Main.aurask
```

Then run:

```bash
aurask run ~/Desktop/Main.aurask
```

AuraSK will:

1. Read the `.aurask` source.
2. Validate the AuraSK syntax.
3. Generate Java internally.
4. Compile the generated Java.
5. Launch the application.

The generated Java implementation is an internal detail and is not part of the language the developer writes.

---

# 🧠 AuraSK Syntax

AuraSK uses a simple component model.

The general structure is:

```text
new.<name> = <Type>
<name>.<property>: <value>

<name>.<event>: {
    ...
}
```

The name can be anything that follows AuraSK's identifier rules.

For example:

```text
new.myWindow = Window
myWindow.title: "My App"

new.loginButton = Button
loginButton.label: "Log In"
```

You are not restricted to names such as `window` or `button`.

---

# 🪟 Windows

Create a window with:

```text
new.mainWindow = Window
mainWindow.title: "My Application"
mainWindow.size: "600, 400"
mainWindow.resizeable: false
```

### Window properties

| Property     | Example          | Description                       |
| ------------ | ---------------- | --------------------------------- |
| `title`      | `"My App"`       | Window title                      |
| `size`       | `"600, 400"`     | Window width and height           |
| `resizeable` | `true` / `false` | Whether the window can be resized |

AuraSK also accepts:

```text
mainWindow.resizable: false
```

---

# 🔘 Buttons

Create a button:

```text
new.myButton = Button
myButton.label: "Click Me"
myButton.color: "PURPLE"
```

### Button properties

```text
myButton.label: "Click Me"
myButton.color: "BLUE"
```

Supported built-in colors currently include:

```text
RED
GREEN
BLUE
PURPLE
ORANGE
YELLOW
PINK
CYAN
WHITE
BLACK
GRAY
```

---

# 🏷️ Labels

Create a label:

```text
new.title = Label
title.text: "Welcome to AuraSK!"
title.color: "CYAN"
```

Labels support:

```text
title.text: "Hello"
title.color: "GREEN"
```

The `title` property is also accepted for compatibility:

```text
title.title: "Hello"
```

---

# ⌨️ Text Fields

Create a text field:

```text
new.nameInput = TextField
nameInput.placeholder: "Enter your name"
nameInput.text: ""
```

Text fields can also use:

```text
nameInput.color: "WHITE"
```

and support the `onChange` event.

---

# ☑️ Check Boxes

```text
new.agree = CheckBox
agree.label: "I agree"
agree.checked: true
agree.color: "GREEN"
```

Supported properties:

```text
label
checked
color
```

---

# 🎚️ Sliders

```text
new.volume = Slider
volume.min: "0"
volume.max: "100"
volume.value: "50"
```

Supported properties:

```text
min
max
value
```

---

# 📊 Progress Bars

```text
new.progress = ProgressBar
progress.min: "0"
progress.max: "100"
progress.value: "25"
```

---

# 🖱️ Events

AuraSK uses event blocks.

For example:

```text
new.button = Button
button.label: "Click Me"

button.onClick: {
    console.print: "Clicked!"
}
```

The component name determines which component receives the event.

For example:

```text
new.login = Button
login.label: "Log In"

new.cancel = Button
cancel.label: "Cancel"

login.onClick: {
    console.print: "Logging in..."
}

cancel.onClick: {
    console.print: "Cancelled."
}
```

---

# 🔄 Changing Components

Component properties can be changed from inside events.

```text
```
