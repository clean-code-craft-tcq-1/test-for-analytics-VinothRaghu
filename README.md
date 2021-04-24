# Test for Analytics

Design tests for Analytics functionality on a Battery Monitoring System.



## Analysis-functionality to be tested

This section lists the Analysis for which _tests_ must be written.

Battery Telemetrics are collected and stored on a server.
Data for a month is stored in a [csv file](https://en.wikipedia.org/wiki/Comma-separated_values).

Analysis must be done on this csv file to find the following:
- minimum
- maximum
- count of breaches (how many times did it cross the threshold in a month?)
- record trends (date & time when the reading was continuously increasing for 30 minutes)

A PDF report of the analysis must be stored every week.
Notification must be sent when a new report is available.

## Tasks

### List Dependencies

List the dependencies of the Analysis-functionality.

1. Access to the Server containing the telemetrics in a csv file
2. Libraries to access the csv file data's like csv library
3. Libraries for writing report to pdf like pdffrw library
4. Libraries for sending notification when pdf new report avilable like universal-notifications
5. Genaral math and numpy Libraries for ease calclulation and trend
6. Libraries for translation like py-translate,goslate if we need to generate report in mulitiple language


### Mark the System Boundary

What is included in the software unit-test? What is not? Fill this table.

| Item                      | Included?     | Reasoning / Assumption
|---------------------------|---------------|---
Battery Data-accuracy       | No            | We do not test the accuracy of data
Computation of maximum      | Yes           | This is part of the software being developed
Off-the-shelf PDF converter | No            | We do not test the pdf converter
Counting the breaches       | Yes           | This is part of the software being developed and we do test for counting the breaches
Detecting trends            | Yes           | This is part of the software being developed and we do test for detecting trends
Notification utility        | Yes           | we do test for notification is sent or not by fake pdf availiblity but notification utility libraries we are not testing                        

### List the Test Cases

Write tests in the form of `<expected output or action>` from `<input>` / when `<event>`

Add to these tests:

1. Write minimum and maximum to the pdf from csv containing proper postive readings
2. Write trends to pdf from csv containing proper postive readings
3. Write count of breaches to pdf from csv containing proper postive readings
4. Write minimum and maximum to the PDF from a csv containing positive and negative readings
5. Write trends to pdf from csv containing positive and negative reading
6. Write count of breaches to pdf from csv containing positive and negative reading
7. Write "Invalid input" to the PDF when the csv doesn't contain expected data
8. Write "Data not avilable" to the PDF when the csv file not accesible
9. sent notification when pdf report file updated and accessible
10. Do not sent notification when pdf report file not updated updated 
11. Do not sent notification when pdf report file updated but not accessible due to server side issue's
12. Write trends "not able to found" to pdf from csv containing oscilating trends
13. write "no breaches" to pdf from csv containing valid readigs without breaches
14. write translation to pdf report once pdf report avilable


(add more)

### Recognize Fakes and Reality

Consider the tests for each functionality below.
In those tests, identify inputs and outputs.
Enter one part that's real and another part that's faked/mocked.

| Functionality            | Input        | Output                      | Faked/mocked part
|--------------------------|--------------|-----------------------------|---
Read input from server     | csv file     | internal data-structure     | Fake the server store
Validate input             | csv data     | valid / invalid             | None - it's a pure function
Notify report availability | pdf file     | available/notavilable       | Fake the pdf avilable
Report inaccessible server | pdf file     | accesible/notaccesible      | mock the accessiblity
Find minimum and maximum   | csv data     | maximum and minimum         | None - it's a pure function
Detect trend               | csv data     | trends detected/notdetected | None - it's a pure function
Write to PDF               | csv data     | pdf data                    | mock pdf data 
