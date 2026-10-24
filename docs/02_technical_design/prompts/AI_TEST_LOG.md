# AI test log (as of 21 Oct 2026)

## Provider limits seen in Google AI Studio (user account, free tier)
| Model group | Requests/min | Tokens/min | Requests/day |
|---|---|---|---|
| Gemini 3.5 Flash Lite, Gemini 3.1 Flash Lite | 15 | 250K | **500** |
| Gemini 2.5 Flash Lite | 10 | 250K | 20 |
| Gemini 3 / 3.6 / 3.7 / 3.8 Flash, 2.5 Flash | 5 | 250K | 20 |
| Gemma 4 26B / 31B | 30 | 16K | 14,400 |
| Pro models, Gemini 2 Flash / Flash Lite | 0 | 0 | 0 (not available on the free tier) |
Limits are per model and per project and can change without notice. Take a dated screenshot for the report.

## Run 1 (10 single words), Gemini 3.8 Flash, earlier prompt (simple_explanation, 3 distractors, no answer_in_example_1)
- JSON valid; translations and explanations looked correct (not yet rated by two raters).
- Distractors too easy (melts, escapes, swims) and repeated between items (melt, boil, bark, wooden, polite).
- Time and tokens not recorded.

## Run 2 (10 phrases: give up ... once in a blue moon), Gemini 3.8 Flash, prompt v2 (long, with answer_in_example_1)
- Time **1 min 55 s**; tokens: input 1,210, output **11,562**, total 12,772.
- The visible JSON is about 2,000-2,500 tokens, so roughly 9,000 output tokens are probably hidden "thinking" tokens (to verify; set thinking to minimal/low and compare).
- JSON valid, all fields present, translations mostly natural. Weak spots: "natolknut'sya" is stiff (better "natknut'sya"); "a blessing in disguise" definition starts with "To be"; example translation "Losing that flight" -> "opozdanie" shifts the meaning.
- Distractors that may also be correct: "call off" (carry out tests), "point out" (figure out the rules), "on the spur of the moment" (once in a blue moon), "looked after" / "waited for" (come across). About 3-4 of 10 sets are risky.
- Prompt v2 dropped `simple_explanation` and made `context_meaning` generic, so "meaning in context" (FR-14, Objective 6) is weakened. Prompt v3 restores both fields.
- Prompt v2 repeats rules twice and asks the model to "check before responding" (encourages long thinking). Prompt v3 is shorter.

## Next tests
1. Gemini 3.5 Flash Lite, thinking minimal/low/off, temperature 0.2-0.4, structured output (response_schema.json), prompt v3, 10 items, Russian. Record time (target <= 15 s), input/output tokens, valid JSON.
2. Same on Gemini 3.1 Flash Lite (backup, separate quota).
3. 30 items in Russian and in Kazakh; a native speaker rates 1/0 per item; compute % correct in context (targets: RU >= 85%, KZ >= 70%).
4. Quality reference: one regular Flash model on 10 items only (20 requests/day).
5. Optional fallback providers: Groq, OpenRouter (:free models), Mistral Free mode; check JSON validity and Kazakh quality.
6. Record results in docs/02_technical_design/calibration/calibration-results.md and decide the final limits.


## Calibration runs 21-22 Oct 2026 (14 runs, all valid JSON)
| Test | Date | Model | Items | Time (s) | Output tokens | Correct (of 10) |
|---|---|---|---|---|---|---|
| RU-1..5 | 21.10 | Gemini 3.8 Flash | 10/20/30/40/50 | 78.3 / 106.4 / 147.2 / 208.8 / 90.8 | 10,643 / 17,638 / 27,580 / 32,106 / 12,846 | 8.5 / 8.5 / 8.5 / 8.3 / 8.7 |
| KZ-1..5 | 21.10 | Gemini 3.8 Flash | 10/20/30/40/50 | 77.8 / 34.5 / 190.1 / 72.5 / 97.4 | 10,847 / 5,281 / 26,042 / 9,637 / 13,396 | 9 / 8.5 / 8.4 / 9 / 8 |
| L-RU-1, L-RU-2 | 22.10 | Gemini 3.5 Flash-Lite | 10 / 50 | 23.7 / 43.3 | 2,340 / 9,259 | 8.5 / 9 |
| L-KZ-1, L-KZ-2 | 22.10 | Gemini 3.5 Flash-Lite | 10 / 50 | 7.6 / 42.9 | 2,854 / 12,871 | 8.5 / 9 |
Findings: time is proportional to output tokens (~130-190 tokens/s); regular Flash spends most tokens on hidden reasoning; Flash-Lite is faster with the same quality and has 500 requests/day (Flash: 20). Decision: Flash-Lite 3.5 primary, 3.1 backup, batches of up to 25 (not yet run: 2 control runs). Distractors: some too easy or overlapping in meaning. The $ shown in AI Studio is only an estimate for paid API use.
