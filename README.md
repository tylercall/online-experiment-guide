# online-experiment-guide
A guide for setting up online experiments with SONA, Qualtrics, and Pavlovia.

This guide is intended for Cognitive Science and Psychology students at Carleton University. It provides tips on setting up online experiments using three platforms: SONA, Qualtrics, and Pavlovia. While each of these platforms has detailed documentation, this documentation often describes highly valuable, time-saving features in technical language that might cause non-technical researchers to overlook them. These oversights could cost researchers both time and money. This guide aims to highlight these features, explain them in non-technical language, and provide clear instructions for using them.

# What features does this guide describe, and why should I care about them?

This guide describes several distinct features:
* Keeping participants anonymous outside of SONA (i.e., in Qualtrics and Pavlovia).
* Form validation in Qualtrics
* Linking platforms together (SONA -> Qualtrics -> Pavlovia)
* Automatic credit granting

When implemented together, these features minimize manual work (and even eliminate the need for some manual operations) and facilitate data analysis and management. In short, they save you time and energy.

# Core concepts

A few (for now, only one?) core concepts appear throughout this guide. I introduce them here before referencing them below.

## Query string

(explain query string)

# SONA Setup

Participants sign up and receive credit for studies in SONA. This section outlines SONA configuration that allows you to maintain anonymized datasets outside of SONA and facilitates the credit granting process.

While setting up your study in SONA, you will be asked, "Should survey participants be identified only by a random, unique ID code?" If you select "yes", every participant who signs up for your study in SONA will be assigned a numerical ID. This ID, called a `SURVEY_ID`, can be viewed next to the participant's name on the "View uncredited timeslots tab".

SONA must then be configured to pass this `SURVEY_ID` to Qualtrics. This is done by including it in the query string of the "Study URL" link. A link to a  Qualtrics survey (without a query string) will probably look something like this: `https://cuhealth.eu.qualtrics.com/jfe/form/SV_14iwKWbMv6n2BQe`.

We append a query string parameter with a name of `id` and a value of `%SURVEY_ID%`, resulting in the following (don't forget the `?` to signify the start of the query string): `https://cuhealth.eu.qualtrics.com/jfe/form/SV_14iwKWbMv6n2BQe?id=%SURVEY_ID%`.

If you are using multiple SONA systems (i.e., the CogSci and Psych platforms), or if you plan to recruit participants from another platform (e.g., Prolific), it might be a good idea to add a second query string parameter (don't forget the `&` separator) to indicate the source from which your parciipant was recruited. For example, `https://cuhealth.eu.qualtrics.com/jfe/form/SV_14iwKWbMv6n2BQe?id=%SURVEY_ID%&source=sona_cogsci`.

With this configuration, SONA will include a unique ID code for each participant who clicks the study link and accesses Qualtrics. You will be able to follow this participant in Qualtrics and Pavlovia without these datasets containing any personally identifiable information. This ID code can then be used for automated or manual credit granting (see below).

# Qualtrics setup

You can use Qualtrics to (1) display consent information and record participants' consent; (2) capture any other participant information relevant to your study; (3) redirect qualifying, consenting participants to Pavlovia, where your study's experiment will take place.

Qualtrics is positioned between SONA and Pavlovia in our experiment stack, so correctly configuring Qualtrics is essential to connecting your experiment data (in Pavlovia) back to your participants. This section of the guide focuses on saving the SONA-generated ID in a Qualtrics survey, then passing this ID to Pavlovia.

## Saving the SONA-generated `id` (and any other query string data)

Above, we configured SONA to pass a participant's `SURVEY_ID` in a query string parameter called `id`. Our Qualtrics survey must extract this value from the query string and save it in the survey data. This is done in the "Survey Flow" section of your Survey configuration.

At the top of the survey flow, add a new element called "Set embedded data". Inside this element, add a new field for each query string parameter being passed to Qualtrics (using the example above, add one called `id` and one called `source`). Use the default behavior of "Value will be set from Panel or URL".

If the participant completes the survey, the `id` and `source` will be included in the survey data along with the participants' survey responses.

## Survey design

Qualtrics surveys are highly customizable, and their [documentation](https://www.qualtrics.com/support/survey-platform/survey-module/survey-module-overview/) is a great way to familiarize yourself with the options available.

The length and complexity of your survey will depend on the needs of your study. Here are some general guidelines for survey design: 

**Use appropriate field types**: (coming soon)

**Validate your inputs**: (coming soon)

**Make required field required**: (coming soon)=

**Use conditional show/hide logic**: (coming soon)

**Prevent participants from completing survey more than once**: (coming soon)

## Redirect to Pavlovia

If participants consent and qualify for your study, they can be redirected from Qualtrics to Pavlovia upon completion of the Qualtrics survey.

You can configure this redirect by configuring the "End of Survey" section (below your survey blocks) of the survey builder. In this section, set the “End of survey message” to “Rediret to URL” and enter full complete redirect (described below) in the “Website URL” field.

The full redirect link contains the base URL (which will navigate participants to Pavlovia) and a query string that uniquely identifies each participant in Pavlovia. The base URL can be found in Pavlovia in the “Recruitment” section of your experiment page. For example: `https://run.pavlovia.org/joe.researcher/my-first-study`. If a user accesses this base URL without any query string information, they will be prompted to enter their participant ID and session number. Using the query string, we can pass these values to Pavlovia and prevent participants from being prompted for this information.

To uniquely (and anonymously) identify your participant in Pavlovia, add a query string containing participant information to the base Pavlovia URL.
You should append a query string to the end of the base URL. This query string must contain a paramater named `participant`. You can dynamically insert the current participant's `id`, which originated in SONA and was saved into the Qualtrics survey as `id`, with the following syntax: `${e://Field/id}`. Here is an example full redirect URL that includes this dynamically inserted participant ID: `https://run.pavlovia.org/joe.researcher/my-first-study?participant=${e://Field/id}`.

If you have enforced that your participants can only complete the Qualtrics survey once (and therefore can only be redirected to Pavlovia once), you may also choose to pass a query string parameter of `session` to Pavlovia: `https://run.pavlovia.org/joe.researcher/my-first-study?participant=${e://Field/id}&session=001` 

This example assumes you only allow participants to complete the Qualtrics survey once and access Pavlovia from Qualtrics once
Value of “participant” should be the id passed to Qualtrics from SONA and saved into your Qualtrics survey.
You can dynamically insert the participants’ ID into the redirect URL with the following syntax: ${e://Field/id}, where “id” is the Qualtrics field name where the SONA id was stored in the survey (see above)
Here is an example redirect link with query string filled out: https://run.pavlovia.org/joe.researcher/my-first-study?participant=${e://Field/id}&session=001

# Pavlovia

(coming soon)

# Granting credit in SONA

You can grant credit to SONA participants in two ways. First, you can manually grant credit in the SONA platform. Second, you can automatically grant credit to participants after they complete the study. Note that if you choose to implement automatic credit granting, this will only work for participants who complete the study. If you want to grant credit to participants who partially complete your study, you will need to do this manually.

## Manual credit granting

To manually grant credit in SONA, log into the SONA platform and access your study. Then, click on "View Uncredited Timeslots". This page displays the names and anonymous survey IDs of all participants who have yet to receive credit for your study. To grant credit, simply select the "Grant credit" button next to a participant's name and apply your changes with the button at the bottom of the page.

## Automatic credit granting

(coming soon)
