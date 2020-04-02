# Peoplebox 1-on-1 meeting Questions-API

Built a comprehensive list of 1-on-1 questions for managers (550+). View with upvotes and categories on https://www.peoplebox.ai/t/one-on-one-meeting-template-manager-questions-list. 

This API allows you to access all questions and their categories along with the **upvoted count**. 

## Overview

## URI and Versioning

We hope to improve the API over time. The changes won't always be backward compatible, so we're going to use versioning. This first iteration will have URIs prefixed with `https://api.peoplebox.ai/v1/` and is structured as described below. There is currently no rate limit.

For versioning purposes, only removal of a non-optional field or alteration of an existing field will be considered incompatible changes. *Clients should gracefully handle additional fields they don't expect, and simply ignore them.*

# Categories & Questions

## Manager Support

- What would you want me to stop doing as your manager?
- How can I provide you more autonomy at work?
- What did your past managers do for you that you'd like me to continue doing?
- What would you want me to continue doing as your manager?
- Is there anything your past managers did that frustrate you?
- What can I do to encourage more creativity & innovation in our team?
- On a scale of 1-5, how would you rate my support to you as your manager?
- Is there anything I can do to improve the performance of our team?
- What can I do to bring down stress levels in our team?
- What changes can I bring in to our 1-on-1 meetings to make them better?
- What can I do to prepare you for success?
- Is the team hesitating to share or discuss anything with me?

## Roadblocks
- Is there something that stressed you out recently at work? How can I help?
- What are the biggest time wasters for you each week?
- How are you progressing on the challenge(s) you were facing last time we spoke?
- Do you have any questions related to your job but are a little hesitant to ask?
- What roadblocks are preventing you from completing your tasks/projects on time?
- What do you find most frustrating at work? What can I do to help you with it?

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
 
 `https://api.peoplebox.ai/v1/questions/3739`
 
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
 
 `https://api.peoplebox.ai/v1/questions/categories?employee_type=manager`
 
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
 
