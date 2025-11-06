# Link Recommendation

## Problem

- Want to avoid ML techniques like embedding since they dont scale for smaller languages. Embedding does not work well with high morphology languages
- Want an extremely fast, deterministic Algorithm
- Linkability is defined as any text that human contributors already used as anchor or label

## Algorithm

### Dataset

- publish bloom dataset for all wikis.
- For every wiki, parse all articles, find label, link for all links and create a dataset. Call it anchor dictionary.
- For an article , Get wikitext, full context. Parse and identify wiki links. - Existing links in it.
- For the section, do an ngram lookup(n<=3, configurable) in bloom filter of all links, link labels
  - Sentencex should support wikitext
- Tree sitter based link addition
