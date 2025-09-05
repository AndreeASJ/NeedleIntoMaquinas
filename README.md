# EISENHOLZ - Industrial Machinery Experience

🏭 **EISENHOLZ** - A 3D interactive experience showcasing industrial machinery and equipment.

## 🚀 Live Demo

This project is hosted on GitHub Pages and can be embedded in iframes for integration with mrxplatform.com.

**Live URL:** `https://andreeasj.github.io/NeedleIntoMaquinas/`

## 📋 Project Overview

This is a 3D interactive experience built with Unity and powered by Needle Engine, featuring:

- **Interactive 3D Models**: High-quality industrial machinery and equipment
- **Progressive Loading**: Optimized asset loading with LOD (Level of Detail) system
- **WebGL Optimization**: Compressed textures and efficient rendering
- **Responsive Design**: Works across desktop and mobile devices
- **iframe Ready**: Designed for seamless embedding in web applications

## 🛠️ Technical Stack

- **Unity 2022.3.62f1**: Game engine for 3D content creation
- **Needle Engine 4.8.9**: Web deployment and optimization (powered by)
- **Three.js 0.169.11**: 3D graphics library
- **WebGL**: Browser-based 3D rendering
- **Progressive GLB**: Optimized 3D model format

## 📁 Project Structure

```
├── index.html              # Main entry point
├── assets/                 # 3D models, textures, and scripts
│   ├── *.glb              # 3D models (progressive loading)
│   ├── *.js               # JavaScript modules
│   ├── *.css              # Stylesheets
│   ├── eisenholz-logo-b.png # EISENHOLZ logo (black background)
│   ├── eisenholz-logo-n.png # EISENHOLZ logo (transparent)
│   └── eisenholz-favicon.ico # EISENHOLZ favicon
├── include/               # External libraries
│   ├── draco/            # Geometry compression
│   ├── ktx2/             # Texture compression
│   └── three/            # Three.js extensions
└── needle.buildinfo.json  # Build metadata
```

## 🎯 Features

### 3D Rendering
- **Progressive Loading**: Models load in multiple quality levels
- **LOD System**: Automatic detail reduction based on distance
- **Compressed Assets**: Draco geometry and KTX2 texture compression
- **Optimized Shaders**: Efficient rendering pipeline

### Performance
- **Asset Optimization**: 33MB total size with efficient compression
- **Lazy Loading**: Assets load as needed
- **Memory Management**: Automatic cleanup and garbage collection
- **Cross-Platform**: Works on desktop and mobile browsers

### Integration
- **iframe Compatible**: Designed for embedding in web applications
- **CORS Ready**: Proper headers for cross-origin embedding
- **Responsive**: Adapts to container size
- **Touch Support**: Mobile-friendly interactions

## 🔧 Deployment

### GitHub Pages Setup

1. **Repository Configuration**:
   ```bash
   # Clone the repository
   git clone https://github.com/AndreeASJ/NeedleIntoMaquinas.git
   cd NeedleIntoMaquinas
   ```

2. **Enable GitHub Pages**:
   - Go to repository Settings
   - Navigate to Pages section
   - Select "Deploy from a branch"
   - Choose "main" branch and "/ (root)" folder
   - Save settings

3. **Access the Live Site**:
   - URL: `https://andreeasj.github.io/NeedleIntoMaquinas/`
   - Automatic deployment on every push to main branch

### iframe Integration

For embedding in mrxplatform.com, following [official Needle Engine embedding guidelines](https://engine.needle.tools/docs/embedding.html#embedding-a-needle-project-into-an-existing-website):

```html
<iframe 
  src="https://andreeasj.github.io/NeedleIntoMaquinas/"
  width="100%" 
  height="600px"
  frameborder="0"
  allowfullscreen
  allow="xr; xr-spatial-tracking; fullscreen; camera; microphone; accelerometer; gyroscope; display-capture; geolocation;"
  sandbox="allow-scripts allow-same-origin allow-presentation allow-forms">
</iframe>
```

### Web Component Integration (Alternative)

For projects with custom scripts, you can also use the web component approach:

```html
<script type="module" src="https://andreeasj.github.io/NeedleIntoMaquinas/assets/needle-engine@4.8.9.js"></script>
<needle-engine src="https://andreeasj.github.io/NeedleIntoMaquinas/assets/scene 1.glb"></needle-engine>
```

## 📊 Performance Metrics

- **Total Size**: ~33.7MB (optimized for web)
- **Initial Load**: ~1.6MB (core engine)
- **Progressive Loading**: Assets load on demand
- **Supported Browsers**: Chrome, Firefox, Safari, Edge
- **Mobile Support**: iOS Safari, Android Chrome

## 🔒 Security & Compatibility

- **CORS Headers**: Properly configured for cross-origin embedding
- **Content Security Policy**: Secure iframe embedding
- **HTTPS Only**: Secure connections required
- **Modern Browsers**: WebGL 2.0 support required

## 🚀 Getting Started

### Local Development

1. **Serve Locally**:
   ```bash
   # Using Python
   python -m http.server 8000
   
   # Using Node.js
   npx serve .
   
   # Using PHP
   php -S localhost:8000
   ```

2. **Access**: Open `http://localhost:8000` in your browser

### Production Deployment

The project is automatically deployed to GitHub Pages when changes are pushed to the main branch.

## 📝 Build Information

- **Build Time**: 2025-09-05T17:41:48.858Z
- **Needle Engine**: 4.8.9
- **Unity Version**: 2022.3.62f1
- **Total Files**: 103 assets
- **Compression**: Draco + KTX2

## 🤝 Contributing

This project is part of the mrxplatform.com ecosystem. For contributions or issues, please contact the development team.

## 📄 License

This project is proprietary software developed for mrxplatform.com. All rights reserved.

---

**🏭 EISENHOLZ** | **Powered by Needle Engine** | **Built with Unity** | **Optimized for Web**
