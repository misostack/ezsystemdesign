# Spaced Repetition Learning App

**Docs && Tools :**

- https://docs.google.com/drawings/d/13UVsWFSem0LhA6VtwZQyBfWF2pDLJQXYBUHrsv7FfWE/edit
- https://app.creately.com/diagram/ct8s4RwjYaE/edit

!["Sample ERD"][./assets/images/sample-erd.jpg]

## I. User Domains

**The stories**

!["Space Repetition Learning App Stories"][spaced_repetition_learning_app]

**Explore User Domains**

!["Explored Domains"][spl_explore_domains]

!["spaced-repetition-learning-app-domains"][spl_domains]

In this step, the user domains had been explored:

### Core Domain

>> **Spaced Repetition Learning**

**Explore the domain's knowledge, actity and influence**

**Keywords:**

**Nouns**

- English learner
- Word ( my word )
- Word list or words ( my word list, new word list)
- Custom Labels
- From list to make a list
- Today
- Yesterday
- Essay
- Topic ( short topic )
- Answers
- English
- Community
- Members
- Kind of tests
- Meaning
- Images
- Fill-in-the-blank
- Quiz

**Verbs**

- Create ( word, words, tests)
- Select ( words from my word lists )
- Group ( word by custom labels)
- Do ( a test )
- Remember
- Learned
- Start
- Review
- Know (  which words need to review again )
- Use ( words )
- Make ( an essay )
- Receive ( answers )
- Know ( english )
- Help
- Correct
- Contribute
- Share

**Adjective or adverbe**

- Every weekend
- Every 2 weeks
- Correct or Not

!["spl core domain explore"][spl_core_domain_explore]

[spl_core_domain_explore]: ./assets/images/spl-core-domain-explore.png

**Explore domain and model it by**:


> Rule of thumb: Entities have an unique identity and one entity can't be substituted for another just because they have the same data. Value Objects have no identity and they can substitute each other if they have the same data. Any change to a value object means a new value object is born. An object can be an entity or a value object depending on the context.

**Examples**:

- An english learner (user) are entity because it have an id and changing some of its properties doesn't change the resource we're working with. It's one of the reasons you work with ids instead of the whole objects.
- **A word is a value object. Change the value of the word and the word changes as well, becoming a different word.**

1.Entities:

- English Learner ==> User ( Type = 'english learner' )
- Wordlist
- Test
- Essay/Topic ( Article )
- Answer ==> Comment from other members

2.Value Objects

- Word
- Label
- Quiz
- Lession

### Generic SubDomains:

- Secured User
- Service Owner
- System Dev



[spaced_repetition_learning_app]: ./assets/images/headfirst-mvc-laravel-spaced-repetition-learning.png

[spl_domains]: ./assets/images/spaced-repetition-learning-app-domains.jpg
[spl_explore_domains]: ./assets/images/spl-explore-domains.png

## II. Define Model with Ubitiquous Language

!["Domain Models version 2020-02-21"][spl_domain_models_v1]

[spl_domain_models_v1]: ./assets/images/spl-domain-models-v2020-02-21.jpg



