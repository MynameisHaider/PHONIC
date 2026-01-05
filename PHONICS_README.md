# Phonics Cards Web Application

A production-ready phonics flash cards web application designed for early childhood education. Perfect for teaching letters A-Z with images, sounds, and example sentences.

## 🎯 Features

### Core Features
- **Complete A-Z Phonics Cards**: 26 letter cards with sounds and words
- **Audio Support**: Text-to-Speech for letters, words, and sentences
- **PDF Download**: Download any phonics card as a printable PDF
- **Kid-Friendly Design**: Bright colors, large fonts, and engaging visuals
- **Responsive Layout**: Works on mobile, tablet, desktop, and projectors
- **Quick Navigation**: Jump directly to any letter with alphabet buttons

### Educational Content
Each phonics card includes:
- Uppercase letter display
- Phonics sound pronunciation (e.g., /æ/ for A)
- Three child-friendly words (CVC or beginner-friendly)
- One simple example sentence
- Emoji placeholders for images

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ or Bun
- Next.js 15
- z-ai-web-dev-sdk (for TTS and image generation)

### Installation

1. **Clone or navigate to the project directory**
   ```bash
   cd /home/z/my-project
   ```

2. **Install dependencies** (already done)
   ```bash
   bun install
   ```

3. **Start the development server** (already running)
   ```bash
   bun run dev
   ```

4. **Access the application**
   ```
   http://localhost:3000
   ```

## 📁 Project Structure

```
phonics-cards/
├── src/
│   ├── app/
│   │   ├── page.tsx              # Main phonics cards page (frontend)
│   │   ├── layout.tsx            # Root layout
│   │   └── api/
│   │       ├── phonics/
│   │       │   └── route.ts      # GET /api/phonics - Serves phonics data
│   │       ├── tts/
│   │       │   └── route.ts      # POST /api/tts - Text-to-Speech API
│   │       ├── generate-pdf/
│   │       │   └── route.ts      # POST /api/generate-pdf - PDF generation
│   │       └── generate-image/
│   │           └── route.ts      # POST /api/generate-image - AI image generation
│   ├── components/ui/            # shadcn/ui components
│   ├── lib/
│   │   ├── db.ts                 # Database utilities
│   │   └── utils.ts              # Utility functions
│   └── hooks/                    # React hooks
├── data/
│   └── phonics.json              # Complete A-Z phonics data
├── public/
│   ├── images/
│   │   └── phonics/              # Generated phonics word images
│   ├── logo.svg
│   └── robots.txt
├── package.json
└── README.md
```

## 🎨 UI/UX Design

### Design Philosophy
- **Kid-Friendly**: Large, readable fonts with bright, engaging colors
- **Accessible**: High contrast, clear navigation, keyboard-friendly
- **Responsive**: Mobile-first design that scales to all devices
- **Educational**: Clear visual hierarchy for learning focus

### Color Scheme
- **Primary**: Orange (`#f97316`) - Energetic and warm
- **Secondary**: Purple (`#9c27b0`) - Creative and engaging
- **Accent**: Blue (`#2196f3`) - Trustworthy and calming
- **Success**: Green (`#4caf50`) - Positive reinforcement

### Typography
- Large, bold fonts for letters (9rem - 12rem)
- Clear, readable fonts for words and sentences
- Responsive sizing for different screen sizes

## 🔌 API Endpoints

### GET `/api/phonics`
Returns complete phonics data for all letters A-Z.

**Response:**
```json
{
  "phonics": [
    {
      "letter": "A",
      "sound": "/æ/",
      "words": [
        { "word": "Apple", "image": "/images/phonics/apple.png" },
        { "word": "Ant", "image": "/images/phonics/ant.png" },
        { "word": "Alligator", "image": "/images/phonics/alligator.png" }
      ],
      "sentence": "An ant ate an apple."
    },
    ...
  ]
}
```

### POST `/api/tts`
Generates audio from text using Text-to-Speech.

**Request:**
```json
{
  "text": "Apple",
  "type": "word",
  "voice": "tongtong",
  "speed": 0.9
}
```

**Response:** WAV audio file

### POST `/api/generate-pdf`
Generates a PDF for a phonics card.

**Request:**
```json
{
  "letter": "A",
  "sound": "/æ/",
  "words": [
    { "word": "Apple", "image": "/images/phonics/apple.png" },
    { "word": "Ant", "image": "/images/phonics/ant.png" },
    { "word": "Alligator", "image": "/images/phonics/alligator.png" }
  ],
  "sentence": "An ant ate an apple."
}
```

**Response:** PDF file (downloadable)

### POST `/api/generate-image`
Generates a cartoon-style image for a phonics word using AI.

**Request:**
```json
{
  "word": "Apple",
  "letter": "A"
}
```

**Response:**
```json
{
  "success": true,
  "filename": "/images/phonics/apple.png",
  "image": "data:image/png;base64,..."
}
```

## 📚 Content Management

### Adding New Phonics Content

To add or modify phonics content, edit `/data/phonics.json`:

```json
{
  "letter": "A",
  "sound": "/æ/",
  "words": [
    { "word": "Apple", "image": "/images/phonics/apple.png" },
    { "word": "Ant", "image": "/images/phonics/ant.png" },
    { "word": "Alligator", "image": "/images/phonics/alligator.png" }
  ],
  "sentence": "An ant ate an apple."
}
```

**Guidelines for content:**
- Use simple, CVC words (Consonant-Vowel-Consonant) when possible
- Keep sentences under 15 words
- Use age-appropriate vocabulary
- Maintain consistent structure across all letters

## 🖼️ Image Management

### Image Requirements
- **Format**: PNG (preferred) or JPG
- **Size**: 256x256 pixels recommended
- **Style**: Cartoon-style, child-friendly illustrations
- **Background**: Transparent or white
- **Color**: Bright, engaging colors suitable for children

### Image Naming Convention
Images should be named using lowercase words:
```
apple.png
ant.png
alligator.png
ball.png
bear.png
```

### Adding Custom Images

1. **Place images in the correct directory:**
   ```bash
   /home/z/my-project/public/images/phonics/
   ```

2. **Follow naming convention:**
   - Use lowercase
   - Use the word name (e.g., `apple.png`)
   - Avoid spaces and special characters

3. **Update phonics.json:**
   Update the image path to match your filename:
   ```json
   { "word": "Apple", "image": "/images/phonics/apple.png" }
   ```

### Image Generation Options

#### Option 1: AI Image Generation (Built-in)
The application includes an AI image generation API:
```bash
curl -X POST http://localhost:3000/api/generate-image \
  -H "Content-Type: application/json" \
  -d '{"word": "Apple", "letter": "A"}'
```

#### Option 2: Free Clipart Resources
- OpenClipart (https://openclipart.org)
- Pixabay (https://pixabay.com)
- Unsplash (https://unsplash.com)
- Freepik (https://www.freepik.com)

#### Option 3: Paid Stock Images
- Shutterstock
- Adobe Stock
- iStock

#### Option 4: Create Your Own
- Use Canva (https://canva.com)
- Use Figma or Adobe Illustrator
- Draw and scan your own illustrations

## 🔊 Audio Management

### Audio Features
The application uses Text-to-Speech (TTS) to generate audio on-demand:
- Letter sounds
- Word pronunciations
- Example sentences

### Audio Generation
Audio is generated dynamically using the z-ai-web-dev-sdk:
- No need to pre-record audio files
- Consistent, clear pronunciation
- Adjustable speed (slower for children)
- Multiple voice options available

### Custom Audio (Optional)

If you prefer using pre-recorded audio files:

1. **Create audio directory:**
   ```bash
   mkdir -p /home/z/my-project/public/audio/{letters,words,sentences}
   ```

2. **Add audio files:**
   - `/public/audio/letters/a.wav`
   - `/public/audio/words/apple.wav`
   - `/public/audio/sentences/a-sentence.wav`

3. **Modify the code to use audio files:**
   Update the `playAudio` function in `page.tsx` to play audio files instead of using TTS.

### Audio File Specifications
- **Format**: WAV (preferred) or MP3
- **Quality**: 44.1kHz or 48kHz
- **Duration**: 1-3 seconds for letters/words, 3-5 seconds for sentences
- **Volume**: Consistent levels across all files

## 📄 PDF Download

The application allows users to download phonics cards as PDF files:

- **Format**: A4 size
- **Content**: Letter, sound, words, and sentence
- **Styling**: Professional, print-ready design
- **Filename**: `phonics-{letter}.pdf` (e.g., `phonics-A.pdf`)

## 🎓 Educational Use Cases

### Classroom Settings
- **Whole Class Learning**: Project on smartboard for group lessons
- **Individual Practice**: Students use tablets or computers
- **Assessment**: Teachers can use cards for quick assessments
- **Homework**: PDF cards can be printed for home practice

### Home Learning
- **Parent-Guided Learning**: Parents use cards with children
- **Self-Paced Learning**: Children can explore independently
- **Printable Materials**: PDFs can be printed offline

### Special Education
- **Visual Learners**: Large images and clear text
- **Auditory Learners**: Audio support for pronunciation
- **Kinesthetic Learners**: Interactive buttons for engagement

## 🛠️ Development

### Available Scripts
```bash
# Start development server
bun run dev

# Run linting
bun run lint

# Build for production
bun run build

# Start production server
bun run start
```

### Tech Stack
- **Framework**: Next.js 15 with App Router
- **Language**: TypeScript 5
- **Styling**: Tailwind CSS 4
- **UI Components**: shadcn/ui (New York style)
- **PDF Generation**: jsPDF
- **AI Services**: z-ai-web-dev-sdk (TTS, Image Generation)

### Code Quality
- ESLint for code quality
- TypeScript for type safety
- Clean, commented code
- Meaningful variable names
- Extensible architecture

## 🌐 Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## 📱 Responsive Breakpoints

- **Mobile**: < 640px (sm)
- **Tablet**: 640px - 1024px (md)
- **Desktop**: 1024px - 1280px (lg)
- **Large Desktop**: > 1280px (xl)

## 🔒 Privacy & Offline Usage

### Online Features
- Text-to-Speech generation (requires internet)
- AI image generation (requires internet)

### Offline Capability
The application can work offline for:
- Viewing phonics cards (if images are pre-loaded)
- Navigation between letters
- PDF generation (uses local generation)

To make it fully offline:
1. Pre-generate all images
2. Pre-download all audio files
3. Cache the application

## 🐛 Troubleshooting

### Common Issues

**Issue**: Phonics cards not loading
- **Solution**: Check that `/data/phonics.json` exists and is valid JSON

**Issue**: Audio not playing
- **Solution**: Check browser audio permissions and internet connection (for TTS)

**Issue**: PDF not downloading
- **Solution**: Check browser popup blocker settings

**Issue**: Images not displaying
- **Solution**: Ensure images are in `/public/images/phonics/` directory

## 📞 Support & Feedback

For issues, questions, or suggestions:
- Check the troubleshooting section above
- Review the code comments for implementation details
- Ensure all dependencies are installed correctly

## 📝 License

This project is part of the z-ai-web-dev-sdk ecosystem.

## 🎉 Acknowledgments

- Built with Next.js 15 and TypeScript
- UI components from shadcn/ui
- Icons from Lucide React
- PDF generation with jsPDF
- AI services from z-ai-web-dev-sdk

---

**Version**: 1.0.0
**Last Updated**: 2025
**Target Audience**: Early childhood educators, parents, and young learners (ages 4-7)
