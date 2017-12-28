
# Table of Contents

1.  [Steps](#org28f052c)
    1.  [UI Steps](#orgd2940d3)
        1.  [Choose Subject and Level](#org02cad3a)
        2.  [Click "See question availability from QB" button to see available questions/types/difficulties](#orgb2a58ca)
        3.  [Number of Questions for each Questions Types](#org8dbd6aa)
        4.  [% of diffilcty levels of questions for the quiz](#orga945f06)
        5.  [Choose list of Units (All checked by default)](#org5842a1d)
        6.  [Send request to QB to get questions](#org188711b)
    2.  [Technical Steps](#org83e2ce4)
        1.  [See question availability from QB](#orgdc7b394)
        2.  [Number of questions](#orgd14416e)
        3.  [% of difficulty levels of questions for the quiz](#org4970c32)
        4.  [Validate against available question statistics on the LS and display corresponding messages if not correct number](#org2be30fd)
        5.  [Question Type](#org2b901a5)
2.  [on QB](#orge07331c)
    1.  [Remove True/False and Matching question types](#org0efa912)
    2.  [question\_quiz table creation - which links quizes with questions](#orgf792e0f)
    3.  [Give questions availability statistics via REST service](#org7c97953)
    4.  [Give list of questions as per AJAX request from LS](#orgdb5ca94)


<a id="org28f052c"></a>

# Steps


<a id="orgd2940d3"></a>

## UI Steps


<a id="org02cad3a"></a>

### Choose Subject and Level


<a id="orgb2a58ca"></a>

### Click "See question availability from QB" button to see available questions/types/difficulties


<a id="org8dbd6aa"></a>

### Number of Questions for each Questions Types


<a id="orga945f06"></a>

### % of diffilcty levels of questions for the quiz


<a id="org5842a1d"></a>

### Choose list of Units (All checked by default)


<a id="org188711b"></a>

### Send request to QB to get questions

1.  Receive JSON data with questions


<a id="org83e2ce4"></a>

## Technical Steps


<a id="orgdc7b394"></a>

### See question availability from QB

1.  Send GET request to get "available questions data"

    1.  Subject ID
    
    2.  Level ID

2.  Receive JSON of "available questions data"

    1.  
    
        {
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
        
        }

3.  Send GET request for "Send request to QB to get questions"

    {
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
    }

4.  Response for "Send request to QB to get questions"

    1.  
    
        {
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
        }


<a id="orgd14416e"></a>

### Number of questions

1.  Multichoice - 10

2.  Short Answer - 20

3.  Long Answer - 20


<a id="org4970c32"></a>

### % of difficulty levels of questions for the quiz

1.  5 difficulties

    1.  Very easy - 10%
    
    2.  Easy - 20%
    
    3.  Medium - 30%
    
    4.  Difficult - 30%
    
    5.  Very difficult - 10%


<a id="org2be30fd"></a>

### Validate against available question statistics on the LS and display corresponding messages if not correct number

1.  For example not enough very difficult questions for Multichoice type etc.


<a id="org2b901a5"></a>

### Question Type

1.  Multichoice

2.  Short Answer

3.  Long Answer


<a id="orge07331c"></a>

# TODO on QB


<a id="org0efa912"></a>

## TODO Remove True/False and Matching question types


<a id="orgf792e0f"></a>

## TODO question\_quiz table creation - which links quizes with questions


<a id="org7c97953"></a>

## TODO Give questions availability statistics via REST service


<a id="orgdb5ca94"></a>

## TODO Give list of questions as per AJAX request from LS

