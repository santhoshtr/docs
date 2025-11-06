# AI Based edit checks

Blog [An Experiment in Detecting Wikipedia Edit Policy Violations with LLMs](https://thottingal.in/blog/2025/04/04/wikipedia-editcheck-llm/)

## Possible approaches

Train a model with <https://github.com/EricFillion/happy-transformer>
Example <https://huggingface.co/vennify/t5-base-grammar-correction>
<https://www.vennify.ai/fine-tune-grammar-correction/>
<https://www.vennify.ai/grammar-correction-python/>

LLAMA GUARD Finetuning:
See

- <https://huggingface.co/meta-llama/Llama-Guard-3-1B>
  <https://github.com/meta-llama/llama-cookbook/blob/main/getting-started/responsible_ai/llama_guard/llama_guard_finetuning_multiple_violations_with_torchtune.ipynb>

## References

- Observations on using LLMs for checking grammar, etc. <https://www.crumplab.com/blog/665_realworld_editing/>

## Article-based features

(Credits Issac Johnson)

- For many models, we filter out list articles and disambiguation pages because the predictions
  often are not relevant given how different these articles are from the standard article.
  Maybe less "harm" and more about noise/frustration for editors. This can be done in a few ways:
  - Disambiguation: existence of `disambiguation` parameter in pageprops – e.g., <https://en.wikipedia.org/w/api.php?action=query&prop=pageprops&titles=John&ppprop=disambiguation%7Cwikibase_item&format=json&formatversion=2>
    - Alternatively, use the QID from the above API query and check for instance-of (P31) = Wikipedia disambiguation page (Q4167410) via <https://www.wikidata.org/w/api.php?action=wbgetclaims&entity=Q397210&property=P31&format=json>
    - List articles: no pageprop but we can use the Wikidata-based instance-of approach and just look for Wikimedia list article (Q13406463)
  - We have also adjusted recommendation visibility based on whether the article is a biography of a living person. Again, a few ways:
    - Wikidata: here you want instance-of (P31) = human (Q5) and no date of death (P570) property. Can also be extra careful by checking the data of birth and and assuming anyone over a certain age is dead, just lacking the property.
  - Categories: article in Living people category, which exists on at least 138 wikis.
    - Is the article under edit restrictions?
    - Here the `info` API has the necessary information: <https://en.wikipedia.org/w/api.php?action=query&prop=info&inprop=protection&titles=Mexico_City&format=json>
    - Article is part of Contentious Topics:
      - I don't think we've done this before and the edit restrictions above will hopefully catch much of this. Part of the challenge is that this is much less well-documented. On English Wikipedia, we could check whether the talk page for the article has the core Contentious Topics template transcluded on it – e.g., <https://en.wikipedia.org/w/api.php?action=query&prop=templates&titles=Talk:Flat%20Earth&tltemplates=Template:Contentious_topics/list&format=json&formatversion=2>.
      - It's less clear (to me) to what degree Contentious Topics exists as a concept on other language editions and how they track it.
    - In theory, we could do other topic-specific exclusions by choosing specific categories to exclude or use LiftWing model outputs as well. I know NSFW-related content has come up in discussions as one potential example here (though I don't know of any categories that would necessarily help with that and we don't currently have a ML model for it).
  - Editor-based features:
    - I won't go into detail here but we've limited actions based on edit-count, whether an editor is part of a particular user group, and how many other actions they've already taken in a given day (so they don't overuse a particular recommendation feature).
    - Edit-based features:
      - Much more model-specific but obviously Edit Check decides when to trigger based upon what content is being added. If a model is related to post-edit moderation, we could also filter edit recommendations based on e.g., revert-risk score for the edit.

## Papers

- Efficiency of LLMs in Identifying Abusive Language Online: A Comparative Study of LSTM, BERT, and GPT | Proceedings of the 2024 Conference on Human Centred Artificial Intelligence - Education and Practice <https://dl.acm.org/doi/abs/10.1145/3701268.3701269>
- A survey of textual cyber abuse detection using cutting-edge language models and large language models <https://arxiv.org/pdf/2501.05443>
- Seeing Like an AI: How LLMs Apply (and Misapply) Wikipedia Neutrality Norms <https://arxiv.org/abs/2407.04183>
