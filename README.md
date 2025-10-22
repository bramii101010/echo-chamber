# Echo Chamber - Atmospheric Audio Looper

Welcome to Echo Chamber! This is a seamless audio looping web app with atmospheric visuals and audio effects.

## 🎵 What This App Does

- Loops audio files without any gaps or clicks
- Provides real-time waveform visualization
- Includes reverb and delay effects
- Features a dark, atmospheric UI with animated background

## 🚀 Getting Started

### View the Live App
The app is hosted at: `https://bramii101010.github.io/echo-chamber/`

### Run Locally
1. Clone this repository
2. Open `index.html` in any modern web browser
3. That's it! No build process needed.

## 🎨 Customization Guide

### Changing Colors

**Main Color Scheme**
The app uses a purple gradient theme. To change it, find and replace these hex codes:

```css
/* Primary gradient colors */
#667eea  /* Light purple */
#764ba2  /* Dark purple */

/* Find these in the CSS and replace with your colors */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

**Background Colors**
```css
/* Main background gradient */
background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 100%);

/* Container background */
background: rgba(20, 20, 40, 0.8);
```

**Suggestion:** Try these color combinations:
- Ocean theme: `#00d2ff` and `#3a7bd5`
- Sunset theme: `#ff6b6b` and `#feca57`
- Forest theme: `#11998e` and `#38ef7d`
- Neon theme: `#f72585` and `#7209b7`

### Customizing Text

**App Title**
```html
<!-- Find this in the HTML around line 240 -->
<h1>Echo Chamber</h1>
<p class="subtitle">Seamless Audio Looper</p>
```

**Footer**
```html
<!-- Find this around line 285 -->
<div class="footer">Echo Chamber v1.0</div>
```

### Adjusting Effects

**Default Effect Values**
```html
<!-- Find these sliders around line 265-280 -->
<input type="range" id="volumeSlider" min="0" max="100" value="80">
<input type="range" id="reverbSlider" min="0" max="100" value="30">
<input type="range" id="delaySlider" min="0" max="100" value="0">
<input type="range" id="fadeSlider" min="0" max="5" step="0.1" value="0.5">
```

Change the `value` attribute to set different defaults.

**Reverb Settings**
```javascript
// Find this function around line 360
function createReverbImpulse() {
    const rate = audioContext.sampleRate;
    const length = rate * 3;  // Change 3 to adjust reverb length (in seconds)
    
    // The decay rate controls how long reverb lasts
    impulseL[i] = (Math.random() * 2 - 1) * Math.exp(-n * 3); // Change 3 for decay speed
}
```

**Delay Time**
```javascript
// Find this around line 370
delayNode.delayTime.value = 0.3;  // Change to adjust delay time (in seconds)
```

### Customizing the Visualizer

**Visualizer Colors**
```javascript
// Find this around line 565
const gradient = canvasContext.createLinearGradient(0, canvas.height - barHeight, 0, canvas.height);
gradient.addColorStop(0, '#764ba2');  // Top color
gradient.addColorStop(1, '#667eea');  // Bottom color
```

**Visualizer Style**
```javascript
// Around line 550
const barWidth = (canvas.width / bufferLength) * 2.5;  // Adjust bar width
barHeight = (dataArray[i] / 255) * canvas.height * 0.8;  // Adjust height sensitivity
```

**Background Effect**
```javascript
// Around line 545
canvasContext.fillStyle = 'rgba(0, 0, 0, 0.2)';  // Trail effect (lower = longer trails)
```

### Star Animation

**Number of Stars**
```javascript
// Find this around line 295
for (let i = 0; i < 100; i++) {  // Change 100 to add more/fewer stars
```

**Star Size and Appearance**
```css
/* Find this around line 40 */
.star {
    width: 2px;   /* Change star size */
    height: 2px;
    background: white;  /* Change star color */
}
```

### Button Styles

**Button Colors**
```css
/* Find around line 145 */
button {
    background: rgba(102, 126, 234, 0.2);
    color: #667eea;
    border: 2px solid #667eea;
}

button:hover:not(:disabled) {
    background: #667eea;
    color: white;
}
```

## 📁 Code Structure

### HTML Sections
- **Lines 1-40**: HTML setup and CSS styles
- **Lines 230-290**: Main app structure (title, buttons, controls)
- **Lines 293-580**: JavaScript code

### JavaScript Sections
- **Lines 295-310**: Star animation setup
- **Lines 315-335**: Audio context initialization
- **Lines 340-365**: Reverb effect creation
- **Lines 368-390**: File upload handler
- **Lines 393-520**: Play/pause/stop functions
- **Lines 523-550**: Effect controls
- **Lines 553-580**: Visualization

## 🔧 Adding New Features

### Add a New Effect

1. **Add HTML slider:**
```html
<div class="effect-control">
    <label>Your Effect Name</label>
    <div class="slider-container">
        <input type="range" id="yourEffectSlider" min="0" max="100" value="50">
        <span class="value-display" id="yourEffectValue">50%</span>
    </div>
</div>
```

2. **Add JavaScript control:**
```javascript
const yourEffectSlider = document.getElementById('yourEffectSlider');

yourEffectSlider.addEventListener('input', (e) => {
    const value = e.target.value;
    document.getElementById('yourEffectValue').textContent = value + '%';
    // Add your effect logic here
});
```

### Add Multiple Audio Files (Layering)

You'll need to:
1. Create an array to store multiple audio buffers
2. Create multiple source nodes
3. Add UI for managing multiple tracks
4. Mix the audio together

(Let me know if you want help implementing this!)

## 🎯 Quick Customization Checklist

- [ ] Change app colors to match your brand
- [ ] Update the title and subtitle
- [ ] Adjust default effect values
- [ ] Customize visualizer colors
- [ ] Modify number of background stars
- [ ] Change button styles
- [ ] Update footer text

## 💡 Tips

- **Test in multiple browsers** (Chrome, Firefox, Safari) to ensure compatibility
- **Use browser DevTools** (F12) to experiment with styles in real-time
- **Start small**: Change one thing at a time and test
- **Back up your work**: Commit changes to GitHub regularly
- **Mobile testing**: Test on actual devices, not just browser mobile view

## 🐛 Common Issues

**Audio won't play:**
- Make sure the file format is supported (MP3, WAV, OGG)
- Check browser console (F12) for errors
- Some browsers require user interaction before playing audio

**Visualizer not showing:**
- Ensure audio is playing
- Check that canvas dimensions are set correctly

**Effects not working:**
- Audio context might be suspended - click play to resume
- Check that effect values are being applied in the play() function

## 📚 Resources

- [Web Audio API Documentation](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
- [Canvas API Documentation](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
- [CSS Gradients](https://cssgradient.io/)
- [Color Palette Generator](https://coolors.co/)

## 🤝 Contributing

Feel free to experiment and make changes! Some ideas:
- Add preset themes (multiple color schemes)
- Create a playlist feature
- Add audio recording capability
- Implement drag-and-drop file upload
- Add keyboard shortcuts
- Create visual themes (space, underwater, etc.)

## 📝 Version History

- **v1.0** - Initial release with seamless looping, reverb, delay, and visualization

---

**Questions?** Open an issue or reach out to the project owner!

Happy coding! 🎵✨
