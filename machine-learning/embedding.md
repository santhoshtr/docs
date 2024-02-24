
* A Visual Guide to FastText Word Embeddings  https://amitness.com/2020/06/fasttext-embeddings/
* What Is FastText? Compared To Word2Vec & GloVe [How To Tutorial In Python] https://spotintelligence.com/2023/12/05/fasttext/


## Morphology and word embeddings

### Morphological Word-Embeddings 

https://aclanthology.org/N15-1140.pdf 

Linguistic similarity is multi-faceted. For instance, two words may be similar with respect to semantics, syntax, or morphology inter alia. Continuous word-embeddings have been shown to capture most of these shades of similarity to some degree. This work considers guiding word-embeddings with morphologically annotated data, a form of semi-
supervised learning, encouraging the vectors to encode a word’s morphology, i.e., words close in the embedded space share morphological features. We extend the log-bilinear model to this end and show that indeed our learned embeddings achieve this, using German as a case study.

### Improve word embedding using both writing and pronunciation

https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0208785

 this paper proposes the concept of a pronunciation-enhanced word embedding model (PWE) that integrates speech information into training to fully apply the roles of both speech and writing to meaning. This paper uses the Chinese language, English language and Spanish language as examples and presents several models that integrate word pronunciation characteristics into word embedding. Word similarity and text classification experiments show that the PWE outperforms the baseline model that does not include speech information. Language is a storehouse of sound-images; therefore, the PWE can be applied to most languages.


### Word Ordering: Two/Too Simple Adaptations of Word2Vec for Syntax Problems

https://aclanthology.org/N15-1142/

We present two simple modifications to the
models in the popular Word2Vec tool, in order to generate embeddings more suited to tasks involving syntax. The main issue with
the original models is the fact that they are
insensitive to word order. While order independence is useful for inducing semantic representations, this leads to suboptimal results when they are used to solve syntax-based
problems. We show improvements in part-of-speech tagging and dependency parsing using our proposed models


## Compositional Morphology for Word Representations and Language Modelling 

https://proceedings.mlr.press/v32/botha14.html

References:

* What are embeddings? https://vickiboykis.com/what_are_embeddings/next.html https://raw.githubusercontent.com/veekaybee/what_are_embeddings/main/embeddings.pdf