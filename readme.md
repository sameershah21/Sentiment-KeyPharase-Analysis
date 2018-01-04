<b>SUMMARY:</b> <br/>
This is a Machine Learning Review Processing code snippet that uses Azure Cognitve Services – Text API to detect sentiments and key phrases of reviews left by users. 
<b>PRE-REQUISITIES SETUP:</b> <br/>
Assumes that you have Azure Data Lake Analytics(ADLA) Service and Azure Data Lake Storage (ADLS) Setup. Refer to following link to set both up: https://docs.microsoft.com/en-us/azure/data-lake-analytics/data-lake-analytics-get-started-portal
<br/><b>Files and folders: </b> <br/>
<b>Input/YelpReview.csv </b> : A scrubbed yelp review input file. It contains ‘comments’ field and other values that will be required to analyze the sentiments of the comments of different reviewers. The same field is also used to detect key phrases that a particular reviewer reviewed.
Using Microsoft best practices, I used the Azure Cloud Explorer and File Explorer to generate the EXTRACT SCRIPT. Also, validated the csv file for proper line endings, separators and encodings
<b>FoodPlaceReviewAnalyzer.usql </b> –  This U-SQL file will >Accept the YelpReview File as input, >Extract KeyPharases and Sentiments for comments by processing the comments field and generate 2 output files – Sentiment.csv and split_keyphrases.csv
<b>Output/sentiment.csv</b> – Generated after the Food Place Review Analyzer Job runs on the ADLA using inputs from ADLS.
<b>Output/split_keyphrases.csv</b> - Generated after the Food Place Review Analyzer Job runs on the ADLA using inputs from ADLS.
<b>TROUBLESHOOTING:</b> <br/>
Q: ADLA job output fails with number of columns, more or less compared to the actual file.
A: Make sure the number of columns in csv match, double check that the Extraction Script is being generated using Visual Studio Tool. Make sure that input datatypes within the usql match the csv. If the csv file has headings then use skipFirstNRows:1 withing Extractors.CSV
Q: Job errors out saying Cannot find ‘TEXT’ within the script
A: Means that text is being parsed correctly. Resolution is same as above.
