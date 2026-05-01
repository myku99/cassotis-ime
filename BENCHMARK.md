# Cassotis Long Sentence Corpus Benchmark-16300

The Cassotis Long Sentence Corpus Benchmark-16300 tracks long-sentence Pinyin decoding quality across releases. It is intended to make release quality measurable instead of relying only on hand-picked example sentences.

## Corpus Source

The corpus is derived from the developer's own novel, [**Elegance in Timelessness**](https://www.qidian.com/book/1037259117/) (Chinese title: [**永恒的舞动**](https://www.qidian.com/book/1037259117/)):

The benchmark extracts eligible Chinese sentences from the corpus and converts each sentence to Pinyin before feeding it to the IME engine.

## Corpus Scale

Benchmark-16300 currently contains 16,300 eligible sentences.

Future benchmark variants may use larger or different corpus sets, but their names should include the corpus size or another clear suffix so results remain comparable.

## Method

- Split text by punctuation and line breaks.
- Ignore sentences containing English letters.
- Ignore sentences shorter than the configured minimum CJK length.
- Convert each sentence to Pinyin with the benchmark reverse-Pinyin builder.
- Generate IME candidates using the engine and dictionary under test.
- Count a sentence as `Top1` pass if the first candidate exactly matches the original sentence.
- Count a sentence as `Top2` pass if either of the first two candidates exactly matches the original sentence.

## Result Publication

Version-specific Benchmark-16300 results are published in `README.md`. This document defines the corpus source, scale, and scoring method.

## Notes

The benchmark is expected to evolve with the IME. Every published result should record the corpus size, dictionary version, test runner behavior, and scoring method so future comparisons remain interpretable.
