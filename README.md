Project Overview:

This project automates REST API testing using Java, Rest Assured, and TestNG.
It targets public APIs from https://reqres.in/  — a commonly used dummy API for learning and practicing API automation.

The test class validates CRUD operations: GET, POST, PUT, and DELETE, demonstrating end-to-end API automation.

Functionalities Automated:
GET Request

Method: GetRequestAPI()
URL: https://reqres.in/api/users/2

Fetches user details via GET request

Validates status code 200

Logs full response (headers, cookies, body)

Testing Types: Functional, Status Code Validation, Response Verification

POST Request

Method: PostRequestAPI()
URL: https://reqres.in/api/users
Request Body:

{
  "name": "diptiranjandash",
  "job": "softwareengineer"
}

Creates a new user

Validates status code 201 and response body fields

Logs complete response

Testing Types: Create Operation, Response Assertions, Data Validation

POST Request with ID Capture

Method: PostRequestAPI_IDcapture()

Captures the dynamically generated user ID for chained testing (PUT & DELETE)

Uses JSONPath for parsing and storing IDs

Testing Types: Dynamic Data Handling, Chained API Testing

PUT Request

Method: PutRequestAPI()
Depends on: PostRequestAPI_IDcapture()
URL: https://reqres.in/api/users/{id}
Request Body:

{
  "name": "dipti ranjan",
  "job": "test engineer"
}


Updates user details for the captured ID

Validates status code 200 and updated fields

Logs response

Testing Types: Update Operation, Data Integrity Check, Chained Testing

DELETE Request

Method: DeleteRequestAPI()
Depends on: PutRequestAPI()
URL: https://reqres.in/api/users/{id}

Deletes the previously created user

Validates status code 204 indicating successful deletion

Testing Types: Delete Operation, End-to-End API Chaining, Status Code Verification

Technical Concepts Used:

Rest Assured: API automation (GET, POST, PUT, DELETE)

TestNG: Structured test execution with priorities & dependencies

JSONPath: Extracting dynamic data from responses

HashMap: Constructing dynamic request bodies

Logging: .log().all() for debugging and traceability

Chained Dependency Testing: dependsOnMethods to maintain workflow from Create → Update → Delete
