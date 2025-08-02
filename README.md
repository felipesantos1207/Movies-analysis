## 🧼 Data Cleaning Process – Step by Step

The following cleaning steps were applied using Google Sheets:

1. **Backup of original data**
   - Created a copy named `movies_original.csv` to preserve the raw version of the dataset before applying any transformations.

2. **Uppercase standardization**
   - Converted all text fields (including titles, director names, and cast) to uppercase for consistency and easier handling in SQL.

3. **Column renaming**
   - Renamed columns such as `DIRECTOR (1)` to `DIRECTOR_2` and `CAST (1)` to `CAST_2` to avoid special characters and parentheses, which can create issues in SQL or BI tools.

4. **Whitespace removal**
   - Trimmed leading and trailing whitespaces in all text fields.
   - Removed duplicated spaces inside strings (e.g., "STAR   WARS" → "STAR WARS") to prevent grouping or filtering issues.

5. **Accent removal (considered but not applied)**
   - I evaluated removing accents from names and titles, but decided to **preserve the original characters** to maintain data quality and avoid losing semantic accuracy.

6. **Primary key validation (`MOVIE_TITLE`)**
   - Verified that `MOVIE_TITLE` contains no null values and is unique across the dataset. Confirmed via filter and blank count functions.

7. **Date formatting**
   - Ensured the `DATE` column was in date format.
   - Adjusted formula ranges to count blanks correctly, avoiding false positives from unused rows.
   - No null or inconsistent dates were found.

8. **Null handling in optional fields**
   - Columns like `DIRECTOR_2` and `CAST_2` are intentionally incomplete for some entries (e.g., films with a single director or small cast). No imputation was done, as missing values are expected and meaningful.

9. **Cleaning numeric fields (`BUDGET` and `REVENUE`)**
   - Removed thousand separators (`,`) and converted values from text to numbers using `VALUE()` and `SUBSTITUTE()` functions.
   - Verified successful conversion by applying `MAX()` and `MIN()`.
   - Smallest value found: `10,000`, considered plausible for low-budget films. No extreme outliers or invalid values (e.g., `0` or negative) were found.

10. **Final validation**
   - Verified formatting across columns
   - Would request a double-check from a colleague if this were a team project
