# Consumer Behaviour (Part 1 of Final Python Project)

- The client has submitted a request to produce a dashboard that enables them to track consumer behaviour.
- The project brief, as well as user stories and application wireframes are available [here.](https://miro.com/app/board/uXjVOdPBydg=/?invite_link_id=165928041830)


## But wait...the data needs cleaning

- Before the dashboard can be produced, the data provided by the client needs to be appropriately extracted and transformed (cleaned).
- This particular project will focus on the data cleaning as part 1, as per the brief.
- A second half of this project (part 2) will be deployed as a dash application and within a separate project to this repository.


## The data and initial observations

- The data was provided by the client via a zip file named `all_files.zip` from the following link [here.](https://drive.google.com/file/d/12T1_3h0kUkgc-flBeSa_nDdHNjuAIsX7/view)
- It should be noted that this file is large and likely takes a few minutes to download and open.
- As per the brief there are clear issues with the data that will need to be resolved in order to successfully provide useful data to the dash app. Explanations of the initial issues are in the following sub-headings.

### Branch sales

- Branch sales data files are split approximately 50% into csv files and json files. In order to allow the data to be handled properly there will need to be an appropriate conversion undertaken to successfully merge the data into a dataframe.
- Branch sales data, specifically the branch name is only identifiable by their filename; there is no identifiable branch information within the file and therefore it would not be possible to merge with any other file using a branch name. There would need to be a way of efficiently adding a new `branch_name` field into the branch sales data that uses part of the filename as the value of this field.
- As per the brief the headings of each file will need to be made consistent.
- The `quantity` field within the data does not appear to be a number data type. This field should be converted to an integer to enable use of `sum()` to avoid the risk of concatenating strings.
- There are many files to work through and it would not be viable to manually create a dataframe from each file; therefore, adding all files to a dataframe will be undertaken using list comprehension.

### Products_list

- It was noticed the products_list file had inconsistencies with regards to the `categories` field. Specifically, there were two conflicting values: `fruits & vegetables` and `fruits & vegetable`. Values will need to be replaced in order to aid with consistency.


## File and Folder setup

1. Data cleaning was successfully undertaken using python notebook, under `data_cleanse.ipynb` of this repo.
2. If using this repo to the clean the data, file placement is very important and the following placements should be conducted:
    - All branch data files (such as `2010-2020_Bassetlaw_outlet.csv`), `branch_expenses.xlsx`, `branch_list.xlsx` and `terminologies.txt` should be placed in a folder from the root folder called `data`.
    - The `products_list.csv` file should be placed into the root folder and kept separate. This is because the list comprehension used to extract the filenames into the appropriate branch row of the first dataframes within `data_cleanse.ipynb` are looking for all csv and json files within the `data` folder. `products_list.csv` should not be extracted into the initial dataframe during list comprehension and therefore is kept separate.


## Running the script

- Once all files are in the correct locations, running the script within `data_cleanse.ipynb` will start to clean and produce a number of new csv files into the root folder. It should be noted that running the script will take several minutes due to the size of the data. Considerations should be made to allocate more virtual memory to support running of this script.
- The following 7 files will be produced in the root folder once the script has completed:
    - `branch_name_list.csv`
    - `grouped_branch_performance.csv`
    - `grouped_categories.csv`
    - `grouped_products.csv`
    - `overall_branch_performance.csv`
    - `profit_per_branch.csv`
    - `region_list.csv`
- These files are then added to the dash application in part 2 of this project. See part 2 of this project for more information.
- Each segment of the script in `data_cleanse.ipynb` has been commented with a brief explanation. See comments for more information.