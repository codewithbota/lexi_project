# AI calibration results

Date: 21-22 October 2026 · Tester: Akbota Karimolda · Google AI Studio, free tier · prompt v3 (`../prompts/`) · output as JSON with a schema

## 1. Limits shown in AI Studio
| Model | Requests per minute | Tokens per minute | Requests per day |
|---|---|---|---|
| Gemini 3.5 Flash-Lite | 15 | 250K | 500 |
| Gemini 3.8 Flash | 5 | 250K | 20 |
| Gemma 4 (26B / 31B) | 30 | 16K | 14,400 |
Limits are per model and per project and can change without notice, so we check them again before each submission.

## 2. Runs (14 in total, all returned valid JSON)
| Test | Model | Items | Time (s) | Output tokens | Correct in context (average of 10) |
|---|---|---|---|---|---|
| RU-1 to RU-5 | Gemini 3.8 Flash | 10 / 20 / 30 / 40 / 50 | 78.3 / 106.4 / 147.2 / 208.8 / 90.8 | 10,643 / 17,638 / 27,580 / 32,106 / 12,846 | 8.5 / 8.5 / 8.5 / 8.3 / 8.7 |
| KZ-1 to KZ-5 | Gemini 3.8 Flash | 10 / 20 / 30 / 40 / 50 | 77.8 / 34.5 / 190.1 / 72.5 / 97.4 | 10,847 / 5,281 / 26,042 / 9,637 / 13,396 | 9 / 8.5 / 8.4 / 9 / 8 |
| L-RU-1, L-RU-2 | Gemini 3.5 Flash-Lite | 10 / 50 | 23.7 / 43.3 | 2,340 / 9,259 | 8.5 / 9 |
| L-KZ-1, L-KZ-2 | Gemini 3.5 Flash-Lite | 10 / 50 | 7.6 / 42.9 | 2,854 / 12,871 | 8.5 / 9 |

The correct-in-context score is our own rating of 10 items per run. A rating by a native speaker is planned (section 5).

## 3. What we learned
- Time grows with the number of output tokens (about 130-190 tokens per second).
- The regular Flash model spends most of its tokens on hidden reasoning, so it is slow (up to 208 s for 40 items). Flash-Lite gives about the same quality in 8-43 s.
- Flash-Lite allows 500 requests per day, the regular Flash only 20.
- Some distractors in the "Insert a word" exercise were too easy or too close in meaning. The code must check the distractors and replace bad sets.
- The dollar amount in AI Studio is only an estimate for the paid API. Our API key belongs to a project without billing, so a limit gives an error and never a charge.

## 4. Decisions
| Question | Decision | Why |
|---|---|---|
| Primary model | Gemini 3.5 Flash-Lite | same quality, faster, 500 requests per day |
| Backup model | Gemini 3.8 Flash | own quota; slower and only 20 requests per day, so it is used only if the primary fails; batches of 10 items for it |
| Batch size | up to 25 items | 10 items take 8-24 s and 50 items about 43 s; a bigger batch means fewer requests per day |
| Text limit | 60,000 characters | a 30-page document is about 54,000 characters |
| PDF limit | 10 MB and 30 pages | a 30-page article usually weighs 1-10 MB |
| Items per lesson | 50 | keeps a lesson within 4 minutes |
| Items per user per day | 150 | with 10-15 test users it stays far below the 500 requests per day |


