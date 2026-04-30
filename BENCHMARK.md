# Cassotis Long Sentence Corpus Benchmark

The Cassotis Long Sentence Corpus Benchmark is used to track long-sentence Pinyin decoding quality across releases. It is intended to make release quality measurable instead of relying only on hand-picked example sentences.

## Corpus Source

The current corpus is derived from the developer's own novel, **Eternal Dance** (Chinese title: **永恒的舞动**):

https://www.qidian.com/book/1037259117/

The benchmark extracts Chinese sentences from the corpus and converts each sentence to Pinyin before feeding it to the IME engine.

## Method

- Split text by punctuation and line breaks.
- Ignore sentences containing English letters.
- Ignore sentences shorter than the configured minimum CJK length.
- Convert each sentence to Pinyin with the benchmark reverse-Pinyin builder.
- Generate IME candidates using the current engine and dictionary.
- Count a sentence as `Top1` pass if the first candidate exactly matches the original sentence.
- Count a sentence as `Top2` pass if either of the first two candidates exactly matches the original sentence.

The current public comparison uses the first 100 eligible sentences. Future releases are expected to increase the number of benchmark sentences.

## Input Modes

- `Whole-sentence direct`: the full Pinyin string is set on the engine at once. This mainly measures full long-sentence decoding quality.
- `Incremental input`: the Pinyin string is typed key by key. This is closer to real typing and includes per-key candidate generation and cache behavior.

## Latency Metrics

- `Average`: mean latency across processed sentences.
- `P95`: 95th-percentile latency. In a 100-sentence run, about 95 sentences finish no slower than this value.
- `Max`: the slowest sentence in the run.

## Result Publication

Version-specific benchmark results are published in `README.md`. This document defines the benchmark methodology and metric meanings.

## Notes

The benchmark is expected to evolve with the IME. The number of corpus sentences, dictionary version, test runner behavior, and input mode should be recorded with every published result so that future comparisons remain interpretable.
