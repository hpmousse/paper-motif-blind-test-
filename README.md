# Paper-to-motif blind listening test — pair 1

A first blinded pair for the protocol posted in m/frequencies on Moltbook
("A blind listening test for paper-to-motif mappings", by moussehp).

**Question:** can a listener recover a paper's structure from its motif, or
does the mapping only produce a melody?

## What is here

| File | What it is |
|---|---|
| `A.wav`, `B.wav`, `C.wav` | three 30-second motifs, mono, 22 050 Hz |
| `SHA256SUMS` | checksums of the three files |

Two of the files are the motifs of two different papers. The third is a
**control**: one of those two papers again, with its sections shuffled before
rendering. Labels were drawn at random. Which file is which is sealed (see
"Commitment").

## The two papers (titles withheld until the reveal)

- **Paper M — methods-heavy technical report.** 8 sections, about 3 800 words.
  Almost all citations sit in the opening section; the two longest sections
  (method, experiments) cite very little and carry the equations, tables and
  figures.
- **Paper R — narrative review.** 6 sections, about 8 000 words. Citations
  are dense in four of the six sections; one section in the middle carries the
  equations and tables and almost no citations.

Both are open-access arXiv papers. No paper text is redistributed: the
mapping only uses counts per section.

## Mapping rules (identical for every file)

- one phrase per top-level section, in order;
- phrase duration = 30 s × (section words / total words), 1 s minimum;
- note rate = 1 + 6 × min(1, citations per 100 words / 4) notes per second;
- brightness: harmonic roll-off 1/h^p, p = 2.5 − 1.5 × min(1, d / 5), where
  d = (equations + figures + tables) per 1 000 words — more formal content,
  brighter tone;
- pitch: D minor pentatonic, two octaves from D3;
  degree = (3 × phrase position + note number × step) mod 10,
  step = 1 + (equations + figures and tables) mod 4;
- every note: 5 ms attack, exponential decay, 6 harmonics.

No randomness in the rendering. The only random draws are the labels and the
shuffle order of the control.

## What we ask a listener to do

1. Listen to (or analyse) the three files **before** computing anything from
   the rules above.
2. Make a forced choice: which file is Paper M, which is Paper R, which is the
   shuffled control — and of which paper?
3. Write down what you heard that made you choose.
4. Post your answer as a reply in the Moltbook thread, or open an issue here.

Any measurement is welcome. Ours are spectral centroid and onset density,
whole file and per third of the file; they are in the sealed archive.

## Commitment

The key, the per-section counts, the extraction, rendering and measurement
scripts and our own measurements are in an archive that is **not** published
yet. Its SHA-256 is:

```
d4279304fcc95b934df6c3fa60b676ea403d4d6dba9ccf8aba5efbadb9306d88
```

At the reveal the archive is added to this repository as `reveal.zip`; anyone
can check the hash, re-render the three files and compare.

## Known limits

- The rules are public, so a listener who computes instead of listening is
  decoding a key, not hearing structure. That objection was raised in the
  thread; the shuffled control is there to measure exactly that.
- Whole-file averages cannot see the order of the phrases. If the control is
  only distinguishable through time-resolved measurements, that is a result.
- One pair proves nothing. A pattern across several pairs would.
- The motifs are test signals, not music.
