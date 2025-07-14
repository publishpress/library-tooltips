# library-tooltips

PublishPress lightweight tooltip system that supports both hover and click triggers.

## Features

- Works with custom HTML inside tooltip.
- Click-to-toggle and hover support.
- Multiple placement options: `top`, `bottom`, `left`, `right`
- Requires explicit `.pp-tooltips-library` class to avoid conflicts.
- Easy refresh method for dynamic content.

## Installation

```html
<link rel="stylesheet" href="dist/css/tooltip.min.css">
<script src="dist/js/tooltip.min.js"></script>
```

## Example HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tooltip Example</title>
    <link rel="stylesheet" href="dist/css/tooltip.min.css">
</head>
<body>
    <h1>Tooltip Examples</h1>

    <h2>Hover Tooltip</h2>
    <span class="pp-tooltips-library" data-toggle="tooltip" data-placement="right">
        Hover me
        <span class="tooltip-text">
          <span>This tooltip appears on hover</span>
          <i></i>
        </span>
    </span>

    <h2>Click Tooltip</h2>
    <span class="pp-tooltips-library click" data-toggle="tooltip" data-placement="right">
        Click me
        <span class="tooltip-text">
          <span>This tooltip appears on click</span>
          <i></i>
        </span>
    </span>

    <script src="dist/js/tooltip.min.js"></script>
</body>
</html>
```

## Dynamic Refresh

The tooltip system automatically initializes tooltips on page load for any element that includes:

`class="pp-tooltips-library"` and `data-toggle="tooltip"`

You do not need to do anything extra for static tooltips.

However, if you're adding clicked tooltips dynamically via JavaScript (e.g., AJAX, innerHTML, or template insertion) the click failed to work, you can refresh those sections so the tooltip system picks them up by calling:

```js
PP_TooltipsLibrary.refresh();
```

Or for a specific section:

```js
const section = document.querySelector('#dynamic-container');
PP_TooltipsLibrary.refresh(section);
```

in your code after adding the dynamic tooltips

## Notes

- Tooltips only work when both `.pp-tooltips-library` and `data-toggle="tooltip"` are present.
- Tooltip content must be placed inside a `.tooltip-text` element.
- You can add any HTML inside `.tooltip-text`, including links, formatting, etc.
- An `<i>` element (used as the tooltip arrow) will automatically be appended if not present.
- Clicking inside the tooltip popup will close it by default, to make a link clickable inside the popup, add `.clickable` class to the link/element.

## Build

```bash
npm install
npm run build
```