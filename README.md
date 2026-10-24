# Lexi

**Kazakh:** Мәтіндерді оқу негізінде ағылшын тілінің лексикасын үйренуге арналған жасанды интеллектті қолданатын мобильді қосымшаны әзірлеу.
**English:** Development of an AI-Powered Mobile Application for English Vocabulary Learning Based on Text Reading.
**Russian:** Разработка мобильного приложения с использованием искусственного интеллекта для изучения английской лексики на основе чтения текстов.

> Status: documentation and design stage (Pre-Defense 1). No application code yet.

## Overview
Lexi helps learners build English vocabulary while reading. Users read articles from a built-in library or add their own text (paste or PDF), highlight unknown words and phrases, and get AI-generated notes: translation (Kazakh or Russian), a simple explanation, the meaning in context, and example sentences. Saved words are practised with flashcards, fill-in-the-blank exercises and word matching, scheduled by spaced repetition.

## Planned features
- Article library with categories, sorting and search
- Own material: paste text or upload a PDF (up to 10 MB and 30 pages)
- Reader with word and phrase highlighting in 5 colours
- AI study notes: translation, simple explanation, meaning in context, 2 examples
- Dictionary: history of lessons
- Practice: Flashcards, Insert a word, Match words, spaced repetition (SM-2)
- Profile: interface language (KZ / EN / RU), translation language (KZ / RU), day/night mode, reminders

## Planned technology
React Native + Expo (mobile app), Supabase (auth, PostgreSQL, storage, Edge Functions), Gemini API (AI), WebView reader. The comparison and reasons are in the technical design document.

## Repository structure
```
docs/
  01_research/            Kamila Melsova: sources, literature review, existing apps, research gap
  02_technical_design/    Akbota Karimolda: technology comparison, requirements, architecture, test plan
  03_ux_prototype/        Application screens (PDF); Figma prototype link will be added
  04_project_management/  Project plan, risks, YouTrack task list
  05_supervisor_feedback/ Feedback log
diagrams/                 Editable draw.io files and PNG exports
tests/                    Test plan pointers and (later) test code
config/                   Configuration examples (no secrets)
```

## Documentation index
| Topic | Location |
|---|---|
| Technical design, requirements, test plan | `docs/02_technical_design/Lexi_Akbota_Technical_Design.docx` |
| Diagrams  | `diagrams/*.drawio` (PNG exports next to them) |
| Application screens | `docs/03_ux_prototype/Lexi_app_screens.pdf` |
| Project plan, milestones, risks | `docs/04_project_management/project-plan.md` |
| Tasks | YouTrack project (link below) |

## Links
- YouTrack: https://botanw.youtrack.cloud/projects/LEX
- Figma prototype: https://www.figma.com/proto/Y0s4UHtc7WlxwF1baMRoms/Lexi--clickable-prototype?page-id=0%3A1&node-id=3-196&p=f&viewport=411%2C12%2C0.13&t=jkkvNbntk5feDWzA-1&scaling=min-zoom&content-scaling=fixed

## Team
| Role | Name | GitHub |
|---|---|---|
| Kamila Melsova: research and requirements | Kamila Melsova | KamilaMelsova |
| Akbota Karimolda: technical design and prototype | Akbota Karimolda | codewithbota |
| Supervisor | Zhanna Sadirmekova| |

## Setup (planned)
Application code will be added after Pre-Defense 1. Environment variables will be described in `config/.env.example`. Real keys must never be committed.


