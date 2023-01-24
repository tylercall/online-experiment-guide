# online-experiment-guide
Guide for setting up online experiments

This guide is intended for Cognitive Science and Psychology students at Carleton University. It provides tips on setting up online experiments using three platforms: SONA, Qualtrics, and Pavlovia. While each of these platforms has detailed documentation, this documentation often describes highly valuable, time-saving features in technical language that might cause non-technical researchers to overlook them. These oversights could cost researchers both time and money. This guide aims to highlight these features, explain them in non-technical language, and provide clear instructions for using them.

## What features does this guide describe?

This guide describes three distinct features:
1. Keeping participants anonymous outside of SONA (i.e., in Qualtrics and Pavlovia).
2. Linking platforms together such that anonymous data from one platform can be reconciled with data from other platforms.
3. Automatic credit granting

## Why are these features useful?

These features, when used together, provide several benefits to both partipants and researchers.

First, participants' user experience will be smoother. They will not have to enter any identifying information in Qualtrics, resulting in a streamlined questionnaire. The same principle applies to Pavlovia, where interactions can be limited to only those necessary for the experiment. Improved user experience translates to higher completion rates and better chances that a participant will recommend your study to friends or classmates.

Second, researchers…

### benefits
If used correctly, these features improve participants' user experience and minimize manual work (data management, ensuring compliance with data security requirements, and granting credit to participants) for researchers.

Participants sign up for studies in SONA, fill out questionnaires and sign consent forms in Qualtrics, and participate in experiments in Pavlovia. While they enter or generate data in all three platforms, their personally identifying information (student ID, name, email address, etc.) should not be recorded in Qualtrics or Pavlovia. The sections below describe how to get SONA to generate a unique, anonymous ID for each participant, then pass this value to Qualtrics, which in turn passes this value to Pavlovia. Optionally, this value can then be used to automatically grant credit to the participant in SONA. 

- keep participants' personally identifying information out of Qualtrics and Pavlovia
- minimize manual data cleaning (asking participants to correct questionnaire data, removing personally identifying information)
- mitigate or eliminate
- 

## SONA

Participants sign up for studies in SONA. They also receive credit (granted by researchers) for their participation in SONA.

- give each participant and anonymous ID
- include ID in link participant clicks to access Qualtrics

## Qualtrics

Participants fill out questionnaires and sign consent forms in Qualtrics. If they consent and qualify to participate, they can be redirected to Pavlovia.

- take survey_id from query string
- save survey_id from into form data

- redirect to Pavlovia
- use survey_id that was passed from SONA to Qualtrics as participant ID for Pavlovia (query string parameter of "participant")

## Pavlovia

- participant query string parameter has ID from SONA.

## Granting credit in SONA
