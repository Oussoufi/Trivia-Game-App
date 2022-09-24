# Quizz Game API - Trivia

This project is consisting of creating a game quizz  API named Trivia quizz.
It serve as a final project for lessons from course 2 : API Development and Documentation of full stack Nanodegree program.
This project consiste of macking the differents Endpoints and documentation of api and successfully runing and testing it.

All backend code follow [PEP8 style guidelines](https://www.python.org/dev/peps/pep-0008/).

## Getting Started

### Pre-requisites and Local Development 
Developers using this project should already have Python3, pip and node installed on their local machines.

### Backend

From the backend folder run `pip install requirements.txt`. All required packages are included in the requirements file. 

To run the application run the following commands: 
```
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```
The application is run on `http://127.0.0.1:5000/` by default and is a proxy in the frontend configuration. 

### Tests

In order to run tests navigate to the backend folder and run the following commands: 

```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```
All tests are kept in that file and should be maintained as updates are made to app functionality.

## API Reference

### Getting Started
- Base URL: At present this app can only be run locally and is not hosted as a base URL. The backend app is hosted at the default, `http://127.0.0.1:5000/`, which is set as a proxy in the frontend configuration. 
- Authentication: This version of the application does not require authentication or API keys.

### Error Handling
Errors are returned as JSON objects in the following format:
```
{
    "success": False, 
    "error": 400,
    "message": "bad request"
}
```
The API will return three error types when requests fail:
- 400: Bad Request
- 404: Resource Not Found
- 422: Not Processable 
- 500: Internal Server Error


### Endpoints 
#### GET '/questions'
- General:
    - Returns a list of questions objects, success value, and total number of questions
    - Results are paginated in groups of 10. Include a request argument to choose page number, starting from
    - Resuls the current_category and the list of categories
    - Use curl `https://curl.se/` in the Terminal in Linux or MacOs or Install in windows [curl](`https://curl.se/`) 
    - BaseUrl `http://127.0.0.1:5000/`

- Sample: `curl http://127.0.0.1:5000/questions` 
```

{
    "catgories": {
        "1": "Science",
        "2": "Art",
        "3": "Geography",
        "4": "History",
        "5": "Entertainment",
        "6": "Sports"
    },
    "currentCategory": "History",
    "questions": [
        {
            "answer": "Apollo 13",
            "category": 5,
            "difficulty": 4,
            "id": 2,
            "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
        },
        {
            "answer": "Tom Cruise",
            "category": 5,
            "difficulty": 4,
            "id": 4,
            "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
        },
        {
            "answer": "Maya Angelou",
            "category": 4,
            "difficulty": 2,
            "id": 5,
            "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
        },
        {
            "answer": "Edward Scissorhands",
            "category": 5,
            "difficulty": 3,
            "id": 6,
            "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
        },
        {
            "answer": "Muhammad Ali",
            "category": 4,
            "difficulty": 1,
            "id": 9,
            "question": "What boxer's original name is Cassius Clay?"
        },
        {
            "answer": "Brazil",
            "category": 6,
            "difficulty": 3,
            "id": 10,
            "question": "Which is the only team to play in every soccer World Cup tournament?"
        },
        {
            "answer": "Uruguay",
            "category": 6,
            "difficulty": 4,
            "id": 11,
            "question": "Which country won the first ever soccer World Cup in 1930?"
        },
        {
            "answer": "George Washington Carver",
            "category": 4,
            "difficulty": 2,
            "id": 12,
            "question": "Who invented Peanut Butter?"
        },
        {
            "answer": "Lake Victoria",
            "category": 3,
            "difficulty": 2,
            "id": 13,
            "question": "What is the largest lake in Africa?"
        },
        {
            "answer": "The Palace of Versailles",
            "category": 3,
            "difficulty": 3,
            "id": 14,
            "question": "In which royal palace would you find the Hall of Mirrors?"
        }
    ],
    "success": true,
    "totalQuestions": 21
}
``` 



#### POST '/questions'
- General:
    - Creates a new question using the submitted question, answer, category and difficulty. Returns the id of the created question, success value, total questions, and question list based on last page number to update the frontend.
    
- Sample: `curl http://127.0.0.1:5000/questions -X POST -H "Content-Type: application/json" -d { "answer": "Camara Seydi Boubou ","category": 4,"difficulty": 2, "question": "Who is the first civil service director in mauritania ?"}'`

```
{
    "categories": [
        {
            "id": 1,
            "type": "Science"
        },
        {
            "id": 2,
            "type": "Art"
        },
        {
            "id": 3,
            "type": "Geography"
        },
        {
            "id": 4,
            "type": "History"
        },
        {
            "id": 5,
            "type": "Entertainment"
        },
        {
            "id": 6,
            "type": "Sports"
        }
    ],
    "created": 29,
    "currentCategory": "History",
    "questions": [
        {
            "answer": "Camara Seydi Boubou ",
            "category": 4,
            "difficulty": 2,
            "id": 29,
            "question": "Who is the first civil service director in mauritania ?"
        },
        {
            "answer": "Oussoufi Camara",
            "category": 4,
            "difficulty": 2,
            "id": 27,
            "question": "Who invented Peanut Butter?"
        },
        {
            "answer": "George Washington Carver",
            "category": 4,
            "difficulty": 2,
            "id": 26,
            "question": "Who invented Peanut Butter?"
        },
        {
            "answer": "Scarab",
            "category": 4,
            "difficulty": 4,
            "id": 23,
            "question": "Which dung beetle was worshipped by the ancient Egyptians?"
        },
        {
            "answer": "Blood",
            "category": 1,
            "difficulty": 4,
            "id": 22,
            "question": "Hematology is a branch of medicine involving the study of what?"
        },
        {
            "answer": "Alexander Fleming",
            "category": 1,
            "difficulty": 3,
            "id": 21,
            "question": "Who discovered penicillin?"
        },
        {
            "answer": "The Liver",
            "category": 1,
            "difficulty": 4,
            "id": 20,
            "question": "What is the heaviest organ in the human body?"
        },
        {
            "answer": "Jackson Pollock",
            "category": 2,
            "difficulty": 2,
            "id": 19,
            "question": "Which American artist was a pioneer of Abstract Expressionism, and a leading exponent of action painting?"
        }
    ],
    "success": true,
    "totalQuestions": 24
}
```






#### GET '/categories/{category_id}/questions'
- General:
    - Returns a list of questions objects by category, success value, and total number of questions
    - Resuls the current_category
    
- Samples: `curl -X GET http://127.0.0.1:5000/categories/3/questions`
```
{
    "currentCategory": "Geography",
    "questions": [
        {
            "answer": "Lake Victoria",
            "category": 3,
            "difficulty": 2,
            "id": 13,
            "question": "What is the largest lake in Africa?"
        },
        {
            "answer": "The Palace of Versailles",
            "category": 3,
            "difficulty": 3,
            "id": 14,
            "question": "In which royal palace would you find the Hall of Mirrors?"
        },
        {
            "answer": "Agra",
            "category": 3,
            "difficulty": 2,
            "id": 15,
            "question": "The Taj Mahal is located in which Indian city?"
        }
    ],
    "success": true,
    "totalQuestions": 3
}
```

### DELETE '/questions/{question_id}'

- General:
    - Deletes the question of the given ID if it exists. Returns the id of the deleted question, success value, total questions, and questions list based on current page number to update the frontend. 
- `curl -X DELETE http://127.0.0.1:5000/questions/28`

```
{
    "deleted": 28,
    "questions": [
        {
            "answer": "Apollo 13",
            "category": 5,
            "difficulty": 4,
            "id": 2,
            "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
        },
        {
            "answer": "Tom Cruise",
            "category": 5,
            "difficulty": 4,
            "id": 4,
            "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
        },
        {
            "answer": "Maya Angelou",
            "category": 4,
            "difficulty": 2,
            "id": 5,
            "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
        },
        {
            "answer": "Edward Scissorhands",
            "category": 5,
            "difficulty": 3,
            "id": 6,
            "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
        },
        {
            "answer": "Muhammad Ali",
            "category": 4,
            "difficulty": 1,
            "id": 9,
            "question": "What boxer's original name is Cassius Clay?"
        },
        {
            "answer": "Brazil",
            "category": 6,
            "difficulty": 3,
            "id": 10,
            "question": "Which is the only team to play in every soccer World Cup tournament?"
        },
        {
            "answer": "Uruguay",
            "category": 6,
            "difficulty": 4,
            "id": 11,
            "question": "Which country won the first ever soccer World Cup in 1930?"
        },
        {
            "answer": "George Washington Carver",
            "category": 4,
            "difficulty": 2,
            "id": 12,
            "question": "Who invented Peanut Butter?"
        },
        {
            "answer": "Lake Victoria",
            "category": 3,
            "difficulty": 2,
            "id": 13,
            "question": "What is the largest lake in Africa?"
        },
        {
            "answer": "The Palace of Versailles",
            "category": 3,
            "difficulty": 3,
            "id": 14,
            "question": "In which royal palace would you find the Hall of Mirrors?"
        }
    ],
    "success": true,
    "totalQuestions": 23
}

```


### POST '/questions/search'

- General : 
    - Create a POST endpoint to get questions based on a search term. It should return any questions for whom the search term is a substring of the question.
- Sample : `curl -X POST http://127.0.0.1:5000/questions/search "Content-Type: application/json" -d {searchTerm":"who"}`

```
{
    "questions": [
        {
            "answer": "Maya Angelou",
            "category": 4,
            "difficulty": 2,
            "id": 5,
            "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
        },
        {
            "answer": "George Washington Carver",
            "category": 4,
            "difficulty": 2,
            "id": 12,
            "question": "Who invented Peanut Butter?"
        },
        {
            "answer": "Alexander Fleming",
            "category": 1,
            "difficulty": 3,
            "id": 21,
            "question": "Who discovered penicillin?"
        },
        {
            "answer": "George Washington Carver",
            "category": 4,
            "difficulty": 2,
            "id": 26,
            "question": "Who invented Peanut Butter?"
        },
        {
            "answer": "Oussoufi Camara",
            "category": 4,
            "difficulty": 2,
            "id": 27,
            "question": "Who invented Peanut Butter?"
        },
        {
            "answer": "Camara Seydi Boubou ",
            "category": 4,
            "difficulty": 2,
            "id": 29,
            "question": "Who is the first civil service director in mauritania ?"
        }
    ],
    "success": true,
    "totalQuestions": 6
}


```

#### POST '/quizzes'
- General:
    - Create a POST endpoint to get questions to play the quiz. This endpoint should take a category and previous question parameters and return a random questions within the given category, if provided, and that is not one of the previous questions.
    
- Sample: `curl -X POST  http://127.0.0.1:5000/questions -H "Content-Type: application/json" -d {"quiz_category":3, previous_questions: [13, 14]}'`








## Deployment N/A

## Authors
Oussoufi Camara,  

## Acknowledgements 
Coach Caryn, the awesome team at Udacity and all Session leads of the ALX fullStack program.
Great thanks for all your support.