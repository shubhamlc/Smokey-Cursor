# 🔥 Smokey Cursor
An interactive WebGL fluid simulation with a love button that triggers a smokey ink-like effect. Move your cursor across the screen to paint fluid, or click the heart to burst a wave of color.

![WebGL](https://img.shields.io/badge/WebGL-990000?style=flat&logo=webgl&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

---

## ✨ Features

- **Real-time fluid simulation** powered by WebGL : runs entirely on the GPU
- **Interactive painting** : move your mouse/finger to trail colorful fluid
- **Love button** : click the heart to trigger a smoky color burst at your cursor position
- **Love counter** : tracks how many times you've clicked the heart
- **Custom cursor** : the default mouse pointer is replaced with a clean red circle, GPU-accelerated with zero lag
- **Touch support** : works on mobile and tablet devices
- **Automatic color cycling** : colors shift over time for a rainbow fluid effect
- **Responsive** : adapts to any screen size

---

## 📁 File Structure

```
├── index.html    # Main HTML structure
├── style.css     # Styles, layout, and custom cursor
├── script.js     # WebGL fluid simulation + interaction logic
└── README.md     # You're reading this
```

---

## 🚀 Getting Started

No build tools, no dependencies, no npm. Just open it.

**Option 1 — Direct open:**
```
Double-click index.html in your file explorer
```

**Option 2 — Local server (recommended to avoid any browser restrictions):**
```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve .
```
Then open `http://localhost:8000` in your browser.

---

## 🎮 How to Use

| Action | Effect |
|--------|--------|
| Move mouse | Paint fluid trails across the screen |
| Click ❤️ button | Trigger a smoky color burst |
| Touch & drag | Works on mobile too |

---

## ⚙️ Configuration

You can tweak the simulation by editing the `config` object at the top of `script.js`:

```js
const config = {
    SIM_RESOLUTION: 128,        // Simulation grid size (lower = faster)
    DYE_RESOLUTION: 1440,       // Visual quality (lower = faster)
    DENSITY_DISSIPATION: 3.5,   // How fast color fades
    VELOCITY_DISSIPATION: 2,    // How fast movement slows down
    PRESSURE: 0.1,              // Fluid pressure
    PRESSURE_ITERATIONS: 20,    // Solver quality (lower = faster)
    CURL: 3,                    // Swirl/vorticity amount
    SPLAT_RADIUS: 0.2,          // Size of each fluid splat
    SPLAT_FORCE: 6000,          // Force applied when moving cursor
    SHADING: true,              // 3D shading effect on fluid
    COLOR_UPDATE_SPEED: 10,     // How fast colors cycle
};
```

---

## 🛠️ How It Works

The simulation is a real Navier-Stokes fluid solver running on the GPU via WebGL shaders. Each frame it:

1. **Computes curl** (vorticity) of the velocity field
2. **Applies vorticity confinement** to keep the fluid swirling naturally
3. **Calculates divergence** of the velocity field
4. **Solves for pressure** using Jacobi iteration
5. **Subtracts the pressure gradient** to make the fluid incompressible
6. **Advects velocity and dye** forward in time

The custom cursor uses `transform: translate()` instead of `top/left` positioning, which means it runs on the GPU compositor thread — completely lag-free.

---

## 🌐 Browser Support

Works in any browser that supports WebGL (which is basically all of them):

- ✅ Chrome / Edge
- ✅ Firefox
- ✅ Safari
- ✅ Mobile browsers (iOS Safari, Chrome Android)

---

## 📄 License

MIT — do whatever you want with it.