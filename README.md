Ah got it — you want the full `README.md` as one clean block of code you can **copy-paste into your editor** or GitHub repo in one shot. Here it is, exactly as you'd want it for your project:

---

```markdown
# 🧠 Local Stable Diffusion WebUI on Mac M2 (DreamShaper NSFW Build)

This is my personal setup for running **Stable Diffusion WebUI** (AUTOMATIC1111) locally on a **Mac mini M2 (16GB RAM)**, fully accelerated via **Apple MPS**, with support for **NSFW photorealistic generation** using the **DreamShaper v8** model.

Everything is installed inside a **Python virtual environment** (no system pollution), GPU-accelerated, uncensored, and ready to generate stunning, high-detail AI images offline.

---

## 🔍 What’s Included

- ✅ AUTOMATIC1111 WebUI (latest build)
- ✅ Python 3.10 + venv
- ✅ Apple Silicon GPU acceleration (MPS)
- ✅ DreamShaper v8 model (NSFW-capable, photorealistic)
- ✅ Clean virtual environment install
- ✅ Safe to remove (contained in one folder)
- ✅ Launches locally at `http://localhost:7860`

---

## 💻 System Info

| Component | Spec |
|----------|------|
| Device   | Mac mini M2 |
| RAM      | 16GB |
| OS       | macOS Sonoma (or later) |
| Python   | 3.10.16 (installed via Homebrew) |
| GPU Accel | MPS (Metal Performance Shaders) |

---

## 🛠 Setup Instructions (Step-by-Step)

### 1. 🍺 Install Homebrew (if needed)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2. 🐍 Install Python 3.10

```bash
brew install python@3.10
brew link python@3.10
```

---

### 3. 🔧 Install Dependencies

```bash
brew install cmake protobuf rust git wget
```

---

### 4. 📁 Clone the WebUI Repo

```bash
cd ~
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
cd stable-diffusion-webui
```

---

### 5. 🧪 Create and Activate Virtual Environment

```bash
python3.10 -m venv venv
source venv/bin/activate
```

---

### 6. 🧠 Install PyTorch with MPS Support

```bash
pip install --upgrade pip setuptools wheel
pip install torch torchvision torchaudio
```

---

### 7. ⚙️ Configure WebUI for Mac

Edit the launch config:
```bash
nano webui-user.sh
```

Add this line (or edit existing):

```bash
export COMMANDLINE_ARGS="--skip-torch-cuda-test --no-half --precision full"
```

Save (`Ctrl + O`, `Enter`) and exit (`Ctrl + X`).

---

### 8. 🎨 Download DreamShaper v8 Model

1. Visit: [https://civitai.com/models/4384/dreamshaper](https://civitai.com/models/4384/dreamshaper)
2. Download the **`.safetensors`** file (e.g. `dreamshaper_8.safetensors`)
3. Move it into your models folder:

```bash
mv ~/Downloads/*.safetensors models/Stable-diffusion/
```

---

### 9. 🚀 Run the WebUI

```bash
./webui.sh
```

Once running, open:
```
http://localhost:7860
```

---

## ✨ Recommended Settings (DreamShaper v8)

- **Resolution**: `512x768` or `640x960`
- **Steps**: `25–30`
- **Sampler**: `DPM++ 2M Karras`
- **CFG Scale**: `7`
- **Restore Faces**: ✅ ON
- **Hires Fix**: ❌ OFF (for now)

### 🔥 Prompt Example:
```
masterpiece, best quality, photorealistic, nude female, soft cinematic lighting, full body, standing pose, 8k, perfect eyes, high detail skin
```

### ❌ Negative Prompt:
```
deformed, blurry, extra limbs, lowres, watermark, text, censored, unrealistic skin
```

---

## 📂 Where Are My Images Saved?

```
~/stable-diffusion-webui/outputs/txt2img-images/
```

Organized by date and time.

---

## ✅ To Run Again Later

```bash
cd ~/stable-diffusion-webui
source venv/bin/activate
./webui.sh
```

---

## 🧼 To Uninstall

Just delete the folder:

```bash
rm -rf ~/stable-diffusion-webui
```

---

## 🧠 Future Add-Ons

- 🔲 ControlNet for pose/image guidance
- 🧩 LoRAs for character control
- 🔧 Batch scripting
- 🎛️ Automatic prompt generator

---

Built for performance, privacy, and freedom.  
No limits. No filters. Full control.  
✌️
