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

==to-do:== why should we care about participant privacy?
- ethical requirement
- if you take personally identifiable information (name, student ID, email address, etc.) in Qualtrics or Pavlovia, you will need to do additional work to anonymize these data sets, and removing data to comply with a withdrawal request may become complicated.

==to-do:== why should we care about minimizing manual work?
-  time consuming
-  error prone
-  tedious

In short, these features minimize manual (i.e., tedious and time-consuming) work for researchers! This automation frees up your time and energy to focus on more interesting tasks, such as data analysis, writing, etc. They also facilitate compliance with best practices regarding participant privacy.

## Core concepts

(some core concepts that come up throughout the tutorial)

### Query string

(explain query string)

## SONA Setup

Participants sign up and receive credit for studies in SONA. This section outlines SONA configuration that allows you to maintain anonymized datasets outside of SONA and facilitates the credit granting process.

While setting up your study in SONA, you will be asked, "Should survey participants be identified only by a random, unique ID code?" If you select "yes", every participant who signs up for your study in SONA will be assigned a numerical ID. This ID, called a `SURVEY_ID`, can be viewed next to the participant's name on the "View uncredited timeslots tab".

SONA must then be configured to pass this `SURVEY_ID` to Qualtrics. This is done by including it in the query string of the "Study URL" link. A link to Qualtrics (without a query string) will probably look something like this: `https://cuhealth.eu.qualtrics.com/jfe/form/SV_14iwKWbMv6n2BQe`. We append a query string parameter with a name of `id` and a value of `%SURVEY_ID%`, resulting in the following (don't forget the `?` to signify the start of the query string): `https://cuhealth.eu.qualtrics.com/jfe/form/SV_14iwKWbMv6n2BQe?id=%SURVEY_ID%`. If you are using multiple SONA systems (i.e., the CogSci and Psych platforms), or if you plan to recruit participants from another platform (e.g., Prolific), it might be a good idea to add a second query string parameter (don't forget the `&` separator) to indicate the source from which your parciipant was recruited. For example, `https://cuhealth.eu.qualtrics.com/jfe/form/SV_14iwKWbMv6n2BQe?id=%SURVEY_ID%&source=sona_cogsci`.

With this configuration, SONA will include a unique ID code for each participant who clicks the study link and accesses Qualtrics. You will be able to follow this participant in Qualtrics and Pavlovia without these datasets containing any personally identifiable information. This ID code can then be used for automated or manual credit granting (see below).

## Qualtrics

### maintain anonymity

Participants sign consent forms and fill out questionnaires in Qualtrics. If they consent and qualify to participate, they can be redirected to Pavlovia for the experiment.

- take survey_id from query string
- save survey_id from into form data

### form validation

### redirect to Pavlovia

- redirect to Pavlovia
- use survey_id that was passed from SONA to Qualtrics as participant ID for Pavlovia (query string parameter of "participant")



## Pavlovia

- participant query string parameter has ID from SONA.

## Granting credit in SONA
