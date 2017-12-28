
# Table of Contents

1.  [Steps](#orgf903464)
    1.  [UI Steps](#org0f3e9f0)
        1.  [Choose Subject and Level](#org47c802f)
        2.  [Click "See question availability from QB" button to see available questions/types/difficulties](#org4656933)
        3.  [Number of Questions for each Questions Types](#orgb31f56c)
        4.  [% of diffilcty levels of questions for the quiz](#org0568f92)
        5.  [Choose list of Units (All checked by default)](#orgbbed009)
        6.  [Send request to QB to get questions](#org3280c68)
    2.  [Technical Steps](#org7b98960)
        1.  [See question availability from QB](#org4c94180)
        2.  [Number of questions](#org4b1e461)
        3.  [% of difficulty levels of questions for the quiz](#orgc48e8ce)
        4.  [Validate against available question statistics on the LS and display corresponding messages if not correct number](#org6f96d10)
        5.  [Question Type](#org406ba05)
2.  [on QB](#orgc1b1d99)
    1.  [Remove True/False and Matching question types](#orgdd49c35)
    2.  [question<sub>quiz</sub> table creation - which links quizes with questions](#org2b6f8f0)
    3.  [Give questions availability statistics via REST service](#org82c158d)
    4.  [Give list of questions as per AJAX request from LS](#org8e9c4c9)


<a id="orgf903464"></a>

# Steps


<a id="org0f3e9f0"></a>

## UI Steps


<a id="org47c802f"></a>

### Choose Subject and Level


<a id="org4656933"></a>

### Click "See question availability from QB" button to see available questions/types/difficulties


<a id="orgb31f56c"></a>

### Number of Questions for each Questions Types


<a id="org0568f92"></a>

### % of diffilcty levels of questions for the quiz


<a id="orgbbed009"></a>

### Choose list of Units (All checked by default)


<a id="org3280c68"></a>

### Send request to QB to get questions

1.  Receive JSON data with questions


<a id="org7b98960"></a>

## Technical Steps


<a id="org4c94180"></a>

### See question availability from QB

1.  Send GET request to get "available questions data"

    1.  Subject ID
    
    2.  Level ID

2.  Receive JSON of "available questions data"

    1.  
    
        {
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
        
        }

3.  Send GET request for "Send request to QB to get questions"

    {
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
        }


<a id="org4b1e461"></a>

### Number of questions

1.  Multichoice - 10

2.  Short Answer - 20

3.  Long Answer - 20


<a id="orgc48e8ce"></a>

### % of difficulty levels of questions for the quiz

1.  5 difficulties

    1.  Very easy - 10%
    
    2.  Easy - 20%
    
    3.  Medium - 30%
    
    4.  Difficult - 30%
    
    5.  Very difficult - 10%


<a id="org6f96d10"></a>

### Validate against available question statistics on the LS and display corresponding messages if not correct number

1.  For example not enough very difficult questions for Multichoice type etc.


<a id="org406ba05"></a>

### Question Type

1.  Multichoice

2.  Short Answer

3.  Long Answer


<a id="orgc1b1d99"></a>

# TODO on QB


<a id="orgdd49c35"></a>

## TODO Remove True/False and Matching question types


<a id="org2b6f8f0"></a>

## TODO question<sub>quiz</sub> table creation - which links quizes with questions


<a id="org82c158d"></a>

## TODO Give questions availability statistics via REST service


<a id="org8e9c4c9"></a>

## TODO Give list of questions as per AJAX request from LS

