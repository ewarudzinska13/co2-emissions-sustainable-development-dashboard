# co2-emissions-sustainable-development-dashboard
Interactive Power BI dashboard analyzing global CO₂ emissions, renewable energy adoption, and climate policies across 174 countries (2002-2021)

# CO₂ Emissions and Sustainable Development Dashboard

Interactive Power BI dashboard analyzing the relationship between economic growth, CO₂ emissions, renewable energy adoption, and climate policies across 174 countries over 20 years (2002-2021).

## Project Overview

This comprehensive dashboard examines:
- Global CO₂ emission trends and patterns
- Impact of economic development (GDP per capita) on emissions
- Effectiveness of climate policies (ETS, carbon tax)
- Renewable energy adoption and its role in emission reduction
- Regional and sectoral emission analysis

## Key Features

### Data Model Architecture
- **Power Query**: Advanced data transformation and ETL processes
  - Dynamic path parameterization for portable data loading
  - Data cleaning and standardization across multiple sources
  - Custom merging and grouping operations
  
- **Power Pivot**: Relational data model with 13 interconnected tables
  - Star schema with fact and dimension tables
  - DAX measures for complex calculations
  - Optimized relationships for performance

### Dashboard Components

**Key Metrics**:
- Total CO₂ emissions
- Global emission share (%)
- Average emissions per capita
- Average life satisfaction score
- Average population and GDP per capita

**Visualizations**:
- Time series analysis of annual emissions (global and by continent)
- World map showing GDP per capita distribution
- Renewable energy share by country
- Sectoral emission breakdown (industry, transport, energy production, etc.)
- Climate policy adoption analysis (ETS and carbon tax)
- Impact assessment of climate policies on emission levels

**Interactive Filters**:
- Continent selector
- Top 5 emitters focus (China, USA, Japan, India, Russia)
- Country income classification (World Bank methodology)
- Individual country selection
- Time range slider (2002-2021)

### Spatial Analysis
Power Maps integration showing:
- CO₂ emissions evolution over time
- GDP per capita temporal changes
- Climate policy implementation patterns
- Renewable energy production trends (hydro, wind, solar, other)

## Data Sources

All data sourced from [Our World in Data](https://ourworldindata.org/):
- CO₂ emissions (total and per capita)
- GDP per capita (World Bank)
- Population statistics
- Renewable energy production (TWh)
- Sectoral emissions breakdown
- Climate policies (ETS and carbon tax)
- Life satisfaction index (Cantril ladder score)
- Continental classifications

## Technical Implementation

### Power Query Transformations
- Automated unique value extraction for data consistency
- Date extraction and calendar table creation
- Missing value imputation strategies
- Dynamic file path handling for portability

### DAX Measures (Examples)
```DAX
// Global emission share
Udział w globalnych emisjach = 
DIVIDE(
    SUM([Annual CO₂ emissions]),
    CALCULATE(
        SUM([Annual CO₂ emissions]),
        ALL('annual-co2-emissions'[Entity]),
        ALL('annual-co2-emissions'[Continent])
    )
)

// Average life satisfaction (excluding zeros)
Średnie zadowolenie z życia = 
DIVIDE(
    SUMX(
        FILTER('annual-co2-emissions', [zadowolenie] > 0),
        [zadowolenie]
    ),
    COUNTX(
        FILTER('annual-co2-emissions', [zadowolenie] > 0),
        [Rok]
    )
)
```

## Key Findings

- Despite increasing renewable energy adoption, global CO₂ emissions continue to rise
- Strong correlation between economic development and emissions
- Climate policies show varied effectiveness across regions
- Sectoral analysis reveals energy production as primary emission source
- Top 5 emitters account for majority of global emissions

## Tools & Technologies

- **Microsoft Power BI Desktop**
- **Power Query** (M language) for data transformation
- **Power Pivot** for data modeling
- **DAX** (Data Analysis Expressions) for calculations
- **Power Maps** for spatial analysis

## Files in Repository

- `Dokumentacja_techniczna.pdf` - Complete technical documentation (in Polish)
- Power BI file (`.pbix`) - [to be added]
- Data folder - Source files from Our World in Data

## Usage

1. Download the `.pbix` file
2. Ensure data files are in the correct folder structure
3. Open in Power BI Desktop
4. Refresh data connections if needed
5. Explore interactive visualizations

## Project Context

Created as part of advanced Business Intelligence coursework at the University of Warsaw, Faculty of Economic Sciences. This project demonstrates proficiency in:
- Data modeling and ETL processes
- Advanced DAX calculations
- Interactive dashboard design
- Spatial data analysis
- Economic and environmental data interpretation

---

**Author**: Dominik Warudzinski  
**Institution**: University of Warsaw, Faculty of Economic Sciences  
**Year**: 2023
