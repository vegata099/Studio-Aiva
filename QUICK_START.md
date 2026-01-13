# AIVA Studio - Quick Start Guide

## ⚡ Quick Setup (3 Steps)

### Step 1: Download Cubism Core Runtime ⭐ REQUIRED

You **MUST** download the Live2D Cubism Core runtime before the app will work:

1. Go to: https://www.live2d.com/en/download/cubism-sdk/
2. Download **Cubism SDK for Web** (Cubism 4 recommended for the included Nami model)
3. Extract the ZIP and find `Core/live2dcubismcore.min.js`
4. Copy it to: `aiva-studio/public/live2d/core/live2dcubismcore.min.js`

**Without this file, the model will not load!**

### Step 2: Run the Development Server

```bash
cd aiva-studio
npm run dev
```

### Step 3: Open in Browser

Open http://localhost:3000 in your browser!

## 🎉 What You'll See

### Home Page (/)
- The Nami Live2D model with mouse tracking
- Move your cursor → the character follows!
- A "Hi! 👋" speech bubble
- Debug IDs panel (top-right) - click to see all parameter/part IDs

### Studio Page (/studio)
- Customization controls (left panel)
- Live model preview (right panel)
- Save/Load/Reset preset buttons
- Expression sliders
- Debug IDs panel for discovering parameter names

## 🔧 Customizing Your Model

1. Open the Studio page
2. Click **🔧 Debug IDs** in the top-right
3. Copy the parameter/part IDs you want to control
4. Edit `public/live2d/aiva/aiva.config.json`
5. Add your sliders and toggles using the copied IDs
6. Refresh the page!

### Example Config

```json
{
  "sliders": [
    {
      "label": "Smile",
      "paramId": "ParamMouthForm",
      "min": -1,
      "max": 1,
      "step": 0.01
    }
  ]
}
```

## 📁 Project Structure

```
aiva-studio/
├── public/live2d/
│   ├── core/
│   │   └── live2dcubismcore.min.js  ← DOWNLOAD THIS!
│   └── aiva/
│       ├── aiva.model3.json         ← Already set up (Nami model)
│       ├── aiva.config.json         ← Customize controls here
│       └── (all other model files)
├── app/
│   ├── page.tsx                     ← Home page
│   └── studio/page.tsx              ← Studio page
├── components/
│   ├── Live2DViewer.tsx
│   └── StudioControls.tsx
└── lib/live2d/
    ├── loadCore.ts
    └── types.ts
```

## ❓ Troubleshooting

### "Failed to load Cubism Core"
→ Download `live2dcubismcore.min.js` and place it in `public/live2d/core/`

### "Failed to load model"
→ Check browser console (F12) for details
→ Verify all texture files are present in `public/live2d/aiva/Nami.4096/`

### Controls don't work
→ Use Debug IDs panel to verify parameter names
→ Check that IDs in config match exactly (case-sensitive!)

### Model doesn't follow mouse
→ This is normal on the Studio page (mouse tracking disabled there)
→ Go to Home page (/) for mouse tracking

## 🎨 Using Your Own Model

1. Place your model files in `public/live2d/aiva/`
2. Rename your `.model3.json` file to `aiva.model3.json` (or update config)
3. Use Debug IDs panel to find parameter/part IDs
4. Update `aiva.config.json` with your model's IDs
5. Refresh!

## 📚 More Details

See `README.md` for comprehensive documentation including:
- Detailed configuration options
- radioParts groups (outfit switchers)
- sliderParam groups (color blending)
- Preset save/load system
- TypeScript types reference

---

**Ready to start? Download the Cubism Core runtime and run `npm run dev`! 🚀**
