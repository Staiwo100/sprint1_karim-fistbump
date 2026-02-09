# Fist Bump Karim - Code Style Guide (Used Claude AI)

## Table of Contents
1. [General Principles](#general-principles)
2. [HTML Structure](#html-structure)
3. [CSS Conventions](#css-conventions)
4. [JavaScript Style](#javascript-style)
5. [Naming Conventions](#naming-conventions)
6. [Comments](#comments)
7. [Organization](#organization)

---

## General Principles

- **Readability First**: Code should be easy to read and understand
- **Consistent Formatting**: Maintain consistent indentation and spacing throughout
- **Separation of Concerns**: Keep HTML structure, CSS styling, and JavaScript logic clearly separated
- **Self-Documenting Code**: Use descriptive names and clear structure

---

## HTML Structure

### Indentation
- Use **4 spaces** for indentation (no tabs)
- Nested elements should be indented one level deeper than their parent

### Element Ordering
```html
<!-- Meta tags first -->
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- Title -->
<title>Page Title</title>

<!-- Styles inline in head -->
<style>
    /* CSS here */
</style>
```

### Comments
- Use HTML comments to mark major sections
- Keep comments concise and descriptive
```html
<!-- Button to open snake mini-game -->
<button id="snakeBtn">🐍 Play Snake</button>

<!-- Main game container -->
<div class="game-container">
```

### Attributes
- Use double quotes for attribute values
- Keep boolean attributes explicit when needed
```html
<canvas id="snakeGame" width="400" height="400"></canvas>
```

---

## CSS Conventions

### Organization
1. **Reset/Base Styles** - Universal selector resets first
2. **Layout Styles** - Major layout containers
3. **Component Styles** - Individual components in logical order
4. **Animations** - Keyframe animations near related components
5. **Utility Classes** - Custom scrollbars and other utilities last

### Selector Naming
- Use **kebab-case** for class names: `.main-game`, `.shop-item`, `.click-effect`
- Use **camelCase** for IDs: `#karim`, `#snakeBtn`, `#shopItems`
- Use descriptive, semantic names that reflect purpose

### Property Ordering
Group related properties together:
```css
.example {
    /* Positioning */
    position: fixed;
    top: 20px;
    left: 50%;
    z-index: 1000;
    
    /* Display & Box Model */
    display: flex;
    width: 100%;
    padding: 15px 30px;
    margin: 0;
    
    /* Visual */
    background: linear-gradient(135deg, #ff6b6b, #ffd700);
    border-radius: 15px;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.4);
    
    /* Typography */
    font-size: 24px;
    font-weight: bold;
    color: white;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    
    /* Animation */
    animation: pulse 1s ease-in-out infinite;
    transform: translateX(-50%);
    transition: transform 0.1s;
}
```

### Comments
- Comment **every CSS block** with its purpose
- Use `/* Comment */` format
- Place comment directly above the selector
```css
/* Main clickable Karim circle */
#karim {
    width: 300px;
    height: 300px;
    /* ... */
}
```

### Values and Units
- Use **rgba()** for colors with transparency
- Use **px** for fixed dimensions, **%** for relative
- Keep color values consistent (hex for solids, rgba for transparency)
- Use **meaningful opacity values**: 0.8, 0.9, 1.0

### Animations
- Define `@keyframes` near the component that uses them
- Use descriptive animation names: `floatUp`, `popIn`, `flashResult`
```css
@keyframes floatUp {
    0% {
        opacity: 1;
        transform: translateY(0);
    }
    100% {
        opacity: 0;
        transform: translateY(-100px);
    }
}
```

---

## JavaScript Style

### Variable Declarations
- Use `let` for variables that will change
- Use `const` for constants and references that won't be reassigned
- Group related variables together
```javascript
// ===== GAME STATE VARIABLES =====
let coins = 0;
let coinsPerClick = 1;
let coinsPerSecond = 0;
let globalMultiplier = 1;
```

### Naming Conventions
- **camelCase** for variables and functions: `coinsPerClick`, `updateDisplay()`
- **SCREAMING_SNAKE_CASE** for true constants (if used)
- **Descriptive names**: `meterActive` not `active`, `snakeRunning` not `running`

### Function Style
- Use **function declarations** for named functions
- Use **arrow functions** for callbacks and inline functions
- One blank line between function definitions
```javascript
// Named function declaration
function getItemCost(item) {
    return Math.floor(item.baseCost * Math.pow(1.15, item.count));
}

// Arrow function for event listener
karimElement.addEventListener('click', (e) => {
    // ...
});
```

### Code Organization Sections
Use banner comments to separate major sections:
```javascript
// ===== SECTION NAME =====
```

Standard sections in order:
1. `GAME STATE VARIABLES`
2. `SHOP ITEMS DATA`
3. `DOM ELEMENT REFERENCES`
4. `EVENT HANDLERS`
5. `HELPER FUNCTIONS`
6. `INITIALIZATION`

### Comments
- Use `//` for single-line comments
- Comment **above** the code being explained
- Use inline comments sparingly, only for clarification
```javascript
// Add coins based on click value and multiplier
coins += coinsPerClick * globalMultiplier;

const duration = 1200;          // 1.2 seconds for full travel
```

### String Literals
- Use **single quotes** for simple strings: `'click-effect'`
- Use **template literals** for interpolation or multi-line strings
```javascript
effect.textContent = `+${actualGain}`;

overlay.innerHTML = `
    <div class="meter-container">
        <!-- ... -->
    </div>
`;
```

### Object Literals
- Use trailing commas in multi-line objects
- Align properties for readability
```javascript
const shopItem = {
    id: 'autoClicker1',
    name: 'Nayan Patel',
    baseCost: 10,
    effect: 0.1,
    effectType: 'cps',
    count: 0,
    imageSrc: './resources/Nayan-Transparent.png'
};
```

### Conditionals and Loops
- Use braces even for single-line blocks
- Add space after keywords
```javascript
if (coins >= cost) {
    coins -= cost;
}

shopItems.forEach(item => {
    // ...
});
```

### DOM Manipulation
- Cache DOM references at the top
- Use `const` for element references
- Use descriptive variable names
```javascript
const karimElement = document.getElementById('karim');
const coinsDisplay = document.getElementById('coins');
```

### Event Listeners
- Use arrow functions for handlers when possible
- Define complex handlers as separate functions
```javascript
// Simple inline handler
button.addEventListener('click', () => {
    overlay.style.display = 'flex';
});

// Complex handler as separate function
karimElement.addEventListener('click', handleKarimClick);
```

### Magic Numbers
- Define magic numbers as variables with descriptive names
- Add inline comments for non-obvious values
```javascript
const duration = 1200;          // 1.2 seconds for full travel
const delay = (count - 1) * 0.5;
const isGreen = markerPosition >= 85; // Green zone is top 15%
```

---

## Naming Conventions

### CSS Classes
- Descriptive, component-based names
- Use state modifiers: `.shop-item.disabled`
- Prefix related components: `.meter-overlay`, `.meter-container`, `.meter-bar`

### IDs
- One word when possible: `#karim`, `#coins`
- CamelCase for multi-word: `#snakeBtn`, `#coinsPerClick`
- Unique and specific to element

### JavaScript Variables
| Type | Convention | Example |
|------|------------|---------|
| Primitives | camelCase | `coins`, `meterActive` |
| Objects | camelCase | `shopItems`, `snake` |
| DOM Elements | camelCase + Element suffix | `karimElement`, `shopItemsContainer` |
| Functions | camelCase + verb | `updateDisplay()`, `getItemCost()` |
| Boolean flags | is/has prefix | `isSuccess`, `hasAirpods` |

### File and Resource Naming
- Use kebab-case for files: `cloud-background.jpg`
- Use PascalCase for proper names: `Karim-Beanie-Airpods.png`
- Descriptive names: `Punch-Green.png` not `img1.png`

---

## Comments

### When to Comment

**Always comment:**
- Major sections (with banner comments)
- Complex logic or algorithms
- Non-obvious values or calculations
- Public functions and their parameters
- CSS blocks and their purpose

**Don't comment:**
- Obvious code: `i++; // increment i`
- Redundant information already in variable names

### Comment Style

**CSS:**
```css
/* Major section header */

/* Specific component description */
.component {
    /* ... */
}
```

**JavaScript:**
```javascript
// ===== MAJOR SECTION =====

// Function description
function doSomething() {
    // Step explanation
    const value = calculate();
    
    const timeout = 1000;       // Inline clarification
}
```

**HTML:**
```html
<!-- Major section description -->
<div class="section">
    <!-- Element purpose if not obvious -->
    <button id="action">Action</button>
</div>
```

---

## Organization

### File Structure
```
project/
├── index.html          (all-in-one file)
├── resources/
│   ├── images/
│   └── assets/
└── codestyle.md
```

### Code Order in HTML File
1. DOCTYPE and head metadata
2. Title
3. Inline styles (CSS)
4. Body structure (HTML)
5. Inline scripts (JavaScript)

### JavaScript Code Order
```javascript
// 1. Game state variables
let gameVar = 0;

// 2. Data structures (arrays, objects)
const gameData = [];

// 3. DOM references
const element = document.getElementById('id');

// 4. Event listeners for DOM elements
element.addEventListener('click', handler);

// 5. Helper functions
function helper() { }

// 6. Main game logic functions
function gameLogic() { }

// 7. Initialization code
initialize();

// 8. Additional game systems (e.g., Snake game)
// Snake game logic here
```

---

## Best Practices

### Performance
- Cache DOM queries in variables
- Use `requestAnimationFrame` for animations
- Use event delegation where appropriate
- Minimize DOM manipulation

### Maintainability
- Keep functions focused and small
- Use descriptive variable names
- Comment complex logic
- Group related code together

### Consistency
- Follow established patterns in the codebase
- Use the same formatting throughout
- Maintain consistent naming across similar elements
- Keep similar code structures aligned

---

## Examples

### Good CSS Block
```css
/* Display for active coin multiplier */
.multiplier-display {
    position: fixed;
    top: 20px;
    left: 50%;
    transform: translateX(-50%);
    background: linear-gradient(135deg, #ff6b6b, #ffd700);
    padding: 15px 30px;
    border-radius: 15px;
    font-size: 24px;
    font-weight: bold;
    color: white;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.4);
    z-index: 1000;
    animation: pulse 1s ease-in-out infinite;
}
```

### Good JavaScript Function
```javascript
// Calculate cost of an item with exponential scaling
function getItemCost(item) {
    return Math.floor(item.baseCost * Math.pow(1.15, item.count));
}

// Purchase an item from the shop
function buyItem(item) {
    const cost = getItemCost(item);
    if (coins >= cost) {
        coins -= cost;              // Deduct cost
        item.count++;               // Increment count

        // Apply item effect based on type
        if (item.effectType === 'cpc') {
            coinsPerClick += item.effect;
        } else if (item.effectType === 'cps') {
            coinsPerSecond += item.effect;
        }

        updateDisplay();
        renderShop();
    }
}
```

### Good Event Listener
```javascript
// ===== KARIM CLICK HANDLER =====
karimElement.addEventListener('click', (e) => {
    // Add coins based on click value and multiplier
    coins += coinsPerClick * globalMultiplier;
    updateDisplay();
    renderShop();

    // Create floating text effect showing coins gained
    const effect = document.createElement('div');
    effect.className = 'click-effect';
    const actualGain = Math.floor(coinsPerClick * globalMultiplier);
    effect.textContent = `+${actualGain}`;
    
    // Position at click location relative to Karim
    effect.style.left = (e.clientX - karimElement.getBoundingClientRect().left) + 'px';
    effect.style.top = (e.clientY - karimElement.getBoundingClientRect().top) + 'px';
    karimElement.appendChild(effect);

    // Remove floating text after animation completes
    setTimeout(() => effect.remove(), 1000);
});
```

---

## Version History

- **v1.0** - Initial style guide based on Fist Bump Karim codebase
