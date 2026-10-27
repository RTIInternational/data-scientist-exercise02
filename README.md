## RTI Data Science Analytics Exercise 02

Welcome to Exercise 02. This exercise provides data from the [National Transportation Safety Board](http://www.ntsb.gov/Pages/default.aspx)'s database of aviation accidents. We'll ask you to perform some routine high-level analytic tasks with the data.

### Some guidance

1. Use open source tools and ecosystems - Python or R. Do not use proprietary tools, such as SAS, SPSS, JMP, Tableau, or Stata. 
2. Use AI, but document your usage. We routinely use both Copilot and Claude Code at RTI. How you use and validate what AI provides is an important discussion topic that we'll cover in the technical interview.
3. Comment your code such that a fellow data scientist who isn't familiar with this data or analysis could understand the steps you take.
4. There are many ways to approach and solve the problems presented in this exercise. We view them as discussion topics, not pass/fail checkboxes.

### Using the Code

OPTION 1
If you wish to submit via an emailed zip file:
1. Clone this repository or [download the code as a zip file](ZIP_ASSET_DOWNLOAD_LINK)
2. Extract this repo and work locally with the code.
3. When finished, zip your project folder (code and writeup) and submit to the email you received the exercise from. Do not encrypt or add a password to the zip.

OPTION 2
If you wish to submit via GitHub:
1. Fork this repository to your personal GitHub account and clone the fork to your computer.
    - **Note**: This does mean you will have a visible public fork of this repo on your github account. If this may cause a privacy issue with your current employer, we suggest using a new/temporary github account to complete the work, or Option 1 above to email a zip file.
2. Save and commit your answers to your fork of the repository, and push them back to your forked repository. Include code and writeup.
3. Provide a link to that fork of the repository in your submission.

### The Task

You will be exploring the data to develop a classification of narratives and writing up a summary of the data and your results. **The whole exercise should take no longer than 4 hours (self-timed)**.

Your **code** needs to perform the following tasks:
1. Read and standardize the json files in a way that facilitates further analysis (i.e. "flatten" them and link with `AviationData`)
2. Prepare ~3 descriptive statistics that convey an overview of the structured data.
3. Perform exploratory analysis of the narrative text, analyzing common words, their use over time, and generate 2-3 plots.
4. Use topic modeling or any other text clustering methodology to cluster/group the incidents based on the narrative text and/or probable cause descriptions. Come up with a short name for each topic or cluster you identify to make it easy to report on.
5. Use an AI-assisted method to examine a small sample of incidents from at least 2 clusters. Assess whether the cluster assignment and cluster name appear reasonable. Briefly describe what you learned and, if applicable, one change you would make with additional time.
* Use any tool you like, but we don't expect you to pay for pro access. For example, Gemini AI Studio or Huggingchat are useful free AI tools. If the free tier limited your work, we can discuss how it limited you and what you would need to solve that limitation (token limitations, security approvals etc are a common issue for today's data scientists)!

Your **writeup** should do the following:
1. Describe your methodology and results in 500 words or less.
  - Include the chart generated as of your write-up. Explain how the chart informs your analysis. 
  - You'll not be punished for going over 500 words, but it is a rough guideline of the length we expect.
2. Include a chart that you feel conveys one important relationship in the data.
* Assume the audience for your write-up is a non-technical stakeholder.
* Assume the audience for your code is a colleague who may need to review or modify it in the future.


### The Data

There are 100+ files in this repository (`data/`):

- `AviationData.xml`: This is a straight export of the database provided by the NTSB. The data has not been altered.
- `AviationData.csv`: This is a CSV version of the XML above, pre-converted to a tabular format so that it's easier to work with for this analysis. The script used for conversion is `parse_xml.py`
- `NarrativeData_xxx.json`: These files were created by taking the `EventId`s from `AviationData.xml` and collecting two additional pieces of data for each event: 
  - `narrative`: This is the written narrative of an incident.
  - `probable_cause`: If the full narrative includes a "probable cause" statement, it is in this field. 
