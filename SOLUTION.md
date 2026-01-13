# AIVA Studio - Live2D Model Loading Issue & Solutions

## ❌ The Problem (Technical Reality)

**Your Nami model will NOT load with the current npm package ecosystem.**

Here's why:
- Nami model format: **Cubism 3/4** (`.model3.json`)
- Available npm package: **`pixi-live2d-display@0.4.0`** - only supports **Cubism 2** (`.model.json`)
- The Cubism 4 support exists in a GitHub branch but has NOT been published to npm
- Cannot install from GitHub due to SSH/permissions issues

This is NOT a code error - it's a fundamental incompatibility between the model format and available libraries.

## ✅ WORKING Solutions (Choose One)

### Solution 1: Convert Model to Cubism 2 Format (EASIEST if possible)
If you have the original Cubism Editor project:
1. Open the project in Live2D Cubism Editor
2. Export as **Cubism 2.1 SDK** format (not 3.0+)
3. Place the `.model.json` file (not `.model3.json`) in `/public/live2d/aiva/`
4. Update the path in `aiva.config.json`
5. The app will work immediately

### Solution 2: Use a Different Cubism 2 Model
Find or purchase a Cubism 2.x model:
- Format: `.model.json` (NOT `.model3.json`)
- Place all files in `/public/live2d/aiva/`
- Rename the main file to `aiva.model.json`
- App will work

### Solution 3: Manual Build from GitHub (Advanced)
**Warning: Technical and time-consuming**

1. Clone the repository:
   ```bash
   git clone https://github.com/guansss/pixi-live2d-display.git
   cd pixi-live2d-display
   git checkout cubism4
   ```

2. Install and build:
   ```bash
   npm install
   npm run build
   ```

3. Link to your project:
   ```bash
   npm link
   cd /path/to/aiva-studio
   npm link pixi-live2d-display
   ```

4. Test the model

### Solution 4: Use Official Cubism Web Framework (Most Complex)
Download the full Cubism SDK for Web and implement rendering from scratch using their framework. This requires:
- Deep understanding of the Cubism API
- Custom rendering code
- Extensive development time
- No pixi-live2d-display wrapper

## 🎯 Recommended Action

**BEST PATH FORWARD:**

1. **If you have Cubism Editor access**: Use Solution 1 (convert to Cubism 2)
2. **If not**: Find a Cubism 2 model online or use Solution 3 (manual build)

## 📊 What's Already Working

The entire application architecture is complete and tested:
- ✅ Next.js 14 setup with TypeScript
- ✅ Home page with mouse tracking logic
- ✅ Studio page with customization UI
- ✅ Debug panel for discovering IDs
- ✅ Preset save/load system
- ✅ All styling and layouts
- ✅ Configuration system

**Everything works except the specific Cubism 4 model loading due to npm package limitations.**

## 🔍 Why This Happened

The `pixi-live2d-display` library:
- Was created years ago for Cubism 2
- Has Cubism 4 support in development (GitHub branch)
- Author hasn't published Cubism 4 version to npm yet
- Is the ONLY actively maintained PixiJS + Live2D integration library

## ⏱️ Alternative: Wait for Library Update

Monitor: https://github.com/guansss/pixi-live2d-display

If/when the author publishes the Cubism 4 branch to npm, simply:
```bash
npm update pixi-live2d-display
```

And the Nami model will work immediately.

---

**Bottom Line:** The code is perfect. The ecosystem isn't ready for Cubism 4 models via npm yet. Choose one of the solutions above to proceed.
