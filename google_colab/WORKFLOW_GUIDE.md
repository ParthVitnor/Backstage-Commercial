# 🎬 Complete Workflow Guide

## The Simple 5-Step Process

### ✅ STEP 1: Process Video on Google Colab

```
You have:
├─ Original video (movie.mp4)
└─ Product image (coffee.png)

Upload to Colab → Run notebook → Get processed video
```

**Time:** 10-30 minutes (automated)

---

### ✅ STEP 2: Download Processed Video

```
Colab generates:
└─ final_video_with_product.mp4 (with ads embedded)

Download → Goes to your ~/Downloads/ folder
```

**Time:** 1-2 minutes

---

### ✅ STEP 3: Move to Frontend Folder

```bash
# On MacBook Terminal
cd /Users/parth/Documents/Backstage_Commercial

# Move video to frontend
mv ~/Downloads/final_video_with_product.mp4 \
   frontend/prime-video-ui/public/videos/
```

**Time:** 10 seconds

---

### ✅ STEP 4: Start Frontend

```bash
# Terminal 1: Start backend (optional - only for shopping features)
cd /Users/parth/Documents/Backstage_Commercial
source venv/bin/activate
python agent_api.py

# Terminal 2: Start frontend
cd frontend/prime-video-ui
npm run dev
```

**Time:** 30 seconds

---

### ✅ STEP 5: User Watches!

```
1. Open browser → http://localhost:5173
2. Click on video
3. Watch video with naturally embedded product
4. Product appears in background (looks real!)
5. Click "Buy on Amazon" if interested
6. Done! ✅
```

**Time:** User's choice

---

## 📁 File Locations at Each Step

### Before Processing:
```
MacBook:
└─ input_files/
    ├─ movie.mp4        (your original video)
    └─ coffee.png       (your product image)
```

### During Processing (Colab):
```
Google Colab Cloud:
├─ movie.mp4                    (uploaded)
├─ coffee.png                   (uploaded)
├─ first_frame.png             (extracted)
├─ bbox.json                   (placement plan)
├─ flux_output.png             (AI-generated frame)
└─ final_video_with_product.mp4 (FINAL OUTPUT)
```

### After Processing (MacBook):
```
MacBook:
├─ Downloads/
│   └─ final_video_with_product.mp4  (downloaded from Colab)
│
└─ frontend/prime-video-ui/public/videos/
    └─ final_video_with_product.mp4  (moved here for users)
```

---

## 🔄 Data Flow Diagram

```
┌─────────────┐
│   MacBook   │
│             │
│ movie.mp4   │
│ coffee.png  │
└──────┬──────┘
       │
       │ UPLOAD (manual)
       ↓
┌─────────────────┐
│  Google Colab   │
│   (GPU Cloud)   │
│                 │
│  1. Analyze     │
│  2. Generate    │
│  3. Render      │
└────────┬────────┘
         │
         │ DOWNLOAD (automatic)
         ↓
┌─────────────────┐
│    MacBook      │
│   ~/Downloads   │
│                 │
│ final_video.mp4 │
└────────┬────────┘
         │
         │ MOVE (manual)
         ↓
┌─────────────────┐
│    Frontend     │
│ public/videos/  │
│                 │
│ final_video.mp4 │ ←─── USER WATCHES THIS
└─────────────────┘
```

---

## 🎯 What Each Component Does

### 1. Google Colab (Processing)
**Purpose:** Heavy GPU work (can't run on MacBook Air M5)
**Does:**
- ✅ Scene analysis
- ✅ Product placement with FLUX
- ✅ Video rendering

**Input:** Video + Product image  
**Output:** Video with product embedded

---

### 2. MacBook (Frontend & API)
**Purpose:** User interface and shopping
**Does:**
- ✅ Serves video to user
- ✅ Shows "Buy" button
- ✅ Handles shopping via NovaAct

**Input:** Processed video  
**Output:** User experience

---

### 3. User's Browser
**Purpose:** Watching and interacting
**Does:**
- ✅ Plays video
- ✅ Shows product overlay
- ✅ Sends buy requests

**Input:** Video stream from frontend  
**Output:** User engagement

---

## 📊 Processing Time Breakdown

| Step | What Happens | Time | Where |
|------|-------------|------|-------|
| 1. Upload to Colab | Upload files | 2-5 min | Manual |
| 2. Scene Analysis | Find placement spots | 1-2 min | Colab Auto |
| 3. FLUX Generation | AI product placement | 2-3 min | Colab Auto |
| 4. Video Rendering | Apply to all frames | 5-20 min | Colab Auto |
| 5. Download | Transfer to MacBook | 1-2 min | Auto |
| 6. Move to folder | Copy to frontend | 10 sec | Manual |
| **Total** | | **11-32 min** | |

**Note:** Steps 2-4 are fully automated once you click "Run All"

---

## 💡 Batch Processing Multiple Videos

Process multiple videos efficiently:

```bash
# Create a batch folder structure
mkdir -p batch_processing/{input,output}

# Place all videos and products
batch_processing/input/
├─ movie1.mp4 + coffee.png
├─ movie2.mp4 + watch.png
└─ movie3.mp4 + laptop.png

# Process each in Colab (reuse same notebook)
# Download all to output folder

# Move all to frontend at once
mv batch_processing/output/*.mp4 \
   frontend/prime-video-ui/public/videos/
```

---

## 🎬 Example: Process "Suits" Episode

### Step-by-step Example:

```bash
# 1. Prepare files on MacBook
cp ~/Desktop/suits_s01e01.mp4 input_files/
cp ~/Desktop/coffee_product.png input_files/

# 2. Open Colab
# - Upload suits_s01e01.mp4
# - Upload coffee_product.png
# - Edit: PRODUCT_DESCRIPTION = "Tim Hortons coffee jar"
# - Click "Run All"
# - Wait ~15 minutes
# - Download: suits_s01e01_with_coffee.mp4

# 3. Move to frontend
mv ~/Downloads/suits_s01e01_with_coffee.mp4 \
   frontend/prime-video-ui/public/videos/

# 4. Start services
# Terminal 1:
python agent_api.py

# Terminal 2:
cd frontend/prime-video-ui && npm run dev

# 5. Open browser
open http://localhost:5173

# 6. User experience:
# - Sees "Suits S01E01 with Coffee" in video list
# - Clicks play
# - At 5:23, coffee jar appears naturally on desk
# - Overlay shows: "Buy Tim Hortons Coffee - $12.99"
# - User clicks → Added to Amazon cart!
```

---

## ✅ Quality Checklist

Before showing to users, verify:

- [ ] Video plays smoothly (no lag)
- [ ] Product looks natural (not obviously fake)
- [ ] Product doesn't cover actors' faces
- [ ] Overlay appears at right time
- [ ] "Buy" button works correctly
- [ ] Product actually exists on Amazon
- [ ] Amazon link is correct

---

## 🚀 Production Deployment Tips

For real-world use:

1. **Automate Colab Processing**
   - Use Colab API to process videos automatically
   - Or use cloud GPU service (AWS, Lambda Labs)

2. **Store Videos on CDN**
   - Upload to AWS S3 or Google Cloud Storage
   - Serve via CloudFront or similar
   - Faster delivery to users

3. **Create Video Library**
   - Database of processed videos
   - Metadata for each product placement
   - User personalization engine

4. **Scale Frontend**
   - Deploy to Vercel or Netlify
   - Use real video player (video.js, Plyr)
   - Add user authentication

---

## 📞 Need Help?

**Processing Issues:** Check `google_colab/README.md`  
**Frontend Issues:** Check `TROUBLESHOOTING.md`  
**General Setup:** Check `SETUP_GUIDE.md`

---

**You're all set! Start processing videos! 🎬✨**
