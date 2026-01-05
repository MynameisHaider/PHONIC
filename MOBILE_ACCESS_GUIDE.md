# Access Phonics Cards on Mobile

Complete guide to accessing your Phonics Cards app running on laptop from your mobile device.

## 📱 Overview

You can access the Phonics Cards app from your phone/tablet by:
1. Connecting both devices to the **same network** (WiFi)
2. Finding your laptop's **local IP address**
3. Opening the app on mobile using that IP address

---

## 🌐 Step 1: Connect Devices to Same Network

Both devices must be on the same WiFi network.

### Option A: Use Home WiFi (Recommended)

1. **Connect Laptop** to your home WiFi
2. **Connect Mobile** to the **same** home WiFi
3. **Same Network Example**:
   - Laptop: Connected to "HomeWiFi"
   - Mobile: Connected to "HomeWiFi" ✓

### Option B: Create Mobile Hotspot

If you don't have WiFi, use your laptop as hotspot:

#### macOS (iPhone Hotspot)
```bash
# On Mac:
1. Click Apple menu → System Preferences → Sharing
2. Select "Internet Sharing"
3. Share from: WiFi / Ethernet
4. To computers using: iPhone USB
5. Connect iPhone to Mac via USB
6. Phone's Personal Hotspot will appear in Mac's list
```

#### Windows Hotspot
1. **Windows Settings** → Network & Internet
2. **Mobile Hotspot** → Turn ON
3. **Note network name** (e.g., "MyHotspot")
4. **Note password** (or set your own)
5. **Connect phone** to this hotspot using password

---

## 🔍 Step 2: Find Your Laptop's IP Address

### On macOS

**Option 1: System Settings**
```
1. Apple menu → System Preferences → Network
2. Select your active connection (WiFi)
3. Click "Advanced..." button
4. Go to "TCP/IP" tab
5. Look for "IPv4 Address" (e.g., 192.168.1.5)
```

**Option 2: Terminal (Faster)**
```bash
# Open Terminal (Cmd + Space, type "Terminal")

# For WiFi connection:
ifconfig | grep "inet " | grep -v 127.0.0.1

# Output example:
inet 192.168.1.5 netmask 0xffffff00 broadcast 192.168.1.255
#            ↑ Your IP is: 192.168.1.5
```

### On Windows

**Option 1: Settings App**
```
1. Windows Key → Type "Network Status"
2. Click "Change adapter options"
3. Right-click your WiFi connection
4. Click "Status" → "Details"
5. Look for "IPv4 Address" (e.g., 192.168.1.5)
```

**Option 2: Command Prompt (Faster)**
```cmd
# Open Command Prompt
# Press Windows Key + R, type "cmd", press Enter

# Run:
ipconfig

# Look for:
Wireless LAN adapter Wireless Network Connection:
   IPv4 Address. . . . . : 192.168.1.5
   ↑ Your IP is: 192.168.1.5
```

### On Linux

```bash
# Open Terminal

# Run:
ip addr show | grep "inet " | grep -v 127.0.0.1

# Or:
ifconfig | grep "inet "
```

---

## 📱 Step 3: Access from Mobile Device

### Option 1: Browser (Safari on iOS, Chrome on Android)

1. **Open browser** on your mobile device
2. **Type the URL**: `http://YOUR_LAPTOP_IP:3000`
3. **Replace** `YOUR_LAPTOP_IP` with your actual IP

**Examples**:
```
If your IP is 192.168.1.5:
http://192.168.1.5:3000

If your IP is 10.0.0.5:
http://10.0.0.5:3000
```

### Option 2: Create QR Code (Easiest)

**On macOS:**
```bash
# Install qr code generator (one time)
brew install qrencode

# Generate QR code:
echo "http://192.168.1.5:3000" | qrencode -o phonics.png

# Open QR and scan with phone
open phonics.png
```

**Online QR Generator** (No installation needed):
1. Visit: https://www.qrcode-generator.com/
2. Enter: `http://YOUR_LAPTOP_IP:3000`
3. Generate QR code
4. Scan with phone camera

### Option 3: Add to Home Screen (iOS)

1. **Open** URL in Safari on iPhone
2. **Tap Share button** (square with arrow)
3. **Select "Add to Home Screen"**
4. **Name it**: "Phonics Cards"
5. **Add** to home screen
6. Now it opens like a native app!

---

## 🔧 Step 4: Ensure Firewall Allows Access

### On macOS

**Allow incoming connections:**

```bash
# System Preferences → Security & Privacy → Firewall
# If Firewall is ON:
# Click "Firewall Options"
# Ensure your Node/Bun process has access
```

**Or temporarily disable for testing:**
```bash
# System Preferences → Security & Privacy → Firewall
# Turn OFF firewall (for testing only)
# Remember to turn back ON after testing
```

### On Windows

**Allow Node.js through firewall:**

1. **Windows Key** → Type "Firewall"
2. **Windows Defender Firewall** → "Allow an app"
3. **Click "Change settings"** (requires admin)
4. **Browse** and find: `bun` or `node`
5. **Check both** Private and Public networks
6. **Click OK**

**Or create rule for port:**
```cmd
# Run as Administrator:
netsh advfirewall firewall add rule name="PhonicsApp" dir=in action=allow protocol=TCP localport=3000
```

### On Linux

```bash
# Allow port 3000 through firewall
sudo ufw allow 3000/tcp

# Or disable firewall temporarily
sudo ufw disable
```

---

## 🚀 Step 5: Test on Mobile

### Quick Test Checklist

- [ ] Both devices on **same WiFi network**
- [ ] Laptop server **running** (`bun run dev` active)
- [ ] Correct **IP address** used
- [ ] **Port 3000** included in URL
- [ ] Browser opened on mobile
- [ ] App loads successfully

### What You Should See

1. **Phonics Cards home page** loads on mobile
2. **Large, kid-friendly** design optimized for touch
3. **All 26 letters** accessible via quick-jump alphabet
4. **Audio works** - tap speaker icons to hear sounds
5. **PDF downloads** - click download button
6. **Responsive layout** adapts to mobile screen

---

## 🎯 Mobile-Specific Features

### Touch-Friendly Navigation

1. **Swipe gestures**: Not yet implemented (use buttons)
2. **Tap buttons**: Large touch targets (44px minimum)
3. **Voice selector**: Easy to tap dropdown
4. **Quick-jump alphabet**: Horizontal scrollable list

### Mobile Audio

✅ **Works perfectly** using Web Speech API
✅ **No internet** needed for audio
✅ **All system voices** available
✅ **Touch to play** - just tap speaker icon

### Mobile PDF

1. **Tap** "Download Card as PDF" button
2. PDF **downloads** to mobile Downloads folder
3. **Can be shared** or printed from phone

---

## 🔄 Keeping Mobile Access Active

### Laptop Must Stay On

⚠️ **Important**: Your laptop must stay on with `bun run dev` running for mobile access to work.

**If you close laptop**:
- Mobile will show: "This site can't be reached"
- Solution: Restart `bun run dev` on laptop

### Check Server Status on Laptop

```bash
# Terminal shows server status
# You should see:
# ▲ Next.js 15.3.5
# - Local:        http://localhost:3000
# ✓ Ready in 2.5s
```

**If you see requests in terminal**:
```
GET / 200 in 123ms
GET / 200 in 234ms
```
✓ Mobile is successfully accessing your laptop!

---

## 🌐 Troubleshooting Mobile Access

### Issue 1: "This site can't be reached" / "Connection refused"

**Cause**: Wrong IP, server not running, or firewall blocking

**Solutions**:

**Check 1: Verify IP address**
```bash
# On laptop, run again to confirm IP:
# macOS:
ifconfig | grep "inet " | grep -v 127.0.0.1

# Windows:
ipconfig
```

**Check 2: Confirm server is running**
```bash
# On laptop terminal, you should see:
# ✓ Compiled in Xms
# Wait for a file change...
```
If not visible, restart: `bun run dev`

**Check 3: Test on laptop browser**
- Open `http://localhost:3000` on laptop
- If it works, server is fine
- Issue is network/IP

**Check 4: Check firewall** (see Step 4 above)
- Temporarily disable firewall
- Test mobile access
- Re-enable firewall once working

### Issue 2: Page Loads Slowly

**Cause**: Weak WiFi signal or laptop performance

**Solutions**:
- **Move devices closer** to WiFi router
- **Connect laptop** via Ethernet if available
- **Close other apps** on laptop to free resources
- **Reduce number of browser tabs** on mobile

### Issue 3: Mobile Shows Desktop Version

**Cause**: Browser in "Desktop mode"

**Solutions**:

**iOS Safari:**
1. Tap "Aa" icon in address bar
2. Select "Request Desktop Website"
3. Toggle OFF (should be unchecked)

**Android Chrome:**
1. Tap ⋮ menu (three dots)
2. Ensure "Desktop site" is OFF

### Issue 4: Audio Not Playing on Mobile

**Cause**: Mobile browser doesn't support Web Speech API

**Solutions**:

**iOS Safari**: ✅ Should work natively
**Android Chrome**: ✅ Should work natively
**Other browsers**: Try Chrome or Safari

**Test in browser console**:
```javascript
// On mobile, open browser DevTools (if available)
// Or connect phone to computer and use Chrome DevTools
console.log(window.speechSynthesis)
// Should show: SpeechSynthesis { ... }
```

### Issue 5: Buttons Too Small to Tap

**Cause**: Mobile browser zoom level

**Solutions**:
- **Double-tap to zoom in** if needed
- **Use landscape mode** for larger buttons
- **Increase text size** in mobile browser settings

---

## 📡 Advanced: Use Tunnel for Remote Access

Want to access from **anywhere** (different WiFi/cellular)?

### Option 1: ngrok (Easiest)

```bash
# Install ngrok (one time)
brew install ngrok  # macOS
# or: choco install ngrok  # Windows

# Expose port 3000:
ngrok http 3000

# Output:
# Forwarding:   https://abc123.ngrok-free.app -> http://localhost:3000
#                                   ↑ Use this URL on mobile anywhere!
```

**Then on mobile, open:**
```
https://abc123.ngrok-free.app
```

### Option 2: LocalTunnel

```bash
# Install localtunnel
npm install -g localtunnel

# Expose port 3000:
localtunnel --port 3000

# Output:
# your url is: https://randomname.localtunnel.me
#                    ↑ Use this URL on mobile anywhere
```

### Option 3: CloudFlare Tunnel

```bash
# Install cloudflared
brew install cloudflared

# Expose port 3000:
cloudflared tunnel --url http://localhost:3000
```

---

## 📱 Mobile Browser Recommendations

### iOS (iPhone/iPad)

**Best Browsers:**
- ✅ **Safari** (Best, native support)
- ✅ **Chrome** (Good alternative)

**Settings:**
- Turn OFF "Request Desktop Website"
- Allow JavaScript (default: ON)
- Enable cookies (default: ON)

### Android

**Best Browsers:**
- ✅ **Chrome** (Best, native support)
- ✅ **Firefox** (Good alternative)
- ✅ **Samsung Internet** (Good)

**Settings:**
- Disable "Desktop site" mode
- Enable JavaScript (default: ON)
- Clear cache if issues occur

---

## 💡 Pro Tips for Mobile Use

### Tip 1: Add to Home Screen

**iOS:**
```
Safari → Share → Add to Home Screen
```

**Android Chrome:**
```
Chrome → ⋮ → Add to Home Screen
```

Now it opens like a native app! 📱

### Tip 2: Use Landscape Mode

For younger children, landscape (horizontal) orientation:
- Shows larger text and buttons
- Easier to tap for small hands
- Better for tablets

### Tip 3: Disable Auto-Lock

On your mobile device settings:
- **Display** → Auto-Lock → Never (while using app)
- Prevents screen from turning off during lessons

### Tip 4: Use Guided Access (iOS) / App Pinning (Android)

**For classroom use with young children:**

**iOS Guided Access:**
```
Settings → Accessibility → Guided Access → Enable
Then: Triple-click home button when in app → Start
Children can't accidentally exit!
```

**Android App Pinning:**
```
Enable in Security settings
Pin the app screen
Requires PIN to exit
```

---

## 🎓 Educational Use: Mobile in Classroom

### Teacher's Laptop + Student Tablets

1. **Teacher runs server** on laptop connected to projector
2. **Students connect** to same WiFi network
3. **Students open** app URL on their tablets
4. **Everyone follows** same letter at own pace
5. **Audio works individually** - no interference

### Station Rotation

1. **Set up multiple devices** with app open
2. **Assign stations** to students (A, B, C...)
3. **Rotate students** every 5-10 minutes
4. **Each station** has different letter cards

---

## 🚨 Common Mistakes

### ❌ Wrong IP Address

**Problem**: Using `localhost:3000` on mobile
**Solution**: Mobile needs `http://192.168.X.X:3000` (laptop's IP)
- `localhost` only works on the same device

### ❌ Different WiFi Networks

**Problem**: Laptop on WiFi A, phone on WiFi B
**Solution**: Both devices on same network

### ❌ Server Not Running

**Problem**: Closed terminal or stopped `bun run dev`
**Solution**: Keep laptop terminal open with server running

### ❌ Firewall Blocking

**Problem**: Laptop firewall blocking connections
**Solution**: Allow Node/Bun or port 3000 through firewall

### ❌ VPN Enabled

**Problem**: VPN on laptop or phone
**Solution**: Disable VPN on both devices for local network access

---

## 📝 Quick Reference Card

**On Laptop:**
```bash
cd ~/Desktop/phonic
bun run dev

# Find IP (macOS):
ifconfig | grep "inet " | grep -v 127.0.0.1

# Find IP (Windows):
ipconfig
```

**On Mobile Browser:**
```
Open: http://YOUR_LAPTOP_IP:3000
Example: http://192.168.1.5:3000
```

**Firewall** (if needed):
```bash
# macOS: System Prefs → Security → Firewall → Allow
# Windows: Allow bun/node.exe through firewall
```

---

## ✅ Success Checklist

You know it's working when:

- [ ] Mobile shows Phonics Cards home page
- [ ] Can tap through all 26 letters
- [ ] Audio plays when tapping speaker icons
- [ ] Can select different voices
- [ ] PDF downloads work
- [ ] Touch-friendly buttons respond quickly
- [ ] Layout looks good on mobile screen

---

## 🆘 Still Having Issues?

1. **Double-check IP address** - most common mistake
2. **Restart server** on laptop: `Ctrl+C` then `bun run dev`
3. **Try different browser** on mobile (Safari/Chrome)
4. **Test on laptop** first: `http://localhost:3000`
5. **Check firewall settings** (temporarily disable to test)
6. **Create QR code** if URL typing is difficult

---

**Version**: 1.0.0
**Works**: iOS Safari, iOS Chrome, Android Chrome, Android Firefox
**Network**: Same WiFi or hotspot required
