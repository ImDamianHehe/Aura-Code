# AuraSK

**AuraSK is a GUI-first programming language for building modern desktop applications.**

AuraSK focuses on making GUI development simple, readable, and expressive.

Instead of manually dealing with complex layout systems and widget configuration, you describe your application using components, properties, events, and statements.

```text
console.print: "Starting..."

new.mainWindow = Window
mainWindow.title: "AuraSK Demo"
mainWindow.size: "600, 500"
mainWindow.resizeable: false

new.welcome = Label
welcome.text: "Welcome to AuraSK!"
welcome.color: "CYAN"

new.button = Button
button.label: "Click Me"
button.color: "PURPLE"

button.onClick: {
    console.print: "Clicked!"
}
```

---

## ✨ Features

* 🖥️ GUI-first programming
* 🧩 Component-based syntax
* 🏷️ User-defined component names
* 📐 Automatic component organization
* 🎨 Modern GUI styling by default
* 🖱️ Event-driven programming
* ⏱️ Timers with `timerWait()`
* 🖨️ Console output
* 🎛️ Built-in GUI components
* 🔄 Change component properties at runtime
* 🧠 AuraSK-specific error messages
* 🧱 Simple syntax designed to grow into a full programming language

---

# Syntax

AuraSK programs are built from four main concepts:

```text
Component
Property
Event
Statement
```

The general syntax is:

```text
new.<name> = <Type>

<name>.<property>: <value>

<name>.<event>: {
    ...
}
```

---

# Components

Components are created using:

```text
new.<name> = <Type>
```

The name can be chosen by the programmer.

```text
new.mainWindow = Window
new.loginButton = Button
new.usernameInput = TextField
```

Names may contain letters, numbers, and underscores.

They must begin with a letter or underscore.

Valid:

```text
new.window1 = Window
new.loginButton = Button
new.main_label = Label
```

Invalid:

```text
new.1button = Button
```

A component name must be unique within the program.

---

# Window

Create a window:

```text
new.mainWindow = Window
```

## Properties

### `title`

```text
mainWindow.title: "My Application"
```

Sets the window title.

### `size`

```text
mainWindow.size: "600, 400"
```

Sets the width and height.

### `resizeable`

```text
mainWindow.resizeable: false
```

Controls whether the window can be resized.

`resizable` is also accepted:

```text
mainWindow.resizable: false
```

---

# Button

Create a button:

```text
new.myButton = Button
```

## Properties

### `label`

```text
myButton.label: "Click Me"
```

Sets the button text.

### `color`

```text
myButton.color: "PURPLE"
```

Sets the button color.

Supported built-in colors:

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

# Label

Create a label:

```text
new.title = Label
```

## Properties

### `text`

```text
title.text: "Welcome!"
```

Sets the label text.

### `title`

The `title` property may also be used:

```text
title.title: "Welcome!"
```

### `color`

```text
title.color: "CYAN"
```

Changes the label text color.

---

# TextField

Create a single-line text field:

```text
new.username = TextField
```

## Properties

### `text`

```text
username.text: "Damian"
```

Sets the initial text.

### `placeholder`

```text
username.placeholder: "Enter your name"
```

Sets placeholder text.

### `color`

```text
username.color: "WHITE"
```

Sets the text color.

---

# TextArea

Create a multi-line text area:

```text
new.message = TextArea
```

## Properties

### `text`

```text
message.text: "Hello!"
```

### `placeholder`

```text
message.placeholder: "Write something..."
```

### `color`

```text
message.color: "WHITE"
```

---

# CheckBox

Create a checkbox:

```text
new.accept = CheckBox
```

## Properties

### `label`

```text
accept.label: "I agree"
```

### `checked`

```text
accept.checked: true
```

or:

```text
accept.checked: false
```

### `color`

```text
accept.color: "GREEN"
```

---

# Slider

Create a slider:

```text
new.volume = Slider
```

## Properties

### `min`

```text
volume.min: "0"
```

### `max`

```text
volume.max: "100"
```

### `value`

```text
volume.value: "50"
```

Example:

```text
new.volume = Slider

volume.min: "0"
volume.max: "100"
volume.value: "50"
```

---

# ProgressBar

Create a progress bar:

```text
new.progress = ProgressBar
```

## Properties

### `min`

```text
progress.min: "0"
```

### `max`

```text
progress.max: "100"
```

### `value`

```text
progress.value: "40"
```

Example:

```text
new.progress = ProgressBar

progress.min: "0"
progress.max: "100"
progress.value: "40"
```

---

# ComboBox

Create a dropdown:

```text
new.mode = ComboBox
```

## Properties

### `items`

Items are separated by commas.

```text
mode.items: "Easy,Normal,Hard"
```

### `value`

Sets the selected item.

```text
mode.value: "Normal"
```

Example:

```text
new.mode = ComboBox

mode.items: "Easy,Normal,Hard"
mode.value: "Normal"
```

---

# Events

Events use blocks:

```text
<component>.<event>: {
    ...
}
```

## `onClick`

Buttons support:

```text
new.myButton = Button
myButton.label: "Click Me"

myButton.onClick: {
    console.print: "Clicked!"
}
```

Different components can have independent events:

```text
new.firstButton = Button
firstButton.label: "One"

new.secondButton = Button
secondButton.label: "Two"

firstButton.onClick: {
    console.print: "First button clicked!"
}

secondButton.onClick: {
    console.print: "Second button clicked!"
}
```

---

# `onChange`

`onChange` is used by components whose value can change.

## TextField

```text
new.username = TextField

username.placeholder: "Username"

username.onChange: {
    console.print: "Text changed!"
}
```

## Slider

```text
new.volume = Slider

volume.min: "0"
volume.max: "100"

volume.onChange: {
    console.print: "Slider changed!"
}
```

## ComboBox

```text
new.mode = ComboBox

mode.items: "Easy,Normal,Hard"

mode.onChange: {
    console.print: "Selection changed!"
}
```

---

# Changing Components

A component can be modified during an event.

```text
new.status = Label
status.text: "Ready"

new.startButton = Button
startButton.label: "Start"

startButton.onClick: {
    status.text: "Running..."
    startButton.label: "Started!"
}
```

This allows components to interact with each other.

Another example:

```text
new.progress = ProgressBar
progress.value: "0"

new.start = Button
start.label: "Start"

start.onClick: {
    progress.value: "75"
}
```

---

# `console.print`

Print text to the application console:

```text
console.print: "Hello AuraSK!"
```

It can be used globally:

```text
console.print: "Starting application..."
```

or inside events:

```text
button.onClick: {
    console.print: "Button clicked!"
}
```

---

# `timerWait`

Wait for a specified number of seconds:

```text
timerWait(3)
```

It can be used globally:

```text
console.print: "Starting..."
timerWait(3)
console.print: "Done!"
```

It can also be used inside events:

```text
button.onClick: {
    button.label: "Waiting..."
    timerWait(3)
    button.label: "Done!"
}
```

---

# Automatic Layout

AuraSK automatically organizes GUI components.

Components are centered and vertically stacked based on declaration order.

Example:

```text
new.window = Window
window.title: "Example"
window.size: "500, 400"

new.first = Label
first.text: "Welcome"

new.second = Button
second.label: "Continue"

new.third = Button
third.label: "Cancel"
```

The layout is automatically organized as:

```text
        Welcome

       [Continue]

        [Cancel]
```

The programmer does not need to manually specify coordinates for basic layouts.

---

# Colors

AuraSK includes built-in named colors.

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

Example:

```text
new.title = Label
title.text: "Hello"
title.color: "CYAN"

new.button = Button
button.label: "Launch"
button.color: "PURPLE"
```

---

# Comments

Comments begin with `//`.

```text
// Create the main window
new.mainWindow = Window

mainWindow.title: "My App"
```

Comments are ignored by the language.

---

# Multiple Components

A program can contain multiple components with different names.

```text
new.mainWindow = Window
mainWindow.title: "My App"
mainWindow.size: "600, 500"

new.title = Label
title.text: "Welcome!"
title.color: "CYAN"

new.username = TextField
username.placeholder: "Username"

new.password = TextField
password.placeholder: "Password"

new.loginButton = Button
loginButton.label: "Log In"
loginButton.color: "PURPLE"

new.cancelButton = Button
cancelButton.label: "Cancel"
cancelButton.color: "RED"

loginButton.onClick: {
    console.print: "Logging in..."
}

cancelButton.onClick: {
    console.print: "Cancelled."
}
```

Components are automatically arranged in declaration order.

---

# Example Application

```text
console.print: "Starting AuraSK..."

new.mainWindow = Window
mainWindow.title: "AuraSK Demo"
mainWindow.size: "600, 650"
mainWindow.resizeable: false

new.heading = Label
heading.text: "Welcome to AuraSK"
heading.color: "CYAN"

new.nameInput = TextField
nameInput.placeholder: "Enter your name"

new.message = TextArea
message.placeholder: "Write something..."

new.accept = CheckBox
accept.label: "I agree"
accept.checked: false
accept.color: "GREEN"

new.mode = ComboBox
mode.items: "Easy,Normal,Hard"
mode.value: "Normal"

new.volume = Slider
volume.min: "0"
volume.max: "100"
volume.value: "50"

new.progress = ProgressBar
progress.min: "0"
progress.max: "100"
progress.value: "25"

new.launchButton = Button
launchButton.label: "Launch"
launchButton.color: "PURPLE"

launchButton.onClick: {
    console.print: "Launching..."
    launchButton.label: "Loading..."
    progress.value: "80"
    timerWait(2)
    launchButton.label: "Launch"
}
```

---

# Error Messages

AuraSK reports language errors using AuraSK-specific diagnostics.

Example:

```text
AuraSK Error [Line 5]
Unknown component: myButton
Create the component before setting its properties.
```

Another example:

```text
AuraSK Error [Line 4]
Unknown component type: AwesomeWidget
Supported types: Window, Button, Label, TextField, TextArea, CheckBox, Slider, ProgressBar, ComboBox.
```

Invalid properties are also reported:

```text
AuraSK Error [Line 8]
myButton.size is not valid for Button.
Supported properties: label, color.
```

The goal is to make errors describe the **AuraSK program itself**, rather than internal implementation details.

---

# Built-in Types

| Type          | Purpose                |
| ------------- | ---------------------- |
| `Window`      | Application window     |
| `Button`      | Clickable button       |
| `Label`       | Text display           |
| `TextField`   | Single-line text input |
| `TextArea`    | Multi-line text input  |
| `CheckBox`    | Boolean selection      |
| `Slider`      | Numeric input          |
| `ProgressBar` | Progress display       |
| `ComboBox`    | Dropdown selection     |

---

# Built-in Events

| Event      | Supported Components              |
| ---------- | --------------------------------- |
| `onClick`  | `Button`, `CheckBox`              |
| `onChange` | `TextField`, `Slider`, `ComboBox` |

---

# Built-in Statements

| Statement       | Purpose                      |
| --------------- | ---------------------------- |
| `console.print` | Print text                   |
| `timerWait()`   | Wait for a number of seconds |

---

# Design Philosophy

AuraSK is designed around a GUI-first programming model.

The developer describes:

```text
What components exist
What those components look like
What those components do
```

instead of manually describing every low-level GUI operation.

A typical AuraSK program follows this pattern:

```text
Create
  ↓
Configure
  ↓
Respond
```

For example:

```text
new.button = Button
button.label: "Start"

button.onClick: {
    console.print: "Started!"
}
```

AuraSK is intended to stay simple at the surface while growing into a more complete programming language underneath.
