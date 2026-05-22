# UrbanPulse Frontend Documentation

UrbanPulse is a high-performance, industrial-grade dashboard designed for **Structural Integrity Monitoring**. It provides real-time telemetry visualization, anomaly detection, and historical analysis for engineering structures.

## 🚀 Technology Stack

### Core
- **React 19**: Modern UI library for component-based architecture.
- **Vite 8**: Next-generation frontend tooling for fast builds and hot module replacement.
- **JavaScript (ESM)**: Utilizing the latest ECMAScript features.

### Styling & UI
- **Tailwind CSS 4**: Utility-first CSS framework for rapid UI development.
- **Lucide React**: Consistent and beautiful iconography.
- **Geist Mono / Inter**: Modern typography for an industrial aesthetic.

### State Management
- **Zustand**: A small, fast, and scalable bearbones state-management solution.
- **Custom Hooks**: Utilized for managing WebSocket connections and real-time data processing.

### Data Visualization
- **Recharts**: Responsive charts for integrity history and trends.
- **uPlot**: Ultra-fast, memory-efficient plotting library for real-time FFT/Waveform data.
- **Canvas-Gauges**: Highly customizable gauges for node health scores.

## 🛠 Architecture Overview

### State Management (`src/store.js`)
The application uses a centralized Zustand store to manage:
- **Node Data**: State of structural nodes (Node A, B, C), including scores and sensor readings.
- **Event Logs**: A history of system alerts and status messages.
- **System State**: WebSocket connectivity status and active node selection.
- **History**: Historical integrity scores for trend analysis.

### Real-time Telemetry (`src/App.jsx`)
The application implements a robust WebSocket handler:
- **Connection**: Connects to `ws://localhost:8080` for live sensor data.
- **Performance**: Uses `requestAnimationFrame` and a buffering system (`pendingUpdates`) to ensure the UI remains smooth even with high-frequency updates.
- **Fault Detection**: Automatically derives system status (Clear, Warning, Critical) based on node integrity scores.

## 🧩 Key Components

- **StatusBanner**: Top-level indicator of the overall system health.
- **NodeCard**: Detailed view of individual sensor nodes with real-time gauges.
- **FFTWaveform**: High-frequency data visualization using uPlot.
- **StructuralMap**: A visual representation of node locations on the monitored structure.
- **HistoricalChart**: Time-series visualization of structural integrity trends.
- **AlertTimeline**: Sequential log of system events and anomalies.

## 🚦 System Logic

### Integrity Scoring
- **Optimal**: 80 - 100%
- **Warning**: 40 - 79% (Indicative of potential issues or maintenance required)
- **Critical**: < 40% (Anomaly detected, potential structural failure)

### Key Reading Metrics
- **Accel X/Y**: Accelerometer data for vibration monitoring (g-force).
- **Piezo**: Piezoelectric sensor data for strain and stress monitoring (Voltage).

## 💻 Development Commands

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Lint the codebase
npm run lint
```

## 📂 Directory Structure

```text
frontend/
├── src/
│   ├── components/     # Reusable UI components
│   ├── assets/         # Static assets and images
│   ├── App.jsx         # Main application logic and WS handler
│   ├── store.js        # Global state management (Zustand)
│   ├── index.css       # Global styles and design tokens
│   └── main.jsx        # Entry point
├── public/             # Public assets
├── vite.config.js      # Vite configuration
└── package.json        # Dependencies and scripts
```
