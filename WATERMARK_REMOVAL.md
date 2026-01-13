# Removing the Watermark

The Nami model includes a watermark on `texture_08.png`. To remove it:

## Option 1: Replace with Blank Texture (Recommended)

1. Create a blank/transparent 4096x4096 PNG image
2. Replace `/public/live2d/aiva/Nami.4096/texture_08.png` with your blank image
3. Refresh the browser

**Why not delete the texture?**
The model's shaders are compiled to expect exactly 9 textures. Removing texture_08 causes a WebGL shader error: "Invalid value of `0` passed to `checkMaxIfStatementsInShader`"

## Option 2: Use Image Editor

Open `texture_08.png` in Photoshop/GIMP and:
1. Delete all content
2. Fill with transparency
3. Save as PNG

## Option 3: Keep As-Is

The watermark is part of the original model. If acceptable, you can leave it.

## Current Status

✅ High quality rendering enabled (1920x1080 @ 2x resolution)  
✅ Antialiasing enabled  
✅ Loading overlay fixed  
⚠️ texture_08.png (watermark) - needs manual replacement to fully remove

The application is otherwise fully functional with mouse tracking, Studio mode, and all features working perfectly.
