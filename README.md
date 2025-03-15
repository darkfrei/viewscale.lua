# viewscale.lua
lightweight and flexible scaling library for LOVE2D


# 📚 ViewScale - Lua Scaling Library for LOVE2D

**ViewScale** is a library that automatically adjusts rendering to match different screen resolutions while maintaining a consistent aspect ratio. It is particularly useful for supporting devices like the Steam Deck and 4K monitors by dynamically adjusting window size, rendering scale, and offsets.

---

## 🌟 Features

- ✅ **Automatically scales rendering** based on screen resolution
- ✅ **Centers the viewport** properly using translation offsets
- ✅ **Supports resizable windows** and updates dynamically
- ✅ **Provides easy-to-use push/pop functions** for transformation
- ✅ **Displays real-time scaling info** in the window title

---

## 📌 How It Works

- The library initializes with a base resolution (default: **1280x800** for Steam Deck).
- If the screen resolution is at least twice as large, it doubles the rendering scale.
- When the window is resized, it recalculates the optimal scale and offsets to keep everything centered.
- Provides `push()` and `pop()` functions to apply and reset transformations in `love.draw()`.

---

## 🚀 Installation

1️⃣ Place `viewscale.lua` in your project folder.

2️⃣ Require it in your `main.lua`:

```lua
local ViewScale = require("viewscale")
```

3️⃣ Call ViewScale.load() in love.load().

4️⃣ Call ViewScale.push() before drawing and ViewScale.pop() after.

## 📝 Usage Example

# 1. Load and Initialize

```lua
function love.load()
    ViewScale.load() -- initialize scaling
end
```

# 2. Handle Window Resizing

```lua
function love.resize(w, h)
    ViewScale.resize(w, h) -- adjust scaling on resize
end
```

# 3. Apply Scaling in **love.draw()**

```lua
function love.draw()
    ViewScale.push() -- apply transformations
    
    -- draw a background rectangle
    love.graphics.setColor(0.35, 0.35, 0.8)
    love.graphics.rectangle("fill", 0, 0, 1280, 800)
    
    ViewScale.pop() -- reset transformations
end
```

# 4. View Scaling Info in Window Title

Automatically updates window title:Window: 2560x1600 | Render: 1280x800 | Scale: 2.00 | Offset: (640.0, 400.0)

## ⚙️ API Reference

```lua
ViewScale.load(baseWidth, baseHeight)
```

Initializes scaling with optional base resolution.

Automatically detects screen resolution.

```lua
ViewScale.resize(w, h)
```

Updates scaling and offsets when the window is resized.

```lua
ViewScale.push()
```

Applies the translation and scaling transformation.

```lua
ViewScale.pop()
```

Resets transformations.

## 🎮 Why Use ViewScale?

✅ Makes your LOVE2D games look perfect on different screen sizes✅ No need to rewrite rendering logic—just use push() and pop()✅ Handles 4K screens by scaling up UI & game elements automatically

* 🎯 Perfect for Steam Deck & High-Resolution Screens! 🚀
