## Instructions to run the tests
I have upload the json files to git-hub repository: 
https://github.com/dave-dalcin/osrm-tests

OSRM_Testing.postman_collection.json -> Postman collection
QA-Driving.postman_environment.json  -> QA environment variables
newman                               -> Folder with Test Report in html format 
readme.txt                           -> This file 
envVariablesReadme.txt 				 -> Read me with enviroment variables and functions description

URL: http://192.168.99.100:5000/
Demo Server: https://router.project-osrm.org/


## Test Cases
I have created 19 Tests placed in Positive Tests folder (8) and Negative Tests folder (11)

Summary: 
Positive Tests: All tests are passing 
Negative Tests: Tests 5 and 8 are expecting to fail due to existing bug 


## Bugs 
ID: 1
Description: Route Service is retrieving route between two near addresses when API calls overseas route
Steps to reproduce: 
	1 - Prepare Route Serivce ENDPOINT with Base URL + Route Service URI . e.g http://192.168.99.100:5000/route/v1/driving
	2 - Add coordinate 0 to the ENDPOINT. e.g Route 0 = 13.388798,52.517033 (Friedrichstraße - Berlin - Deustchland) 
	3 - Add an overseas coordinate to the ENDPOINT. e.g overseas coordinate  = -45.88694,-23.17944 (Jardin Bela Vista - Sao Paulo - Brasil) 
	4 - Run the request
Expected behavior: API should return the message "no route found"
Actual: API is replacing the overseas coordinate with another existing coordinate. e.g 13.113544,52.386378 (Paul-Neumann-Straße - Postdam - Deustchland
Test Data: ENDPOINT = http://192.168.99.100:5000/route/v1/driving/13.388798,52.517033;-45.88694,-23.17944 
Remarks: Error is happening on latest OSRM version. ERror is not happening on OSRM DEMO server. 
Please try: https://router.project-osrm.org/route/v1/driving/13.388798,52.517033;-45.88694,-23.17944

# BUG 
ID: 2 
Description: Trip Service is retrieving route between two near addresses when API calls overseas route 
Steps to reproduce:  
	1 - Prepare Route Serivce ENDPOINT with Base URL + Trip Service URI . e.g http://192.168.99.100:5000/trip/v1/driving 
	2 - Add coordinate 0 to the ENDPOINT. e.g Route 0 = 13.388798,52.517033 (Friedrichstraße - Berlin - Deustchland)  
	3 - Add an overseas coordinate to the ENDPOINT. e.g overseas coordinate  = -45.88694,-23.17944 (Jardin Bela Vista - Sao Paulo - Brasil) 
	4 - Run the request 
Expected behavior: API should return the message "no route found" 
Actual: API is replacing the overseas coordinate with another existing coordinate. e.g 13.113544,52.386378 (Paul-Neumann-Straße - Postdam - Deustchland 
Test Data: ENDPOINT = http://192.168.99.100:5000/trip/v1/driving/13.388798,52.517033;-45.88694,-23.17944  
Remarks: Error is happening on latest OSRM version. ERror is not happening on OSRM DEMO server. 
Please try: https://router.project-osrm.org/trip/v1/driving/13.388798,52.517033;-45.88694,-23.17944


# Answer for Question 2
Question: Describe how the tests you have written could be integrated in a fully automated CI/CD pipeline

Suggested enviornment: git, postman,  newman, Jenkins and Virtual Machines
The Collections and Environment were uploaded to Github: https://github.com/dave-dalcin/osrm-tests
The Jenkins host should have access to any AWS or Docker machine with Chama Application compiled from Master Branch;
Make sure that QA-Driving.postman_environment.json is pointing to Chama Application ENDPOINT running on virtual machine ;
Create a job on Jenkins or any other Job orchestration server to download json files from gitand run the following newman command line:

newman run OSRM_Testing.postman_collection.json -e QA-Driving.postman_environment.json

Newman will perform the tests and output the results



