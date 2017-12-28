
# Table of Contents

1.  [Steps](#orga53fd12)
    1.  [UI Steps](#org63ea50c)
        1.  [Choose Subject and Level](#org234b4f2)
        2.  [Click "See question availability from QB" button to see available questions/types/difficulties](#orgd7011f4)
        3.  [Number of Questions for each Questions Types](#org93c244f)
        4.  [% of diffilcty levels of questions for the quiz](#org81a3752)
        5.  [Choose list of Units (All checked by default)](#org97f1d60)
        6.  [Send request to QB to get questions](#org4edecbe)
    2.  [Technical Steps](#org39be014)
        1.  [See question availability from QB](#orgc08c89f)
        2.  [Number of questions](#org4cd5e72)
        3.  [% of difficulty levels of questions for the quiz](#orgd219747)
        4.  [Validate against available question statistics on the LS and display corresponding messages if not correct number](#org97debf1)
        5.  [Question Type](#org664c987)
2.  [on QB](#orgd6e372f)
    1.  [Remove True/False and Matching question types](#org4b13dd5)
    2.  [question\_quiz table creation - which links quizes with questions](#orgf7fcf4d)
    3.  [Give questions availability statistics via REST service](#org3dec771)
    4.  [Give list of questions as per AJAX request from LS](#org3fc3d9e)



<a id="orga53fd12"></a>

# Steps


<a id="org63ea50c"></a>

## UI Steps


<a id="org234b4f2"></a>

### Choose Subject and Level


<a id="orgd7011f4"></a>

### Click "See question availability from QB" button to see available questions/types/difficulties


<a id="org93c244f"></a>

### Number of Questions for each Questions Types


<a id="org81a3752"></a>

### % of diffilcty levels of questions for the quiz


<a id="org97f1d60"></a>

### Choose list of Units (All checked by default)


<a id="org4edecbe"></a>

### Send request to QB to get questions

1.  Receive JSON data with questions


<a id="org39be014"></a>

## Technical Steps


<a id="orgc08c89f"></a>

### See question availability from QB

1.  Send GET request to get "available questions data"

    1.  Subject ID
    
    2.  Level ID

2.  Receive JSON of "available questions data"

    1.  
    
        ~{
            "question\_type":
            {
                "multi\_choice": {
                    "total\_question\_number": 222,
                    "unused\_question\_number": 122,
                    "by\_difficulty\_level": {
                        "very\_easy": 100,
                        "easy": 40,
                        "medium": 232,
                        "difficult": 234,
                        "very\_difficult": 111
                    }
                },
                "short\_answer": {
                    "total\_question\_number": 234,
                    "unused\_question\_number": 122,
                    "by\_difficulty\_level": {
                        "very\_easy": 100,
                        "easy": 40,
                        "medium": 232,
                        "difficult": 234,
                        "very\_difficult": 111
                    }
                },
                "long\_answer": {
                    "total\_question\_number": 234,
                    "unused\_question\_number": 122,
                    "by\_difficulty\_level": {
                        "very\_easy": 100,
                        "easy": 40,
                        "medium": 232,
                        "difficult": 234,
                        "very\_difficult": 111
                    }
                }
            },
        
        }~

3.  Send GET request for "Send request to QB to get questions"

    ~{
        "unit\_ids": [
            123,234, 234234, 123123, 234234, 123123, 234234, 123123213, 234234324, 123123
        ],
        "total\_questions": 50,
        "is\_unique\_questions": false,
        "question\_type": {
            "multi\_choice": {
                "number": 10,
                "difficulty\_level": {
                    "very\_easy":6,
                    "easy": 1
                    "medium": 1
                    "difficult": 1
                    "very\_difficult": 1
                }
            },
            "short\_answer": {
                "number": 20,
                "difficulty\_level": {
                    "very\_easy":6,
                    "easy": 1
                    "medium": 1
                    "difficult": 1
                    "very\_difficult": 1
                }
    
    },
    "long\_answer": {
        "number": 20,
        "difficulty\_level": {
            "very\_easy":6,
            "easy": 1
            "medium": 1
            "difficult": 1
            "very\_difficult": 1
        }
    }
    
        },
    }~

4.  Response for "Send request to QB to get questions"

    1.  
    
        ~{
            "questions": [
                {
                    "id": 1,
                    "title": "Title",
                    "body": "BODY",
                    "rubric": "llksdjflksdj",
                    "type": "short\_answer",
                    "difficulty\_level": "very\_easy",
                    "qual\_link": {},
                    "answers": [
                        {
                            "id": 1,
                            "body": "This is the answer",
                            "question\_id": "The question\_id",
                            "correct": 1
                        }
                    ]
                }
            ]
        }~


<a id="org4cd5e72"></a>

### Number of questions

1.  Multichoice - 10

2.  Short Answer - 20

3.  Long Answer - 20


<a id="orgd219747"></a>

### % of difficulty levels of questions for the quiz

1.  5 difficulties

    1.  Very easy - 10%
    
    2.  Easy - 20%
    
    3.  Medium - 30%
    
    4.  Difficult - 30%
    
    5.  Very difficult - 10%


<a id="org97debf1"></a>

### Validate against available question statistics on the LS and display corresponding messages if not correct number

1.  For example not enough very difficult questions for Multichoice type etc.


<a id="org664c987"></a>

### Question Type

1.  Multichoice

2.  Short Answer

3.  Long Answer


<a id="orgd6e372f"></a>

# TODO on QB


<a id="org4b13dd5"></a>

## TODO Remove True/False and Matching question types


<a id="orgf7fcf4d"></a>

## TODO question\_quiz table creation - which links quizes with questions


<a id="org3dec771"></a>

## TODO Give questions availability statistics via REST service


<a id="org3fc3d9e"></a>

## TODO Give list of questions as per AJAX request from LS

