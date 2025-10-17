# Assignment

## Brief

Write the SQL DML statements for the following questions.

## Instructions

Paste the answer as SQL in the answer code section below each question.

### Question 1

Select the minimum and maximum price per sqm of all the flats.

``
# missed the sqm meter
Select max(resale_price/floor_area_sqm) as Max_Price, min(resale_price/floor_area_sqm) as Min_Price from resale_flat_prices_2017

```

### Question 2

Select the average price per sqm for flats in each town.

```
# missed the sqm meter
Select town, Round(Avg(resale_price/floor_area_sqm),2) as Avg_Price from resale_flat_prices_2017 group by town
order by Avg_Price

```

### Question 3

Categorize flats into price ranges and count how many flats fall into each category:

- Under $400,000: 'Budget'
- $400,000 to $700,000: 'Mid-Range'
- Above $700,000: 'Premium'
  Show the counts in descending order.

```
SELECT 
    CASE 
        WHEN resale_price < 400000 THEN 'Budget'
        WHEN resale_price BETWEEN 400000 AND 700000 THEN 'Mid-Range'
        WHEN resale_price > 700000 THEN 'Premium'
    END AS price_category,
    COUNT(*) AS flat_count
FROM 
    resale_flat_prices_2017
GROUP BY 
    price_category
ORDER BY 
    flat_count DESC;

```

### Question 4

Count the number of flats sold in each town during the first quarter of 2017 (January to March).

```
SELECT 
    town,
    COUNT(*) AS flats_sold
FROM 
    resale_flat_prices_2017
WHERE 
    "month" >= '2017-01-01' AND  "month" < '2017-04-01'
GROUP BY 
    town
ORDER BY 
    flats_sold DESC;

# Ans#2
Select town, count(*) as units_sold from resale_flat_prices_2017
where month in ('2017-01','2017-02','2017-03') group by town order by units_sold desc



```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
