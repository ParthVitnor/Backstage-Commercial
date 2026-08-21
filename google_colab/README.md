# 🚀 Google Colab Video Processing Setup

This folder contains everything needed to process videos entirely on Google Colab.

## 📋 Workflow Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                    COMPLETE WORKFLOW                             │
└─────────────────────────────────────────────────────────────────┘

1. UPLOAD TO COLAB
   ├─ Original video (movie.mp4)
   └─ Product image (product.png)

2. PROCESS ON COLAB (GPU)
   ├─ Scene analysis
   ├─ Product placement
   ├─ Video generation
   └─ Creates: final_video_with_product.mp4

3. DOWNLOAD FROM COLAB
   └─ final_video_with_product.mp4 → MacBook

4. PLACE IN FRONTEND FOLDER
   └─ Copy to: frontend/prime-video-ui/public/videos/

5. USER WATCHES
   └─ Opens frontend → Plays video → Sees product ads
```

---

## 📁 Files in This Folder

```
google_colab/
├── README.md                          (This file - instructions)
├── BackstageCommercials_Colab.ipynb  (Complete Colab notebook)
├── colab_setup.py                    (Helper functions)
├── requirements_colab.txt            (Colab dependencies)
└── sample_config.json                (Configuration template)
```

---

## 🎯 Quick Start

### Step 1: Open Colab Notebook

1. Go to: https://colab.research.google.com/
2. Click **File → Upload Notebook**
3. Upload: `BackstageCommercials_Colab.ipynb` from this folder
4. Change runtime: **Runtime → Change runtime type → GPU (T4)**

### Step 2: Upload Your Files

In Colab, upload:
- Your video file (e.g., `movie.mp4`)
- Your product image (e.g., `coffee.png`)

### Step 3: Run All Cells

Click **Runtime → Run all** and wait (~10-30 minutes depending on video length)

### Step 4: Download Result

The notebook will automatically download: `final_video_with_product.mp4`

### Step 5: Place in Frontend

```bash
# On MacBook
mv ~/Downloads/final_video_with_product.mp4 \
   /Users/parth/Documents/Backstage_Commercial/frontend/prime-video-ui/public/videos/
```

### Step 6: User Can Watch

```bash
# Start frontend
cd /Users/parth/Documents/Backstage_Commercial/frontend/prime-video-ui
npm run dev

# Open http://localhost:5173
# Video with product ads is ready to play!
```

---

## 📖 Detailed Instructions

See the notebook for complete step-by-step instructions with explanations.

---

## 💡 Tips

- ✅ Process videos in batches to save time
- ✅ Use Google Drive to store processed videos
- ✅ Keep Colab runtime alive by clicking periodically
- ✅ Download videos immediately before session expires

---

## 🔧 Troubleshooting

**Out of Memory?**
- Use shorter video clips (under 30 seconds)
- Enable quantization in the notebook

**Session Timeout?**
- Save to Google Drive frequently
- Use Colab Pro for longer sessions

**Slow Processing?**
- Upgrade to A100 GPU (faster)
- Process at off-peak hours

---

## ✅ Success Checklist

- [ ] Colab notebook uploaded and GPU enabled
- [ ] Video and product uploaded to Colab
- [ ] All cells ran successfully
- [ ] Final video downloaded to MacBook
- [ ] Video copied to frontend/public/videos/
- [ ] Frontend running and video plays correctly
- [ ] Product ads appear during playback

---

**Ready to process videos in the cloud! ☁️🎬**
