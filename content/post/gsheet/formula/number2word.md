---
title: "Number2word"
date: 2021-10-17T17:26:29+05:30
draft: false
tags: [formula]
categories: [google-sheet]
---
## Number to Word

When ever you need to convert a number to word (without decimals) indian format use the below function.
When using in Google sheets, you just need to call the below function:
``` =number2Word(<cell address>) ```


```javascript
function number2Word(number){
    
    let word="";
    
    const digits = ["zero" , "one" , "two" , "three", "four"
    , "five", "six", "seven", "eight", "nine"];
    
    const teens = ["eleven" , "twelve" , "thirteen" , "fourteen" , "fifteen" , 
    "sixteen" , "seventeen" , "eighteen" , "nineteen"  ]
    
    const decals = ["ten" , "twenty" , "thirty" , "forty" , "fifty" , "sixty" , "seventy" , "eighty" , "ninety"];
    
    
    const originalNumber = parseInt(number);
    
    let tokenizeNumber = originalNumber;
    
    // originalNumber
    
    // crores
    if(tokenizeNumber>=10000000){
        const croresAmount = tokenizeNumber/10000000;
        word += number2Word(croresAmount) + " crores "
        tokenizeNumber=tokenizeNumber%10000000;
    }
    //lacs
    if(tokenizeNumber>=100000){
        const lacsAmount = tokenizeNumber/100000;
        word += number2Word(lacsAmount) + " lacs "
        tokenizeNumber=tokenizeNumber%100000;
    }
    if(tokenizeNumber>=1000){
        const thousandAmount = tokenizeNumber/1000;
        word += number2Word(thousandAmount) + " thousand "
        tokenizeNumber=tokenizeNumber%1000;
    }
    
    if(tokenizeNumber>=100){
        const thousandAmount = tokenizeNumber/100;
       word += number2Word(thousandAmount) + " hundred "
       tokenizeNumber=tokenizeNumber%100;
    }
    
    
    if(tokenizeNumber<100 ){
    // print if number is multiple of 10
    if(tokenizeNumber > 0    && Math.floor(tokenizeNumber/10) == tokenizeNumber/10 ){
        word+= decals[tokenizeNumber/10 - 1];
    }else if(tokenizeNumber>=20){
        
        const decalNumber = Math.floor(tokenizeNumber/10)-1;
        const remainderNumber = Math.floor(tokenizeNumber%10);
        
            word+= decals[decalNumber] + " " + digits[remainderNumber] 
    }else if(tokenizeNumber>=10){
        word+= teens[tokenizeNumber%10-1]
    }else if (tokenizeNumber<10){
        if ( tokenizeNumber > 0 || originalNumber == 0 ){
            word+= digits[tokenizeNumber] 
        }
             
    }
    }
    return word;
}    

```
