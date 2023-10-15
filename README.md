## Description of the different versions of the dataset

The following repository contain the data for the paper 'Moderation in the Wild: Investigating User-Driven Moderation in Online Discussions'.
The guidelines of the annotation study are available in the directory `guidelines`.

The data is available in two versions: `UMOD_non_aggregated.csv` and `UMOD_aggregated.csv` in the directory `dataset`.

### UMOD_non_aggregated.csv

This version contains each instance and annotations by one annotator. The annotations are not aggregated.

- *id*: [string]
- *preceding_comment*: [string] the comment that expresses the original opinion or argument
- *reply*: [string] an answer to the preceding comment that should be rated as whether it expresses some form of moderation
- moderation [yes/no]: whether the reply is a form of moderation
- *subjectivity*: [1-5] how opinionated is the comment
- *agressiveness*: [1-5] agressive comments can be defined as comments that are insulting, threatening, sarcastic, or hostile
- *constructiveness*: [1-5] constructive comments can be defined as high-quality comments that make a contribution to the conversation
- *sentiment*: [positive / negative / neutral] 
- *annotator*: [string] a unique identifier for each annotator (anonimized)
- *role*: [user / moderator / none]
- *race*: [black / white / asian / mixed / other]
- *sex*: [male / female]
- *age*: [int]
- *none*: [binary] no function is suitable for the comment or the comment does not express any function
- *social*: [binary] welcoming / greeting / encouraging others to participate
- *improveQuality*: [binary] feedback on the quality of the comment / argument (e.g. asking for clarification, asking for evidence, asking for sources)
- *organizing*: [binary] directs the comment to another comment or user
- *content*: [binary] correcting / adding information
- *broadening*: [binary] bringing in new perspectives or encouraging others to do so
- *policing*: [binary] encouraging civil and respectful behavior
- *siteIssues*: [binary] helps to resolve issues with the site or to explain rules of the site
- *offTopic*: [binary] indicates irrelevant content, off-point statements
- *agreeWithOpinion*: [yes / no / opinion not clear]

### UMOD_aggregated.csv

This version creates an aggregated version of the annotations. Each instance exists exactly once and was annotated by between 7 and 10 annotators. Each instance has a reply comment, a preceding comment and a comment id.
The annotations are aggregated by the following rules:

- *softlabel_mace*: [float between 0 and 1] the probability that the comment is a user moderation comment. Can be used as a soft label for user moderation. It has been aggregated using MACE (Hovy 2013).
- *softlabel_raw*: [float between 0 and 1] the probability that the comment is a user moderation comment. Can be used as a soft label for user moderation. It has been aggregated using the raw annotations.
- *subjectivity*: [float between 1 and 5] mean
- *agressiveness*: [float between 1 and 5] mean
- *constructiveness*: [float between 1 and 5] mean
- *sentiment*: [positive / negative / neutral] majority sentiment
- *functions*: [binary] if at least 1/2 of all annotators selected a function, it is considered as a function of the comment 
- *agreeWithOpinion*: [yes / no / opinion not clear] the number of annotators that selected the corresponding answer for that instance
- *entropy_moderation*: [float between 0 and 1.5] the normalized entropy of the raw annotations for that item. The higher, the more disagreement.
- *relamountRole*: [float between 0 and 1] the relative amount of annotators that selected the moderator role for that instance. The higher, the more annotators selected the same role.
- *countModFunctions*: [int] the number of different moderator functions that were selected for that instance.
- *annot_similarity_pre*: [float between 0 and 1] the cosine similarity between the initial definitions of usermoderation of all annotators for that instance. The higher, the more similar the annotators were in their understanding of user moderation.
- *annot_similarity_post*: [float between 0 and 1] the cosine similarity between the final (post-study) definitions of usermoderation of all annotators for that instance. The higher, the more similar the annotators were in their understanding of user moderation.
- *numAnnotators*: [int] the number of annotators that annotated that instance.
- *seedmodel*: [string] the seed model that was used for selecting this candidate item. Either (chat)GPT, expert or negative.
- *flagged*: [binary] whether the comment was flagged by any annotator as disturibing or not.

### UMOD_reply_wiht_linguistic_and_tan2016_features.csv

This file contains the reply comment with id and the additional features that were used in the paper for the analysis of constructiveness.
