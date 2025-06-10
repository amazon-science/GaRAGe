## GaRAGe

### A Benchmark with Grounding Annotations for RAG Evaluation

This repository contains the data for the paper (ACL 2025 Findings): [GaRAGe: A Benchmark with Grounding Annotations for RAG Evaluation](https://arxiv.org/abs/2506.07671).

GaRAGe is a large RAG benchmark with human-curated long-form answers and annotations of each grounding passage, allowing a fine-grained evaluation of whether LLMs can identify relevant grounding when generating RAG answers. This benchmark contains 2366 questions of diverse complexity, dynamism, and topics, and includes over 35K annotated passages retrieved from both private document sets and the Web, to reflect real-world RAG use cases. This makes it an ideal test bed to evaluate an LLM's ability to identify only the relevant information necessary to compose a response, or provide a deflective response when there is insufficient information. 

## Data Format

Each entry in the [GaRAGe dataset](data/GaRAGe_benchmark.jsonl) is a JSON object containing the following fields: `sample_id`, `question_date`, `grounding`, `question`, `question_valid`, `question_false_premise`, `question_seeking`, `question_sensitive`, `question_type`, `question_complexity`, `question_category`, `question_popularity`, `evidence_relevant`, `evidence_correct`, `answer_generate`, `answer_related_info`, `answer_validate`, `comments`, `evidence_cited`, `question_tag` and `topic_tag`.  Each field is explained below:

- sample_id: an unique identifier of the datapoint.
- question_date: the timestamp of the question.
- grounding: a list of passages. For each passage, we provide the text prefixed by a citation marker, the age of the passage, the date of the passage and the provider (either web or ent).
- question: the question for the current datapoint.
- question_valid: wether the question is valid or not. A valid question is understandable, complete, answerable, not harmful or about sensitive topics.
- question_false_premise: wether the question is false premise or not.
- question_seeking: if the question is information seeking or not.
- question_sensitive: whether the question is time sensitive or not.
- question_type: in case the question is time-sensitive, whether it is Slow-Changing or Fast-Changing.
- question_complexity: reflects the complexity of the question among the dimensions: Simple, Simple w. condition, Set, Comparison, Aggregation, Multi-Hop, Post-processing heavy.
- question_category: the domain of the question chosen from a list of 25 domains: Science, Finance, Health, Travel, Sports, etc.
- question_popularity: the popularity of the subject addressed by the question between: Head, Torso and Tail.
- evidence_relevant: it contains a list of tags of YES/NO, signalling the relevancy of each passage from grounding.
- evidence_correct: it contains a list of tags of ANSWER-THE-QUESTION/RELATED-INFORMATION/UNKNOWN for each passage from grounding.
- answer_generate: a human-written answer to the question, using the ANSWER-THE-QUESTION passages.
- related_info: a revised version of answer_generate, with additional related information which might be interesting to the topic of the question.
- answer_validate: whether the answer was validated by an additional annotator.
- comments: additional annotator comments for the current datapoint.
- evidence_cited: a list of tags signalling if a passage was cited in the written answer.
- question_tag: if the question was generated using web or enterprise paragraphs.
- topic_tag: if the topic used for generating the question was web or enterprise oriented.

## Citation
```
@misc{sorodoc2025garagebenchmarkgroundingannotations,
      title={GaRAGe: A Benchmark with Grounding Annotations for RAG Evaluation}, 
      author={Ionut-Teodor Sorodoc and Leonardo F. R. Ribeiro and Rexhina Blloshmi and Christopher Davis and Adrià de Gispert},
      year={2025},
      eprint={2506.07671},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2506.07671}, 
}
```

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the CC-BY-NC-4.0 License. See the [LICENSE](LICENSE) file.

## Contact

For feedback or questions please contact [Ionut-Teodor Sorodoc](https://sorodoc.github.io/).