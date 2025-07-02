# Aerosol Monitoring Software - User Manual 📖

![Software Interface](assets/dashboard_screenshot.png)

## Table of Contents
1. [System Requirements](#-system-requirements)
2. [Quick Start Guide](#-quick-start-guide)
3. [Interface Overview](#-interface-overview)
4. [Data Acquisition](#-data-acquisition)
5. [Data Visualization](#-data-visualization)
6. [Alert Configuration](#-alert-configuration)
7. [Data Export](#-data-export)
8. [Troubleshooting](#-troubleshooting)
9. [FAQ](#-faq)

---

## 🖥️ System Requirements
### Hardware
- Aethalometer/Nephelometer with serial output
- Windows/macOS/Linux PC
- Minimum 4GB RAM
- 500MB disk space

### Software
- Python 3.8+
- Required packages:
  ```bash
  pyserial==3.5
  matplotlib==3.6
  pandas==1.5
  ```

---

## 🚀 Quick Start Guide
1. **Connect Instrument**:
   ```python
   # config.py
   SERIAL_PORT = 'COM3'  # Change to your port
   BAUD_RATE = 9600      # Match instrument settings
   ```

2. **Launch Application**:
   ```bash
   python src/main.py
   ```

3. **Login**:
   - Default credentials:
     - User: `researcher` (view-only)
     - Admin: `admin` (full access)

---

## 🖱️ Interface Overview
### Main Dashboard
| Component          | Description                          |
|--------------------|--------------------------------------|
| **Live Plot Tab**  | Real-time BC concentration graphs    |
| **Daily Stats**    | 24-hour trend visualization         |
| **Alerts Panel**   | Threshold violation notifications    |
| **Control Bar**    | Start/Stop data acquisition         |

![Interface Labels](assets/interface_annotated.png)

---

## 📡 Data Acquisition
### Starting Monitoring
1. Navigate to **Control Bar**
2. Click ▶️ "Start Acquisition"
3. Verify connection status:
   - ✅ Green: Active data flow
   - ❌ Red: Connection error

### Expected Output
```
[12:30:45] Connected to AE33 @ COM3
[12:30:46] Receiving BC_370nm: 1.24 µg/m³
[12:30:47] Data saved to 20240515_data.csv
```

---

## 📊 Data Visualization
### Viewing Live Data
1. Select wavelength (370nm-880nm)
2. Adjust time window:
   - `1h` (default)
   - `6h`
   - `24h`

### Historical Data
1. Go to **Daily Plot Tab**
2. Select date from calendar widget
3. Click "Load Data"

---

## 🚨 Alert Configuration
### Setting Thresholds (Admin Only)
1. Navigate: **Settings → Alert Config**
2. Enter values:
   ```yaml
   370nm: 5.0 µg/m³  # Warning level
   880nm: 3.0 µg/m³  # Critical level
   ```
3. Choose alert type:
   - 🔔 Sound alert
   - 🟡 Visual highlight

### Alert Types
| Level     | Indicator          | Sound       |
|-----------|--------------------|-------------|
| Warning   | Yellow border      | Single beep |
| Critical  | Flashing red       | Siren       |

---

## 📤 Data Export
### Exporting Reports
1. Select time range
2. Choose format:
   ```bash
   CSV  # For Excel/Pandas
   JSON # For web applications
   XLSX # Formatted Excel
   ```
3. Click "Export"

### File Naming Convention
```
YYYYMMDD_HHMMSS_export.[format]
e.g. 20240515_143000_export.csv
```

---

## 🛠️ Troubleshooting
### Common Issues
| Symptom                  | Solution                          |
|--------------------------|-----------------------------------|
| "Port COM3 not found"    | Check device manager for correct port |
| Frozen plots             | Restart application              |
| Missing historical data  | Verify data/ directory exists    |

### Error Logs
Location: `logs/error_log.txt`
Sample entry:
```
[ERROR] 2024-05-15 14:30: SerialTimeout - No data received in 5s
```

---

## ❓ FAQ
**Q: How do I change admin password?**  
A: Edit `config/users.json` (admin access required)

**Q: Can I monitor multiple instruments?**  
A: Yes! Run multiple instances with different config.py ports

**Q: Where is raw data stored?**  
A: In `data/` directory with timestamped CSV files

---

## 📞 Support
For technical assistance, contact:  
📧 parthdavecse@gmail.com 
🔗 [Issue Tracker](https://github.com/ParthDaveCSE/Aerosol-Monitoring-Software/issues)

*Last Updated: May 2024 | v1.2.0*
