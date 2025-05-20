# Austin Bikeshare SQL Project - Most Popular Bike

## Overview
A fictional bikeshare company in Austin, TX has reached a major milestone and wants to celebrate their success. The marketing team plans to write a blog post announcing the **popularity of their most used bike**. They've asked for the following data:
- Which bike is used most often?
- What is the average duration of its trips?
- Which station is it most likely to be found at?

To answer these questions, we used **Google BigQuery** (Sandbox) to query the public Austin bikeshare dataset.

---

## Tools Used
- Google BigQuery (Sandbox)
- SQL

---

## Project Steps
1. Queried the dataset to find the bike with the **highest number of rides**
2. Calculated the **average duration** of trips for that bike
3. Created a **temporary table** to isolate rides from that bike
4. Determined the **most frequent starting station** for that bike

---

## Sample SQL Snippet
```sql
-- Step 1: Identify the most used bike
SELECT
  bike_id,
  COUNT(*) AS ride_count,
  AVG(duration_minutes) AS avg_duration
FROM `bigquery-public-data.austin_bikeshare.bikeshare_trips`
GROUP BY bike_id
ORDER BY ride_count DESC
LIMIT 1;
