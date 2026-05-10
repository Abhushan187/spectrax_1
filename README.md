# 🎯 SpectraX - Real-Time Pose Tracking & Visualization

<div align="center">

[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev/)
[![Three.js](https://img.shields.io/badge/Three.js-000000?style=for-the-badge&logo=three.js&logoColor=white)](https://threejs.org/)
[![Socket.io](https://img.shields.io/badge/Socket.io-010101?style=for-the-badge&logo=socket.io&logoColor=white)](https://socket.io/)
[![Express](https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)

*Advanced real-time pose detection and 3D visualization using MediaPipe and WebGL*

[Features](#features) • [Quick Start](#quick-start) • [Architecture](#architecture) • [Contributing](#contributing) • [License](#license)

</div>

---

## ✨ Features

- 🎥 **Real-Time Pose Detection** - Detect human pose from webcam using MediaPipe
- 🌐 **3D Visualization** - Beautiful 3D pose rendering with Three.js
- ⚡ **WebSocket Communication** - Real-time data streaming via Socket.io
- 📱 **Full-Stack Application** - React frontend + Express.js backend
- 🔄 **Live Processing** - Process 30+ FPS with smooth animations
- 🎨 **Interactive UI** - React-based controls and settings
- 🚀 **Production Ready** - TypeScript for type safety, ESLint for code quality
- 📦 **Modular Architecture** - Easy to extend and customize

---

## 🚀 Quick Start

### Prerequisites

- **Node.js** >= 16.x
- **npm** or **yarn**
- **Modern browser** with webcam support (Chrome, Firefox, Edge, Safari)

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/Somil450/spectrax_1.git
cd spectrax_1
```

2. **Install frontend dependencies:**
```bash
npm install
```

3. **Install backend dependencies:**
```bash
cd server
npm install
cd ..
```

### Running Locally

**Terminal 1 - Start Frontend (React + Vite):**
```bash
npm run dev
```
Frontend will be available at: `http://localhost:5173`

**Terminal 2 - Start Backend (Express + Socket.io):**
```bash
cd server
npm run dev
```
Backend will be available at: `http://localhost:3000`

### Build for Production

```bash
# Build frontend
npm run build

# Backend is already production-ready
```

---

## 🏗️ Architecture

### Project Structure

```
spectrax_1/
├── src/
│   ├── components/          # React components
│   │   ├── PoseDetector.tsx
│   │   ├── Visualization3D.tsx
│   │   └── Controls.tsx
│   ├── utils/               # Utility functions
│   ├── hooks/               # Custom React hooks
│   ├── App.tsx
│   └── main.tsx
├── server/
│   ├── index.js             # Express server
│   ├── package.json
│   └── README.md
├── vite.config.ts
├── tsconfig.json
└── package.json
```

### Tech Stack

**Frontend:**
- **React 18** - UI framework
- **TypeScript** - Type safety
- **Vite** - Fast build tool & dev server
- **Three.js** - 3D graphics library
- **MediaPipe** - AI pose detection
- **Socket.io Client** - Real-time communication
- **Lucide React** - UI icons

**Backend:**
- **Express.js** - Web server
- **Socket.io** - WebSocket communication
- **CORS** - Cross-origin resource sharing

### Data Flow

```
Webcam Input
    ↓
MediaPipe Pose Detection (Browser)
    ↓
Pose Landmarks (33 keypoints)
    ↓
Socket.io Emit to Server
    ↓
Backend Processing & Broadcasting
    ↓
Three.js 3D Visualization
```

---

## 📖 Usage

### Basic Example

1. **Allow camera access** when prompted
2. **Stand in front of your webcam**
3. **See your pose detected and visualized in 3D**
4. **Adjust settings** from the control panel

### Features Explained

| Feature | Description |
|---------|-------------|
| **Confidence Threshold** | Adjust detection confidence (0-1) |
| **Smoothing** | Enable/disable pose smoothing for better tracking |
| **3D Rotation** | Auto-rotate or manual control of 3D view |
| **Skeleton Color** | Customize skeleton color for visualization |
| **FPS Display** | Monitor real-time performance |

---

## 🔧 Configuration

### Environment Variables

Create `.env` file in project root:

```env
VITE_BACKEND_URL=http://localhost:3000
VITE_SOCKET_URL=ws://localhost:3000
```

### Backend Configuration

Edit `server/index.js`:

```javascript
const PORT = process.env.PORT || 3000;
const CORS_ORIGIN = process.env.CORS_ORIGIN || 'http://localhost:5173';
```

---

## 📊 API Reference

### Socket.io Events

**Client → Server:**
```javascript
socket.emit('pose_frame', {
  landmarks: [...],      // 33 pose keypoints
  confidence: 0.95,      // Detection confidence
  timestamp: Date.now()  // Frame timestamp
});
```

**Server → Client:**
```javascript
socket.on('pose_processed', (data) => {
  // Process received pose data
  console.log(data);
});
```

---

## 🎨 Customization

### Change 3D Visualization Color

In `src/components/Visualization3D.tsx`:
```typescript
const skeletonColor = new THREE.Color(0x00ff00); // Green
```

### Adjust Pose Detection Sensitivity

In `src/components/PoseDetector.tsx`:
```typescript
const options = {
  modelComplexity: 1,        // 0, 1, or 2
  smoothLandmarks: true,
  enableSegmentation: false,
  smoothSegmentation: true,
  minDetectionConfidence: 0.5,
  minTrackingConfidence: 0.5
};
```

### Modify Server Port

In `server/index.js`:
```javascript
const PORT = 4000; // Change from 3000 to 4000
```

---

## 🐛 Troubleshooting

### Camera Not Working
- ✅ Check browser permissions
- ✅ Ensure HTTPS or localhost
- ✅ Try different browser
- ✅ Check camera is not in use

### WebSocket Connection Failed
- ✅ Ensure backend is running on correct port
- ✅ Check CORS configuration
- ✅ Verify firewall settings
- ✅ Check network connection

### Low FPS Performance
- ✅ Reduce model complexity (modelComplexity: 0)
- ✅ Disable segmentation
- ✅ Close other browser tabs
- ✅ Lower webcam resolution

### Inaccurate Pose Detection
- ✅ Improve lighting conditions
- ✅ Keep full body in frame
- ✅ Increase detection confidence
- ✅ Adjust camera angle

---

## 📚 Use Cases

- 🏋️ **Fitness Apps** - Exercise form tracking and correction
- 🎮 **Gaming** - Motion-controlled games
- 🎬 **Animation** - Motion capture for animation
- 📊 **Analytics** - Posture analysis and monitoring
- 🤸 **Sports** - Performance tracking and analysis
- 🎯 **Rehabilitation** - Physical therapy monitoring
- 🎪 **Interactive Installations** - Art and creative projects

---

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Quick Contribution Guide

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** changes (`git commit -m 'Add AmazingFeature'`)
4. **Push** to branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Good First Issues

- 🔧 Add settings panel for pose detection tuning
- 🎨 Create new visualization themes
- 📱 Mobile responsiveness improvements
- 📚 Improve documentation
- 🧪 Add unit tests

See [Issues](https://github.com/Somil450/spectrax_1/issues) for more opportunities!

---

## 📋 Roadmap

- [ ] Multi-person pose detection
- [ ] Hand and face detection integration
- [ ] Recording and playback functionality
- [ ] Export pose data as JSON/CSV
- [ ] Performance optimization
- [ ] Mobile app (React Native)
- [ ] Cloud deployment guides
- [ ] Advanced analytics dashboard
- [ ] REST API endpoints
- [ ] Docker support

---

## 🔐 Security

- Input validation on all socket events
- CORS protection enabled
- No sensitive data stored
- Regular dependency updates
- Report security issues to: [security email]

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**Somil Jain** - [@Somil450](https://github.com/Somil450)

---

## 🙏 Acknowledgments

- [MediaPipe](https://mediapipe.dev/) - Pose detection
- [Three.js](https://threejs.org/) - 3D visualization
- [React](https://react.dev/) - UI framework
- [Vite](https://vitejs.dev/) - Build tool
- [Socket.io](https://socket.io/) - Real-time communication

---

## 📞 Support

- 💬 Open an [Issue](https://github.com/Somil450/spectrax_1/issues)
- 📧 Email: contact@example.com
- 🐦 Twitter: [@Somil450](https://twitter.com)
- 💻 Website: [your-website.com](https://your-website.com)

---

<div align="center">

**[⬆ back to top](#-spectrax---real-time-pose-tracking--visualization)**

Made with ❤️ by Somil Jain

</div>
