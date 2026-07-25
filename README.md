# docx-to-kimi-prompt

Convert academic case report DOCX content into a structured **Kimi Slides** markdown prompt.

## Format

Output: 22–24 slides, 4-section structure:

| Section | Slides | Content |
|---------|--------|---------|
| **Pendahuluan** | 2 | Title + Prolog/Teaser |
| **Case Illustration** | 3–4 | Patient journey, diagnostics, pacing response |
| **Discussion** | 13–15 | Disease basics, hemodynamics, core topic, guidelines |
| **Summary** | 2 | Key takeaways + References |

## Usage

1. Load the **docx-to-kimi-prompt** skill in Hermes Agent
2. Provide your case report DOCX or markdown file
3. The agent extracts data and produces a ready-to-paste Kimi prompt
4. Paste into Kimi → **Adaptive mode → Academic Research**

## Example

See [SKILL.md](./SKILL.md) for full workflow, pitfalls, and verification checklist.

Built for clinical case reports in cardiology — adaptable to any medical/scientific topic.
