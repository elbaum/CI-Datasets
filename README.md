# Continuous Integration Testing Datasets
 
This repository contains continue integration testing datasets to support the software testing and analysis community in the design and implementation of more effective and efficient testing and analysis techniques that can operate at large scale and speed. 

We anticipate that this dataset could be used for: 
1. Analyze continuous, and large scale testing processes. 
2. Develop predictive models to increase test performance.
3. Assess and refine tests scheduling and selection techniques.

 
### Rails Dataset
This dataset is gathered from the system rails/rails hosted on Travis CI (https://travis-ci.org/rails/rails/). Rails is an open source project writen in Ruby, with more than 50,000 builds on Travis CI. From that pool of builds, we collected 3000 consecutive builds from March 2016 to August 2016. We removed 196 canceled builds, ending with 2804 builds that include more than 3.5 million test suite execution records. For each test suite, the dataset includes rich information such as test suite identifiers, test suite execution time, job, and build identifiers, start times, finish times and outcome status.

The Rails dataset file is compressed using zip. The fields in the file are semicolon-separated, and the fields' decription is in the DataFields.

If you use this dataset please cite:
Jingjing Liang, Sebastian Elbaum, and Gregg Rothermel, "The Rails Dataset of Testing Results from Travis CI", https://github.com/elbaum/CI-Datasets, 2018.

The Rails dataset was prepared through a collaborative effort involving Jingjing Liang, Sebastian Elbaum and Gregg Rothermel.

### Google Dataset
Google conducts many quality assurance activities at many levels. This dataset reflects one activity type, and a small sample on that type. Still, the clean dataset includes a sample of over 2.5 Million test suite (note that these are not test cases) executions, collected during a period of of 15 days over a sample of Google products. For each test suite execution, the dataset includes rich information such as the status outcome, execution time, rescaled change request number, and the language used. For continuous integration usage, we separate this dataset into two subdatasets, Google Pre and Google Post, according to test suites' execution "stage" ("pre" and "post").

These Google datasets files are compressed using zip. The fields in the file are comma-separated, and the fields' description is in the DataFields.

If you use this dataset please cite:
Cite it as: Sebastian Elbaum, Andrew Mclaughlin, and John Penix, "The Google Dataset of Testing Results", https://github.com/elbaum/CI-Datasets, 2018.

The Google dataset was prepared through a collaborative effort involving Sebastian Elbaum (Google Visiting Scientist from the University of Nebraska Lincoln), and Andrew Mclaughlin and John Penix (engineers at Google).

 
## Rights and licences

The dataset will be made freely available without restrictions.
 

# Papers and tools

### Rails Dataset

ICSE 2018

The first paper using this dataset was "Redefining Prioritization: Continuous Prioritization for Continuous Integration", by Jingjing Liang, Sebastian Elbaum, and Gregg Rothermel, ICSE 2018.

Link: https://www.icse2018.org/event/icse-2018-technical-papers-redefining-prioritization-continuous-prioritization-for-continuous-integration

### Google Dataset

FSE 2014

The first paper to use the dataset was "Techniques for Improving Regression Testing in Continuous Integration Development Environments", by Sebastian Elbaum, Gregg Rothermel, and John Penix, FSE 2014.

Link: https://dl.acm.org/citation.cfm?id=2635910

ICSE 2018

The second paper to use the dataset was "Redefining Prioritization: Continuous Prioritization for Continuous Integration", by Jingjing Liang, Sebastian Elbaum, and Gregg Rothermel, ICSE 2018.

Link: https://www.icse2018.org/event/icse-2018-technical-papers-redefining-prioritization-continuous-prioritization-for-continuous-integration




# Data Fields


### Rails Dataset

 Field   | Description                                 

 Test Suite  | String representing the test sutie name including the test suite directory(names separated by "/").

 Test Suite Start Time | String representing the time when the test suite started to execute.

 Test Suite Duration | Number representing the test suite execution time in seconds.
 
 Test Suite Runs     | Integer representing the number of test suites executions.
 
 Test Suite Assertions | Integer representing the number of assertions in the test suite.
 
 Test Suite Failures | Integer representing the number of failed test cases in the test suite.                           
 
 Test Suite Errors   | Integer representing the number of errored test cases in the test suite.
 
 Test Suite Skips    | Integer representing the number of skipped test cases in the test suite.
 
 Build Number        | Integer representing the number of build that a test suite belongs to.

 Build Pull Request | Boolean representing whether the build is a pull request or not.
 
 Commit Sha          | String representing the unique object committed. Commit sha is a string with 40 characters.

 Build State         | String representing build execution status including failed, and passed.
 
 Build Start Time    | String representing the time when the build started to execute.
 
 Build Finish Time   | String representing the time when the build finished executing.
 
 Build Duration      | Number representing the wall clock of the whole build time in seconds, including the building time, 
 and testing time.
 
 Job Id              | Integer representing the id of the job that the test suite belong to.
 
 Job Start Time      | String representing the time when the job started to execute.

 Job Allow Failure   | Boolean representing whether the job is set "allow failure".


 



Notes:

1. Relationship between BUILD, JOB, TEST SUITE: each build contains multiple jobs, and each job will execute multiple test suites.

2. "Allow Failure" is a boolean variable for each job. If the job is set "Allow Failure = true", then even if the job contains some failed test suite executions, the job is still assumed as Passed by Travis.



### Google Dataset


Test Suite | String representing the test suite name. The names have been obfuscated but most of the directory structure (names separated by “/”) has been retained. 

Change Request | String representing the rescaled change request number that lead to the execution of the test suite. 

Stage | String representing the testing stage. Only two stages are considered, “Pre” and “Post” stages. Each change is likely to go into these testing stages in sequence, with the “Post” stage being more extensive than the “Pre” stage. 

Status | String representing the test suite execution status. It can take two values: “Passed” or “Failed” (this last case means that at least one test case in the test suite failed). 

Launch Time | String representing the “date of the month:hours:minutes:seconds” when the test suite was executed. 

Execution Time | Integer representing the test suite execution time in milliseconds.

Size | String representing the size of the tests in the test suite. The classification used includes three types of test annotations “Small”, ”Medium”, or ”Large”, where bigger tests are meant to take more time or require more resources to execute. 

Shard_number | Integer representing the number of shards used to execute the suite. Shards are used to parallelize the test suite execution over multiple processors.

Run_number | Integer representing the number of runs performed on each test suite on a single change list. Multiple runs may be required, for example, to confirm test results or validate non-functional behavior.

Language | String representing the programming language used by the suite. 


