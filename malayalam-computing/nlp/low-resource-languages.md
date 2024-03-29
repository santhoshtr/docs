# Low resource languages

{% embed url="https://arxiv.org/abs/2103.12028" %}

It is an analysis of parallel language corpus datasets popularly used in machine learning domain. The paper argues that the quality of these datasets are poor for low resource languages and raises many questions on its usage, reported results based on this poor data. For measuring the quality the authors recruited volunteers from many languages. CCAligned, ParaCwal, WikiMatrix are some such popular datasets. Wikimatrix is dataset from Wikipedia by aligning sentences from articles in multiple languages. This paper reports that "two-thirds of the audited sampleswere on average misaligned. We noticed that sentences were often similar in structure, but describeddifferent facts" - which is not a surprise given wikipedia articles are rarely exact translations.

They use a term called "Representation washing" to describe a problem with this low quality datasets for low resource languages. I liked it.

> Since there are datasets which contain many low-resource languages, the community may feel a sense of progress and growing equity, despite the actual quality of the resources for these languages.Similarly, if low-quality datasets are used as bench-marks they may exaggerate model performance, making low-resource NLP appear more solved than it is — or conversely, if models perform poorly when trained with such data, it may be wrongly assumed that the task of learning models for these languages is harder than it actually is or infeasible given current resources. These effects could result in productive effort being redirected away from these tasks and languages

 



