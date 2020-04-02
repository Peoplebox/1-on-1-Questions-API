# 1-on-1 meeting Questions for Managers with social upvotes - API

We decided to build a comprehensive list of 1-on-1 questions for managers (550+) with upvotes and categories (View Upvotes and Alternatives on https://www.peoplebox.ai/t/one-on-one-meeting-template-manager-questions-list) 

[![Alt text](https://img.youtube.com/vi/PXPgv7hoR2A/0.jpg)](https://www.youtube.com/watch?v=PXPgv7hoR2A)


Posted it on Producthunt and became #2 Product of the day with over 700 upvotes

<a href="https://www.producthunt.com/posts/1-on-1-meeting-questions-for-managers?utm_source=badge-featured&utm_medium=badge&utm_souce=badge-1-on-1-meeting-questions-for-managers" target="_blank"><img src="https://api.producthunt.com/widgets/embed-image/v1/featured.svg?post_id=186748&theme=light" alt="1-on-1 Meeting Questions for Managers - Browse most popular 1-on-1 questions by categories | Product Hunt Embed" style="width: 250px; height: 54px;" width="125px" height="27px" /></a>

So decided to built an API to allow  access all questions and their categories along with the **upvoted count**. 

## Overview

# Questions API

## URI and Versioning

We hope to improve the API over time. The changes won't always be backward compatible, so we're going to use versioning. This first iteration will have URIs prefixed with `https://api.peoplebox.ai/v1/` and is structured as described below. There is currently no rate limit.

For versioning purposes, only removal of a non-optional field or alteration of an existing field will be considered incompatible changes. *Clients should gracefully handle additional fields they don't expect, and simply ignore them.*

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
 
# Categories & Questions

## Manager Support

-	What would you want me to stop doing as your manager?
-	How can I provide you more autonomy at work?
-	What did your past managers do for you that you'd like me to continue doing?
-	What would you want me to continue doing as your manager?
-	Is there anything your past managers did that frustrate you?
-	What can I do to encourage more creativity & innovation in our team?
-	On a scale of 1-5, how would you rate my support to you as your manager?
-	Is there anything I can do to improve the performance of our team?
-	What can I do to bring down stress levels in our team?
-	What changes can I bring in to our 1-on-1 meetings to make them better?
-	What can I do to prepare you for success?
-	Is the team hesitating to share or discuss anything with me?
-	What aspects of your work would you like me to direct you more in?
-	Is there anything you like in particular about my management style?
-	Can you think of an instance where I said or did something you didn't like or agree with?
-	Is there anything in particular that you dislike about my management style?
-	What aspects of work would you like me to direct you less in?
-	Do you have a preferred mode of communication to keep me updated on your tasks or projects?
-	Is there anything you would like me to clarify or re-explain to our team?
-	What can I do to build our team's reputation in the company?

[View Upvotes & Alternatives](https://www.peoplebox.ai/t/one-on-one-meeting-template-manager-questions-list)

## Roadblocks
-	Is there something that stressed you out recently at work? How can I help?
-	What are the biggest time wasters for you each week?
-	How are you progressing on the challenge(s) you were facing last time we spoke?
-	Do you have any questions related to your job but are a little hesitant to ask?
-	What roadblocks are preventing you from completing your tasks/projects on time?
-	What do you find most frustrating at work? What can I do to help you with it?
-	What is the one thing that's holding the team back from performing at its best?
-	What’s stopping you from achieving your long term goals?
-	What makes you feel helpless at work or prevents you from reaching your full potential?
-	Do you have a way in your mind to get through the biggest hurdle that we are currently facing?
-	How do you overcome any hurdles at work?
-	What challenges did you face last week that prevented you from giving your best?
-	Do you have any worries related to your work, role or company? How can I help?
-	Is there any particular activity that you spend most of your time on?
-	What areas are you struggling with while managing your team?

[View Upvotes & Alternatives](https://www.peoplebox.ai/t/one-on-one-meeting-template-manager-questions-list)

## Career Growth & Development
-	What new skills would you like to develop to meet your career goals?
-	Whom would you like to have as your mentor?
-	What specific training & development opportunities will help you in your career growth?
-	What professional goals would you like to accomplish in the coming year?
-	Have any of your future career goals changed since the last time we spoke?
-	What work you do is most in line with your long-term goals?
-	What kind of career growth do you value more? (new responsibilities, leading a team, promotion, learning a new skill, etc.)
-	Which part of your job do you need additional guidance or training in?
-	How can the training programs you've attended be made better?
-	How else can your strengths benefit our team and the company?
-	Is your current role helping you grow in your career at the pace you want?
-	What is the next step you see in your career?
-	Do you experience a skill gap that hinders you from reaching your goals?
-	What are your long term professional goals and why do they matter to you?
-	Which of your professional skills would you like to hone further?
-	What skills are required to achieve your goals? How confident are you in these skills?
-	How do you see your personal goals aligning with your team goals?
-	What other skills do you have that you feel we are not fully utilizing?
-	What other areas or functions of the company interest you?
-	Do you feel your future goals are realistic and attainable?
-	What's the most important thing in your career right now?
-	What's your plan of action to reach your ideal role?
-	Are there any other roles in the company that interest you?
-	What more do you need in your career right now?

[View Upvotes & Alternatives](https://www.peoplebox.ai/t/one-on-one-meeting-template-manager-questions-list)

## Feedback
-	Are you happy with the amount of feedback we give to each other in the team?
-	Do you find my feedback specific and actionable?
-	Are you able to share any kind of feedback with me openly?
-	What feedback do you have for me to become a better manager?
-	Are there any specific areas on which you'd like more feedback?
-	What could I do to ease the concerns you have while giving me honest feedback?
-	Do your peers share their feedback with you? What constructive feedback did you receive from them?
-	Is there any project on which you want more feedback from me?
-	What can I do to provide you more meaningful feedback?
-	Does it make you uncomfortable to share constructive feedback with your colleagues?
-	Would you like to receive more feedback from me and the team?
-	How do you prefer to get feedback from me?
-	Is the feedback I give you sufficient?
-	Whom do you get valuable feedback from the team?

[View Upvotes & Alternatives](https://www.peoplebox.ai/t/one-on-one-meeting-template-manager-questions-list)

## Goals & Alignment
-	What one goal, if accomplished, will have the greatest impact on your life? How would it impact?
-	On an individual level, is there any goal you feel you might have difficulty achieving?
-	Would you like a mentor to help you achieve your long term goals?
-	What would you like to change if you don’t see yourself making any progress?
-	Do you feel like you’re growing in your role? What makes you say that?
-	Which of your current work is most in line with your future goals?
-	Do you think any of our team goals are unrealistic and unachievable?
-	What are your top priorities right now?
-	Do you have a clear understanding of the new goals and expectations?
-	What are some of the goals you would like to achieve in the next quarter?
-	What achievements or goals you aren’t very proud of? Why?
-	Do you see yourself making progress on your goals here?
-	What goals will be challenging for you to accomplish this month/quarter?

[View Upvotes & Alternatives](https://www.peoplebox.ai/t/one-on-one-meeting-template-manager-questions-list)

## Icebreakers
-	What do you wish you’d learnt when you were younger?
-	What is one belief that has made you who you are today?
-	If you could go back in time and give your younger self an advice, what would it be?
-	Who has been the most influential person in your life?
-	What signs should I look for to know that you're in a bad mood?
-	What are you passionate about in your professional & personal life?
-	What social causes are close to your heart?
-	If you were to go back in the past and learn something you couldn't, what would it be?
-	Is there something most of the people around don't know about you?
-	What do you do to cheer yourself up when you're feeling low?
-	Is there anything you like to do in your free time to bust stress but don’t have the time?
-	What's the best decision you've made till now?
-	If you had to choose a topic to teach in college, what would you choose?
-	What self-care regime do you follow every week?
-	If you had 3 options to choose a career in which you'll never fail, what would you choose?
-	If you could wake up one morning with a new quality, what would it be?
-	Who are some leaders you admire? What do you admire about them?
-	How do you unwind after work or on weekends?
-	Do you have a to-read book list for this year?
-	What does your ideal weekday look like?
-	Given a choice of anyone in the world, whom would you like to have as your dinner guest?

[View Upvotes & Alternatives](https://www.peoplebox.ai/t/one-on-one-meeting-template-manager-questions-list)

## Organizational Feedback
-	What changes would you bring in if you were given the reins of this company?
-	Do you believe the top leadership team is all on the same page?
-	Which is one workplace practice that you like the most here?
-	What could we do differently to be more creative and innovative as a company?
-	Do you have clarity about the company level goals set by top leadership?
-	Would you say our company is loyal to its employees?
-	What about our company culture impresses you the most at work every day?
-	How confident are you about our ability to succeed as a team and a company?
-	What, according to you, is our company's biggest problem?
-	Do you have clarity on our company's strategy and how your role fits into it?
-	How are your personal values aligned with the company's mission and vision?
-	What is one thing that we should definitely do to enhance our product?
-	How would you rate the communication within our company? What would you change?
-	Do you believe that your individual goals and the team's goals stand by the company's mission?
-	Do you need any clarity on our company’s strategies and/or goals?
-	Do you have any questions about the company's mission and your role in its success?

## Recognition
-	What form of recognition would you prefer the most: public or private, new responsibilities, awards, promotion, cash, etc?
-	What makes you feel valued at work?
-	Do you feel recognized for your efforts and contributions?
-	Is there anything that makes you feel undervalued at work?
-	What is that one thing I can do to make you feel more recognized at work?
-	If you could credit someone for your success, who would it be?
-	What has been your biggest accomplishment recently that you are proud of?
-	Whom did you help perform better and succeed at work recently? How?
-	What efforts would you like to be most recognized for?
-	Who has done an incredible job in the team lately?
-	Whom did you appreciate recently and for what ?
-	What feedback or praises have you got in your current role?

## Role Clarity & Expectations
-	Do you need more clarity on what's required of your current role?
-	What do you expect from this role? (eg: learning, personal development, tasks ownership, etc)
-	How can I make sure your talent is matched to the right role?
-	Are all your roles & responsibilities well defined to you? Do you have any doubts?
-	What aspect of your role do you need more clarity on?
-	How can I make your role more exciting?
-	How do you think your role contributes to the company's success?
-	Do your current roles & responsibilities stand up to your expectations? If not, why?
-	How can I help you to get more role clarity?
-	Do you have a current job description?

## Team Work & Collaboration
-	Do you face difficulty in getting along with anyone in our team?
-	Which aspects of our team culture would you change?
-	What is something that the team is lacking?
-	What's one thing our team needs to start doing?
-	What would you do differently if you were managing the team?
-	What do you think are our team's greatest strengths and weaknesses?
-	What team building activities can we have to build more collaboration?
-	Do you feel your team members support you enough?
-	What do you think about our team’s relationship with other teams?
-	What kind of person would be a good fit for our team?
-	How can I strengthen trust & collaboration in our team?
-	Who in our team do you depend on and trust the most? Why?
-	If you were making a new team, who would you like to have in it and why?
-	What do you feel our team is good at?
-	What are some ways we can improve communication in our team?
-	How would you rate the communication in our team?
-	Is everyone in the team doing their fair share of work?
-	Whom do you admire in our team? What do you like about them?
-	What improvements can we make in our processes as a team?
-	How would you describe our team’s work environment?

## Tools & Resources
-	Do you have the necessary tools and resources to perform your job?
-	What tools or resources would help you increase your productivity at work?
-	Is there any new technology we can adopt to help you and the team?
-	What tools and resources help you the most in your daily work?
-	Do you have all the information needed to carry out your tasks?
-	Do I effectively communicate the information you require?
-	What type of work environment brings out the best in you?
-	Are there any tools and/or resources that you rarely use and can get rid of it?
-	What's one thing we can change in our office environment to boost the efficiency of our team?

## Work Responsibilities & Performance
-	How would your ideal job/position differ from your current one?
-	If you could work on anything for the next month, what would it be? What makes you say that?
-	Which additional responsibility would you like to take on to make your role more challenging?
-	Is there anything I should know about the project but don’t?
-	Which other projects or assignments you'd like to contribute to?
-	Do you find your current responsibilities in the role challenging?
-	What type of work helps you make the best use of your skills?
-	What according to you will drive your success for the next 3-4 months?
-	Where do you think your skills can be best utilized?
-	Do any of your current tasks feel redundant and meaningless to you?
-	What work would you pass over to someone else to focus on new challenging responsibilities?
-	Reflecting on last week, what could have been done better?
-	What went well at work this week?
-	How satisfied are you with your current performance? Where would you like to improve?
-	How do you see your role evolving in the near future?
-	What frustrates you about [Project X]?
-	What excites you the most about your role and current work responsibilities?
-	What can I do to make the project more challenging/interesting for you and the team?
-	How do you see your next week at work?
-	Were you in a tough spot at work lately? How you could’ve handled things differently?
-	Which project(s) did you enjoy working on the most recently, and why?
-	What are you keen on learning from the project?
-	What have you learned so far while working on [Project X]?
-	Is something bothering you about any current or upcoming projects/tasks?

## Work Satisfaction
-	What do you enjoy the most in your current role?
-	On a scale of 1-5, how happy are you at work? How can I make it better for you?
-	Would you say you are proud of the work you do here?
-	What's the best part about working here?
-	What were your big or small wins in the past month?
-	What did you have fun doing in the past, but haven’t got the chance to do it recently?
-	What aspect of your work is extremely exhausting and demanding?
-	When did you enjoy working here the most?
-	When do you think your energy and focus is lowest at work?
-	Which part of the day are you at your productive best?
-	Did you find anything unexpected about your role since you've joined that made you happy or sad?
-	What kinds of flexibility would help you in balancing your work and home life?
-	What do you feel proud of in your current work?
-	What work routine helps you stay productive at work?
-	What would you like to do at work, but haven’t been able to?
-	What has challenged you in your role in the past 3 to 6 months?
-	How do you feel about your current workload?
-	How are you coping with your workload?
-	How satisfied are you in the way you and your team are progressing?
