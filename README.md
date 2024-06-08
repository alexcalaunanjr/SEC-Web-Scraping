# Sustainability Report Scraping
### SEC Sustainability Disclosure Search
This code scrapes data from various companies and analyzes the correlation of a company's use of various words in their report against how sustainable they really are.

## TOOLS USED / PREREQUISITES
- <a href="https://docs.anaconda.com/free/miniconda/miniconda-install/">Miniconda</a> (Conda) for python environments with the necessary libraries/packages
- <a href="https://code.visualstudio.com/download">Visual Studio Code</a> (IDE to write/run code)
- Selenium (Library for web automation; to be used for webscraping)
- Basic python libraries


## Get started 
### 1. Create your environment
With miniconda installed, in your cmd/terminal, cd to the path you want to create your environment in.

Once done, create python environment using the following command:\
`conda create --prefix=[NameOfEnvironemnt] python=3.11.9`

Replace `[NameOfEnvironemnt]` to the environment name you want, for example:\
`conda create --prefix=FYP python=3.11.9`

Once that's done, follow the instructions to activate the environment:\
`conda activate /path/to/your/env`

### 2. Install necessary libraries
While in the directory of this project (with requirements.txt), run the following command to install all the necessary libraries:\
`pip install -r requirements.txt`

### 3. Running the Selenium webscraping bot using Visual Studio Code (VSC)
Before running the code, make sure to have the necessary extensions needed for Visual Studio Code by doing the following:

#### 1. Install Jupyter extension on VSC:
From the left hand side tabs, click extension (icon with 4 boxes), search 'jupyter', and install. This will allow you to open/run jupyter notebook files (.ipynb) on VSC.

<p align='center'>
 <img class='Extension' src='./readme/image.png' width=300 style="display: block; margin: 0 auto;">
</p>
<br>

#### 2. Prepare the Environments needed for the scraping:
<p align='center'>
 <img src='./IMG_7527.gif'>
</p>

1) Open scraper.ipynb
2) On the top right, select the environemnt
3) In the pop up, click 'Python Environments...'
4) Select the environment you created earlier 


#### 3. Run
- Click on 'Run All' in the bar of buttons in the file scraper.ipynb

<br>
<br>

# <B>REPORT WORD COUNT PIPELINE<B>
### PREP:
1. Choose Filers
2. Set year to 2009 (default to 2018 at first load)
3. Get number of companies
### COLLECT DATA:
4. For each Issue, do the following:\
    5. For each Year, do the following:\
        6. Each page shows 100 companies, therefore get total number of pages from that\
        7. Get all company names per page, then access report\
            &nbsp;&nbsp;&nbsp;&nbsp;a. Get each row from page\
            &nbsp;&nbsp;&nbsp;&nbsp;b. Add to dataframe\
            &nbsp;&nbsp;&nbsp;&nbsp;c. Check if Report column is 'Non Disclosure' or 'View Report'\
            &nbsp;&nbsp;&nbsp;&nbsp;d. If 'View Report', do the following:\
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i. Click the link\
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ii. Click 'View Extended Disclosures' (if not clicked already)\
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;iii. Get all excerpts\
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;iv. Count the total words, and the keywords (Green, Climate, Sustainability)\
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;v. Add to dataframe\
            &nbsp;&nbsp;&nbsp;&nbsp;e. Else, put '-' at in the columns [Green, Climate, Sustainability], and put 'No Disclosure'\
        8. After getting, go to next page (loop starting from 1, and check against each iteration to click data=i+1)\
        9. Repeat 5-6 till done with last page\
10. End 