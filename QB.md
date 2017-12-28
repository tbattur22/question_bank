
# Table of Contents

1.  [Steps](#org3246804)
    1.  [UI Steps](#org3bec11f)
        1.  [Choose Subject and Level](#orge2d1523)
        2.  [Click "See question availability from QB" button to see available questions/types/difficulties](#org8e9dc16)
        3.  [Number of Questions for each Questions Types](#orgfebc14e)
        4.  [% of diffilcty levels of questions for the quiz](#orgab52b43)
        5.  [Choose list of Units (All checked by default)](#org5062859)
        6.  [Send request to QB to get questions](#orgdbcb73a)
    2.  [Technical Steps](#org50b110a)
        1.  [See question availability from QB](#orgce4d2e6)
        2.  [Number of questions](#org7f23c7d)
        3.  [% of difficulty levels of questions for the quiz](#org4776def)
        4.  [Validate against available question statistics on the LS and display corresponding messages if not correct number](#org1eefe06)
        5.  [Question Type](#org0188502)
2.  [on QB](#orga4a0deb)
    1.  [Remove True/False and Matching question types](#orgd110cb8)
    2.  [question<sub>quiz</sub> table creation - which links quizes with questions](#org24dea25)
    3.  [Give questions availability statistics via REST service](#org5b7c584)
    4.  [Give list of questions as per AJAX request from LS](#orgd35d4ab)


<a id="org3246804"></a>

# Steps


<a id="org3bec11f"></a>

## UI Steps


<a id="orge2d1523"></a>

### Choose Subject and Level


<a id="org8e9dc16"></a>

### Click "See question availability from QB" button to see available questions/types/difficulties


<a id="orgfebc14e"></a>

### Number of Questions for each Questions Types


<a id="orgab52b43"></a>

### % of diffilcty levels of questions for the quiz


<a id="org5062859"></a>

### Choose list of Units (All checked by default)


<a id="orgdbcb73a"></a>

### Send request to QB to get questions

1.  Receive JSON data with questions


<a id="org50b110a"></a>

## Technical Steps


<a id="orgce4d2e6"></a>

### See question availability from QB

1.  Send GET request to get "available questions data"

    1.  Subject ID
    
    2.  Level ID

2.  Receive JSON of "available questions data"

    1.  
    
        ~{
            "question<sub>type</sub>":
            {
                "multi<sub>choice</sub>": {
                    "total<sub>question</sub><sub>number</sub>": 222,
                    "unused<sub>question</sub><sub>number</sub>": 122,
                    "by<sub>difficulty</sub><sub>level</sub>": {
                        "very<sub>easy</sub>": 100,
                        "easy": 40,
                        "medium": 232,
                        "difficult": 234,
                        "very<sub>difficult</sub>": 111
                    }
                },
                "short<sub>answer</sub>": {
                    "total<sub>question</sub><sub>number</sub>": 234,
                    "unused<sub>question</sub><sub>number</sub>": 122,
                    "by<sub>difficulty</sub><sub>level</sub>": {
                        "very<sub>easy</sub>": 100,
                        "easy": 40,
                        "medium": 232,
                        "difficult": 234,
                        "very<sub>difficult</sub>": 111
                    }
                },
                "long<sub>answer</sub>": {
                    "total<sub>question</sub><sub>number</sub>": 234,
                    "unused<sub>question</sub><sub>number</sub>": 122,
                    "by<sub>difficulty</sub><sub>level</sub>": {
                        "very<sub>easy</sub>": 100,
                        "easy": 40,
                        "medium": 232,
                        "difficult": 234,
                        "very<sub>difficult</sub>": 111
                    }
                }
            },
        
        }~

3.  Send GET request for "Send request to QB to get questions"

    ~{
        "unit<sub>ids</sub>": [
            123,234, 234234, 123123, 234234, 123123, 234234, 123123213, 234234324, 123123
        ],
        "total<sub>questions</sub>": 50,
        "is<sub>unique</sub><sub>questions</sub>": false,
        "question<sub>type</sub>": {
            "multi<sub>choice</sub>": {
                "number": 10,
                "difficulty<sub>level</sub>": {
                    "very<sub>easy</sub>":6,
                    "easy": 1
                    "medium": 1
                    "difficult": 1
                    "very<sub>difficult</sub>": 1
                }
            },
            "short<sub>answer</sub>": {
                "number": 20,
                "difficulty<sub>level</sub>": {
                    "very<sub>easy</sub>":6,
                    "easy": 1
                    "medium": 1
                    "difficult": 1
                    "very<sub>difficult</sub>": 1
                }
    
    },
    "long<sub>answer</sub>": {
        "number": 20,
        "difficulty<sub>level</sub>": {
            "very<sub>easy</sub>":6,
            "easy": 1
            "medium": 1
            "difficult": 1
            "very<sub>difficult</sub>": 1
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
                    "type": "short<sub>answer</sub>",
                    "difficulty<sub>level</sub>": "very<sub>easy</sub>",
                    "qual<sub>link</sub>": {},
                    "answers": [
                        {
                            "id": 1,
                            "body": "This is the answer",
                            "question<sub>id</sub>": "The question<sub>id</sub>",
                            "correct": 1
                        }
                    ]
                }
            ]
        }~


<a id="org7f23c7d"></a>

### Number of questions

1.  Multichoice - 10

2.  Short Answer - 20

3.  Long Answer - 20


<a id="org4776def"></a>

### % of difficulty levels of questions for the quiz

1.  5 difficulties

    1.  Very easy - 10%
    
    2.  Easy - 20%
    
    3.  Medium - 30%
    
    4.  Difficult - 30%
    
    5.  Very difficult - 10%


<a id="org1eefe06"></a>

### Validate against available question statistics on the LS and display corresponding messages if not correct number

1.  For example not enough very difficult questions for Multichoice type etc.


<a id="org0188502"></a>

### Question Type

1.  Multichoice

2.  Short Answer

3.  Long Answer


<a id="orga4a0deb"></a>

# TODO on QB


<a id="orgd110cb8"></a>

## TODO Remove True/False and Matching question types


<a id="org24dea25"></a>

## TODO question<sub>quiz</sub> table creation - which links quizes with questions


<a id="org5b7c584"></a>

## TODO Give questions availability statistics via REST service


<a id="orgd35d4ab"></a>

## TODO Give list of questions as per AJAX request from LS

