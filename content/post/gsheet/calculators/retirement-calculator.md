---
title: "Retirement Calculator"
date: 2021-10-17T11:04:46+05:30
draft: true
---

## YARC - Yet Another Retirement Calculator
Nowadays retirement calculators are available a dime a dozen. Every other day a new "fintech startup" is created and provides you with the "best" retirement calculator.
While I have absoluitely nothing against such free services and retirement calculators, my biggest pet peeve is the amount of personal data we are happily sharing with these individuals.
Just assume your next door neighbour comes to you and asks you how much have you saved and whats your retirement plan like. There is a 80% chance you will never share any definite information with the indivudal in question. 
Then why is us that we just love to use these new age calculators and share our deepest and darkest secrets with these site happily. No questions asked.

While on the front of it this is meaningless data, the fact of the matter is you generally land up sharing the below information
1. PAN Number
2. D.O.B.
3. EPF Details (almost all calulcators now have an EPF import feature)
4. MF investment details (again all calculators have a CAS import feature)
5. Loan/Debt information

While I do not doubt the intention of these sites, what I doubt is the level of security and data management plans in place. 
All it would take is a disgruntled engineer, a poorly patched system or a "free" software installation, and all these critical information would be floating the deep dark web (and share with the "Jamtara Gangs").
This is a big price to pay for something thats really not that difficult to achieve through a simple google sheet and some simple functions.

In this article I try and provide a simple calculator (which by no means is as elaborate as the financial calculators in different sites) however it gets the job done.
Additionally its totally protected and available just for you.
Caveat: Yes the data is also "shared" with google. However I would trust an organization like google which anyways has all my data thanks to the android phones and gmail and is spending millions on engineers and securing data.

### Getting Started
Any basic retirement calculator needs to have the below functionalities
1. D.O.B.
2. Current Income
3. Current Expenditure
4. Expected Expediture post retirement
5. Current Savings (if any)

Retirement can be in 2 flavours:
1. Where we exhaust all our savings by the time we retire
2. Where we still have some buffer kitty by the time we retire 


Ideal Retirement:




```javascript

/**
* existingAmount - The amount which is already saved , can be 0
* amount - The regular amount invested at monthly
* roi - The annual rate of interest
* months - The total time period of investment
* coumpoundingFrequency - The time period at which the amount will be compounded
  1 - Monthly (Mutual Funds)
  3 - Quarterly (Savings Bank Account)
 12 - Annual (eg. EPF/PPF etc)   
*/

function topupCompounding( existingAmount , amount , roi , months , coumpoundingFrequency , topupPercent ) {
  
  var total = existingAmount;
  var tempInterest  = 0;

  for(let i=0;i<months;i++) 
  {
    total = total + amount;
    let interest = total * roi / 12 / 100; 
    tempInterest+=interest;    
    if((i+1)%coumpoundingFrequency==0 || (i+1)==months){
        total+=tempInterest;
        tempInterest=0;
    }

if((i+1)%12==0){
    amount = amount * (100+ topupPercent)/100;
}
 
  }
  return total;
}

```