# Mobile Phone Dataset Analysis

## Dataset Summary
- **1,017 unique mobile phones** with 15 features after cleaning
- **Price range**: ₹99 to ₹489,990 across budget to premium segments
- **Key features**: Name, price, rating, specifications (RAM, storage, battery, display)
- **Data types**: Mixed numerical, categorical, and text data

## Data Cleaning Process Applied

### 1. Missing Values
- **FM radio (71% missing)** and **external memory (34% missing)** - retained as non-critical
- **No missing values** in essential features (Name, Price, Rating)

### 2. Duplicates
- Removed **2 duplicate phones** based on name
- Final dataset: **1,017 unique phones**

### 3. Feature Engineering
Extracted numerical features from text using regex:
- **RAM (GB)**: `"12 GB RAM, 256 GB inbuilt"` → `12`
- **Storage (GB)**: `"12 GB RAM, 256 GB inbuilt"` → `256` 
- **Battery (mAh)**: `"5000 mAh Battery with 67W"` → `5000`
- **Display Size**: `"6.67 inches, 1080 x 2400"` → `6.67`
- **Brand**: `"Samsung Galaxy S21"` → `"Samsung"`

### 4. Outliers
- Detected **150+ price outliers** using IQR method
- **Retained all outliers** (represent legitimate ultra-premium segment)

## Key Insights

### Market Trends
- **Average rating**: 4.38/5 (consistent quality across segments)
- **Budget phones** (<₹15K) dominate market volume
- **Strong correlation**: Price vs Spec Score (r=0.6), Price vs RAM (r=0.5)
- **Top brands**: Samsung, Xiaomi, OnePlus seem to lead the market

### Technical Specifications
- **RAM**: 1-24GB (8-12GB most common)
- **Storage**: 4-512GB internal
- **Battery**: 800-28,000mAh (avg ~5,300mAh)
- **Display**: 1.77-10.2 inches (avg ~6.6")

## Challenges and Solutions

### 1. Unstructured Text Data
**Problem**: Specifications stored as free text  
**Solution**: Developed regex patterns to extract numerical features with 95%+ success rate

### 2. High Missing Data in Some Features
**Problem**: FM radio (71%) and external memory (34%) missing  
**Solution**: Analyzed missing patterns, retained rows with critical information complete

### 3. Extreme Price Variations
**Problem**: Prices from ₹99 to ₹489,990 affecting analysis  
**Solution**: Used IQR outlier detection but retained all data as legitimate market segments

### 4. Feature Extraction Accuracy
**Problem**: Inconsistent text formatting across specifications  
**Solution**: Created robust regex patterns and validated through statistical analysis

## Files
- `mobile.csv` - Original dataset
- `mobile_phones_cleaned.csv` - Cleaned dataset  
- `mobile_data_analysis.ipynb` - Analysis notebook

## Next Steps
- Price prediction modeling using RAM, storage, battery features
- Market segmentation analysis
- Brand positioning and competitive analysis
