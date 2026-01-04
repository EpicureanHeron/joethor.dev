---
title: "Gratitude Journal Google App Script Guide"
date: 2026-01-04
---

# Gratitude Journal Google App Script Guide

During the pandemic I took a Coursera course [The Science of Well-Being](https://www.coursera.org/learn/the-science-of-well-being). As part of the course, I learned about the importance of gratitude. 

I created a tiny script to help me write a gratitude journal each day. With the New Year, I thought it would be good to get out there and show off this script that, honestly, has helped me be more grateful. 

It uses [Google App Script](https://developers.google.com/workspace/guides/get-started), which is basically Javascript that has Google Office Suite API endpoints baked in. 

This should be something you can copy and paste, make a tiny edit to the code, and get deployed in around 5-10 minutes without any prior knowledge regarding how to code. 

Feel free to use this script in your life to help capture your moments of gratitude and create a sustainable and positive habit. 

I have been using this daily since March 11th, 2021. It has captured everything from the feeling of having fresh sheets on my bed to additions to our family. 

## Overview

Each day at around 6:00 PM, a document is created in my Gratitude Journal Google Drive folder. I get sent an email with a link to the document. 

I then fill out the journal, usually as I am going to bed, to capture what I was grateful for on the day. 

## Setup

### Create Google Drive Structure and Document 

Create a new Google Doc with the name, "Gratitude Template". 

Here is the text I use in the template for a prompt (I found it online years ago):

```
Instructions

Take 5-10 minutes to write down five things for which you are grateful.

Take a moment to be mindful of the things you are writing down (e.g., imagine the person or thing you’re writing about).

Some samples:

What’s something that you are grateful to have today that you didn’t have a year ago?
What’s something or someone that makes you feel safe?
What did you accomplish today?
How are you able to help others?
What’s something or someone that makes you feel safe?


Response


```

Create a new Google Drive folder called, "Gratitude Journal". 


#### A Note on Names

The above names are essential for the script to work. Feel free to update them as you see fit, but you will also need to update the references in the script. 

### Google App Script

Navigate to [script.google.com](https://script.google.com/home?pli=1)

Create a new project. 

Feel free to copy and past the below code. 


```
function triggerSetUp() {

ScriptApp.triggerSetup('createNewJournal')
.timeBased()
.atHour(18)
.everyDays(1)
.nearMinute()
.create()

}
function createNewJournal(){


  var gratitudeFolder = DriveApp.getFoldersByName("Gratitude Journal").next()

  var template = gratitudeFolder.getFilesByName('Gratitude Template').next()

  var formattedDate = Utilities.formatDate(new Date(), "GMT", "yyyy-MM-dd")

  var name = 'Gratitude ' + formattedDate

  var newTrackingDoc = template.makeCopy(name, gratitudeFolder)

  emailTrackingLink(newTrackingDoc, formattedDate)
}



function emailTrackingLink(newLink, formattedDate) {
    // email link to newly created document to myself

    var htmlText = "<p>Remember to do your gratitude journal for " + formattedDate + ".  <a href='" + newLink.getUrl() + "'>Here is the direct link</a>. "

    MailApp.sendEmail({
        to: 'YOUREMAIL@EMAILCOM',
        subject: "Gratitude Journal " + f.ormattedDate,
        htmlBody: htmlText

    })


};
```

Make sure you update your email in the `to: 'YOUREMAIL@EMAILCOM'` line. 

### Setting Up The Trigger

I believe the UI on the Google App Script will give you an option on the interface for a "function to run". It may default to `triggerSetUp`.

Either way, select the `triggerSetUp` from the UI toolbar and that will create the scheduled job (effectively a cron job).

Then, around 1800 AKA 6:00 PM (give or take 10 minutes) you should receive an email to your account from your Google account with the link to your new Gratitude Journal for the day. 
