# awc_details
Webscraping: Fetch Health Centre (Aanganwadi) Details
The file BSOUP_AWC_KAR_DISTRICTS.ipynb is python code to scrape Aanganwadi details from the ICDS website http://icds-wcd.nic.in/. 

## Input files

1. awc_dist_code_to_process.csv - is a control file with district code and a flag (y/n) to indicate whether Aanganwadi Center (AWC) details for the district should be
extracted or not.
  
## Output files

1. awc_karnataka_districts + current_timestamp - with AWC co-ordinates for all districts in the state
2. awc_monitoring_details_final_ + district_code + current_timestamp - for each district as indicated in the input control file
3. Intermediate files such as awc_failed_first_try_ + district_code are created to temporarily store records where the extract process fails. These get overridden if the code is re-run.

## Processing

1. Read input file awc_dist_code_to_process.csv to find out which districts to process
2. Input file has 2 fields: 1) input_dist_code 2)input_process_y_n; edit this file to control which districts to process
3. Each AWC has two urls from which we extract data. For example for AWC = 29572011016, the urls are:
  http://icds-wcd.nic.in/icdsknowawcformat.aspx?awcode=29572011016&State_Code=29&District_Code=572&Project_Code=2957201 (AWC monthly details)
  http://icds-wcd.nic.in/icdsmis_ViewCurMonMPR.aspx?awcid=29572011016&State_Code=29&District_Code=572&Project_Code=2957201 (AWC monthly details at caste/gender level)
4. The extraction for each AWC will be attempted for a max of three times 
5. Records not extracted after three attempts if any will be written to awc_failed_third_try_ + district code + timestamp

## Installations required

Requires BeautifulSoup to be installed on your system.

## Usage

1. Download the .ipynb file to a folder on your system
2. Input file awc_dist_code_to_process.csv must be available in the same folder as the .ipynb file
3. Output files with scraped details are created in the same folder as the .ipynb file once the code runs successfully
4. This code should be executed before date rolls over to a new month. To extract details for April 2022, run the code on or before 30th April 2022, ideal schedule date would be around April 25th. 
5. Output file layout is as described in awc_columns_description.xlsx

