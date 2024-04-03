# Automating-Data-Manipulation-using-Cloud-Functions
Here, you will find a Google Cloud Function that is like a helpful assistant for your data tasks. When you upload CSV files to your Google Cloud Storage, this function springs into action, using the pandas library in Python to tidy up your data, uncover insights, and then neatly store the cleaned-up data in another Cloud Storage bucket.

## Functionality

Changes in a storage bucket trigger the Cloud Function and perform the following operations on CSV files:

- Reads the CSV file from the Cloud Storage bucket.
- Cleans the data by removing duplicate rows and performing descriptive statistics.
- Generates insights such as the number of rows and columns, data types, memory usage, etc.
- Computes additional metrics such as the total number of app titles containing specific keywords, average app ratings, average ratings by category, etc.
- Outputs the cleaned data to another Cloud Storage bucket as a CSV file.

## Usage

To use this Cloud Function:

1. **Create a Google Cloud Platform (GCP) Project:**
   - Sign in to the Google Cloud Console: https://console.cloud.google.com/.
   - Create a new project or select an existing one.

2. **Enable Required APIs:**
   - Navigate to the "APIs & Services" > "Library" section in the Cloud Console.
   - Enable the Cloud Functions API and Cloud Storage API for your project.

3. **Prepare the CSV Data:**
    - Make sure to create two Cloud Storage buckets, one to access the input `.csv` file from, and the other to store the processed 
    `.csv` file. Also, they should exist in the same project as your Cloud function!

4. **Deploy the Cloud Function:**
    - Select the Google Cloud project you want to work on.
    - Go to the "Cloud Functions" section in the Cloud Console.
    - Click on the "Create Function" button.
    - Give the `function name`, `region name`, trigger types as `Cloud Storage`, Event type as `finalized`, and `bucket name` (where your 
      input `.csv` file is stored).
    - Select the “runtime” you wish to write your function in. I have chosen Python for this demonstration. 
    - Download the  “bucket-upload-triggered-function.zip” and extract the source code of the function. Copy the contents of “main.py” 
      and “requirements.txt” respectively. 
    - In line 115, replace the file path in `.to_csv` with the name of your output storage bucket and the name of the output `.csv` file. 
    - Click on the "Create" button to deploy the function.

4. **Trigger the Function:**
   - Upload a CSV file in a Cloud Storage bucket monitored by the Cloud Function.
   - The Cloud Function will be triggered automatically upon changes in the bucket and process the uploaded CSV file.

5. **Access the Output:**
   - Once the function is triggered, the cleaned data will be stored in another Cloud Storage bucket (`gs://apps-data-output/cleaned_data.csv` in this example).
   - You can access the cleaned data from the output bucket for further analysis or processing.
   - You can view the output of the data analysis in the `Permissions` tab!
