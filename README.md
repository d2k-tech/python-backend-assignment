# Python Backend Assignment

Hi there! We are happy you are interested in joining the backend engineering team as python developer here at D2K Technonologies.

We believe it is important that our assessment of your skills matches the technical challenges you will face as an developer at the company. Please carve out approximately 3-4 hours for this assignment. For that, we want you to build a REST APIs application using [Python][5](>3.10) ([Django Rest Framework][1] or [fastapi][2]) for managing the user’s data.You should use SQL database(i.e [postgres][3]) to store the application data.  

> NOTE: _Attention to detail and meeting all requirements is important in the project. Completing it in less time will not give you any preference._

## Your mission
Develop an API oriented backend application which provides API endpoints to manage users and their details.

User should have the following attributes:-

```
ID
First Name
Last Name
Company Name
Age
City
State
Zip
Email
Web
```

Application should have the following endpoints:

1. `GET /api/users` - To list the users

    - Response with HTTP status code 200 on success

    ```json
    [
      {
        "id": 1,
        "first_name": "James",
        "last_name": "Butt",
        "company_name": "Benton, John B Jr",
        "city": "New Orleans",
        "state": "LA",
        "zip": 70116,
        "email": "jbutt@gmail.com",
        "web": "http://www.bentonjohnbjr.com",
        "age": 70
      },
      {
        "id": 2,
        "first_name": "Josephine",
        "last_name": "Darakjy",
        "company_name": "Chanay, Jeffrey A Esq",
        "city": "Brighton",
        "state": "MI",
        "zip": 48116,
        "email": "josephine_darakjy@darakjy.org",
        "web": "http://www.chanayjeffreyaesq.com",
        "age": 48
      }
    ]
    ```

     - Add support of follwing query parameters:
       - `page` - a number for page, to support pagination.
       - `limit` - Limit number of items to be returned, default limit is **5**
       - `search` - search user by name as a substring in `First Name` or `Last Name`. It should be case-insensitive search.
       - `sort` - name of field to sort results. By default it returns items in ascending order if this parameter exists, and if the value of parameter is prefixed with `-` character (i.e `-age`), then it should return items in descending order

     Sample query endpoint:- `/api/users?page=1&limit=10&search=James&sort=-age` This endpoint should return list of 10 users whose first name or last name contains substring given name and sort the users by age in descending order of page 1.

2. `POST /api/users` - To create a new user

    - Request payload should be like this in json format :-

    ```json
    {
      "id": 2,
      "first_name": "Josephine",
      "last_name": "Darakjy",
      "company_name": "Chanay, Jeffrey A Esq",
      "city": "Brighton",
      "state": "MI",
      "zip": 48116,
      "email": "josephine_darakjy@darakjy.org",
      "web": "http://www.chanayjeffreyaesq.com",
      "age": 48
    }
    ```

     - Response with HTTP status code 201 on success
       ```json
       {}
       ```
     - This endpoint will create a new user in the database

3. `GET /api/users/{id}` - To get the details of a user

    - Here `{id}` would be the user ID in path parameter
    - Response with HTTP status code 200 on success

    ```json
    {
      "id": 1,
      "first_name": "James",
      "last_name": "Butt",
      "company_name": "Benton, John B Jr",
      "city": "New Orleans",
      "state": "LA",
      "zip": 70116,
      "email": "jbutt@gmail.com",
      "web": "http://www.bentonjohnbjr.com",
      "age": 70
    }
    ```

    Sample query looks like:- `GET /api/users/1`

4. `PUT /api/users/{id}` - To update the details of a user

     - Here `{id}` would be the user ID in path parameter
     - Request Payload should be like in json format for updating first name, last name and age:-
       ```json
       {
         "first_name": "Josephine",
         "last_name": "Darakjy",
         "age": 48
       }
       ```
     - Response with HTTP status code 200 on success
       {}

5. `DELETE /api/users/{id}` - To delete the user

    - Here {id} will be the id of the user in path parameter
    - Response with HTTP status code 204 on success

## Resources:

- To download sample data of users, [click here][4]
  
## **Instructions**

- Please include `README.md` that includes all the details and instructions on how to setup and run the project
- Please note, your repository should not contain irrelevant folders/files like cache files, build/dist directories etc.
- Please try to comment/commit your code as much as you think is needed.
- Please take some time to briefly answer the following questions at the end of your submission.
  ```
  - How long did it take you to complete this assignment?
  
  - What about this assignment did you find most challenging?
  
  - What about this assignment did you find unclear?
  
  - What challenges did you face that you did not expect?
  
  - Do you feel like this assignment has an appropriate level of difficulty?
  
  - Briefly explain your decisions to use tools, frameworks and libraries like fastapi, DRF etc.
  
  - Did you make certain assumptions and decisions around the application? Please elaborate on your reasonings.
  ```

## Bonus Points
- Usage of python tooling like `poetry`, `pre-commit`, `ruff`, `black`
- Build API documentation using [OpenAPI][6] spec
- Write unit tests and functional tests
- Proper logging by emitting logs 


[1]: https://www.django-rest-framework.org/
[2]: https://fastapi.tiangolo.com/
[3]: https://www.postgresql.org/
[4]: https://d2k-static-assets.s3.ap-south-1.amazonaws.com/assignment-files/python-backend-assignment/users.json
[5]: https://www.python.org/
[6]: https://spec.openapis.org/oas/latest.html#
