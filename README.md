📊 Hotel Booking Cleaning Python Project


A Python project for cleaning hotel booking data.

1
🛠️ Tools:
Python (Pandas)


🧹 Data Cleaning Process
1. Initial dataset size: 22,000 records.
2. Duplicate removal: Dropped 2,000 duplicate records based on booking ID and guest information.
3. Guest name (guest_name) cleanup:
    - Removed unnecessary spaces.
    - Converted text to title case (e.g., john smith → John Smith).
    - Replaced missing values (NaN) with 'Unknown'.
4. Email column cleanup:
    - Removed leading/trailing spaces.
    - Replaced missing values (NaN) with 'Unknown'.
    - Replaced missing values (NaN) with 'Unknown'.
6. Listing city (listing_city) cleanup:
    - Standardized city names by fixing inconsistent or misspelled entries.
8. Payment status (payment_status) cleanup:
    - Replaced missing values with 'n/a'.
    - Standardized inconsistent values (e.g., 'paid', 'unpaid', 'free', 'n/a').
10. Review score (review_score) cleanup:
    - Standardized invalid values and typos.
    - Replaced missing values with 0 (indicating no review left).
11. Cancellation status (is_cancelled) cleanup:
    - Standardized inconsistent formats (e.g., 'No', ' no', 'YES', etc.) to 'Yes' / 'No'.
12. Business logic – Free bookings:
    - If price_per_night == 'free', then set payment_status = 'Free'.
13. Date columns (checkin_date, checkout_date) cleanup:
    - Converted to datetime format.
    - Ensured checkout_date > checkin_date; corrected any logical inconsistencies.
14. Nights (nights) logic:
    - If nights == 'seven' → calculate nights as checkout_date - checkin_date.
    - If nights is missing → calculate as checkout_date - checkin_date.
    - If nights < 0 → replaced with abs(nights).
15. Price per night (price_per_night) logic:
    -If value is 'free' or missing → set to 0.
16. Total price (total_price) logic:
    - If contains 'error' or is missing → recalculate or clean accordingly.
17. Cross-field logic:
    - If both price_per_night and nights are 0 → set total_price = 0.
    - If price_per_night == 0 → set total_price = price_per_night * nights.
18. Price imputation:
    - Filled missing values in price_per_night using the mean price grouped by listing_city and nights.
--------------
Output result:
| **Column Name**      | **Description**                                                                  |
|----------------------|--------------------------------------------------------------------------------- |
| `booking_id`         | Unique ID for each booking.                                                      |
| `guest_name`         | Name of the guest.                                                               |
| `email`              | Guest's email address.                                                           |
| `listing_id`         | ID of the listed property.                                                       |
| `listing_city`       | City name (`'Los Angeles'`, `'San Francisco'`, `'New York'`).                    |
| `checkin_date`       | Date the guest checks in.                                                        |
| `checkout_date`      | Date the guest checks out.                                                       |
| `nights`             | Number of nights booked.                                                         |
| `price_per_night`    | Cost per night.                                                                  |
| `total_price`        | Total cost for the stay.                                                         |
| `payment_status`     | Payment completion status (`'Pending'`, `'n/a'`, `'Paid'`, `'Unpaid'`, `'Free'`).|
| `review_score`       | Guest's review rating (0–5). If 0 – review is absent.                            |
| `is_cancelled`       | Indicates if booking was cancelled (`'Yes'`, `'No'`).                            |
