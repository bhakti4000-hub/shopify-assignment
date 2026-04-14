# shopify-assignment
Shopify Featured Products with Infinite Scroll


📌 Overview
This project implements a custom Shopify collection page where:

15 featured products are always shown at the top
Remaining products are displayed after featured products
Infinite scroll loads additional products
Sorting and filtering behave as per Shopify default behavior


⚙️ Implementation Details
1. Featured vs Non-Featured Separation
Products are fetched using Shopify AJAX API (/products.json)
Tags are normalized using:
product.tags.map(tag => tag.toLowerCase().trim())
Products with tag featured are stored separately
Maximum 15 featured products are collected

2. Initial Load Logic
First request fetches up to 50 products
Ensures all 15 featured products are collected
Displays:
15 featured products
5 normal products

3. Infinite Scroll
Scroll event triggers next page fetch
Each request loads 20 products
Only non-featured products are appended after initial load

4. Duplicate Prevention
Used Set() to track displayed product IDs:
let displayedIds = new Set();
Prevents duplicate rendering across pages

5. Sorting & Filtering
When sort_by or filter params are detected in URL:
Custom JavaScript is disabled
Shopify default behavior is used
Ensures no featured pinning during sorting/filtering

6. Scalability
Products are fetched in pages (20 at a time)
Avoids loading entire collection at once
Works efficiently for large collections

7. Limitations & Solution
Shopify Liquid cannot reorder paginated products dynamically
Used JavaScript to:
Fetch products via API
Reorder featured products on the frontend

🚀 Final Result
Featured products always appear at the top
Infinite scroll loads products smoothly
Sorting and filtering work as expected
No duplicate products
