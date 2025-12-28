# ScrollSim

A self-hosted visual content management system with a modern feed-based interface.

## Features

- 📸 **Photo & Video Support** - Display images and videos in an organized feed
- 🎠 **Carousel Posts** - Group multiple media files together
  - Time-based: Files uploaded at the same time auto-group
  - Folder-based: Create a folder, all files inside = one post
- 🎥 **Video Management** - Duration display, sorting by length
- 🌙 **Dark Mode** - Easy on the eyes
- 📱 **Responsive Design** - Works on desktop and mobile
- 🔒 **Privacy First** - Everything stays on your local network

## Use Cases

- Content creators planning visual posts
- Photographers organizing portfolio presentations
- Agencies demonstrating content strategies
- Personal media library with social-style browsing
- Testing content layouts and combinations

## Quick Start

### Prerequisites
- Node.js 16+ 
- npm or yarn

### Installation

1. Clone the repository
```bash
git clone https://github.com/yourusername/scrollsim.git
cd scrollsim
```

2. Set up the server
```bash
cd server
npm install
cp .env.example .env
# Edit .env if needed
npm start
```

3. Set up the client (in a new terminal)
```bash
cd client
npm install
cp .env.example .env
# Edit .env to point to your server
npm run dev
```

4. Open http://localhost:5173

## Configuration

### Client Setup
Create `client/.env`:
```bash
VITE_API_URL=http://localhost:3001
```

For network access, use your computer's IP:
```bash
# Find your local IP
# Windows: ipconfig
# Mac/Linux: ifconfig or ip addr

VITE_API_URL=http://YOUR_LOCAL_IP:3001
```

### Server Setup
Create `server/.env`:
```bash
PORT=3001
MEDIA_DIR=./media
```

## Usage

### Adding Content

#### Option 1: Web Upload
1. Click **Upload** button
2. Select account/create new
3. Choose files
4. Add caption (optional)
5. Upload

#### Option 2: File System
```
server/media/
└── YourAccount/
    ├── pfp.jpg              # Profile picture
    ├── photo1.jpg           # Single post
    ├── video1.mp4           # Video post
    └── vacation/            # Folder = Carousel
        ├── caption.txt      # Optional custom caption
        ├── photo1.jpg
        ├── photo2.jpg
        └── video.mp4
```

After adding files manually, click **Rescan** in the UI.

### Creating Carousels

**Method 1: Time-based**
- Upload multiple files with the same timestamp
- They'll automatically group into a carousel

**Method 2: Folder-based** (Recommended)
- Create a folder in `server/media/Username/`
- Add all carousel files to that folder
- Folder's creation date = post date
- Files are sorted: images first, then videos

### Customization

**Captions:**
Edit `server/captions.json` to customize auto-generated captions.

**Bios:**
Edit `server/bios.json` to customize account bios.

**Follower Counts:**
Create `followers.txt` in account folder:
```
2500000
```

## Project Structure
```
scrollsim/
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/    # UI components
│   │   ├── config.js      # API configuration
│   │   └── main.jsx       # Entry point
│   └── package.json
│
├── server/                 # Express backend
│   ├── media/             # Your content goes here
│   ├── captions.json      # Caption templates
│   ├── bios.json          # Bio templates
│   ├── server.js
│   └── package.json
│
└── README.md
```

## Tech Stack

- **Frontend:** React, Vite, Tailwind CSS, React Router
- **Backend:** Node.js, Express
- **Features:** Infinite scroll, dark mode, responsive design

## Docker Support
```bash
docker-compose up -d
```

See `docker-compose.yml` for configuration.

## Contributing

Contributions welcome! Please feel free to submit a Pull Request.

## License

MIT License - see LICENSE file for details

## Support

- GitHub Issues: [Report bugs or request features]
- Discussions: [Ask questions or share ideas]

---

**Note:** This is a personal media server meant for local/private use. 
Not affiliated with any social media platforms.
