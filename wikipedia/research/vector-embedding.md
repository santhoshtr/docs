# Vector embedding

## Notes

June 5 2025: <https://qwenlm.github.io/blog/qwen3-embedding/> announced qwen3 embedding model supporting 100+ languages. They claim the are leading in evaluation dashboards.

It is interesting to note that, as per <https://huggingface.co/Qwen/Qwen3-Embedding-4B> examples, the cosine similarity between

```python
queries = [
    "What is the capital of China?",
    "Explain gravity",
]
documents = [
    "The capital of China is Beijing.",
    "Gravity is a force that attracts two bodies towards each other. It gives weight to physical objects and is responsible for the movement of planets around the sun.",
]
```

is reported as `tensor([[0.7534, 0.1147],      [0.0320, 0.6258]])`

I would say that using such low similarity scores for QA or RAG tasks is very fragile. Proving my argument at <https://thottingal.in/blog/2025/03/14/natural-language-qa-for-wikipedia-and-wikidata/>

## Notebooks

- <https://github.com/pamelafox/vector-embeddings-demos>
- <https://blog.pamelafox.org/2025/05/a-visual-exploration-of-vector.html>
