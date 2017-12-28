
# Table of Contents

1.  [Steps](#orgbc2b175)
    1.  [UI Steps](#org3c115f3)
        1.  [Choose Subject and Level](#orgc24a474)
        2.  [Click "See question availability from QB" button to see available questions/types/difficulties](#orga8600f6)
        3.  [Number of Questions for each Questions Types](#org19ee3c1)
        4.  [% of diffilcty levels of questions for the quiz](#orgf6a096e)
        5.  [Choose list of Units (All checked by default)](#orgdaec52c)
        6.  [Send request to QB to get questions](#org534e8cd)
    2.  [Technical Steps](#orgcf44471)
        1.  [See question availability from QB](#orgda7b976)
        2.  [Number of questions](#orgf60116d)
        3.  [% of difficulty levels of questions for the quiz](#orgb0f3045)
        4.  [Validate against available question statistics on the LS and display corresponding messages if not correct number](#orgbce17ea)
        5.  [Question Type](#org3baa7f6)
2.  [on QB](#orga307c65)
    1.  [Remove True/False and Matching question types](#org6c72752)
    2.  [question\_quiz table creation - which links quizes with questions](#org747c2f0)
    3.  [Give questions availability statistics via REST service](#org06c32e2)
    4.  [Give list of questions as per AJAX request from LS](#org3da3714)


<a id="orgbc2b175"></a>

# Steps


<a id="org3c115f3"></a>

## UI Steps


<a id="orgc24a474"></a>

### Choose Subject and Level


<a id="orga8600f6"></a>

### Click "See question availability from QB" button to see available questions/types/difficulties


<a id="org19ee3c1"></a>

### Number of Questions for each Questions Types


<a id="orgf6a096e"></a>

### % of diffilcty levels of questions for the quiz


<a id="orgdaec52c"></a>

### Choose list of Units (All checked by default)


<a id="org534e8cd"></a>

### Send request to QB to get questions

1.  Receive JSON data with questions


<a id="orgcf44471"></a>

## Technical Steps


<a id="orgda7b976"></a>

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

    1.  
    
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


<a id="orgf60116d"></a>

### Number of questions

1.  Multichoice - 10

2.  Short Answer - 20

3.  Long Answer - 20


<a id="orgb0f3045"></a>

### % of difficulty levels of questions for the quiz

1.  5 difficulties

    1.  Very easy - 10%
    
    2.  Easy - 20%
    
    3.  Medium - 30%
    
    4.  Difficult - 30%
    
    5.  Very difficult - 10%


<a id="orgbce17ea"></a>

### Validate against available question statistics on the LS and display corresponding messages if not correct number

1.  For example not enough very difficult questions for Multichoice type etc.


<a id="org3baa7f6"></a>

### Question Type

1.  Multichoice

2.  Short Answer

3.  Long Answer


<a id="orga307c65"></a>

# TODO on QB


<a id="org6c72752"></a>

## TODO Remove True/False and Matching question types


<a id="org747c2f0"></a>

## TODO question\_quiz table creation - which links quizes with questions


<a id="org06c32e2"></a>

## TODO Give questions availability statistics via REST service


<a id="org3da3714"></a>

## TODO Give list of questions as per AJAX request from LS

