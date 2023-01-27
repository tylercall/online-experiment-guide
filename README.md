# online-experiment-guide
A guide for setting up online experiments with SONA, Qualtrics, and Pavlovia.

This guide is intended for Cognitive Science and Psychology students at Carleton University. It provides tips on setting up online experiments using three platforms: SONA, Qualtrics, and Pavlovia. While each of these platforms has detailed documentation, this documentation often describes highly valuable, time-saving features in technical language that might cause non-technical researchers to overlook them. These oversights could cost researchers both time and money. This guide aims to highlight these features, explain them in non-technical language, and provide clear instructions for using them.

## What features does this guide describe, and why should I care about them?

This guide describes several distinct features:
* Keeping participants anonymous outside of SONA (i.e., in Qualtrics and Pavlovia).
* Form validation in Qualtrics
* Linking platforms together
* Automatic credit granting

When implemented together, these features minimize manual work (and even eliminate the need for some manual operations) and facilitate data analysis and management. In short, they save you time and energy.

## Core concepts

A few (for now, only one?) core concepts appear throughout this guide. I introduce them here before referencing them below.

### Query string

(explain query string)

## SONA Setup

Participants sign up and receive credit for studies in SONA. This section outlines SONA configuration that allows you to maintain anonymized datasets outside of SONA and facilitates the credit granting process.

While setting up your study in SONA, you will be asked, "Should survey participants be identified only by a random, unique ID code?" If you select "yes", every participant who signs up for your study in SONA will be assigned a numerical ID. This ID, called a `SURVEY_ID`, can be viewed next to the participant's name on the "View uncredited timeslots tab".

SONA must then be configured to pass this `SURVEY_ID` to Qualtrics. This is done by including it in the query string of the "Study URL" link. A link to a  Qualtrics survey (without a query string) will probably look something like this: `https://cuhealth.eu.qualtrics.com/jfe/form/SV_14iwKWbMv6n2BQe`.

We append a query string parameter with a name of `id` and a value of `%SURVEY_ID%`, resulting in the following (don't forget the `?` to signify the start of the query string): `https://cuhealth.eu.qualtrics.com/jfe/form/SV_14iwKWbMv6n2BQe?id=%SURVEY_ID%`.

If you are using multiple SONA systems (i.e., the CogSci and Psych platforms), or if you plan to recruit participants from another platform (e.g., Prolific), it might be a good idea to add a second query string parameter (don't forget the `&` separator) to indicate the source from which your parciipant was recruited. For example, `https://cuhealth.eu.qualtrics.com/jfe/form/SV_14iwKWbMv6n2BQe?id=%SURVEY_ID%&source=sona_cogsci`.

With this configuration, SONA will include a unique ID code for each participant who clicks the study link and accesses Qualtrics. You will be able to follow this participant in Qualtrics and Pavlovia without these datasets containing any personally identifiable information. This ID code can then be used for automated or manual credit granting (see below).

## Qualtrics setup

You can use Qualtrics to (1) display consent information and record participants' consent; (2) capture any other participant information relevant to your study; (3) redirect qualifying, consenting participants to Pavlovia, where your study's experiment will take place.

Qualtrics is positioned between SONA and Pavlovia in our experiment stack, so correctly configuring Qualtrics is essential to connecting your experiment data (in Pavlovia) back to your participants. This section of the guide focuses on saving the SONA-generated ID in a Qualtrics survey, then passing this ID to Pavlovia.

### Saving the SONA-generated `id` (and any other query string data)

Above, we configured SONA to pass a participant's `SURVEY_ID` in a query string parameter called `id`. Our Qualtrics survey must extract this value from the query string and save it in the survey data. This is done in the "Survey Flow" section of your Survey configuration.

At the top of the survey flow, add a new element called "Set embedded data". Inside this element, add a new field for each query string parameter being passed to Qualtrics (using the example above, add one called `id` and one called `source`). Use the default behavior of "Value will be set from Panel or URL".

If the participant completes the survey, the `id` and `source` will be included in the survey data along with the participants' survey responses.

### Survey validation

Qualtrics surveys are highly customizable, and their documentation is the best resource to learn how to design the survey that is right for your study. 
Here are some basic guidelines to follow when designing your survey:
- to do
- to do

### Redirect to Pavlovia

If they consent and qualify to participate, they can be redirected to Pavlovia for the experiment.

- take survey_id from query string
- save survey_id from into form data

### form validation

### redirect to Pavlovia

- redirect to Pavlovia
- use survey_id that was passed from SONA to Qualtrics as participant ID for Pavlovia (query string parameter of "participant")



## Pavlovia

- participant query string parameter has ID from SONA.

## Granting credit in SONA
