

# 🍽️ Zomato Interactive Analytics Dashboard

## 📊 Overview

This Power BI project explores restaurant insights using the Zomato dataset. The dashboard provides deep analysis of restaurant distribution, customer preferences, pricing trends, and ratings across multiple cities and countries. It enables stakeholders to make data-driven decisions in the food service domain.

---

## 🎯 Objective

To  make it more **interactive, bookmark,slicers,drill through are used**:

- Global restaurant distribution
- Most popular cuisines
- City-wise pricing and affordability
- Ratings overview and trends
- Online delivery and table booking analysis
- Restaurant popularity based on user votes
- Geospatial distribution of restaurants

---

## 📁 Dataset

**Source**: Zomato Restaurant Dataset  
**Columns include**:
- Restaurant ID, Name, Country Code, City, Address
- Locality & Locality Verbose
- Longitude & Latitude
- Cuisines, Price for Two, Currency
- Has Table Booking, Has Online Delivery, Is Delivering
- Price Range, Aggregate Rating, Rating Color & Text, Votes

---

## 📌 Key Features

### 1. Restaurant Distribution (Country & City)
- Visual: Map and Bar Chart
- Filters: Country, City
- Insights: Which cities and countries have the highest restaurant density

### 2. Top Cuisines Offered
- Visuals: Column Chart, Treemap, and Donut Chart
- Insights: Most popular cuisines globally and by city

### 3. Pricing and Affordability
- Visuals: Bar Chart and Heatmap
- Filters: Country, Currency
- Insights: Budget vs Premium cities, country-wise cost comparison

### 4. Ratings Overview
- Visuals: Histogram, Bar Chart (Rating Text vs Count), Color Coded
- Insights: Distribution of ratings, top-rated cities

### 5. Delivery & Table Booking Analysis
- Visuals: Stacked Bar, Pie Chart, Matrix
- Insights: Cities with most delivery and table booking options

### 6. Votes and Popularity
- Visuals: Scatter Plot (Votes vs Rating), Top 10 Table
- Insights: Do votes correlate with better ratings?

### 7. Geolocation Visualization
- Visual: Map using Latitude and Longitude
- Tooltip: Restaurant Name, Cuisine, Rating, Online Delivery

---

## 🔄 Interactive Functionalities

- **Buttons**:  
  - Toggle views (e.g., Ratings vs Price)
  - Use of **Bookmarks** to switch between key dashboards


- **Slicers & Filters**:
  - Country, City, Cuisine, Price Range, Rating Text

- **Custom Tooltips**:
  - Hover over visuals to see restaurant-level insights

- **Drill-Through Pages**:
  - Click on City or Restaurant → View detailed metrics including:
    - List of Restaurants
    - Average Ratings
    - Votes
    - Top Cuisines

---

## 🛠️ Tools & Technologies

- **Power BI Desktop**
- DAX (Data Analysis Expressions)
- Data Cleaning & Modeling
- Bookmarks, Tooltips, Slicers, Drill-through, Buttons

---
## 🧮 DAX Calculations
To enhance the interactivity and insights of the dashboard, two custom DAX columns were created:
1. Delivery and Booking Status

        DeliveryBookingStatus = 
            SWITCH(
                TRUE(),
                Zomato[Has Online delivery] = "Yes" && Zomato[Has Table booking] = "Yes", "Both",
                Zomato[Has Online delivery] = "Yes" && Zomato[Has Table booking] = "No", "Only Delivery",
                Zomato[Has Online delivery] = "No" && Zomato[Has Table booking] = "Yes", "Only Table Booking",
                "None"
            )

🔹 Purpose:
This column classifies each restaurant based on its service availability. It supports the Matrix visualization to compare cities with both services.

🔹 Used In:

Matrix: City vs Delivery and Table Booking

Filter slicers to analyze combined services

3. Price Category

           PriceCategory = 
            VAR cost = [Average Cost for two]
            VAR high = PERCENTILEX.INC(ALL('zomato'), 'zomato'[Average Cost for two], 0.8)
            VAR low = PERCENTILEX.INC(ALL('zomato'), 'zomato'[Average Cost for two], 0.2)
            RETURN
                SWITCH(
                    TRUE(),
                    cost >= high, "Premium",
                    cost <= low, "Budget",
                    "Mid-Range"
                )

🔹 Purpose:
This column classifies restaurants based on their price range into categories for better understanding of affordability trends.

🔹 Used In:

Visual filters like Affordability by City/Country

Bar Charts showing Price Category vs Average Rating

Drill-through pages and slicers


---

## 🚀 How to Use

1. Clone this repository
2. Open the `.pbix` file in Power BI Desktop
3. Explore and interact with filters, slicers, and bookmarks
4. Use drill-through functionality for deeper insights

---

## 📌 Author

**Fareeda Rasheed**  
Data Science & Analytics Enthusiast  
[http://linkedin.com/in/fareeda-rasheed-631983249 ](#)  | [fareedafari2001@gmail.com](#)

---



