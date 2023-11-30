## :clipboard: Context details
**Dataset**
dimView_NS

**Table**
dimView_NS_Azure_Extract

**Scheduled Query**
dimView_NS_Azure_Extract

Runs daily at 9.30am Irish time

**Type**
External table

**Description**
Query set to run take a daily a snapshot of OYY SEM extract, which has been created for all the active and non-test restaurants.

 

## :white_check_mark: Usage
BigQuery 

factView_GA_Restaurant-Level-Stats 

factView_GA_Campaign-Level-Stats

 

## :pencil: Process & Operational Details
1. Storage Transfer
  - Azure extract transfer created with a URL list.tsv in Storage Transfer
  - Transfer scheduled to run every day at 9AM Irish time

2. Cloud Storage 
  - File exported to Cloud Storage > bGenius feed > stgorderyoyodwprod.blob.core.windows.net > sem-dataextract

3. BigQuery
  - Table dimView_NS_Azure_Extract created from the Cloud Storage file. Scheduled query set to run everyday at 9.30AM Irish time


     CREATE OR REPLACE EXTERNAL TABLE `rare-deployment-311310.dimView_NS.dimView_NS_Azure_Extract`
     OPTIONS (
       format = 'CSV',
       allow_quoted_newlines	= TRUE,
       uris = ['gs://bgenius-feed/stgorderyoyodwprod.blob.core.windows.net/*.csv']
)


 

Add label
