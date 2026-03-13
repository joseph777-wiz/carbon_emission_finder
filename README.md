# 🌿 Live Carbon Emission Tracker

A dynamic, real-time web application designed to calculate, track, and visualize the carbon footprint of a campus or facility. Initially developed for FISAT as part of a final year project, this tool blends manual consumption inputs with live IoT data to provide a comprehensive view of environmental impact.

Drawing on methodologies from the Carbon Neutral Panchayat Program, the tracker ensures accurate emission calculations and translates them into actionable insights, such as the number of trees required to offset the carbon footprint.

## ✨ Key Features

* **Live IoT Integration:** Fetches real-time electricity consumption data directly from an ESP32 smart meter via the ThingSpeak API.
* **Comprehensive Tracking:** Calculates emissions from multiple sources, including Electricity, Diesel, LPG, and Wood/Biomass.
* **Real-time Environment Data:** Displays live Temperature and Air Quality Index (AQI) using satellite estimates based on the configured coordinates.
* **Nature's Offset Plan:** Automatically calculates the number of trees needed to sequester the generated annual emissions.
* **Interactive Visualizations:** Features dynamic, animated bar charts for source breakdowns and a responsive UI built with Tailwind CSS.

---

## 💻 Tech Stack

* **Frontend:** HTML5, JavaScript (Vanilla)
* **Styling:** Tailwind CSS (via CDN)
* **Icons:** FontAwesome
* **APIs:** * **ThingSpeak API:** For live smart meter telemetry.
* **Open-Meteo API:** For live weather and AQI data.



---

## ⚙️ Configuration & Setup

Because this is a static, client-side application, no backend server is required. You can run it locally by simply opening the `.html` file in a browser, or deploy it instantly using GitHub Pages.

To customize the tracker for your specific smart meter and location, you need to update a few constants in the `<script>` section of the code.

### 1. IoT / Smart Meter Setup (ThingSpeak)

Locate the IoT configuration section in the code and replace the placeholder values with your ThingSpeak channel details:

```javascript
// --- IoT CONFIGURATION ---
const CHANNEL_ID = "YOUR_CHANNEL_ID"; 
const READ_API_KEY = "YOUR_READ_API_KEY"; 

```

### 2. Location Setup (Weather & AQI)

To fetch accurate temperature and air quality data, update the latitude, longitude, and display name:

```javascript
// --- LOCATION CONFIGURATION ---
const LAT = 10.230829; // Default: FISAT Latitude
const LON = 76.408503; // Default: FISAT Longitude
const LOCATION_NAME = "Live from FISAT"; 

```

---

## 🧮 Emission Methodology

The calculations use standard emission factors (EF) to convert consumption into kilograms of $\text{CO}_2$. The total emission is calculated using the following formula:

$$Total \, Emission = \sum (Consumption_{source} \times EF_{source})$$

**Default Emission Factors Used:**

* **Electricity:** $0.727 \, \text{kg CO}_2/\text{kWh}$
* **Diesel:** $2.68 \, \text{kg CO}_2/\text{L}$
* **LPG:** $2.98 \, \text{kg CO}_2/\text{kg}$
* **Wood:** $1.65 \, \text{kg CO}_2/\text{kg}$

**Tree Offset Logic:**
The system assumes an average mature tree sequesters approximately $25 \, \text{kg}$ of $\text{CO}_2$ per year.

$$\text{Trees Needed} = \lceil \frac{\text{Daily Emissions} \times 365}{25} \rceil$$

---

## 🚀 How to Deploy on GitHub Pages

1. Create a new repository on GitHub and upload your `index.html` file.
2. Go to the repository **Settings**.
3. Navigate to **Pages** on the left sidebar.
4. Under "Build and deployment", select the **main** branch and save.
5. In a few minutes, your Live Carbon Emission Tracker will be accessible via the provided GitHub Pages URL.

---

## 🤝 Contributing

Contributions, issue reports, and feature requests are welcome! If you want to add new fuel sources, integrate different IoT platforms (like Blynk or AWS IoT), or improve the UI, feel free to submit a Pull Request.
