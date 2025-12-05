# Interactive 3D Graphene Lattice

A high-performance, browser-based 3D simulation of a single-layer Graphene structure. Built with **Three.js**, this project visualizes the atomic honeycomb lattice with accurate chemical geometry and real-time floating wave physics.

> *(Replace the image path below with a screenshot of your simulation)*  
![Graphene Preview](./screenshot.png)

---

## 🎥 Demo Video

> *(Replace the video path below with your demo video or a GIF preview)*  

[▶ **Watch Demo Video**](./demo.mp4)

Or embed directly in GitHub (works when the file exists in the repo):

```markdown
<video src="./demo.mp4" width="600" controls></video>
```

---

## ✨ Features

- **Precise Geometry**  
  Generates a chemically accurate hexagonal (honeycomb) lattice using a staggered “dumbbell” algorithm.

- **High Performance**  
  Utilizes `THREE.InstancedMesh` for atoms and `THREE.BufferGeometry` for bonds — allowing hundreds of atoms to render with a *single draw call*.

- **Dynamic Physics**  
  Real-time sine–wave undulation simulates atomic vibrations or a floating liquid-like ripple.

- **Interactive Controls**  
  Full camera control with `OrbitControls` (Zoom, Pan, Rotate).

- **Responsive Layout**  
  Automatically adapts to window resizing.

---

## 🚀 Quick Start

Because ES Modules are used, browsers block loading when opened via `file://`.  
You **must run a local server**.

### **Option 1: VS Code (Recommended)**

1. Install the **Live Server** extension.  
2. Open your project folder.  
3. Right-click `index.html` → **Open with Live Server**.

---

### **Option 2: Python**

```bash
# Python 3
python -m http.server 8000
```

Then open:  
**http://localhost:8000**

---

### **Option 3: Node.js**

```bash
npx serve
```

---

## ⚙️ Configuration

Modify the `CONFIG` object at the top of your script:

```js
const CONFIG = {
    // Grid Dimensions
    gridCols: 25,
    gridRows: 25,

    // Geometry
    bondLength: 1.5,
    atomRadius: 0.15,

    // Physics / Animation
    waveSpeed: 1.2,
    waveHeight: 1.5,
    waveFreq: 0.25,

    // Visuals
    bgColor: 0xffffff,
    atomColor: 0x000000,
    bondColor: 0x000000
};
```

---

## 🧠 How It Works

### **Graphene Geometry**

Graphene forms a hexagonal lattice. Instead of generating every hexagon, the algorithm creates *dumbbells* (two atoms + bond) and staggers them row-by-row.

- **Instanced Rendering:**  
  `THREE.InstancedMesh` is used to render all atoms extremely efficiently.

- **Dynamic Bonds:**  
  Bonds use a `LineSegments` geometry that updates every frame so the lines always follow the atoms.

---

### **Physics Simulation**

The floating ripple is produced by modifying each atom’s Y-position every frame:

```
Y = sin(x * freq + time) + cos(z * freq + time)
```

This generates a smooth sheet-wide undulation.

---

## 🤝 Contributing

Feel free to fork or extend the project!

Ideas for future improvements:

- **Graphite Stacking** — multiple graphene layers  
- **Interactive Ripples** — sheet reacts to mouse clicks  
- **Material Properties** — textures, roughness, shading experiments  

---

## 📄 License

MIT License — free to use and modify.

