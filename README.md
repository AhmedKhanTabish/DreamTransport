# 🚌 DreamTransport - Public Transport Optimization

An intelligent system for optimizing bus routes and stops for public transport in **Neumarkt i.d. OPf.** based on passenger data, punctuality analysis, and mathematical optimization algorithms.

## 📋 Project Overview

DreamTransport is a data-driven system for public transport optimization that was developed to:

- **Optimally place stop hubs** based on passenger volume
- **Optimize bus routes** for better efficiency and passenger satisfaction
- **Improve punctuality** through analysis of delay data
- **Analyze and optimize passenger flows**

The system uses real public transport data from Neumarkt i.d. OPf. and applies advanced optimization algorithms.

## 🏗️ Architecture & Technology Stack

### Backend & Data Processing
- **Python 3.x** - Main programming language
- **SQLite** - Local database for transport data
- **Pandas** - Data analysis and processing
- **PDFplumber** - Data extraction from PDF documents

### Optimization Algorithms
- **K-Median Algorithm** - For optimal hub placement
- **Hub-and-Spoke Optimization** - For route optimization
- **Greedy & Batch Optimization** - For incremental improvements
- **Haversine Distance Calculation** - For geographic optimizations

### Data Sources
- **Timetables** (Excel, PDF)
- **Passenger Statistics** (PDF)
- **Punctuality Analysis** (CSV)
- **Stop data** with coordinates

## 📁 Project Structure

```
DreamTransport/
├── 📊 Data/
│   ├── CSV/                    # CSV files with transport data
│   ├── *.pdf                   # Timetables and statistics
│   └── *.xlsx                  # Excel data
├── 🗄️ Database/
│   ├── schema.sql              # Database schema
│   ├── transport.db            # Main database
│   └── neumarkt.sqlite         # SQLite database
├── 🔧 Core Modules/
│   ├── build_db.py             # Database construction from various sources
│   ├── select_hubs.py          # Hub optimization with K-Median
│   ├── hub_optimizer.py        # Route optimization
│   └── compute_stop_distances.py # Distance calculations
├── 📈 Analysis/
│   ├── bc.ipynb                # Jupyter notebook for geocoding
│   └── heuristics_list.txt     # Optimization heuristics
├── 📤 Outputs/
│   └── hub_optimizer_outputs/  # Optimization results
└── 📋 Documentation/
    ├── requirements.txt         # Python dependencies
    └── README.md               # This file
```

## 🚀 Installation & Setup

### Prerequisites
- Python 3.8+
- SQLite3
- Internet connection for geocoding (OpenStreetMap)

### Installation

1. **Clone repository**
```bash
git clone [repository-url]
cd DreamTransport
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Build database**
```bash
python build_db.py
```

## 💻 Usage

### 1. Hub Optimization

Optimize the placement of stop hubs based on passenger volume:

```bash
python select_hubs.py --db transport.db --k 6
```

**Parameters:**
- `--db`: Database path
- `--k`: Number of desired hubs
- `--min_hub_sep_km`: Minimum distance between hubs (optional)

### 2. Route Optimization

Optimize existing bus routes for better efficiency:

```bash
python hub_optimizer.py --hubs 76,99,119,135,142,145 --mode greedy --topN 5
```

**Parameters:**
- `--hubs`: Comma-separated list of hub stop IDs
- `--mode`: Optimization mode (`greedy` or `batch`)
- `--topN`: Number of best candidates to evaluate

### 3. Database Construction

Create a new database from various data sources:

```bash
python build_db.py --csv [csv-path] --pdf [pdf-path] --db [db-path]
```

## 📊 Data Model

The system uses the following main tables:

- **`stops`** - Stops with passenger volume and coordinates
- **`routes`** - Bus routes
- **`route_stops`** - Stops per route with sequence
- **`performance_metrics`** - Punctuality data and delays

## 🔍 Optimization Metrics

The system optimizes based on:

- **Passenger-weighted distances** to hubs
- **Average hops** between stops
- **Hub load distribution** (Coefficient of Variation)
- **Route complexity** and similarity
- **Directness** of connections

## 📈 Outputs

### Hub Optimization
- `selected_hubs.csv` - Selected hub stops
- `selected_hubs.json` - Detailed hub information

### Route Optimization
- `final_routes.csv` - Optimized routes
- `candidates_report.json` - Detailed optimization report
- `applied_changes.json` - Applied changes

## 🎯 Use Cases

- **Transport planning** for cities and municipalities
- **Bus network optimization** based on passenger data
- **Analysis of delay patterns** and their causes
- **Planning new stops** at optimal locations
- **Route optimization** for better efficiency

## 🔬 Technical Details

### Algorithms
- **K-Median with passenger weights** for hub placement
- **Partitioning Around Medoids (PAM)** for local optimization
- **Hub-and-Spoke topology** for efficient connections
- **Greedy heuristics** for incremental improvements

### Distance Calculation
- **Haversine formula** for geographic distances
- **Graph-based distances** for network connections
- **Weighted distances** based on passenger volume

## 🤝 Contributing

The project is developed for a hackathon context. Contributions are welcome:

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Create a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

The MIT License is a permissive license that allows for:
- Commercial use
- Modification
- Distribution
- Private use

While providing liability protection for the authors.

## 👥 Team

**DreamTransport** was developed by a team of 5 developers during a hackathon:

- **Tabish** - Team Member
- **Usman** - Team Member  
- **Mohammed** - Team Member
- **Saad** - Team Member
- **Jeva** - Team Member

### Project Focus
Developed with focus on sustainable mobility and intelligent transport optimization for the public transport system in Neumarkt i.d. OPf., Germany.

## 📞 Contact

For questions or suggestions, please contact the development team or open an issue on GitHub.

---

**🚀 Ready for the future of public transport!**
