# Technical design (Akbota Karimolda)

| File / folder | Content |
|---|---|
| `Lexi_Akbota_Technical_Design.docx` | the main document: technology comparison with weighted scores, 36 functional (20 Must, 11 Should, 5 Could) and 13 non-functional requirements, architecture, data model, AI workflow, verification and evaluation plan (12 metrics, 35 test cases), failure handling, work plan |
| `calibration/calibration-results.md` | results of the AI test (14 runs, 21-22 October 2026) and the decisions about models and limits |
| `prompts/` | the AI prompt (v3), the JSON schema of the response, an example request, and the AI test log |

## Main decisions
- Mobile app: React Native + Expo (score 4.55 against Flutter 3.90)
- Backend: Supabase (login, PostgreSQL, Edge Functions); the Gemini key is kept only on the server
- AI: Gemini 3.5 Flash-Lite as the primary model, Gemini 3.8 Flash as the backup
- Limits: text up to 60,000 characters (about 30 pages), PDF up to 10 MB and 30 pages, up to 50 items in one lesson, batches of up to 25 items, 150 items per user per day

The limits are initial values. We check them on the prototype and change them if the measurements require it.
