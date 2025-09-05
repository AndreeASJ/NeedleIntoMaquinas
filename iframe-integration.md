# EISENHOLZ - iframe Integration Guide for mrxplatform.com

## 🎯 Quick Integration

### Choosing the Right Embedding Method

Based on the [official Needle Engine documentation](https://engine.needle.tools/docs/embedding.html#embedding-a-needle-project-into-an-existing-website), here are the three main approaches:

1. **Web Component Embedding** - Best for full control and custom scripts
2. **iframe Embedding** - Best for CMS integration (WordPress, etc.)
3. **CDN Embedding** - Best for simple projects with core components only

### Option 1: Web Component Embedding (Recommended)

For projects with custom scripts, use the web component approach:

```html
<script type="module" src="https://andreeasj.github.io/NeedleIntoMaquinas/assets/needle-engine@4.8.9.js"></script>
<needle-engine src="https://andreeasj.github.io/NeedleIntoMaquinas/assets/scene 1.glb"></needle-engine>
```

### Option 2: Basic iframe Embedding

```html
<iframe 
  src="https://andreeasj.github.io/NeedleIntoMaquinas/"
  width="100%" 
  height="600px"
  frameborder="0"
  allowfullscreen
  allow="xr; xr-spatial-tracking; fullscreen; camera; microphone; accelerometer; gyroscope; display-capture; geolocation;"
  sandbox="allow-scripts allow-same-origin allow-presentation allow-forms"
  title="EISENHOLZ - Industrial Machinery Experience">
</iframe>
```

### Option 3: CDN Embedding (For Core Components Only)

If your project uses only core components without custom scripts:

```html
<script type="module" src="https://cdn.jsdelivr.net/npm/@needle-tools/engine/dist/needle-engine.min.js"></script>
<needle-engine src="https://andreeasj.github.io/NeedleIntoMaquinas/assets/scene 1.glb" background-blurriness="0.8"></needle-engine>
```

### Responsive iframe Container

```html
<div class="iframe-container" style="position: relative; width: 100%; height: 0; padding-bottom: 56.25%; /* 16:9 aspect ratio */">
  <iframe 
    src="https://andreeasj.github.io/NeedleIntoMaquinas/"
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
    frameborder="0"
    allowfullscreen
    allow="xr; xr-spatial-tracking; fullscreen; camera; microphone; accelerometer; gyroscope; display-capture; geolocation;"
    sandbox="allow-scripts allow-same-origin allow-presentation allow-forms"
    title="EISENHOLZ - Industrial Machinery Experience">
  </iframe>
</div>
```

## 🔧 Advanced Integration

### React Component Example

```jsx
import React, { useEffect, useRef } from 'react';

const EisenholzMachinery = ({ width = '100%', height = '600px' }) => {
  const iframeRef = useRef(null);

  useEffect(() => {
    const handleMessage = (event) => {
      // Verify origin for security
      if (event.origin !== 'https://andreeasj.github.io') return;
      
      if (event.data.type === 'iframe-ready') {
        console.log('EISENHOLZ iframe is ready');
        // Perform any initialization here
      }
    };

    window.addEventListener('message', handleMessage);
    return () => window.removeEventListener('message', handleMessage);
  }, []);

  return (
    <iframe
      ref={iframeRef}
      src="https://andreeasj.github.io/NeedleIntoMaquinas/"
      width={width}
      height={height}
      frameBorder="0"
      allowFullScreen
      allow="xr; xr-spatial-tracking; fullscreen; camera; microphone; accelerometer; gyroscope; display-capture; geolocation;"
      sandbox="allow-scripts allow-same-origin allow-presentation allow-forms"
      title="Needle Into Máquinas - 3D Interactive Experience"
      style={{
        border: 'none',
        borderRadius: '8px',
        boxShadow: '0 4px 6px rgba(0, 0, 0, 0.1)'
      }}
    />
  );
};

export default EisenholzMachinery;
```

### Vue.js Component Example

```vue
<template>
  <div class="needle-container">
    <iframe
      ref="needleIframe"
      src="https://andreeasj.github.io/NeedleIntoMaquinas/"
      :width="width"
      :height="height"
      frameborder="0"
      allowfullscreen
      allow="xr; xr-spatial-tracking; fullscreen; camera; microphone; accelerometer; gyroscope; display-capture; geolocation;"
      sandbox="allow-scripts allow-same-origin allow-presentation allow-forms"
      title="Needle Into Máquinas - 3D Interactive Experience"
      @load="onIframeLoad"
    />
  </div>
</template>

<script>
export default {
  name: 'EisenholzMachinery',
  props: {
    width: {
      type: String,
      default: '100%'
    },
    height: {
      type: String,
      default: '600px'
    }
  },
  mounted() {
    window.addEventListener('message', this.handleMessage);
  },
  beforeUnmount() {
    window.removeEventListener('message', this.handleMessage);
  },
  methods: {
    handleMessage(event) {
      if (event.origin !== 'https://andreeasj.github.io') return;
      
      if (event.data.type === 'iframe-ready') {
        this.$emit('ready');
      }
    },
    onIframeLoad() {
      this.$emit('loaded');
    }
  }
};
</script>

<style scoped>
.eisenholz-container {
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}
</style>
```

## 🎨 Styling Options

### Custom CSS Classes

```css
.eisenholz-iframe {
  border: none;
  border-radius: 12px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.12);
  transition: box-shadow 0.3s ease;
}

.needle-iframe:hover {
  box-shadow: 0 12px 48px rgba(0, 0, 0, 0.18);
}

.eisenholz-container {
  position: relative;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  padding: 20px;
  border-radius: 16px;
}

.eisenholz-loading {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 18px;
}
```

## 📱 Responsive Design

### Mobile-First Approach

```css
.eisenholz-responsive {
  width: 100%;
  height: 0;
  padding-bottom: 56.25%; /* 16:9 aspect ratio */
  position: relative;
}

.needle-responsive iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

/* Mobile adjustments */
@media (max-width: 768px) {
  .eisenholz-responsive {
    padding-bottom: 75%; /* 4:3 aspect ratio for mobile */
  }
}

@media (max-width: 480px) {
  .eisenholz-responsive {
    padding-bottom: 100%; /* 1:1 aspect ratio for small screens */
  }
}
```

## 🔒 Security Considerations

### Content Security Policy

```html
<meta http-equiv="Content-Security-Policy" 
      content="frame-src https://andreeasj.github.io; 
               script-src 'self' 'unsafe-inline' https://andreeasj.github.io;">
```

### Sandbox Attributes

```html
<!-- Recommended sandbox attributes -->
sandbox="allow-scripts allow-same-origin allow-presentation allow-forms"

<!-- For maximum security (may limit functionality) -->
sandbox="allow-scripts allow-same-origin"
```

## 🚀 Performance Optimization

### Lazy Loading

```html
<iframe 
  src="https://andreeasj.github.io/NeedleIntoMaquinas/"
  loading="lazy"
  width="100%" 
  height="600px"
  frameborder="0"
  allowfullscreen
  sandbox="allow-scripts allow-same-origin allow-presentation">
</iframe>
```

### Intersection Observer for Lazy Loading

```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const iframe = entry.target;
      iframe.src = iframe.dataset.src;
      observer.unobserve(iframe);
    }
  });
});

document.querySelectorAll('[data-src]').forEach(iframe => {
  observer.observe(iframe);
});
```

## 🔧 Troubleshooting

### Common Issues

1. **iframe not loading**: Check CORS headers and HTTPS
2. **Performance issues**: Ensure proper caching headers
3. **Mobile issues**: Verify viewport meta tag
4. **Security warnings**: Review sandbox attributes

### Debug Mode

```javascript
// Enable debug logging
window.addEventListener('message', (event) => {
  console.log('iframe message:', event.data);
  console.log('origin:', event.origin);
});
```

## 📊 Analytics Integration

### Google Analytics

```javascript
// Track iframe interactions
window.addEventListener('message', (event) => {
  if (event.origin === 'https://andreeasj.github.io') {
    gtag('event', 'iframe_interaction', {
      'event_category': 'eisenholz_machinery',
      'event_label': event.data.type
    });
  }
});
```

## 🎯 Best Practices

1. **Always use HTTPS**: Required for WebGL and modern browsers
2. **Set proper dimensions**: Avoid layout shifts
3. **Handle loading states**: Show loading indicators
4. **Test on mobile**: Ensure touch interactions work
5. **Monitor performance**: Use browser dev tools
6. **Implement error handling**: Graceful fallbacks

---

**Ready to integrate?** Copy the basic iframe code above and customize as needed for your mrxplatform.com implementation!
