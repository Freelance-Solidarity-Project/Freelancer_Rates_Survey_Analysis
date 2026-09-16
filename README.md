FSP-NWU Freelancer Rates Survey Analysis

**Project Description:**

Since 2020, the Freelance Solidarity Project, the National Writers Union’s digital media division, has collected data about freelance media workers’ rates. An online survey invites any freelancer to enter their rate and other information about any given assignment. The survey is anonymous and each response represents a single project. The full database of responses is publicly accessible, and, until now, the survey data has been used primarily as a negotiation tool. With more information about what outlets actually pay, freelancers are better equipped to individually push for a higher rate. However, in 2024, members of the union decided to analyze the data to understand better what people are being paid across the industry. The idea was to use the data to collectively push for improved labor conditions. To improve the data set, the Freelance Solidarity Project’s rate research working group spent a year between May 2024 and May 2025 encouraging freelancers to enter all of their rates for the year into the database. We pulled the dataset on November 5, 2025, and began analyzing it for patterns. 

Freelance Solidarity Project’s rates database page is here: [https://nwu.org/freelance-solidarity-project/rate-sharing/](https://nwu.org/freelance-solidarity-project/rate-sharing/) 

You can find the survey here: [https://docs.google.com/forms/d/e/1FAIpQLSdS\_3Dnn6Rj67YOEAME2SEdyyhdI\_eX1iwpFr6J8-fs0Vvnlw/viewform](https://docs.google.com/forms/d/e/1FAIpQLSdS_3Dnn6Rj67YOEAME2SEdyyhdI_eX1iwpFr6J8-fs0Vvnlw/viewform)

**Definitions:** 

**fsp\_rates\_database\_19940327-20251105.Original.csv**

Output file produced after running our codebase analysis.

**ffsp\_rates\_database\_19940327-20251105.Analysis.csv**

Dataset builds off of the “Original” csv, adding new fields used for analysis. 

**Pay\_Rate\_Type**

Pay\_Rate\_Type describes the metric by which the 'Pay\_Rate\_in\_Dollars' field is applied — a given project is paid for at the value of the 'Pay\_Rate\_in\_Dollars' field multiplied by the number of words, graphics, articles, etc. Or, it is paid as a flat rate, which means that the value listed in the 'Total\_Pay' field was the total value paid.

**Pay\_Per\_Word\_Reported**

Pay\_Rate\_In\_Dollars, only for fields where Pay\_Rate\_Type \= per word. Entered manually based on review of entry data. 

Significance: This field describes rates that the respondent described as “per word.” This field is the most likely to describe respondents’ negotiated per-word rate. 

**Pay\_per\_word\_calculated**

Total\_Pay divided by Word\_Count.

- Only exists for fields where word count exists.

Significance: This field describes what respondents actually made per word, based on their total pay and story word count, which may occasionally differ from their reported pay per word rate. All entries are now able to be compared by their calculated pay rate per word, even if their reported pay rate type (per article, flat rate, no reported rate, etc) is not per word. However, we are not able to calculate this value for data rows that do not include word count at all. 

**Pay\_per\_word\_aggregate**

This field combines two ways of calculating pay rate per word. 

- This field only includes projects where job\_focus is “writing and reporting,” except in the cases noted below. 

  - If the project data includes a Pay\_Per\_Word\_Calculated value ( Total\_Pay / Word\_Count), then Pay\_Per\_Word\_Aggregate \= Pay\_Per\_Word\_Calculated.

  - If the project data does NOT include a Pay\_Per\_Word\_Calculated value, then Pay\_Per\_Word\_Aggregate \= Pay\_Per\_Word\_Reported.

  - If the project includes neither a Pay\_Per\_Word\_Calculated value, nor a Pay\_Per\_Word\_Reported value, then it is left blank.

Significance: This field is the data set’s most comprehensive list of per-word rates. It combines Pay\_Per\_Word\_Reported and Pay\_per\_word\_calculated, to give us the maximum number of values possible. In order to reflect the most accurate rates of how much people were paid per word, we chose to reference the Pay\_Per\_Word\_Calculated field over the Pay\_Per\_Word\_Reported field. Pay\_Per\_Word\_Reported is used in cases where a pay per word rate was provided, but no word count value was provided. 

Note:  Although this field focuses on projects where job\_focus is “writing and reporting,” it includes some entries that combine writing and reporting with other mediums. One example is an illustrated article. The rate seems to include illustrations in addition to the word count. There’s also a photo essay, a recipe development entry, and a project that involved product testing that came with photos. For items 276 and 849, job\_focus was marked editing in the original csv, but job\_cleaned indicated the project also involved writing. So those values have been included in pay\_per\_word aggregate.

**Hourly\_Pay\_Reported**

Pay\_Rate\_In\_Dollars, only for fields where Pay\_Rate\_Type \= per hour. Entered manually based on review of entry data.

Significance: This data represents cases where participants reported a rate that was paid by the hour. Note that the sample size is very small. 

**Avg\_Hourly\_Pay**

Total\_Pay divided by Hours\_Worked.

Significance: This field is the calculated value for how much a respondent made per hour, based on the Total\_Pay divided by the number of reported hours worked in the Hours\_Worked field. We cannot calculate values here if there are no hours worked reported. 

**Aggregate\_Hourly\_Pay**

This field combines two ways of calculating pay rate per hour.

- If the project data includes a Avg\_Hourly\_Pay value, then Aggregate\_Hourly\_Pay \= Avg\_Hourly\_Pay.

  - If the project data does NOT include a Avg\_Hourly\_Pay value, then Aggregate\_Hourly\_Pay \= Hourly\_Pay\_Reported.

  - If the project includes neither an Avg\_Hourly\_Payl value, nor a Hourly\_Pay\_Reported value, then it is left blank.

  - Entered manually based on review of entry data. 

Significance: This field includes the data set’s most comprehensive list of hourly rates. It combines Avg\_Hourly\_Pay and Hourly\_Pay\_Reported, to give us the maximum number of values possible. As much as possible, this field is meant to capture what people were actually paid, so it prioritizes Avg\_Hourly\_Pay over Hourly\_Pay\_Reported.

**Gender\_Identity\_Clean**

Simplified version of Gender\_Identity field. Uses only the tags listed below. Uses as many tags as apply. Entered manually based on review of entry data.

* Trans if Gender\_Identity includes   
  * ‘Trans’ and/or ‘Transmasc.’

* Nonbinary if Gender\_Identity includes   
  * ‘Two spirit’ and/or ‘Genderqueer’ and/or ‘Genderfluid’ and/or ‘Gender Expansive’ and/or ‘bigender’ and/or ‘Agender.’

* Cis if Gender\_Identity includes   
  * ‘Cis.’

* Male if Gender\_Identity includes   
  * ‘Male.’

* Female if Gender\_Identity includes   
  * ‘Female.’  
      
* Prefer not to say if Gender\_Identity includes   
  * ‘Prefer not to say.’

* No additional tag needed if Gender\_Identity includes Butch, because the term could apply to any gender. 

**Race\_Ethnicity\_Clean**

Cleaned version of Race and/or Ethnicity field. Uses only the tags listed below. Uses as many tags as apply. 

* White if Race and/or Ethnicity includes   
  * ‘White’ or ‘White passing.’

* Asian if Race and/or Ethnicity includes   
  * ‘Southeast Asian’ and/or ‘South Asian’ and/or ‘East Asian’ and/or ‘Asian.’

* South Asian if Race and/or Ethnicity includes   
  * ‘South Asian.’

* Pacific Islander if Race and/or Ethnicity includes   
  * ‘Pacific Islander.’

* Indigenous if Race and/or Ethnicity includes   
  * ‘Native American’ and/or ‘First Nation’ and/or ‘Indigenous.’

* Black if Race and/or Ethnicity includes   
  * ‘Black.’

* African if Race and/or Ethnicity includes   
  * ‘North African’ or ‘African.’

* Jewish if Race and/or Ethnicity includes   
  * ‘Jewish.’

* MENA if Race and/or Ethnicity includes   
  * ‘Middle Eastern’ and/or ‘North African’ and/or ‘Arab.’

* Latinx if Race and/or Ethnicity includes   
  * ‘Latinx’ and/or ‘Hispanic’ and/or ‘Latine.’

* West Indian if Race and/or Ethnicity includes   
  * ‘West Indian.’

* Prefer not to say if Race and/or Ethnicity includes   
  * ‘Prefer not to say.’


  
Significance: Race and Ethnicity categories were chosen to be as inclusive as possible and to reflect as many journalism associations as possible. Some identities will fall under multiple categories. 

**Individual Race and Ethnicity Fields**

Entered manually based on review of entry data.

Multiple\_Selected  
If Race\_Ethnicity\_Clean includes multiple tags, then cell says “yes.”

MENA  
If Race\_Ethnicity\_Clean includes the tag “MENA,” then cell says “yes.”

Black  
If Race\_Ethnicity\_Clean includes the tag “Black,” then cell says “yes.”  
​​  
White  
If Race\_Ethnicity\_Clean includes the tag “White,” then cell says “yes.”

Asian  
If Race\_Ethnicity\_Clean includes the tag “Asian,” then cell says “yes.”

South Asian  
If Race\_Ethnicity\_Clean includes the tag “South Asian,” then cell says “yes.”

African  
If Race\_Ethnicity\_Clean includes the tag “African,” then cell says “yes.”

Latinx  
If Race\_Ethnicity\_Clean includes the tag “Latinx,” then cell says “yes.”

West Indian  
If Race\_Ethnicity\_Clean includes the tag “West Indian,” then cell says “yes.”

Indigenous  
If Race\_Ethnicity\_Clean includes the tag “Indigenous,” then cell says “yes.”

Jewish  
If Race\_Ethnicity\_Clean includes the tag “Jewish,” then cell says “yes.”

Pacific\_Islander  
If Race\_Ethnicity\_Clean includes the tag “Pacific\_Islander,” then cell says “yes.”

No\_Race\_Ethnicity\_Data   
If Race\_Ethnicity\_Clean includes “Prefer not to Say” or is blank, then cell says “yes.”

Significance: Used to analyze rates based on demographics. 

**Individual Gender Fields**

Entered manually based on review of entry data. 

Trans  
If Gender\_Identity\_Clean includes the tag “Trans,” then cell says “yes.”

Nonbinary  
If Gender\_Identity\_Clean includes the tag “Nonbinary,” then cell says “yes.”

Cis  
If Gender\_Identity\_Clean includes the tag “Cis,” then cell says “yes.”

Male  
If Gender\_Identity\_Clean includes the tag “Male,” then cell says “yes.”

Female  
If Gender\_Identity\_Clean includes the tag “Female,” then cell says “yes.”

No\_Gender\_Data  
If Gender\_Identity\_Clean is tagged as “Prefer not to Say” or is blank, then cell says “yes.”

Significance: Used to analyze rates based on gender. 

**News\_Type**

*Significance:* Freelance media workers produce a range of products for a range of clients. The vast majority of rate survey respondents described rates from clients that publish journalism. However some respondents worked for nonprofit advocacy organizations, retail companies, universities, etc. The authors of this analysis sought to differentiate rates from outlets that practice journalism, from rates from other types of clients. A team of five reviewers determined the appropriate tag for each entry. 

*News*:   
The rate comes from an organization whose primary purpose is to produce independent editorial content, including articles, images, videos, or audio, in service of a mission centered on journalism, criticism, or advice. 

The “news” tag can apply to outlets that support their editorial content with a for-profit model. However, the editorial side of the outlet should be largely independent of the business side. The purpose of the organization should go beyond driving profit or selling products. 

It’s okay for a “news” outlet to be mission-driven, but non-profits that produce content in service of a specific campaign or advocacy effort, are not labeled “news.”

When in doubt, reviewers looked for an editorial policy, which at times provided clarification about mission and potential conflicts of interest. 

*Ambiguous*

There is no hard line between “news” and “not news.” To acknowledge this, reviewers created a third tag called “ambiguous.”

Most of the rates tagged as “ambiguous” are tied to assignments by organizations or companies whose primary purpose is something other than to produce news. This group includes, for example, the magazines of advocacy non-profits, a porn site, a music platform, a car listings site, a university publication, a research aggregator, and a book review site published by Taiwan’s Ministry of Culture. 

Some are magazines that seem to exist primarily to publish PR. In other cases, freelancers submitted the name of a publisher or podcast studio, rather than a specific publication or show. If a significant proportion of the publisher or studio’s output was news, reviewers used the tag “ambiguous.”

The “ambiguous” tag also applies to rates from literary and arts magazines that primarily publish pieces of art or literature. In contrast, reviewers applied the label “news” to other literary magazines where a significant proportion of the output is criticism and analysis.

For ambiguous cases, reviewers also looked at the assignment for clarification on how the item should be tagged. Overall, a significant proportion of the freelancers who submitted rates for “ambiguous” outlets seem like they produced actual journalism. However, reviewers prioritized their decision-making based on the goal of the outlet overall, and tagged entities as ambiguous if the function was not clearly about news. 

*Not\_news*

Anything that clearly does not fit the definition of “news.” 

Academic journals of peer reviewed articles are “not\_news.” 

Publishing houses and podcast studios are marked “not\_news,” unless they primarily produce news. Same for entries where a media conglomerate, but not a specific outlet, was entered. Exceptions apply in cases where the assignment description is clearly news.

If an outlet identifies as a "brand" and publishes reviews of products, and nowhere mentions that it's independent from the products it discusses, then it's "not news."

