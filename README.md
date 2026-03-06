# 🌍 Earthquake Data Analysis
*Temporal & Spatial Indicators • Clustering • Interactive Dashboard*

---

A data analytics project exploring earthquake activity patterns across time and geography using historical seismic records and modern validation datasets.

The analysis focuses on two key questions:

- **Temporal analysis** → When does seismic activity change?
- **Spatial analysis** → Where do earthquakes concentrate geographically?

The project transforms earthquake datasets into analytical indicators and interactive visualizations.

---

## 🎯 Project Goals

This project investigates earthquake activity using temporal and spatial indicators.

### Temporal Indicators
- Event counts per time window
- Long-term trends
- Moving average smoothing
- Activity spikes and anomalies

**Goal** → Understand how seismic activity evolves over time

### Spatial Indicators
- Geographic clustering
- Hotspot identification
- Cluster boundaries
- Relation to tectonic zones

**Goal** → Identify where earthquake activity concentrates geographically

**Temporal** = time dimension  
**Spatial** = location dimension

---

## 📊 Dataset

Two datasets were used for analysis and validation.

### NOAA Historical Earthquake Dataset
**Source:** NOAA Significant Earthquake Database

| Metric       | Value                     |
|--------------|---------------------------|
| Records      | 4,424 earthquake events  |
| Features     | 38 columns               |
| Time coverage| 2150 BC – 2020 AD        |
| Key attributes| Year, Latitude, Longitude, Magnitude |

**Purpose:**
- Long-term seismic activity analysis
- Temporal trend indicators
- Spatial clustering

### USGS Modern Earthquake Dataset
**Source:** USGS Earthquake Feed

| Metric       | Value                     |
|--------------|---------------------------|
| Records      | 183 events                |
| Features     | 22 columns                |
| Attributes   | Time, Latitude, Longitude, Depth, Magnitude |
| Metadata     | gap, rms, quality indicators |

**Purpose:**
- External validation
- Comparison with modern earthquake observations

---

## 📈 Analytical Indicators

The analysis framework consists of five indicators.

### 1️⃣ Indicator 1 — Earthquakes per Century
Measures long-term earthquake activity patterns.

**Method:**
- Group events into 100-year bins
- Count earthquakes per century

**Example concept:**
```python
df['Century'] = (df['Year'] // 100) * 100
result = df.groupby('Century').size()
```

**Insight:** Helps identify historical reporting patterns and long-term trends.

### 2️⃣ Indicator 2 — Magnitude Normalization
Magnitude values were normalized using Min-Max scaling.

**Formula:** (x - min) / (max - min)

**Benefits:**
- Scales values between 0 and 1
- Enables comparison across datasets
- Improves clustering and visualization

Magnitude patterns typically show: many small events → few large events

### 3️⃣ Indicator 3 — Temporal Analysis
Temporal indicators examine earthquake frequency across time.

**Metrics analyzed:**
- Event counts per year
- Activity trends
- Moving average smoothing

**Example:**
```python
yearly_counts['Moving_Average'] = yearly_counts['Count'].rolling(window=10).mean()
```

Moving averages help reveal long-term seismic activity patterns.

### 4️⃣ Indicator 4 — Spatial Clustering
Spatial clustering identifies earthquake hotspots.

**Method used:** KMeans clustering

**Input features:**
- Latitude
- Longitude

**Configuration:** KMeans (k = 5)

**Outcome:**
- Earthquake events grouped into five clusters
- Each cluster represents a coarse seismic hotspot region

### 5️⃣ Indicator 5 — External Validation
Modern earthquake observations from USGS were used to validate patterns.

**Validation checks:**
- Magnitude distribution
- Geographic hotspots
- Event frequency patterns

**Purpose:** Ensure historical insights align with modern seismic data.

---

## 📊 Interactive Dashboard

An interactive dashboard was built using Dash + Plotly.

**Dashboard includes:**
- Earthquakes per century
- Magnitude distribution
- Temporal trend with moving average
- Spatial clustering visualization
- USGS validation charts

**Run dashboard:**
```python
app = create_dashboard(fig1, fig2, fig3, fig4, fig5)
app.run(debug=True, port=8051)
```

The dashboard allows interactive exploration of earthquake indicators.

---

## 🧠 Key Insights
- Temporal indicators reveal changes in seismic activity over time
- Spatial clustering highlights geographic earthquake hotspots
- Magnitude distributions follow expected seismic patterns
- External validation increases confidence in historical observations
- Dashboards make complex data accessible to non-technical users

---

## ⚠️ Limitations
**Historical earthquake catalogs have limitations:**
- Detection bias in older records
- Incomplete historical coverage

**Clustering limitations:**
- KMeans assumes round clusters
- Fault systems may follow linear structures

---

## 🚀 Future Improvements
**Potential extensions:**
- Apply DBSCAN or HDBSCAN clustering
- Include depth and magnitude as clustering features
- Integrate tectonic plate boundary datasets
- Build real-time earthquake monitoring systems

---

## 🛠 Technologies Used
- Python
- Pandas
- NumPy
- Scikit-learn
- Plotly
- Dash

---

## 🧩 Skills Demonstrated
- Temporal Data Analysis
- Spatial Data Analysis
- Geospatial Clustering
- Statistical Indicators
- Feature Engineering
- Interactive Data Visualization
- Scientific Data Interpretation
- Dashboard Development

---

## 📂 Project Structure
```
earthquake-analysis
│
├── data
│   ├── earthquakes.csv
│   └── usgs_current.csv
│
├── notebooks
│   └── earthquake_analysis.ipynb
│
├── dashboard
│   └── dashboard_app.py
│
└── README.md
```

---

## 📚 References
- [NOAA Significant Earthquake Database](https://www.ngdc.noaa.gov/hazel/view/hazards/earthquake/event-data)
- [USGS Earthquake Data Feeds](https://earthquake.usgs.gov/earthquakes/feed/)
- [USGS Ring of Fire Documentation](https://www.usgs.gov/programs/earthquake-hazards/ring-fire)
- [USGS Magnitude Scale Documentation](https://www.usgs.gov/programs/earthquake-hazards/magnitude-types)