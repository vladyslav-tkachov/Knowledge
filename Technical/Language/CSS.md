## **1. Basics: Linking CSS to HTML**

### **Code Example: Linking an External Stylesheet**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Basics</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Hello, CSS!</h1>
    <p>This is a styled paragraph.</p>
</body>
</html>
```

```css
/* styles.css */
body {
    background-color: #f0f0f0;
    font-family: Arial, sans-serif;
}
h1 {
    color: blue;
    font-size: 36px;
}
p {
    color: gray;
    font-size: 18px;
}
```

### **Key Concepts**
- **Inline CSS**: Use `style` attribute directly in HTML.
- **Internal CSS**: `<style>` tag inside `<head>`.
- **External CSS**: Link a `.css` file using `<link>` for separation of concerns.

---

## **2. Selectors**

### **Code Example: Common Selectors**
```css
/* Universal selector */
* {
    margin: 0;
    padding: 0;
}

/* Tag selector */
p {
    color: green;
}

/* Class selector */
.box {
    border: 1px solid black;
}

/* ID selector */
#main-heading {
    font-size: 24px;
}
```

### **Key Concepts**
- **Universal Selector (`*`)**: Applies to all elements.
- **Type Selector**: Targets specific tags like `p`, `h1`, etc.
- **Class Selector (`.className`)**: Reusable across multiple elements.
- **ID Selector (`#idName`)**: Unique for a single element.

---

## **3. Colors and Backgrounds**

### **Code Example: Colors**
```css
/* Named colors */
h1 {
    color: red;
}

/* Hexadecimal */
p {
    color: #3498db;
}

/* RGB */
div {
    background-color: rgb(52, 152, 219);
}

/* RGBA (with transparency) */
span {
    background-color: rgba(52, 152, 219, 0.5);
}
```

### **Code Example: Background Images**
```css
body {
    background-image: url("background.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
}
```

---

## **4. Fonts and Text**

### **Code Example: Font Styling**
```css
/* Google Font */
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

body {
    font-family: 'Roboto', sans-serif;
}

h1 {
    font-size: 2em;
    text-align: center;
    text-transform: uppercase; /* Capitalizes all letters */
    letter-spacing: 2px; /* Adds space between letters */
    word-spacing: 4px; /* Adds space between words */
    line-height: 1.5; /* Adjusts space between lines */
}
```

---

## **5. Box Model**

### **Code Example: Box Model Components**
```css
div {
    width: 300px;
    height: 200px;
    margin: 20px; /* Space outside the element */
    padding: 10px; /* Space inside the element */
    border: 2px solid black; /* Border of the element */
    background-color: lightgray;
}
```

### **Key Concepts**
- Every HTML element is a rectangular box.
- **Content** → **Padding** → **Border** → **Margin**.
- Use `box-sizing: border-box;` to include padding and border in width/height.

---

## **6. Layouts: Flexbox**

### **Code Example: Flexbox Basics**
```css
.container {
    display: flex;
    justify-content: space-between; /* Horizontal alignment */
    align-items: center; /* Vertical alignment */
    gap: 10px; /* Space between items */
}

.item {
    background-color: lightblue;
    padding: 20px;
    border: 1px solid blue;
}
```

```html
<div class="container">
    <div class="item">Item 1</div>
    <div class="item">Item 2</div>
    <div class="item">Item 3</div>
</div>
```

### **Key Concepts**
- **Flexbox** simplifies layouts:
  - `justify-content`: Align items horizontally.
  - `align-items`: Align items vertically.
  - `flex-wrap`: Wrap items to the next row if necessary.

---

## **7. Layouts: CSS Grid**

### **Code Example: Grid Basics**
```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* 3 equal columns */
    grid-gap: 10px; /* Space between items */
}

.item {
    background-color: lightgreen;
    padding: 20px;
}
```

```html
<div class="container">
    <div class="item">Item 1</div>
    <div class="item">Item 2</div>
    <div class="item">Item 3</div>
</div>
```

### **Key Concepts**
- **Grid Layout** provides powerful 2D layouts:
  - `grid-template-columns/rows`: Define rows and columns.
  - `grid-gap`: Add spacing between items.

---

## **8. Animations**

### **Code Example: Simple Animation**
```css
@keyframes slideIn {
    from {
        transform: translateX(-100%);
        opacity: 0;
    }
    to {
        transform: translateX(0);
        opacity: 1;
    }
}

.box {
    animation: slideIn 2s ease-in-out;
}
```

```html
<div class="box">I slide in!</div>
```

### **Key Concepts**
- Define animations using `@keyframes`.
- Apply animations with the `animation` property.

---

## **9. Media Queries**

### **Code Example: Responsive Design**
```css
body {
    font-size: 16px;
}

@media (max-width: 600px) {
    body {
        font-size: 14px; /* Smaller font for smaller screens */
    }
}
```

### **Key Concepts**
- Use media queries for responsive designs.
- `@media (max-width: ...)` targets screens below a certain width.

---

## **10. Pseudo-Classes and Pseudo-Elements**

### **Code Example: Pseudo-Classes**
```css
a:hover {
    color: red; /* Changes color when hovered */
}

input:focus {
    border-color: blue; /* Highlights input field on focus */
}
```

### **Code Example: Pseudo-Elements**
```css
h1::after {
    content: "✨";
    color: gold;
}
```

---

## **11. Advanced Selectors**

### **Code Example: Attribute Selectors**
```css
input[type="text"] {
    border: 1px solid gray;
}

a[target="_blank"] {
    color: green;
}
```

### **Code Example: Combinators**
```css
/* Descendant selector */
div p {
    color: red;
}

/* Child selector */
div > p {
    color: blue;
}

/* Adjacent sibling */
h1 + p {
    color: orange;
}

/* General sibling */
h1 ~ p {
    color: purple;
}
```

---

## **12. Transformations**

### **Code Example: Transform**
```css
.box {
    transform: rotate(45deg) scale(1.5);
}
```

---

## **13. Gradients**

### **Code Example: Linear and Radial Gradients**
```css
div {
    background: linear-gradient(to right, red, yellow);
}

circle {
    background: radial-gradient(circle, red, yellow);
}
```

---

## **14. Shadows**

### **Code Example: Box Shadows**
```css
.box {
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.3);
}
```

---

## **15. Variables (CSS Custom Properties)**

### **Code Example: Defining Variables**
```css
:root {
    --primary-color: #3498db;
    --secondary-color: #2ecc71;
}

body {
    color: var(--primary-color);
}
```

---

## **16. Z-Index and Stacking Context**

### **Code Example: Stacking Elements**
```css
div {
    position: relative;
}

.box1 {
    background: red;
    width: 100px;
    height: 100px;
    position: absolute;
    z-index: 1; /* Behind box2 */
}

.box2 {
    background: blue;
    width: 100px;
    height: 100px;
    position: absolute;
    z-index: 2; /* In front of box1 */
}
```

```html
<div class="box1"></div>
<div class="box2"></div>
```

### **Key Concepts**
- **`z-index`** controls the stack order of overlapping elements.
- Elements with higher `z-index` values appear in front.
- **Stacking Context**:
  - Created by properties like `position: relative;`, `opacity`, or `transform`.

---

## **17. CSS Specificity**

### **Code Example: Specificity Rules**
```css
/* Low specificity */
p {
    color: blue;
}

/* Medium specificity */
.article p {
    color: green;
}

/* High specificity */
#main p {
    color: red;
}
```

### **Key Concepts**
- **Specificity** determines which styles are applied when multiple selectors match:
  1. Inline styles: `style="color: red"` (highest specificity).
  2. IDs: `#id`.
  3. Classes: `.class`, attributes, pseudo-classes.
  4. Tags: `p`, `div`, etc. (lowest specificity).

---

## **18. Units in CSS**

### **Absolute Units**
- **`px`**: Pixels, fixed size, unaffected by user settings.
- **`cm`, `mm`, `in`**: Physical dimensions (rarely used).

### **Relative Units**
- **`%`**: Percentage relative to the parent element.
- **`em`**: Relative to the font size of the parent.
- **`rem`**: Relative to the root element (`<html>`).
- **`vh`, `vw`**: Viewport height/width (1vh = 1% of viewport height).

### **Code Example: Units in Action**
```css
body {
    font-size: 16px; /* Base font size */
}

h1 {
    font-size: 2rem; /* 32px */
}

p {
    width: 50%; /* Half the width of its container */
}

.section {
    height: 50vh; /* Half the height of the viewport */
}
```

---

## **19. CSS Transitions**

### **Code Example: Adding Smooth Transitions**
```css
.button {
    background-color: blue;
    color: white;
    padding: 10px 20px;
    transition: background-color 0.3s ease, transform 0.3s ease;
}

.button:hover {
    background-color: green;
    transform: scale(1.1); /* Slight zoom */
}
```

### **Key Concepts**
- `transition`: Specifies which properties change and their duration.
- Common values:
  - `ease`: Slow start, fast middle, slow end.
  - `linear`: Constant speed.

---

## **20. Pseudo-Elements vs Pseudo-Classes**

### **Pseudo-Classes Recap**
- Used for states like hover or focus (`:hover`, `:focus`).
- Example:
  ```css
  a:hover {
      color: red;
  }
  ```

### **Pseudo-Elements Recap**
- Style specific parts of an element (`::before`, `::after`).
- Example:
  ```css
  h1::before {
      content: "🔥 ";
  }
  ```

### **Key Difference**
- **Pseudo-Classes**: Apply styles based on an element’s state.
- **Pseudo-Elements**: Create "virtual" elements that don’t exist in the DOM.

---

## **21. Advanced Selectors**

### **Code Example: Attribute Selectors**
```css
input[type="text"] {
    border: 1px solid gray;
}

input[placeholder*="search"] {
    background-color: yellow;
}
```

- `[attribute]`: Matches elements with the attribute.
- `[attribute="value"]`: Matches attributes with an exact value.
- `[attribute^="value"]`: Matches if the value starts with something.
- `[attribute$="value"]`: Matches if the value ends with something.
- `[attribute*="value"]`: Matches if the value contains something.

---

## **22. Gradients**

### **Advanced Gradient Techniques**
```css
div {
    background: linear-gradient(to right, red, yellow, green);
}

button {
    background: radial-gradient(circle, #ff0000, #000000);
}
```

### **Key Concepts**
- **Linear Gradient**:
  - Syntax: `linear-gradient(direction, color1, color2, ...)`.
- **Radial Gradient**:
  - Syntax: `radial-gradient(shape, color1, color2, ...)`.

---

## **23. Clipping and Masking**

### **Code Example: Clip Path**
```css
div {
    clip-path: polygon(50% 0%, 100% 100%, 0% 100%);
    background-color: orange;
    width: 200px;
    height: 200px;
}
```

### **Key Concepts**
- `clip-path`: Crops elements into shapes like circles, polygons, etc.
- Use tools like [Clippy](https://bennettfeely.com/clippy/) to generate clip-paths visually.

---

## **24. CSS Grid: Advanced Features**

### **Code Example: Named Grid Areas**
```css
.container {
    display: grid;
    grid-template-areas:
        "header header"
        "sidebar main"
        "footer footer";
    grid-template-columns: 1fr 3fr;
}

.header {
    grid-area: header;
}
.sidebar {
    grid-area: sidebar;
}
.main {
    grid-area: main;
}
.footer {
    grid-area: footer;
}
```

---

## **25. CSS Variables: Advanced Use**

### **Code Example: Dynamic Theming**
```css
:root {
    --main-bg-color: #ffffff;
    --main-text-color: #333333;
}

body {
    background-color: var(--main-bg-color);
    color: var(--main-text-color);
}

/* Change variables dynamically */
.dark-theme {
    --main-bg-color: #333333;
    --main-text-color: #ffffff;
}
```

---

## **26. Filters**

### **Code Example: Image Filters**
```css
img {
    filter: grayscale(50%) blur(2px) brightness(1.2);
}
```

### **Available Filters**
- **`grayscale(%)`**: Converts image to grayscale.
- **`blur(px)`**: Applies a blur effect.
- **`brightness(value)`**: Adjust brightness.

---

## **27. Important CSS Properties**

### **Overflow**
```css
div {
    width: 200px;
    height: 100px;
    overflow: scroll; /* Adds scrollbars */
}
```

### **Positioning**
- **Static**: Default.
- **Relative**: Positioned relative to itself.
- **Absolute**: Positioned relative to the nearest positioned ancestor.
- **Fixed**: Stays in place during scrolling.
- **Sticky**: Sticks to a position based on scroll.

---

### **28. CSS Shorthand Properties**

- **Margin and Padding**
  ```css
  margin: 10px 20px 30px 40px; /* top, right, bottom, left */
  ```

- **Background**
  ```css
  background: url("image.jpg") no-repeat center/cover;
  ```

---

## **29. Debugging CSS**

### **Browser Developer Tools**
- Open with `F12` or `Ctrl+Shift+I`.
- Inspect elements and test CSS changes in real-time.

### **CSS Validation**
- Use tools like [W3C CSS Validator](https://jigsaw.w3.org/css-validator/) to check for errors.

---

### **30. Helpful Resources**
1. [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS) - Comprehensive reference.
2. [Can I Use](https://caniuse.com/) - Check browser compatibility.
3. [CSS Tricks](https://css-tricks.com/) - Tips and guides.

---


