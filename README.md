# CI-Datasets
Continuous integration testing dataset

## Rails Dataset
This dataset is gathered from rails/rails of Travis CI (https://travis-ci.org/rails/rails/). Rails is an open source project writen in Ruby, and it has more than 50,000 builds on Travis CI. From that pool of builds, we collected 3000 consecutive builds from March 2016 to August 2016. After removing the 196 cancled builds, the dataset ended up with 2804 builds with more than 3.5 million test suite execution records.

If you use it please:

Cite it as: Jingjing Liang, Sebastian Elbaum, and Gregg Rothermel, "The Rails Dataset of Testing Results from Travis CI", https://github.com/elbaum/CI-Datasets, 2018.

## Google Dataset
This dataset is gathered from Google products with more than 3.3 Million test suite execution records. The dataset collected 15 consecutive days' data.

If you use it please:

Cite it as: Sebastian Elbaum, Andrew Mclaughlin, and John Penix, "The Google Dataset of Testing Results", https://github.com/elbaum/CI-Datasets, 2018.


"Summary Dataset" provides details on mtivation, context, and process to get the data. "Data Fields" provides details on the data fields. A list of efforts using the dataset can be found in "Papers and tools".




# Summary Dataset

## Motivation and Goals

The dataset is meant to provide the software engineering research community, especially the software testing and analysis community, with a sample of test suite execution results from a fast, large scale, and continuous testing infrastructure. 


## Context

Rails is an open source project with frequent builds on Travis CI. This dataset contains 2804 consecutive builds in total with a sample of more than 3.5 million test sutie executions over five months ( March 2016 to August 2016). For each test suite, the dataset includes rich information such as test suite identifiers, test suite execution time, job, and build identifiers, start times, finish times and outcome status.


## Potential Usages

We anticipate that this dataset could be used for: 
1. Analyze continuous, and large scale testing processes. 
2. Develop predictive models to increase test performance.
3. Assess and refine tests scheduling and selection techniques.


## Format

The dataset file is compressed using zip. The fields in the file are colon-separated, and the fields' decription is in the DataFields.


## Rights and licences

The dataset will be made freely available without restrictions.


## Questions

If you have questions, please direct them to: Jingjing Liang


## Authors

The dataset was prepared through a collaborative effort involving Jingjing Liang, Sebastian Elbaum and Gregg Rothermel.




# Papers and tools

ICSE 2018

The first paper using this dataset was "Redefining Prioritization: Continuous Prioritization for Continuous Integration", by Jingjing Liang, Sebastian Elbaum, and Gregg Rothermel, ICSE 2018.




# Data Fields

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






