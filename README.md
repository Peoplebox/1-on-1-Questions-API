# Peoplebox 1-on-1 meeting Questions-API

## Overview

## URI and Versioning

We hope to improve the API over time. The changes won't always be backward compatible, so we're going to use versioning. This first iteration will have URIs prefixed with `https://api.peoplebox.ai/v1/` and is structured as described below. There is currently no rate limit.

For versioning purposes, only removal of a non-optional field or alteration of an existing field will be considered incompatible changes. *Clients should gracefully handle additional fields they don't expect, and simply ignore them.*

# Questions API

 The API's to fetch information related to questions are as follows -
 
 ## Index
 
 This API returns the list of all questions paginated(if used) as per your choice
 
 ### URL
 
 `GET` https://api.peoplebox.ai/v1/questions
 
 ### Parameters
 
 Field | Description
------|------------
**employee_type** | `manager` - Case-sensitive. Required.
only_parents | `true` or `false` - It will give only parent questions without the alternatives if true.
alternatives | `true` or `false`  - It will give parent questions aong with the alternatives if true.
category | For filtering based on categories - `/v1/questions?category=['Career Growth & Development', 'Career Growth & Development']`
search_term | For searching of questions based on their `talking_point` field - `/v1/questions?search_term="mentor"`
page | Starts from `1`
per_page | can be any number you want

### Example Response

`https://api.peoplebox.ai/v1/questions?page=1&per_page=2&alternatives=true&employee_type=manager`

```javascript
[
    {
        "category": "Work-life",
        "talking_point": "What obstacles are you encountering right now?",
        "talking_point_type": "manager",
        "bookmark_count": 39,
        "parent_agenda_id": null,
        "alternatives": [
            {
                "id": 16566,
                "category": "Work-life",
                "talking_point": "What were your biggest time wasters or roadblocks last week or the week before?",
                "talking_point_type": "manager",
                "created_at": "2020-01-07T04:18:45.000Z",
                "updated_at": "2020-03-19T12:42:01.000Z",
                "parent_agenda_id": 16565,
                "bookmark_count": 23
            },
            {
                "id": 16567,
                "category": "Work-life",
                "talking_point": "What is keeping you from accomplishing your work? What are the roadblocks or bottlenecks?",
                "talking_point_type": "manager",
                "created_at": "2020-01-07T04:18:45.000Z",
                "updated_at": "2020-03-19T12:42:01.000Z",
                "parent_agenda_id": 16565,
                "bookmark_count": 16
            },
            {
                "id": 16568,
                "category": "Work-life",
                "talking_point": "List down your top 3 roadblocks for next week?",
                "talking_point_type": "manager",
                "created_at": "2020-01-07T04:18:45.000Z",
                "updated_at": "2020-03-19T12:42:01.000Z",
                "parent_agenda_id": 16565,
                "bookmark_count": 4
            },
            {
                "id": 16569,
                "category": "Work-life",
                "talking_point": "What are the biggest roadblocks for you each week?",
                "talking_point_type": "manager",
                "created_at": "2020-01-07T04:18:45.000Z",
                "updated_at": "2020-03-19T12:42:01.000Z",
                "parent_agenda_id": 16565,
                "bookmark_count": 2
            },
            {
                "id": 16571,
                "category": "Work-life",
                "talking_point": "Is there anything blocking you from getting your work done?",
                "talking_point_type": "manager",
                "created_at": "2020-01-07T04:18:45.000Z",
                "updated_at": "2020-03-19T12:42:01.000Z",
                "parent_agenda_id": 16565,
                "bookmark_count": 2
            }
        ]
    },
    {
        "category": "Work-life",
        "talking_point": "What worries you?",
        "talking_point_type": "manager",
        "bookmark_count": 34,
        "parent_agenda_id": null,
        "alternatives": []
    }
]


```

### Response
 
 Field | Description
------|------------
category | Category of the question
talking_point | Question text/title
talking_point_type | Is the question for a manager or a report
bookmark_count | Toal number of upvotes 
parent_agenda_id | Id of the parent of this question
alternatives | List of alternatves/children of this question


## Show
 
 This API returns the details of a question
 
 ### URL
 
 `GET` https://api.peoplebox.ai/v1/questions/:id
 
 ### Parameters
 
 ### Example Response
 
 `https://api.peoplebox.ai/v1/questions/16588`
 
 ```javascript
 {
    "category": "Career Growth & Development",
    "talking_point": "What makes you stay in this job?",
    "talking_point_type": "manager",
    "bookmark_count": 5,
    "parent_agenda_id": null
}
```
 
 
# Questions API

 The API to fetch categories of question -
 
 ## Categories
 
  This API returns all the categories
 
 ### URL
 
 `GET` https://api.peoplebox.ai/v1/questions/categories
 
 ### Parameters
 Field | Description
------|------------
**employee_type** | `manager` - Case-sensitive. Required.


 ### Example Response
 
 `https://api.peoplebox.ai/v1/questions/categories`
 
 ```javascript
  [
    "Alignment",
    "Being helpful/being awesome:",
    "Career Development",
    "Career Growth & Development",
    "Company Culture",
    "Company Improvement",
    "Conversation Starter",
    "Employee Motivation",
    "Feedback",
    "Feeling valued",
    "Feeling Values",
    "General check-in questions",
    "Goals & Alignment",
    "Happiness",
    "Job Performance",
    "Job Satisfaction",
    "Long Term Goals",
    "Manager",
    "Manager Support",
    "Materials & equipments",
    "Organizational Feedback",
    "Personal Life",
    "Progress Questions",
    "Recognition",
    "Relationships",
    "Self Improvement",
    "Team and Company",
    "Team Dynamics",
    "Team Relations",
    "Work Responsibilities",
    "Work-life"
]
 ```
 
