# Phonics Cards - Offline Setup Guide

Complete guide to running the Phonics Cards project offline on localhost:3000

## 📁 Project Structure

After downloading, your folder should look like this:

```
phonic/
├── data/
│   └── phonics.json
├── db/
│   └── custom.db
├── examples/
│   └── websocket/
├── mini-services/
├── prisma/
│   └── schema.prisma
├── public/
│   ├── images/
│   │   └── phonics/
│   ├── logo.svg
│   └── robots.txt
├── skills/
├── src/
│   ├── app/
│   │   ├── api/
│   │   │   ├── generate-image/
│   │   │   │   └── route.ts
│   │   │   ├── generate-pdf/
│   │   │   │   └── route.ts
│   │   │   ├── phonics/
│   │   │   │   └── route.ts
│   │   │   └── tts/
│   │   │       └── route.ts
│   │   ├── globals.css
│   │   ├── layout.tsx
│   │   └── page.tsx
│   ├── components/
│   │   └── ui/
│   ├── hooks/
│   └── lib/
├── .env
├── .eslintrc.json
├── Caddyfile
├── bun.lock
├── next.config.ts
├── package.json
├── postcss.config.mjs
├── tailwind.config.ts
├── tsconfig.json
└── README.md
```

## 🎯 Prerequisites

### Required Software

1. **Bun Runtime** (JavaScript runtime and package manager)
   - Download from: https://bun.sh
   - Windows: `powershell -c "irm bun.sh/install.ps1 | iex"`
   - macOS/Linux: `curl -fsSL https://bun.sh/install | bash`

2. **Node.js** (Alternative to Bun)
   - Version: Node.js 18+ recommended
   - Download from: https://nodejs.org

3. **Git** (Optional, for version control)
   - Download from: https://git-scm.com

### System Requirements

- **RAM**: 4GB minimum (8GB recommended)
- **Disk Space**: 500MB minimum
- **OS**: Windows, macOS, or Linux
- **Browser**: Chrome, Firefox, Safari, or Edge (latest version)

## 📥 Step 1: Prepare the Project Folder

### Option A: Download via Command Line (if you have the project files)

```bash
# Navigate to your Desktop
cd ~/Desktop

# Create phonic folder (if it doesn't exist)
mkdir phonic

# Copy all project files to phonic folder
# (Copy the entire Next.js project directory contents)
```

### Option B: Manual Download

1. Create a new folder named `phonic` on your Desktop
2. Download/copy all project files into this folder
3. Ensure the folder structure matches the structure shown above

## 🔧 Step 2: Install Dependencies

### Using Bun (Recommended)

```bash
# Navigate to project folder
cd ~/Desktop/phonic

# Clean install dependencies
bun install

# This will read package.json and install all required packages
# Time: 1-2 minutes on first run
```

### Using Node.js

```bash
# Navigate to project folder
cd ~/Desktop/phonic

# Clean install dependencies
npm install

# This will read package.json and install all required packages
# Time: 2-3 minutes on first run
```

### What Gets Installed?

The following packages will be installed automatically:

- **Next.js 15**: React framework
- **React 19**: UI library
- **TypeScript 5**: Type-safe JavaScript
- **Tailwind CSS 4**: Styling framework
- **shadcn/ui components**: Pre-built UI components
- **jsPDF**: PDF generation library
- **Prisma**: Database ORM
- **z-ai-web-dev-sdk**: AI services (optional, for online features)

## 🗄 Step 3: Set Up Environment (Optional)

The project includes a `.env` file. Check if it exists:

```bash
# Check if .env file exists
ls -la .env

# If it doesn't exist, create it
touch .env
```

For offline use, you typically don't need any environment variables.
If the project has API keys or configuration, they would be in this file.

## 🚀 Step 4: Run the Development Server

### Option A: Using Bun (Recommended)

```bash
# Navigate to project folder
cd ~/Desktop/phonic

# Start development server
bun run dev

# Output:
# ▲ Next.js 15.3.5
# - Local:        http://localhost:3000
# - Network:      http://192.168.x.x:3000
```

### Option B: Using Node.js

```bash
# Navigate to project folder
cd ~/Desktop/phonic

# Start development server
npm run dev

# Output:
# ▲ Next.js 15.3.5
# - Local:        http://localhost:3000
# - Network:      http://192.168.x.x:3000
```

### What Happens When You Run This?

1. **Next.js starts** - The framework boots up
2. **Port 3000 opens** - Local server starts on this port
3. **Compilation begins** - TypeScript and React code compiles
4. **Hot reload activates** - Changes to files auto-reload the page
5. **Ready message appears** - "Ready in X.X seconds"

## 🌐 Step 5: Access the Application

### Local Access

Open your browser and go to:

```
http://localhost:3000
```

### Network Access (Optional)

If you want to access from other devices on the same network:

```bash
# Find your IP address
# Windows:
ipconfig

# macOS/Linux:
ifconfig | grep inet

# Access from other devices:
http://YOUR_IP_ADDRESS:3000
```

Example:
```
http://192.168.1.5:3000
```

## 🎵 Step 6: Test Audio Features

The application uses browser's Web Speech API for audio:

1. Open http://localhost:3000 in your browser
2. Click on any phonics card's audio button
3. Listen to the letter, word, or sentence pronunciation
4. Try different voices from the dropdown in the header

**Note**: Audio works 100% offline using browser's built-in speech synthesis!

## 📥 Step 7: Test PDF Download

1. Click "Download Card as PDF" button
2. The PDF will download to your Downloads folder
3. Open and verify it contains the correct phonics content

## 📚 Using the Application

### Basic Navigation

1. **Browse Letters**: Use Previous/Next buttons
2. **Quick Jump**: Click letters in the alphabet bar
3. **Play Audio**: Click speaker icons to hear pronunciations
4. **Download PDFs**: Click the purple download button
5. **Change Voices**: Select from dropdown in header

### All Features

✅ **26 Phonics Cards** - Complete A-Z set
✅ **Audio Pronunciation** - Letter sounds, words, sentences
✅ **Multiple Voices** - Choose from system voices
✅ **PDF Export** - Download printable cards
✅ **Kid-Friendly Design** - Large text, bright colors
✅ **Responsive** - Works on phones, tablets, desktops

## 🔄 Development Workflow

### Making Changes to the Project

1. **Edit Files**: Any file in `src/` folder
2. **Auto Reload**: Browser updates automatically
3. **Check Terminal**: For compilation status
4. **Fix Errors**: If errors appear, fix and save again

### Common Files to Edit

```
src/app/page.tsx              # Main phonics cards interface
src/app/api/phonics/route.ts  # Phonics data API
data/phonics.json              # A-Z phonics content
src/app/globals.css           # Global styles
```

### Hot Reload Example

```bash
# Edit src/app/page.tsx
# Save file (Ctrl+S / Cmd+S)
# Terminal shows: ✓ Compiled / in 234ms
# Browser automatically refreshes with changes
```

## 🛠️ Troubleshooting

### Issue: Port 3000 Already in Use

**Error Message**:
```
Port 3000 is already in use
```

**Solution 1: Kill existing process**
```bash
# Find process using port 3000
lsof -i :3000

# Kill the process
kill -9 PID

# Try running again
bun run dev
```

**Solution 2: Use a different port**
```bash
# Run on port 3001 instead
PORT=3001 bun run dev

# Access at: http://localhost:3001
```

### Issue: "bun: command not found"

**Error Message**:
```
bun: command not found
```

**Solution**: Install Bun first
```bash
# macOS/Linux
curl -fsSL https://bun.sh/install | bash

# Windows (PowerShell)
powershell -c "irm bun.sh/install.ps1 | iex"

# Then run:
bun run dev
```

### Issue: Dependencies Not Installing

**Error Message**:
```
Error: Cannot find module '...'
```

**Solution 1: Clean install
```bash
# Remove existing node_modules
rm -rf node_modules bun.lock

# Or for npm:
rm -rf node_modules package-lock.json

# Reinstall dependencies
bun install
```

**Solution 2: Update package manager
```bash
# Update Bun
bun upgrade

# Or update npm
npm install -g npm@latest
```

### Issue: Audio Not Playing

**Check 1: Browser support**
```javascript
// Open browser console (F12)
// Run:
console.log('Speech synthesis:', window.speechSynthesis)

// Should show: SpeechSynthesis { ... }
```

**Check 2: Permissions**
- Ensure browser has microphone/speaker permissions
- Check system volume is not muted

**Check 3: Voice loading**
- Wait a few seconds after page load
- Refresh the page
- Try selecting a different voice

### Issue: Page Shows Blank/Loading

**Check 1: Compilation errors**
```bash
# Look in terminal for red error messages
# Fix the errors shown
```

**Check 2: TypeScript errors**
```bash
# Run linter to find issues
bun run lint

# Fix any errors shown
```

**Check 3: Browser console**
```javascript
// Press F12 to open DevTools
// Check Console tab for errors
// Fix any JavaScript errors
```

### Issue: PDF Not Downloading

**Check 1: Browser popup blocker**
- Disable popup blocker for localhost:3000
- Or click "Allow popups" in browser toolbar

**Check 2: Try different browser**
- Chrome/Edge usually work best
- Firefox sometimes blocks blob downloads

## 💡 Tips for Offline Use

### 1. Pre-Load Resources

Before going offline:
1. Open the application in browser
2. Visit all 26 phonics cards
3. Test audio playback for each
4. Browser will cache these resources

### 2. Use HTTPS (Production)

When deploying offline/intranet:
```bash
# Generate production build
bun run build

# Run production server
bun run start
```

### 3. Static Export (Optional)

For completely static files:
```bash
# Edit next.config.ts to enable static export
output: 'export'

# Then build:
bun run build

# Files in out/ folder can be served by any web server
```

## 📦 Production Deployment

### Building for Production

```bash
# Navigate to project
cd ~/Desktop/phonic

# Create optimized production build
bun run build

# Output:
# ✓ Linting and checking validity of types
# ✓ Creating an optimized production build...
# ✓ Compiled successfully
```

### Running Production Server

```bash
# Start production server
bun run start

# Access at: http://localhost:3000
# This is faster than dev mode and doesn't compile on the fly
```

### Deployment Options

1. **Vercel**: `vercel deploy`
2. **Netlify**: `netlify deploy --prod`
3. **Docker**: Create Dockerfile and deploy
4. **Static Server**: Serve `build/` folder with nginx/Apache

## 📊 Project Scripts Available

Check all available scripts in `package.json`:

```bash
# View all scripts
cat package.json | grep -A 20 "scripts"

# Or run without arguments to see help
bun run
```

Common scripts:
```bash
bun run dev      # Development server (hot reload)
bun run build    # Production build
bun run start    # Production server
bun run lint     # Code quality check
bun run db:push  # Push database schema
```

## 🎓 Educational Use

### Classroom Setup

1. **Install on Teacher Computer**: Follow steps 1-4 above
2. **Project to Smartboard**: Connect computer to classroom display
3. **Open Browser**: Navigate to http://localhost:3000
4. **Full Screen**: Press F11 for immersive experience

### Student Access

**Option A: Multiple Devices**
- Run server on teacher computer
- Students access via network IP: `http://TEACHER_IP:3000`
- Each student can work independently

**Option B: Single Device**
- Use smartboard/projector
- Teacher leads interactive session
- Students take turns selecting letters

### Printing PDFs

1. Download individual phonics card PDFs
2. Print as flashcards
3. Laminate for durability
4. Use in offline classroom activities

## 📝 Notes

- The application works **100% offline** after initial setup
- Audio uses browser's **Web Speech API** - no external service needed
- PDF generation works offline with jsPDF
- Images use **emoji placeholders** - can be replaced with local images later
- Data is stored in **JSON files** - no database required for offline use

## 🆘 Need Help?

If you encounter issues:

1. Check the **Troubleshooting** section above
2. Look at **terminal output** for error messages
3. Open **browser DevTools** (F12) for JavaScript errors
4. Check that **Bun/Node** is properly installed
5. Verify you're in the **correct directory** (~/Desktop/phonic)

---

**Version**: 1.0.0
**Last Updated**: 2025
**Platform**: Cross-platform (Windows, macOS, Linux)
