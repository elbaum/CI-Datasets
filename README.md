# CI-Datasets
Continuous integration testing dataset

"Summary Dataset" provides details on mtivation, context, and process to get the data. "Data Fields" provides details on the data fields. A list of efforts using the dataset can be found in "Papers and tools".

### Rails Dataset
This dataset is gathered from rails/rails of Travis CI (https://travis-ci.org/rails/rails/). Rails is an open source project writen in Ruby, and it has more than 50,000 builds on Travis CI. From that pool of builds, we collected 3000 consecutive builds from March 2016 to August 2016. After removing the 196 cancled builds, the dataset ended up with 2804 builds with more than 3.5 million test suite execution records.

If you use it please:

Cite it as: Jingjing Liang, Sebastian Elbaum, and Gregg Rothermel, "The Rails Dataset of Testing Results from Travis CI", https://github.com/elbaum/CI-Datasets, 2018.

### Google Dataset
This dataset is gathered from Google products with more than 3.3 Million test suite execution records. The dataset collected 15 consecutive days' data.

If you use it please:

Cite it as: Sebastian Elbaum, Andrew Mclaughlin, and John Penix, "The Google Dataset of Testing Results", https://github.com/elbaum/CI-Datasets, 2018.







# Summary Dataset

## Motivation and Goals

The dataset is meant to provide the software engineering research community, especially the software testing and analysis community, with a sample of test suite execution results from a fast, large scale, and continuous testing infrastructure. 


## Context

### Rails Dataset
Rails is an open source project with frequent builds on Travis CI. Rails project is writen in Ruby with more than 50,000 builds. This dataset collects 2804 consecutive builds in total with a sample of more than 3.5 million test sutie executions over five months ( March 2016 to August 2016). For each test suite, the dataset includes rich information such as test suite identifiers, test suite execution time, job, and build identifiers, start times, finish times and outcome status.

### Google Dataset
Google conducts many quality assurance activities at many levels. This dataset reflects one activity type, and a small sample on that type. Still, the dataset includes a sample of over 3.3 Million test suite (note that these are not test cases) executions, collected during a period of of 15 days over a sample of Google products. For each test suite execution, the dataset includes rich information such as the status outcome, execution time, rescaled change request number, and the language used.


## Potential Usages

We anticipate that this dataset could be used for: 
1. Analyze continuous, and large scale testing processes. 
2. Develop predictive models to increase test performance.
3. Assess and refine tests scheduling and selection techniques.


## Format

The Rails dataset file is compressed using zip. The fields in the file are colon-separated, and the fields' decription is in the DataFields.

The Google dataset file is compressed using tar.bz2. The fields in the file are comma-separated, and the fields' description is in the DataFields.


## Rights and licences

The dataset will be made freely available without restrictions.


## Questions

If you have questions, please direct them to: Jingjing Liang


## Authors

The Rails dataset was prepared through a collaborative effort involving Jingjing Liang, Sebastian Elbaum and Gregg Rothermel.

The Google dataset was prepared through a collaborative effort involving Sebastian Elbaum (Google Visiting Scientist from the University of Nebraska Lincoln), and Andrew Mclaughlin and John Penix (engineers at Google).


# Papers and tools

### Rails Dataset

ICSE 2018

The first paper using this dataset was "Redefining Prioritization: Continuous Prioritization for Continuous Integration", by Jingjing Liang, Sebastian Elbaum, and Gregg Rothermel, ICSE 2018.

### Google Dataset

FSE 2014

The first paper to use the dataset was "Techniques for Improving Regression Testing in Continuous Integration Development Environments", by Sebastian Elbaum, Gregg Rothermel, and John Penix, FSE 2014.

ICSE 2018

The second paper to use the dataset was "Redefining Prioritization: Continuous Prioritization for Continuous Integration", by Jingjing Liang, Sebastian Elbaum, and Gregg Rothermel, ICSE 2018.




# Data Fields


### Rails Dataset

 Field   | Description                                 

 Test Suite  | String representing the test sutie name including the test suite directory(names separated by "/").

 Test Suite Duration | Number representing the test suite execution time in second.
 
 Test Suite Runs     | Integer representing the number of test cases executions.
 
 Test Suite Assersions | Integer representing the number of assertions in the test suite.
 
 Test Suite Failures | Integer representing the number of failed test cases in the test suite.                           
 
 Test Suite Errors   | Integer representing the number of errored test cases in the test suite.
 
 Test Suite Skips    | Integer representing the number of skipped test cases in the test suite.
 
 Build Number        | Integer representing the number of build that the test suite belong to.
 
 Commit Sha          | String representing the unique object committed. Commit sha is a string with 40 characters.
 
 Job Id              | Integer representing the id of the job that the test suite belong to.
 
 Job Number          | Number representing the number of the job that the test suite belong to. 
 
 Commit Branch       | String representing the branch that the commit is commited to.
 
 Build State         | String representing build execution status including failed, and passed.
 
 Build Start Time    | String representing the time when the build started to execute.
 
 Build Finish Time   | String representing the time when the build finished executing.
 
 Build Duration      | Number representing the wall clock of the whole build time in second, including the building time, 
 and testing time.
 
 Job State           | String representing the job's execution status including passed, failed, errored.
 
 Job Start Time      | String representing the time when the job started to execute.
 
 Job Finish Time     | String representing the time when the job finished executing.
 
 Job Duration        | Number representing the wall clock of the whole job time in second.
 
 Job Allow Failure   | Boolean representing whether the job is set "allow failure".
 
 Build Pull Request  | Boolean representing whether the build is pull request or not.
 
 Test Suite Order in the Job     | Integer representing the order of test suite in the certain job.



Note:

1. Relationships between BUILD, JOB, TEST SUITE

   Each build contains multiple jobs, and each job will execute multiple test suites.

2. "Allow Failure" is a boolean variable for each job. If the job is set "Allow Failure = true", then even the job contains some failed test suite executions, the job is still passed.

3. Job Number: Number representing the number of the job that the test suite belong to. For example, 33391.1 is a job number. This number is consisted as below:
			33391 (build number) + "." + 1 (job number)



### Google Dataset 

Field   | Description 

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


