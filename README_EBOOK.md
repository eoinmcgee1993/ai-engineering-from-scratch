# LEXIS OS Emagazine - Standalone PDF Generator

**Professional interactive PDF ebook generator for the LEXIS Cognitive OS technical narrative.**

![Status](https://img.shields.io/badge/status-production%20ready-green)
![Node](https://img.shields.io/badge/node-%3E%3D14.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-blue)

---

## 🚀 Quick Start

### 1. Clone & Install

```bash
# Clone the repository
git clone https://github.com/eoinmcgee1993/ai-engineering-from-scratch.git
cd ai-engineering-from-scratch

# Install dependencies
npm install
```

### 2. Generate PDF

```bash
npm run generate
```

✅ **Done!** Your PDF is ready at: `./dist/LEXIS_OS_Emagazine_Q3_2026.pdf`

---

## 📄 What You Get

A **6-page professional ebook** with:

✓ **Cover Page** - Issue #1 Q3 2026 specifications  
✓ **Technical Interview** - 2 pages of deep-dive discussion  
✓ **Architecture Blueprints** - 6-layer cognitive OS diagram  
✓ **High-Fidelity Design** - Dark-mode optimized rendering  
✓ **Print-Ready** - 300 DPI resolution  
✓ **Professional Metadata** - Title, author, keywords embedded

---

## 📋 Page Structure

```
Page 1 (Front)   → Cover with Title & Status
Page 1 (Back)    → Specifications & Environment Matrix
Page 2 (Front)   → The Paranoid Operator Interview
Page 2 (Back)    → Dialectic Metrics Discussion
Page 3 (Front)   → Core Architecture Layers
Page 3 (Back)    → Transaction Projections & Details
```

---

## 🛠️ Technical Details

### Requirements

- **Node.js** 14.0 or higher
- **npm** or yarn
- ~50MB disk space

### Dependencies

- `jspdf` ^2.5.1 - PDF generation library

### Supported Platforms

- ✅ macOS (Intel & Apple Silicon)
- ✅ Windows (32-bit & 64-bit)
- ✅ Linux (all distributions)

---

## 📝 Customization

### Edit Content

Open `generate-ebook.js` and modify the `pages` array:

```javascript
const pages = [
  {
    title: 'COVER',
    front: {
      header: 'LEXIS_OS_ISSUE_01 // Q3_2026',
      title: 'YOUR TITLE HERE',
      // ... more content
    },
    // ...
  },
];
```

### Change Colors

Modify the `colors` object at the top of the script:

```javascript
const colors = {
  cyan: [34, 211, 238],        // RGB values
  white: [244, 244, 245],
  // ... more colors
};
```

### Output Location

Edit this line to change where the PDF is saved:

```javascript
const filename = path.join(outputDir, 'YOUR_FILENAME.pdf');
```

---

## 🎯 Usage Examples

### Generate with custom output name

```bash
# Edit generate-ebook.js line ~200
# Change: const filename = path.join(outputDir, 'LEXIS_OS_Emagazine_Q3_2026.pdf');
# To:     const filename = path.join(outputDir, 'MyCustomName.pdf');
npm run generate
```

### Run multiple times

```bash
npm run generate  # Generates dist/LEXIS_OS_Emagazine_Q3_2026.pdf
npm run generate  # Overwrites the file
```

---

## 📊 Output Example

```
🚀 LEXIS OS Emagazine Generator v1.0.0
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📄 Rendering COVER (Front)...
📄 Rendering COVER (Back)...
📄 Rendering INTERVIEW (Front)...
📄 Rendering INTERVIEW (Back)...
📄 Rendering ARCHITECTURE (Front)...
📄 Rendering ARCHITECTURE (Back)...
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ EBOOK GENERATED SUCCESSFULLY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📦 File: /path/to/dist/LEXIS_OS_Emagazine_Q3_2026.pdf
📊 Pages: 6
💾 Size: 187.45 KB
```

---

## ⚠️ Troubleshooting

### Error: "npm: command not found"

**Solution**: Install Node.js from https://nodejs.org/

```bash
# Verify installation
node --version
npm --version
```

### Error: "Permission denied"

**Solution**: Make the script executable

```bash
chmod +x generate-ebook.js
node generate-ebook.js
```

### Error: "Cannot find module 'jspdf'"

**Solution**: Install dependencies

```bash
npm install
```

### PDF not appearing in dist folder

**Solution**: Check directory permissions

```bash
ls -la dist/
mkdir -p dist
npm run generate
```

---

## 🔧 Advanced Options

### Use as Node module

```javascript
// In your own Node.js project
const { spawnSync } = require('child_process');
const result = spawnSync('npm', ['run', 'generate']);
```

### Batch generate multiple versions

```bash
# Create a shell script to generate multiple times
for i in {1..10}; do
  npm run generate
done
```

---

## 📦 File Structure

```
ai-engineering-from-scratch/
├── generate-ebook.js          # Main generator script
├── package.json               # Dependencies & scripts
├── README.md                  # This file
└── dist/                      # Output directory (created on first run)
    └── LEXIS_OS_Emagazine_Q3_2026.pdf
```

---

## 🔐 Security

- ✅ **100% Offline** - No internet required after installation
- ✅ **No Data Collection** - All processing local
- ✅ **Open Source** - Code is transparent and auditable
- ✅ **MIT Licensed** - Free for commercial use

---

## 📚 API Reference

### generateEbook()

Main function that creates the PDF.

```javascript
generateEbook()  // Returns: void (writes file to disk)
```

### Configuration Objects

#### Page Object

```javascript
{
  title: string,              // Page section name
  front: ContentObject,       // Front side content
  back: ContentObject         // Back side content
}
```

#### Content Types

```javascript
// Cover content
{
  header: string,
  title: string,
  status: string,
  description: string
}

// Interview content
{
  heading: string,
  content: string
}

// Architecture content
{
  heading: string,
  architecture: string,
  subsection: {
    title: string,
    desc: string
  }
}
```

---

## 🚢 Deployment

### Docker

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "run", "generate"]
```

Build and run:

```bash
docker build -t lexis-ebook .
docker run -v $(pwd)/dist:/app/dist lexis-ebook
```

### GitHub Actions

```yaml
name: Generate Ebook
on: [push]
jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
        with:
          node-version: '18'
      - run: npm install
      - run: npm run generate
      - uses: actions/upload-artifact@v2
        with:
          name: ebook
          path: dist/
```

---

## 📄 License

MIT License - See LICENSE file for details

---

## 👨‍💻 Author

**Owen McGee**  
Creator of LEXIS Cognitive OS

---

## 🙏 Support

For issues, feature requests, or questions:

1. Check existing GitHub issues
2. Create a new issue with:
   - Node.js version (`node --version`)
   - OS information
   - Error message / screenshot
   - Steps to reproduce

---

## 📋 Changelog

### v1.0.0 (Current)
- ✅ Initial release
- ✅ 6-page emagazine with full content
- ✅ Production-ready PDF generation
- ✅ Dark-mode optimized styling
- ✅ Print-ready resolution

---

## 🎯 Roadmap

Future enhancements:
- [ ] CLI argument support for custom output names
- [ ] Template system for multiple ebook styles
- [ ] Batch generation mode
- [ ] Image embedding support
- [ ] Dynamic content from JSON files

---

**LEXIS COGNITIVE OS V1.0.0**  
**The Machine That Doesn't Blink**  
**© Q3 2026 // All Rights Reserved**  
**CLASSIFIED // EXECUTIVE BRIEFING**

---

*Last updated: Q3 2026*
