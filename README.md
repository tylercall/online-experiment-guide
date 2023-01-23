# online-experiment-guide
Guide for setting up online experiments

This guide is intended for Cognitive Science and Psychology students at Carleton University. It provides tips on setting up online experiments using three platforms: SONA, Qualtrics, and Pavlovia.

While each of these platforms has its own documentation (insert links here), I have found that some of the most useful (i.e., time-saving) features are easily missed by users who don't have experience with integrating online systems. This guide highlights these features, explains their value, and provides instructions for using them.

If used correctly, these features improve participants' user experience and minimize manual work (data management, ensuring compliance with data security requirements, and granting credit to participants) for researchers.

Participants sign up for studies in SONA, fill out questionnaires and sign consent forms in Qualtrics, and participate in experiments in Pavlovia. While they enter or generate data in all three platforms, their personally identifying information (student ID, name, email address, etc.) should not be recorded in Qualtrics or Pavlovia. The sections below describe how to get SONA to generate a unique, anonymous ID for each participant, then pass this value to Qualtrics, which in turn passes this value to Pavlovia. Optionally, this value can then be used to automatically grant credit to the participant in SONA. 


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
