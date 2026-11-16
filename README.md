# Custom-Excel-Exporter
This module is used to export data in any required custom format. No additional UI configuration is required to implement the export functionality. You can directly use the Java Action to export data in your desired format in a simple and efficient way.

# Dependencies
• MxModelReflection 
 
• Excel Exporter
 
• Community Commons

Note : In this module, Excel Exporter and MxModelReflection are used only for JAR-related purposes.
Community Commons are used to implement custom logic for optimization and learning purposes.

# JAVA Configuration :
CustomExcelExport For CSV and XLSX

 1. FileName

Specify the file name for the Excel file to be downloaded. The name provided here will be used as the downloaded file name.

2. FileDocument

Create an object for your custom entity, which must be generalized from the System.FileDocument entity. This object is used to store and manage the generated Excel file.

3. Headers

Provide the column headers as comma-separated values. These headers will be displayed in the first row of the Excel file.

Example: HeaderValue1, HeaderValue2, HeaderValue3,etc....

Each value represents a column header in the exported Excel file.

4. ListToExport

Pass the list of objects containing the data you want to export to Excel. The objects in this list will be processed to generate the Excel file.

5. AttributeNames

Provide the exact attribute names of the entity associated with the objects in ListToExport. These names are used internally by the Java Action to retrieve and map the corresponding attribute values to the Excel columns.

Specify the attribute names as comma-separated values.

Example: AttributeName1, AttributeName2, AttributeName3, etc...

# CustomExcelExport For CSV ZIP
The five parameters described above serve the same purpose as in the previous Java Action. The only difference is that a new parameter, RecordSizePerCSV, has been introduced.

6. RecordSizePerCSV

This parameter specifies the maximum number of records to be included in a single exported Excel file. The input list will be split into multiple files based on the configured record count.

Example:

If the ListToExport contains 3,000 records and If we set the RecordSizePerCSV to 1000, the records will be divided into the following files:

Note: Ensure that the order of the attribute names matches the order of the headers so that the exported data appears under the correct column headings.

Note : 
   *If you are using a single entity, you can directly pass the same entity list to export the file.

   *If you need to export association attributes, you can simply create a Non-Persistent Entity, map the required attributes to it, and pass the Non-Persistent Entity list to export the data.

 # CSV JAVA Configuration
   
<img width="1177" height="851" alt="Screenshot for CSV" src="https://github.com/user-attachments/assets/116c8b40-d270-428f-b9a4-8ddd789b9ff6" />

# Output
<img width="1915" height="872" alt="Screenshot Output" src="https://github.com/user-attachments/assets/5064539d-5715-4b1e-86ee-6d7e51872dc9" />

 # ZIP JAVA Configuration
 <img width="1038" height="846" alt="Screenshot For Zip Java" src="https://github.com/user-attachments/assets/218b9cf8-9511-4478-bbf6-494f954725f2" />


# Optimization
Using this custom Java Action, the export process can handle up to 8 lakh records in approximately 5–10 seconds under the tested conditions.

However, retrieving a large list of records can take significantly more time than processing and exporting the data. Therefore, it is recommended to use OQL (Object Query Language) to retrieve the required records efficiently and then pass the retrieved list to this Java Action for processing and export.

This approach helps optimize the overall export workflow by reducing the time spent retrieving data and enabling faster processing of large datasets.

Recommendation: Use OQL to retrieve the required records and the custom Java Action to process and export them. Actual performance may vary depending on the database, server resources, data complexity, and export configuration.
