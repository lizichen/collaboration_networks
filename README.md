# Key Research Questions:

### 1 .How do NSF programs vary in the extent to which they
1. foster new collaborations
2. strengthen existing collaborations
3. foster/strengthen different kinds of collaborations:
     i.e. cross-disciplinary collaborations; this may not be an appropriate question for all programs, but will be for many sustainability science programs, and other programs that specifically seek to encourage collaboration across traditional disciplinary boundaries as a way of tackling “wicked”

### 2. Which programs foster successful collaborations as measured by
1. more publications,
2. more joint authorship,
3. higher-ranked publications, **[? how to measure ?]**
4. more highly cited publications.

### 3. Which programs foster the production of manuscripts that have broad implications within/beyond their field (as analyzed through network analysis and number and origin of citations)?  
1. *which papers connect to other clusters of authors/papers more effectively?*

### 4. Across programs, how do factors such as *the followings* affect the success and network impacts of collaborations?  
1. award size/amount,
2. geographic distribution(affiliation/universities) of co-awardees,
3. number of awardees, etc.,

    **Cross-Disciplinarity might also be thought of as a factor that potentially influences success*

## Object Relation Diagram:
![relationship](https://github.com/lizichen/collaboration_networks/blob/master/ObjectsRelationDiagram.jpg "Relationship Diagram")

## Development Log:
- **[Oct 2016]** Design the research direction and articulate steps of development.
    + Proposed using Scopus open API for data retrieval.
    + Obtained 2015 NSF Award data and stored in MySQL.
- **[Nov 2016]** Implement a PHP website that can find the exact awardee with correct Scopus ID.
- **[Dec 2016]** Add function to the website that can download top 20 publications of an awardee where the awardee is the first author of the publications.
- **[Jan 2017]** Due to Scopus API limit calls and slowness of data retrieval, abandon the previous implementation design. Propose to bring Scopus Data to the local for speed-up and data pre-processing. 
- **[Feb 2017]** Hack through the Scopus web request to find a non-API calling approach that can download detailed structured data to the local computer.
- **[March 2017]** Obtain a list of all the potential awardee Scopus IDs for each awardee. Obtain lists of co-authors for each found Scopus ID. Find the exact awardee Scopus ID. (Detailed description, steps, scriptings, and diagram, please see [Data_Scrapping_And_PreProcess/README.md][datapreprocee])
    + **[March 15, 2017]** Some authors do not exist in Scopus Website, the list of not-found awardee names are collected in file: **HTML_NOT_FOUND_LIST.txt** and **AWARDEES_NOT_FOUND_IN_SCOPUS.txt**
    + **[March 16, 2017]** Due to the bash script, some requests to the Scopus Server returns zero byte html files. For all these awardee names, we have to send requests to the server again for getting the data. A list of such awardee names/id are stored in **ZERO_BYTE_HTML_LIST.txt** and **ZERO_BYTE_ID.txt** where the ID refers to the $ID used in author_$ID.html
    + **[March 16, 2017]** Some awardees name are missing from the investigator.csv. **Verify_All_Awardees_By_Name.ipynb** is used to verify any missing awardee names. all the missing awardee names are stored in **MISSING_AWARDEES.txt**. All these awardee names have to be re-run with the script **get_authors_html_page.sh**. 

[datapreprocee]:https://github.com/lizichen/collaboration_networks/blob/master/Data_Scrapping_And_PreProcess/README.md
