# online-experiment-guide
A guide for setting up online experiments

This guide is intended for Cognitive Science and Psychology students at Carleton University. It provides tips on setting up online experiments using three platforms: SONA, Qualtrics, and Pavlovia. While each of these platforms has detailed documentation, this documentation often describes highly valuable, time-saving features in technical language that might cause non-technical researchers to overlook them. These oversights could cost researchers both time and money. This guide aims to highlight these features, explain them in non-technical language, and provide clear instructions for using them.

## What features does this guide describe, and why should I care about them?

This guide describes several distinct features:
* Keeping participants anonymous outside of SONA (i.e., in Qualtrics and Pavlovia).
* Form validation in Qualtrics
* Linking platforms together
* Automatic credit granting

When implemented together, these features yield several benefits:
* minimizing manual work for anonymizing data sets
* minimizing manual work for cleaning questionnaire data
* facilitating reconciling data across platforms
* facilitating removing data of participants who request to have their data withdrawn
* minimizing manual work for credit granting

In short, these features minimize manual (i.e., tedious and time-consuming) work for researchers! This automation frees up your time and energy to focus on more interesting tasks, such as data analysis, writing, etc. They also facilitate compliance with best practices regarding participant privacy.

### Participant privacy

(to be continued…)

Participants sign up for studies in SONA, fill out questionnaires and sign consent forms in Qualtrics, and participate in experiments in Pavlovia. While they enter or generate data in all three platforms, their personally identifying information (student ID, name, email address, etc.) should not be recorded in Qualtrics or Pavlovia. The sections below describe how to get SONA to generate a unique, anonymous ID for each participant, then pass this value to Qualtrics, which in turn passes this value to Pavlovia. Optionally, this value can then be used to automatically grant credit to the participant in SONA. 
 

## SONA

Participants sign up for studies in SONA. They also receive credit (granted by researchers) for their participation in SONA.

- give each participant and anonymous ID
- include ID in link participant clicks to access Qualtrics

## Qualtrics

### maintain anonymity

Participants fill out questionnaires and sign consent forms in Qualtrics. If they consent and qualify to participate, they can be redirected to Pavlovia.

- take survey_id from query string
- save survey_id from into form data

### form validation

### redirect to Pavlovia

- redirect to Pavlovia
- use survey_id that was passed from SONA to Qualtrics as participant ID for Pavlovia (query string parameter of "participant")



## Pavlovia

- participant query string parameter has ID from SONA.

## Granting credit in SONA
