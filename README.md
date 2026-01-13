# AIVA Studio - Live2D Model Viewer & Customization

A Next.js 14 application for loading and customizing Live2D Cubism 3/4 models with mouse tracking and preset management.

## ✅ WORKING - Cubism 4 Model Successfully Loading!

The Nami Cubism 4 model is now successfully loading using the correct import path.

## 🎯 Features

- **Live2D Cubism 4 Support** - Loads `.model3.json` models (VTube Studio compatible)
- **Mouse Tracking** - Head and eyes follow cursor movement
- **Studio Mode** - Customize model appearance with sliders and toggles
- **Preset System** - Save and load customizations (localStorage)
- **Debug Panel** - View all available parameters and parts
- **TypeScript** - Fully typed for better development experience

## 🚀 Quick Start

```bash
# Install dependencies
npm install

# Run development server
npm run dev
```

Visit http://localhost:3000

## 📁 Project Structure

```
aiva-studio/
├── app/
│   ├── page.tsx              # Home page with model viewer
│   └── studio/page.tsx       # Studio customization page
├── components/
│   ├── Live2DViewer.tsx      # Main Live2D rendering component
│   └── StudioControls.tsx    # Customization UI controls
├── lib/live2d/
│   ├── loadCore.ts           # Cubism Core loader utility
│   └── types.ts              # TypeScript definitions
└── public/live2d/
    ├── core/
    │   └── live2dcubismcore.min.js  # Cubism runtime
    └── aiva/
        ├── Nami.model3.json  # Your Live2D model
        ├── aiva.model3.json  # Copy of Nami model
        ├── aiva.config.json  # Customization config
        └── ...               # Model textures and files
```

## 🔧 Critical: Cubism 4 Import

**IMPORTANT:** You MUST import from the Cubism 4 build:

```typescript
// ✅ CORRECT - Cubism 4
import { Live2DModel } from 'pixi-live2d-display/cubism4';

// ❌ WRONG - Cubism 2 only
import { Live2DModel } from 'pixi-live2d-display';
```

## 📦 Dependencies

- **Next.js 14** - React framework with App Router
- **PixiJS 7** - 2D rendering engine
- **pixi-live2d-display** - Live2D + PixiJS integration
- **TypeScript** - Type safety

## 🎨 Adding Your Own Model

1. Place your Cubism 3/4 model files in `/public/live2d/aiva/`
2. Your main file should be `.model3.json` format
3. Update `/public/live2d/aiva/aiva.config.json`:
   ```json
   {
     "modelUrl": "/live2d/aiva/YourModel.model3.json",
     ...
   }
   ```

## 🔍 Finding Parameter & Part IDs

1. Navigate to http://localhost:3000
2. Look for the "🔧 Debug IDs" panel
3. Click to expand and see all available:
   - **Parameters** - For sliders (ParamAngleX, ParamMouthSmile, etc.)
   - **Parts** - For toggles (Part_Hair, Part_Outfit, etc.)

## ⚙️ Customization Config

Edit `/public/live2d/aiva/aiva.config.json`:

```json
{
  "modelUrl": "/live2d/aiva/aiva.model3.json",
  "defaultPreset": {
    "params": {},
    "parts": {}
  },
  "groups": [
    {
      "id": "outfit",
      "label": "Outfit",
      "type": "radioParts",
      "options": [
        {
          "label": "Default",
          "parts": { "Part_OutfitA": 1, "Part_OutfitB": 0 }
        }
      ]
    }
  ],
  "sliders": [
    {
      "label": "Smile",
      "paramId": "ParamMouthSmile",
      "min": 0,
      "max": 1,
      "step": 0.01
    }
  ]
}
```

## 🎮 Mouse Tracking

Creates natural head movement by mapping cursor position to:
- `ParamAngleX` - Horizontal head rotation
- `ParamAngleY` - Vertical head rotation  
- `ParamBodyAngleX` - Body tilt
- `ParamEyeBallX` - Eye horizontal movement
- `ParamEyeBallY` - Eye vertical movement

## 💾 Preset System

- **Save**: Stores current parameter and part values to localStorage
- **Load**: Restores previously saved configuration
- **Reset**: Returns to default preset from config

Storage key: `aiva:preset`

## 🐛 Troubleshooting

### Model Not Loading

1. Check console for errors
2. Verify `/public/live2d/core/live2dcubismcore.min.js` exists
3. Confirm model path in `aiva.config.json` is correct
4. Ensure using Cubism 4 import: `pixi-live2d-display/cubism4`

### Wrong Cubism Version Error

```
Could not find Cubism 2 runtime
```

This means you're using the wrong import. Change to:
```typescript
import { Live2DModel } from 'pixi-live2d-display/cubism4';
```

### React Strict Mode Issues

Disabled in `next.config.mjs` for Live2D compatibility:
```javascript
reactStrictMode: false
```

## 📝 Tech Notes

- **Cubism Core**: Loaded from CDN as fallback, local file preferred
- **Client-Only**: Live2D components use `'use client'` directive
- **Canvas Rendering**: PixiJS Application manages rendering loop
- **Parameter Updates**: Direct core model API for real-time changes

## 🎯 Next Steps

Current implementation includes:
- ✅ Model loading with Cubism 4
- ✅ Mouse tracking
- ✅ Basic customization
- ✅ Preset system
- ✅ Debug panel

Future enhancements:
- Add chat integration
- Voice synthesis (ElevenLabs)
- Animation triggers
- More polished UI
- Idle animations

## 📜 License

This project structure is MIT licensed. Live2D Cubism and model files have their own licenses.
