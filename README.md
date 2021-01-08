
        

# ASE Data: A reasonable financial data API

## Contents

* **Overview**
  - ASE Data provides financial data for American companies and financial news.
  - For the majority of developers, financial APIs are expensive, and in our expierience, even misleading.
  - ASE Data has been designed to be cheap and fast, perfect to the average developer not willing to spend hundreds or even thousands a month on public data.
       <br>       <br>



* **Documentation** 
  - All data is accessed through requests send to:      **http://www.ase-data.com**
    - This is the base url for all of the requests.  Any endpoint must be appended to this in requests
    - For the entirety of the documentation, the base URL will be omitted or refered to as http://www.ase-data.com
    
       <br>
       
  - The primary use case is to access financial reports, such as annual and quarterly reports:
    - These reports are accessed throught the endpoint **/api/stock?ticker={ticker}&docs={document type}**
    - This returns a JSON object, structured by year, that contains all financial information filed by the company.
    
    <br>
    
  - There are a number of endpoints that provide data released by the SEC.
    - The data and endpoints are as follows:
      - **Trading suspensions: /api/trading_suspensions**
        - Returns a JSON object enumerating suspended entities. This request takes no parameters.
      - **Press releases: /api/sec_releases**
        - Returns a JSON object with recent information relating to the SEC. This request takes no parameters.
      - **Litigation headlines: /api/litigation**
        - Returns a JSON object with recent litigation headlines. This request does not take any parameters.
      - **SEC investing news: /api/investing**
        - Returns a JSON object enumerating releases related to investing. This request takes no parameters

* **Examples**:
  - Some example endpoints once you have an api key:
    - http://www.ase-data.com/api/stock?ticker=tsla&docs=10-k&key={api-token} 
    - http://www.ase-data.com/api/fraud?key={api-token} 
    - http://www.ase-data.com/litigation?key={api-token} 
    - http://www.ase-data.com/trading_suspensions?key={api-token} 
    - http://www.ase-data.com/sec_releases?key={api-token} 
    - http://www.ase-data.com/investing?key={api-token} 
    - http://www.ase-data.com/news?key={api-token} 


  - Requirements: 
    - A standard medium is needed to send requests and retreive responses from the server.
    - An example of this is the "requests" library in python, but can be any library in any language that has similar functionality
  
  - Example 1: enumerate the financial information in Tesla's annual reports:
    ```
    URL: http://www.ase-data.com/api/stock?ticker=tsla&docs=10-k
    
    Sample Output (Most of the output is omitted):
       {
        "12-137560": {
          "Accounts Payable Current": {
           "2011": [
            "56141000"
           ]
          },
          "Accounts Receivable Net Current": {
           "2011": [
            "9539000"
           ]
          }
        }
       }       
    ```
  - Example 2: enumerate the names of entities known to the SEC that are fradulent:
    ```
    URL: http://www.ase-data.com/api/fraud
    
    Sample Output (Most of the output is omitted):
       {
        "12 West Capital Management": "Impersonators of Genuine Firms",
        "1st American Securities": "Unregistered Soliciting Entities",
        "1st New York Financial Corporation": "Unregistered Soliciting Entities",
        "247 Options Trade": "Unregistered Soliciting Entities",
        "365Tradeposition": "Unregistered Soliciting Entities",
        "426 Investments Incorporated": "Unregistered Soliciting Entities",
        "ACT Transfer Services": "Unregistered Soliciting Entities",
        "ADG Capital LLC": "Impersonators of Genuine Firms"
       }
    
    ```
  - Example 3: enumerate the headlines of all lidigation proceedings recently filed by the SEC, listings by defendant:
    ```
    URL: http://www.ase-data.com/api/litigation
    
    Sample Output (Most of the output is omitted):
      {
        "Alex Forester, Michael Hicks, Yarden Krampf, Christopher Lee, Sean O'Neal, Michael Raynor, and Lee Sobel":
          {"description":"SEC Charges Seven Individuals with Unregistered Brokerage Activity Related to the Sale of Numerous Microcap Securities",
          "link":"https://www.sec.gov/litigation/litreleases/2020/lr24952.htm",
          "published":"Tue, 27 Oct 2020 13:53:00 EDT"},
        "Amir Bruno Elmaani":
          {"description":"SEC Charges Individual for Self-Minting Scam and Unregistered ICO",
          "link":"https://www.sec.gov/litigation/litreleases/2020/lr24980.htm",
          "published":"Wed, 09 Dec 2020 17:37:28 EST"},
        "Anthony Thompson, Jr., et al.":
          {"description":"SEC Obtains Final Judgments Against Stock Promoters",
          "link":"https://www.sec.gov/litigation/litreleases/2020/lr25001.htm",
          "published":"Wed, 30 Dec 2020 16:48:50 EST"},
        "Applied BioSciences Corp.":
          {"description":"SEC Obtains Final Judgment Against Company for Misleading Covid-19-Related Claims",
          "link":"https://www.sec.gov/litigation/litreleases/2020/lr24977.htm",
          "published":"Mon, 07 Dec 2020 17:22:13 EST"}
      }
    ```

* **For any further infomration, feel free to contact us at ase-data@protonmail.com**:
