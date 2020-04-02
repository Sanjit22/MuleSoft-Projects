# Fetch the Data from Database and perform some orchestration :

1. Create two different Databases and within that there has a table on each of them. One table called ***Student Details*** consists of three columns – “***StudentID***”, “***Name***”, “***Stream***” and another table called ***Stream Details*** consists two columns – “***Stream***” and “***Subject***”.

2. Design a ***RAML*** for two different ***System-APIs***, one ***Process-API*** and one ***Experience-API***.

3. Create two different ***System-APIs*** – <br/>
		***StudentDeails-Sys-API*** and ***StreamDetails-Sys-API*** <br/>
    to fetch the data from the respective databases. 

4. Create one ***Process-API*** that will broadcast to Student Details by calling the ***StudentDeails-Sys-API*** and ***StreamDetails-Sys-API***. In ***Process-Layer*** do some orchestration and the output of the ***Process-layer*** is in the json format and the data looks like –
```
    [
        {
            ‘Name’ : ‘Ranjit Sen’,
            ‘Subjects’ : [
                ‘Physics’,
                ‘Chemistry’,
                ‘Mathematics’
            ]
        }
    ] 
```
5. Create an ***Experience-Layer*** which is defined to expose the end user to the API. So, we should define and implement the high-level logic in the API. The purpose of this API is to interact with the Process API and process the output to the end user with the process status.

