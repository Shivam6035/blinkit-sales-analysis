# blinkit-sales-analysis

### A Sanapshot of Datase
```python?code_reference&code_event_index=2
import pandas as pd

# Load the main data file
file_path = "blinkit excel dash board.xlsx - BlinkIT Grocery Data.csv"

try:
    df = pd.read_csv(file_path)
    
    # Get and print the column information
    print("--- Data Column Information ---")
    df.info()
    
    # Get and print the first 10 rows for a snapshot
    print("\n--- Data Snapshot (First 10 Rows) ---")
    print(df.head(10).to_markdown(index=False))
    
    # Get and print unique values for key categorical columns
    print("\n--- Unique Value Examples ---")
    print("\nItem Fat Content:")
    print(df['Item Fat Content'].unique())
    
    print("\nItem Type:")
    print(df['Item Type'].unique())
    
    print("\nOutlet Location Type:")
    print(df['Outlet Location Type'].unique())
    
    print("\nOutlet Size:")
    print(df['Outlet Size'].unique())

    print("\nOutlet Type:")
    print(df['Outlet Type'].unique())

except Exception as e:
    print(f"Error loading or processing file: {e}")

```

```text?code_stdout&code_event_index=2
--- Data Column Information ---
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 8523 entries, 0 to 8522
Data columns (total 13 columns):
 #   Column                     Non-Null Count  Dtype  
---  ------                     --------------  -----  
 0   Item Fat Content           8523 non-null   object 
 1   sr no                      8523 non-null   int64  
 2   Item Identifier            8523 non-null   object 
 3   Item Type                  8523 non-null   object 
 4   Outlet Establishment Year  8523 non-null   int64  
 5   Outlet Identifier          8523 non-null   object 
 6   Outlet Location Type       8523 non-null   object 
 7   Outlet Size                8523 non-null   object 
 8   Outlet Type                8523 non-null   object 
 9   Item Visibility            8523 non-null   float64
 10  Item Weight                7060 non-null   float64
 11  Sales                      8523 non-null   float64
 12  Rating                     8523 non-null   float64
dtypes: float64(4), int64(2), object(7)
memory usage: 865.7+ KB

--- Data Snapshot (First 10 Rows) ---
| Item Fat Content   |   sr no | Item Identifier   | Item Type             |   Outlet Establishment Year | Outlet Identifier   | Outlet Location Type   | Outlet Size   | Outlet Type       |   Item Visibility |   Item Weight |    Sales |   Rating |
|:-------------------|--------:|:------------------|:----------------------|----------------------------:|:--------------------|:-----------------------|:--------------|:------------------|------------------:|--------------:|---------:|---------:|
| Regular            |       1 | FDX32             | Fruits and Vegetables |                        2012 | OUT049              | Tier 1                 | Medium        | Supermarket Type1 |        0.100014   |         15.1  | 145.479  |        5 |
| Low Fat            |       2 | NCB42             | Health and Hygiene    |                        2022 | OUT018              | Tier 3                 | Medium        | Supermarket Type2 |        0.00859605 |         11.8  | 115.349  |        5 |
| Regular            |       3 | FDR28             | Frozen Foods          |                        2016 | OUT046              | Tier 1                 | Small         | Supermarket Type1 |        0.0258965  |         13.85 | 165.021  |        5 |
| Regular            |       4 | FDL50             | Canned                |                        2014 | OUT013              | Tier 3                 | High          | Supermarket Type1 |        0.0422779  |         12.15 | 126.505  |        5 |
| Low Fat            |       5 | DRI25             | Soft Drinks           |                        2015 | OUT045              | Tier 2                 | Small         | Supermarket Type1 |        0.0339702  |         19.6  |  55.1614 |        5 |
| low fat            |       6 | FDS52             | Frozen Foods          |                        2020 | OUT017              | Tier 2                 | Small         | Supermarket Type1 |        0.00550548 |          8.89 | 102.402  |        5 |
| Low Fat            |       7 | NCU05             | Health and Hygiene    |                        2011 | OUT010              | Tier 3                 | Small         | Grocery Store     |        0.0983124  |         11.8  |  81.4618 |        5 |
| Low Fat            |       8 | NCD30             | Household             |                        2015 | OUT045              | Tier 2                 | Small         | Supermarket Type1 |        0.0269037  |         19.7  |  96.0726 |        5 |
| Low Fat            |       9 | FDW20             | Fruits and Vegetables |                        2014 | OUT013              | Tier 3                 | High          | Supermarket Type1 |        0.0241293  |         20.75 | 124.173  |        5 |
| Low Fat            |      10 | FDX25             | Canned                |                        2018 | OUT027              | Tier 3                 | Medium        | Supermarket Type3 |        0.101562   |        nan    | 181.929  |        5 |

--- Unique Value Examples ---

Item Fat Content:
['Regular' 'Low Fat' 'low fat']

Item Type:
['Fruits and Vegetables' 'Health and Hygiene' 'Frozen Foods' 'Canned'
 'Soft Drinks' 'Household' 'Snack Foods' 'Meat' 'Breads' 'Hard Drinks'
 'Others' 'Dairy' 'Breakfast' 'Baking Goods' 'Seafood' 'Starchy Foods']

Outlet Location Type:
['Tier 1' 'Tier 3' 'Tier 2']

Outlet Size:
['Medium' 'Small' 'High']

Outlet Type:
['Supermarket Type1' 'Supermarket Type2' 'Grocery Store'
 'Supermarket Type3']

```

Detailed snapshot of your dataset, based on the "BlinkIT Grocery Data.csv" file.

The dataset contains **8,523 rows** and **13 columns**, representing individual product sales across various retail outlets. It's designed to analyze how different factors—like the product type, its visibility, and the store's characteristics—influence sales.

Here is a breakdown of each column:

### Product Details

  * **Item Identifier**: A unique code (e.g., FDX32) assigned to each specific product.
  * **Item Type**: The category the product belongs to. You have 16 distinct categories, including 'Fruits and Vegetables', 'Snack Foods', 'Household', and 'Health and Hygiene'.
  * **Item Fat Content**: A nutritional attribute, categorized as 'Low Fat' or 'Regular'. (Note: The data has a minor inconsistency, listing both 'Low Fat' and 'low fat', which would need to be cleaned for accurate analysis).
  * **Item Weight**: The physical weight of the product. This column has a significant amount of missing data (only 7,060 of 8,523 rows have a value).
  * **Item Visibility**: A percentage or ratio (a decimal value) indicating how much shelf space or promotion a product receives in the store.
  * **Rating**: A customer or internal rating for the product (e.g., 4, 5).

### Outlet (Store) Details

  * **Outlet Identifier**: A unique code (e.g., OUT049) assigned to each specific store.
  * **Outlet Establishment Year**: The year the store was first opened, ranging from 2011 to 2022 in your data.
  * **Outlet Size**: The size of the store, categorized as 'Small', 'Medium', or 'High'.
  * **Outlet Location Type**: The type of area where the store is located, classified as 'Tier 1', 'Tier 2', or 'Tier 3'.
  * **Outlet Type**: The format of the store. You have 4 types, including 'Supermarket Type1', 'Supermarket Type2', 'Supermarket Type3', and 'Grocery Store'.

### Key Metrics

  * **sr no**: A simple serial number or row index (from 1 to 8523).
  * **Sales**: This is your primary performance metric. It's a numerical value representing the total sales for that specific product in that specific outlet.

##  dashboard
<img width="1988" height="1060" alt="image" src="https://github.com/user-attachments/assets/bf6ca5d2-01d3-4ac5-a59a-2decc2585ffe" />

<img width="1997" height="1065" alt="image" src="https://github.com/user-attachments/assets/d4ff686d-4a85-4889-8782-5a72fcf8a5fb" />

<img width="1994" height="1068" alt="image" src="https://github.com/user-attachments/assets/7603ccb7-a3d3-495f-a264-e272237fdc64" />

<img width="1996" height="1057" alt="image" src="https://github.com/user-attachments/assets/b99244be-bfe5-44bb-8b0d-e8ab0b15b41e" />

