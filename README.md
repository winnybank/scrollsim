# ScrollSim

A self-hosted visual content management system with a modern feed-based interface.

![ScrollSim Demo](https://via.placeholder.com/800x400?text=Add+Screenshot+Here)

## ✨ Features

- 📸 **Photo & Video Support** - Display images and videos in an organized feed
- 🎠 **Carousel Posts** - Group multiple media files together
- 🎥 **Video Management** - Duration display, sorting by length
- 🌙 **Dark Mode** - Easy on the eyes
- 📱 **Responsive Design** - Works on desktop and mobile
- 🔒 **Privacy First** - Everything stays on your local network

## 🎯 Use Cases

- Content creators planning visual posts
- Photographers organizing portfolio presentations
- Personal media library with social-style browsing
- Testing content layouts and combinations

---

## 🚀 Quick Start Guide

### Step 1: Install Prerequisites

#### Install Node.js

**Windows:**
1. Go to [nodejs.org](https://nodejs.org)
2. Download the **LTS version** (recommended for most users)
3. Run the installer
4. Keep clicking "Next" with default settings
5. Restart your computer after installation

**Mac:**
1. Go to [nodejs.org](https://nodejs.org)
2. Download the **LTS version**
3. Open the `.pkg` file and follow the installer
4. Or use Homebrew: `brew install node`

**Linux:**
```bash
# Ubuntu/Debian
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs

# Fedora
sudo dnf install nodejs

# Arch
sudo pacman -S nodejs npm
```

**Verify installation:**
```bash
node --version   # Should show v18.x.x or higher
npm --version    # Should show 9.x.x or higher
```

#### Install a Good Terminal (Windows Only)

Pick one of these (much better than default CMD):

**Option 1: Windows Terminal (Recommended)**
- Install from Microsoft Store
- Modern, tabs, customizable
- Built-in to Windows 11

**Option 2: Cmder**
- Download from [cmder.net](https://cmder.net)
- Download the **Full version**
- Extract to `C:\cmder`
- Run `Cmder.exe`

**Option 3: Git Bash**
- Comes with Git for Windows
- Download from [git-scm.com](https://git-scm.com)

**Mac/Linux:** Use the built-in Terminal (it's already great!)

---

### Step 2: Download ScrollSim

**Option A: Using Git (Recommended)**
```bash
git clone https://github.com/yourusername/scrollsim.git
cd scrollsim
```

**Option B: Download ZIP**
1. Click the green **Code** button on GitHub
2. Click **Download ZIP**
3. Extract the ZIP file
4. Open terminal and navigate to the folder:
   ```bash
   cd path/to/scrollsim
   ```

---

### Step 3: Set Up the Server

Open your terminal and run these commands one by one:

```bash
# Navigate to server folder
cd server

# Install dependencies (this might take a minute)
npm install

# Start the server
npm start
```

You should see:
```
Server running on http://localhost:3001
Media directory: /path/to/scrollsim/server/media
Indexed 0 posts from 0 users
```

**✅ Server is running!** Leave this terminal window open.

---

### Step 4: Set Up the Client

Open a **NEW terminal window** (keep the server running in the first one):

```bash
# Navigate to client folder
cd client

# Install dependencies
npm install

# Start the client
npm run dev
```

You should see:
```
VITE v5.x.x ready in xxx ms

➜  Local:   http://localhost:5173/
➜  Network: http://192.168.x.x:5173/
```

**✅ Client is running!**

---

### Step 5: Open the App

Open your web browser and go to:
```
http://localhost:5173
```

You should see the ScrollSim interface! 🎉

---

## 📱 Access from Your Phone

1. Make sure your phone is on the **same WiFi network** as your computer
2. In the terminal where you ran `npm run dev`, look for the **Network** URL
3. It will look like: `http://192.168.1.XXX:5173`
4. Open that URL on your phone's browser

**Example:**
```
➜  Local:   http://localhost:5173/
➜  Network: http://192.168.1.105:5173/   ← Use this on your phone
```

---

## 📁 Adding Content

### Method 1: Using the Upload Button (Easiest)

1. Click the **➕ Upload** button in the app
2. Select or create an account name
3. Choose your photos/videos
4. Add a caption (or leave blank for auto-generated)
5. Click **Upload**
6. Done! Your content appears in the feed

### Method 2: Adding Files Directly

Navigate to the `server/media` folder and create a folder for each account:

```
server/media/
└── MyAccount/
    ├── pfp.jpg              ← Profile picture (optional)
    ├── photo1.jpg           ← Single photo post
    ├── video1.mp4           ← Single video post
    └── vacation/            ← Folder = Carousel post
        ├── photo1.jpg
        ├── photo2.jpg
        └── video.mp4
```

**After adding files manually:**
1. Go back to the app
2. Click the **Rescan** button in the top right
3. Your new content will appear!

---

## 🎠 Creating Carousel Posts

A carousel is multiple photos/videos in one post (swipeable).

### Easy Way: Create a Folder

1. Go to `server/media/YourAccount/`
2. Create a new folder (e.g., `beach-trip`)
3. Put all related photos/videos inside that folder
4. Click **Rescan** in the app

**Example:**
```
server/media/MyAccount/beach-trip/
├── 01-sunrise.jpg
├── 02-swimming.mp4
├── 03-sunset.jpg
└── caption.txt          ← Optional: Add custom caption
```

The folder becomes one carousel post with 3 items!

**Tips:**
- Name files with numbers (`01-`, `02-`) to control order
- Images show first, then videos
- Folder creation date = post date

---

## 🎨 Customization

### Custom Captions

Edit `server/captions.json` to change auto-generated captions:

```json
{
  "default": [
    "Your custom caption here 😊",
    "Another caption option ✨",
    "Add as many as you want 🔥"
  ]
}
```

### Custom Bios

Edit `server/bios.json` to change account bios:

```json
[
  "Your custom bio here 📸",
  "Another bio option 🎨",
  "Mix and match ✨"
]
```

### Custom Follower Count

Create a file named `followers.txt` in the account folder:

```
server/media/MyAccount/followers.txt
```

Content:
```
2500000
```

---

## ⚙️ Configuration (Advanced)

### Change the Server Port

Create `server/.env`:
```bash
PORT=3001
```

### Point Client to Different Server

Create `client/.env`:
```bash
VITE_API_URL=http://localhost:3001
```

For network access, use your computer's IP:
```bash
# Windows: Open CMD and type: ipconfig
# Mac: System Settings → Network
# Linux: Terminal: ip addr

VITE_API_URL=http://YOUR_IP:3001
```

---

## 🛠️ Troubleshooting

### "npm: command not found"
- Node.js isn't installed or not in PATH
- Restart your terminal after installing Node.js
- On Windows, restart your computer

### "Port 3001 already in use"
- Another app is using that port
- Change the port in `server/.env` to `PORT=3002`
- Or stop the other app

### "Cannot GET /"
- Server isn't running
- Make sure you ran `npm start` in the `server` folder
- Check that the terminal shows "Server running..."

### Videos won't play
- Check file format (.mp4 and .webm work best)
- Try re-encoding: `ffmpeg -i input.mov -c:v libx264 output.mp4`

### Content not showing after upload
- Click the **Rescan** button
- Refresh the page
- Check that files are in `server/media/AccountName/`

### Can't access from phone
- Make sure phone is on same WiFi
- Check firewall isn't blocking port 5173
- Windows: Allow Node.js through firewall when prompted

---

## 🔄 Updating ScrollSim

```bash
# Pull latest changes
git pull

# Update server dependencies
cd server
npm install

# Update client dependencies
cd ../client
npm install

# Restart both servers
```

---

## 📂 Project Structure

```
scrollsim/
├── client/                 ← Frontend (React app)
│   ├── src/
│   │   ├── components/    ← UI components
│   │   └── config.js      ← API settings
│   └── package.json
│
├── server/                 ← Backend (Node.js)
│   ├── media/             ← YOUR CONTENT GOES HERE
│   ├── captions.json      ← Caption templates
│   ├── bios.json          ← Bio templates
│   ├── server.js          ← Main server code
│   └── package.json
│
└── README.md              ← This file
```

---

## 💡 Tips & Tricks

### Keyboard Shortcuts
- **J** - Scroll down to next post
- **K** - Scroll up to previous post
- **L** - Like post (coming soon)

### Best Practices
- Use consistent naming for files (`01-`, `02-`, etc.)
- Keep videos under 100MB for best performance
- Use `.jpg` for photos, `.mp4` for videos
- Create separate accounts for different content types

### Performance
- The app works best with 100-500 posts per account
- For 1000+ posts, consider creating multiple accounts
- Videos load thumbnails only until you click play

---

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest features
- Submit pull requests

---

## 📄 License

MIT License - see LICENSE file for details

---

## 🆘 Need Help?

- **GitHub Issues:** [Report bugs or ask questions](https://github.com/yourusername/scrollsim/issues)
- **Discussions:** [Community help and ideas](https://github.com/yourusername/scrollsim/discussions)

---

## 🎉 That's It!

You're ready to use ScrollSim! Start by:
1. Clicking **Upload** and adding your first post
2. Or create a folder in `server/media/YourName/` and add some photos
3. Explore the interface and have fun organizing your content!

**Enjoy!** 🚀
