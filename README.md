# Program Overview
<h4>Purpose:</h4> 
The purpose of this program is to leverage the LegiScan API to automate the collection, identification, and extraction of bill data, minizing manual efforts and improving efficiency.  

<br><h4>Requirements:</h4>
To run this program you'll need the following
- API Key from https://legiscan.com/
- Permission to Download & Create new files
- Latest Version of Python Installed https://www.python.org/downloads/
- Reliable internet

<br><h4>Recommendations:</h4>
- It is recommended to run the program once per week to check for any updates to bill data
- To limit unnecessary API calls when monitoring a small number of states, adjust the *stateCodes* parameter as needed
- If the search criteria is too broad or too restrictive, refine or broaden the *relevanceFilter* and *searchTerms* parameters as needed
- Do not set relevanceFilter too low, as it'll result in too many subsequent API calls when collecting Bill Info

<br><h4>Features:</h4> 
- Minized API usage by downloading new datasets only when updated are detected
- Automatically updating bill data when changes are detected
- Adjustable filtering criteria through *relevanceFilter* and *searchTerms* parameters
- Aggregation of all collected bill data into a singular dataset for easy exporting and extraction
- Exporting all bill data into a single Excel workbook sorted by bill relevance

<br><h4>Outputs:</h4> 
The final codeblock in this program outputs a single Excel workbook with individual sheets that correspond to the dates in the *stateCodes* parameter.
Below is a breakdown of each of the columns, please note if a specific cell is empty, it's due to the API not providing an input for that given cell.
- *latest_update*: datetime of when the row was aggregated from the dataset, format: *MM-DD-YYYY* 
- *relevance*: a percentage from (0-100) representing how closely the bill matches the search criteria
- *state*: abbreviation of the state the bill is from
- *bill_number*: number of the bill
- *date_introduced*: date the bill was introduced
- *description*: description of the bill
- *status*: current status of the bill
    - Possible values include: *Introduced*, *Engrossed*, *Enrolled*, *Passed*, *Vetoed*, *Failed*, *N/A*
- *link*: direct link to the bill
- *chamber*: Legislative chamber associated with the bill
    - *Note*: *chamber* is inferred from the prefix of the *bill_number* and may be *House*, *Senate*, or the prefix itself
- *party*: political party of the primary sponsor
- *primary* sponsor: list of the primary sponsor
- *co-sponsor*: list of co-sponsors
- *joint sponsor*: list of joint sponsors
- *generic/unspecified sponsor*: list of generic/unspecified sponsors
