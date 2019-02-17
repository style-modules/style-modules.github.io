---
title: "Style Modules: The Future-Proof Modular CSS Framework"
---

# A new way to write CSS

**Style Modules** only set properties from CSS3 variables

```css
/* module-buttons.css */
.sm-button--primary {
  padding: var(--sm__spacing);
  border-style: var(--sm__border__style);
  border-width: var(--sm__border__width);
  border-color: var(--sm__border__color--primary);
}
```

Variables that are set in a **config file**

```css
/* config-official.css */
:root {
  --sm__immutable-root__spacing: 1rem;
  --sm__immutable-root__border__style: solid;
  --sm__immutable-root__border__width: 1px;
  --sm__immutable-root__border__color: #222;
  --sm__immutable-root__border__color--primary: blue;
}
:root, .sm-config__reset {
  --sm__spacing: var(--sm__immutable-root__spacing);
  --sm__border__style: var(--sm__immutable-root__border__style);
  --sm__border__width: var(--sm__immutable-root__border__width);
  --sm__border__color: var(--sm__immutable-root__border__color);
  --sm__border__color--primary: var(--sm__immutable-root__border__color--primary);
}
```

That can be overridden for a specific section of your code by combining **CSS Variables** with **CSS Cascade**

```css
/* project-styles.css */
.sm-config__dark-mode {
  --sm__border__color--primary: darkblue;
}
```

```html
<!-- index.html -->
<body>
  <button class="sm-button--primary">I'm a blue button</button>
  <div class="sm-config__dark-mode">
    <button class="sm-button--primary">I'm a dark blue button</button>
  </div>
</body>
```

And can be reset back to it's default value (you can use `.sm-config__reset` to reset all values to their defaults)

```css
/* project-styles.css */
.sm-config__not-dark-mode {
  --sm__border__color--primary: var(--sm__immutable-root__border__color--primary);
}
```

```html
<!-- index.html -->
<body>
  <button class="sm-button--primary">I'm a blue button</button>
  <div class="sm-config__dark-mode">
    <button class="sm-button--primary">I'm a dark blue button</button>
    <div class="sm-config__not-dark-mode">
      <button class="sm-button--primary">I'm a blue button (back to the config default)</button>
    </div>
  </div>
</body>
```

# A work in progress

Style Modules is still experimental (currently in open alpha), and isn't ready for any production environments.

You can join the development process by opening an issue in the [style-modules/alpha](https://github.com/style-modules/alpha/issues) issue tracker or by joining the style modules [gitter chat](https://gitter.im/style-modules).

---
<br />
<small>Style Modules Copyright &copy; 2019 Samuel Champagne & Style Modules Contributors</small>
