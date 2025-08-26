Chinook SQL Data Analysis

This project explores the Chinook SQLite database, a sample music store dataset. Using SQL queries in combination with Python (SQLite + Pandas + Matplotlib), we analyze sales, customers, employees, and track information to uncover useful business insights.

-   Dataset composition

The database used is Chinook_Sqlite.sqlite, which contains tables such as:

Album
Artist
Customer
Employee
Genre
Invoice
InvoiceLine
MediaType
Playlist
PlaylistTrack
Track

-   Analysis Performed

1. Previewing Data

Extracted the first 10 albums from the Album table.

2. Sales by Country
SELECT Customer.Country, SUM(Invoice.Total) AS Total_Sales
FROM Invoice
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
GROUP BY Customer.Country
ORDER BY Total_Sales DESC;


Insight: The USA leads with the highest sales, followed by Canada and France.

3. Top 5 Customers

Identified customers with the highest purchase amounts.

Insight:    Helena Holý is the top spender.

4. Most Popular Artist
SELECT ar.Name AS Artist, SUM(il.UnitPrice * il.Quantity) AS TotalSales
FROM InvoiceLine il
JOIN Track t ON il.TrackId = t.TrackId
JOIN Album al ON t.AlbumId = al.AlbumId
JOIN Artist ar ON al.ArtistId = ar.ArtistId
GROUP BY ar.ArtistId
ORDER BY TotalSales DESC
LIMIT 1;


Insight: Iron Maiden generated the highest track sales.

5. Average Invoice Value by Country

Merged Invoice and Customer tables to calculate the mean spending per invoice.
Insight:    Countries like Chile and Hungary show higher average invoice totals compared to others.

6. Employee Sales Performance

Measured revenue linked to employees (via their supported customers).
Insight:    Jane Peacock is the top-performing sales employee.

7. Monthly Sales Trends

Grouped invoices by month and plotted revenue trends with Matplotlib.
Point:  Helps visualize seasonality and revenue growth over time.

## Key Insights

The USA dominates sales, accounting for the majority of revenue.

A small group of loyal customers contributes significantly to overall purchases.

Rock and metal genres (Iron Maiden, AC/DC, etc.) generate high revenue.

Some employees clearly outperform peers in sales contributions.

Monthly trends highlight periods of strong performance, useful for forecasting.

⚙️ Tech Stack

Python (Pandas, Matplotlib, SQLite3)

SQL for querying relational data

Google Colab / Jupyter Notebook for interactive analysis


## Next Steps

Extend analysis to include genre popularity and playlist insights.

Build a Streamlit dashboard for interactive exploration.

Integrate machine learning models for customer segmentation.