# [splunk-impervacwaf](https://splunkbase.splunk.com/app/6627)
Splunk App - The Imperva CWAF app provides and easy-to-use experience to analyze traffic information passing to your web servers and applications and details the important information in dashboards.

# Setup process
## Imperva
1. Activate logging and configure the log integration settings in the Imperva Cloud Security Console. (Account > SIEM Logs > WAF Log Setup)
1. Select 'Amazon S3' as the Connection type.
1. Disable Encryption. (This is how this app was tested)
1. Select 'CEF' as format type
1. Disable Compression.
1. Enter in the Amazon S3 API Details (Key and Secret) and S3 Bucket Path. (example: imperva-logs/waflogs)
1. Ensure 'Website Log Levels' are set to 'All Logs'.
1. Account > SIEM Logs > Website Log Levels

## Splunk
1. Install 'Splunk Add-on for Amazon Web Services (AWS)'.
1. Go to 'Splunk Add-on for Amazon Web Services (AWS)' > 'Configuration' tab > Add.
1. Enter Name, AWS Key ID, Secret Key and region category if appropriate. Save. 'example: Name=Imperva, AWS Key ID=1234567HGSD, Secret Key=12345LKJH, region=Global'
1. Create an index in Splunk called 'imperva'.
1. Create a data input in Splunk. Go to 'Settings' > 'Data Inputs' > Locate 'AWS S3' > '+ Add'.
1. Fill in the details like the example below. (If not listed below, leave default)
> Name=imperva, AWS Account=Imperva, Bucket Name=imperva-logs, Key prefix=waflogs/
> -More Settings-
> Set sourcetype=manual, Source type=imperva:cef, Index=imperva
1. Finally, Install the 'Imperva CWAF' app.
1. Restart Splunk if needed.

## Strange formatting of logs
* If logs are coming through with strange formatting, try setting the logs to uncompressed in the Imperva WAF console.

# Version (Latest)
> 1.1.1

# Author
* Travis Anderson
