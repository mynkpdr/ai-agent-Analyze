# AI Agent Data Analysis Pipeline

[![CI/CD Pipeline](https://github.com/mynkpdr/ai-agent-Analyze/actions/workflows/ci.yml/badge.svg)](https://github.com/mynkpdr/ai-agent-Analyze/actions)

A Python-based data analysis pipeline with automated CI/CD using GitHub Actions. This project analyzes sales data and publishes results automatically to GitHub Pages.

## Overview

This project processes sales data from a CSV file and generates analytical insights including:
- Total row count
- Number of distinct regions
- Top 3 products by revenue
- 7-day rolling average revenue by region

The analysis results are automatically generated and published via GitHub Actions.

## Features

- **Automated Data Analysis**: Processes sales data and computes key metrics
- **CI/CD Pipeline**: Automated code quality checks and deployment
- **Code Quality**: Ruff linting for Python code standards
- **GitHub Pages Deployment**: Automatic publishing of analysis results

## Deployment

- **Repository**: [https://github.com/mynkpdr/ai-agent-Analyze](https://github.com/mynkpdr/ai-agent-Analyze)
- **Live Demo**: [https://mynkpdr.github.io/ai-agent-Analyze/](https://mynkpdr.github.io/ai-agent-Analyze/)
- **Latest Results**: [https://mynkpdr.github.io/ai-agent-Analyze/result.json](https://mynkpdr.github.io/ai-agent-Analyze/result.json)

## Project Structure

```
.
├── execute.py              # Main analysis script
├── data.csv               # Sales data (converted from Excel)
├── requirements.txt       # Python dependencies
├── .github/
│   └── workflows/
│       └── ci.yml        # GitHub Actions workflow
├── .gitignore            # Git ignore rules
├── LICENSE               # MIT License
└── README.md             # This file
```

## Requirements

- Python 3.11 or higher
- pandas 2.3.0 or higher

## Installation

1. Clone the repository:
```bash
git clone https://github.com/mynkpdr/ai-agent-Analyze.git
cd ai-agent-Analyze
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

## Usage

Run the analysis script:
```bash
python execute.py > result.json
```

The script will:
1. Read data from `data.csv`
2. Calculate revenue metrics
3. Output results as JSON to stdout

### Output Format

The script outputs a JSON object with the following structure:

```json
{
  "row_count": 500,
  "regions": 4,
  "top_n_products_by_revenue": [
    {"product": "product_name", "revenue": 12345.67}
  ],
  "rolling_7d_revenue_by_region": {
    "Region1": 1234.56,
    "Region2": 2345.67
  }
}
```

## CI/CD Pipeline

The GitHub Actions workflow (`.github/workflows/ci.yml`) automatically:

1. **Code Quality Check**: Runs `ruff` linter on the Python code
2. **Execute Analysis**: Runs `execute.py` and generates `result.json`
3. **Deploy to Pages**: Publishes the results to GitHub Pages

### Workflow Triggers

- Push to `main` branch
- Manual workflow dispatch

### Viewing CI Logs

1. Go to the [Actions tab](https://github.com/mynkpdr/ai-agent-Analyze/actions)
2. Click on the latest workflow run
3. View the logs for each step:
   - Ruff linting results
   - Script execution output
   - Deployment status

## Data Analysis Details

### Metrics Calculated

1. **Row Count**: Total number of records in the dataset
2. **Regions**: Count of distinct geographic regions
3. **Top Products by Revenue**: Top 3 products ranked by total revenue
4. **Rolling 7-Day Revenue**: Last value of 7-day moving average of daily revenue for each region

### Data Schema

The input CSV (`data.csv`) contains the following columns:
- `date`: Transaction date
- `region`: Geographic region
- `product`: Product name
- `units`: Number of units sold
- `price`: Price per unit

Revenue is calculated as: `revenue = units × price`

## Development

### Code Quality

The project uses `ruff` for Python code linting. Run locally:

```bash
pip install ruff
ruff check execute.py
```

### Testing Locally

```bash
# Run the analysis
python execute.py

# Save output to file
python execute.py > result.json

# View formatted output
python execute.py | python -m json.tool
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

Mayank Kumar Poddar

## Contributing

This project is part of an AI agent challenge. Contributions should follow the evaluation criteria specified in the project brief.

## Acknowledgments

- Built with Python and pandas
- Automated with GitHub Actions
- Deployed on GitHub Pages
