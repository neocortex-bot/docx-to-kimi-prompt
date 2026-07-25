---
name: docx-to-kimi-prompt
description: "Convert academic case report DOCX into a structured Kimi Slides markdown prompt (Adaptive mode, Academic Research). Output: 22-24 slide outline with 4-section format (Pendahuluan, Case Illustration, Discussion, Summary). Bahasa Inggris, bullet points, data-driven."
version: 1.0.0
platforms: [linux]
metadata:
  hermes:
    tags: [kimi, slides, presentation, case-report, academic, cardiology]
    related_skills: [academic-draft-generator, humanize-writing, paper-qa]
triggers:
  - "user asks to create a Kimi Slides prompt from a case report"
  - "user has a DOCX or markdown case report and wants a presentation"
  - "user wants to convert clinical data into a structured academic presentation"
---

# DOCX to Kimi Prompt — Academic Case Report to Kimi Slides

Transform a completed academic case report (DOCX or markdown) into a ready-to-paste Kimi Slides prompt in markdown format. Output is designed for **Adaptive mode to Academic Research** scenario.

## Output Format

The Kimi prompt follows a strict **4-section** structure:

| Section | Slides | Content |
|---------|--------|---------|
| **Pendahuluan** | 2 | Title slide + Prolog/Teaser that hooks the audience and previews the discussion |
| **Case Illustration** | 3-4 | Concise patient journey: profile, diagnostics, hemodynamics, pacing response. Only essential data. |
| **Discussion** | 13-15 | Deep dive: basic disease, comprehensive analysis, core topic, resolution, guidelines. Merges theory with case. |
| **Summary** | 2 | Key takeaways (4 points) + References and Q&A |

## Workflow

### Step 1: Extract Data from DOCX

Read the DOCX or markdown file to extract:

- **Patient demographics**: age, sex, comorbidities, duration
- **Admission data**: vitals, EKG findings, lab results, imaging
- **Hemodynamics**: echo parameters (LVEF, CO, CI, SVR, LVOT VTI, SV)
- **ABG data**: pH, PaO2, PaCO2, SaO2, HCO3, BE, lactate
- **Key lab**: CRP, HbA1c, WBC, eGFR, Na, K
- **Pacing data**: TPM settings, response, rhythm transitions
- **Guidelines applied**: ESC 2021 Pacing, ESC 2024 AF
- **Final plan**: PPM date, medications, multidisciplinary

### Step 2: Map to 4-Section Structure

#### Pendahuluan (2 slides)
1. **Title Slide**: title, authors, affiliation, year
2. **Prolog/Teaser**: clinical snapshot hook + "The Question" + preview of what will be discussed. End with a provocative bottom line.

#### Case Illustration (3-4 slides)
3. **Patient Profile and Admission**: demographics, comorbidities, HPI, admission vitals
4. **Diagnostic Findings**: EKG, lab highlights, imaging, initial diagnosis
5. **Hemodynamics and Pacing Response**: echo, ABG, TPM response, rhythm transitions (AF -> sinus)

#### Discussion (13-15 slides)
Break into 5 sub-sections:

**3.1 Basic Disease: Conduction Disorders (4 slides)**
6. Classification of Bradyarrhythmias (ESC 2021)
7. Sinus Pause, Junctional Escape and First-Degree AVB: applied to case
8. Diabetes and the Conduction System: AGEs, CAN, prevalence data
9. Reversible vs Intrinsic Causes: evaluation table

**3.2 Comprehensive Analysis: Hemodynamics (2 slides)**
10. Oxygen Delivery (DO2) in Low CO States: calculation
11. Compensatory Vasoconstriction: physiology cascade

**3.3 Core Topic: SpO2-SaO2 Discrepancy (5 slides)**
12. How Pulse Oximetry Works: PPG, PI
13. The Discrepancy: our case, evidence
14. Evidence from Literature: Giuliano, Karlsson, Jung
15. Differential Diagnosis: table
16. Role of Diabetic Autonomic Neuropathy (CAN)

**3.4 Resolution: Pacing Response (3 slides)**
17. TPM as Diagnostic and Therapeutic Tool
18. Rhythm Transition: brady to AF to sinus
19. Hemodynamic Comparison: admission vs day 2

**3.5 Management and Guidelines (3 slides)**
20. PPM Indications (ESC 2021)
21. AF Management: CHA2DS2-VA and HAS-BLED (ESC 2024)
22. Final Comprehensive Plan: checklist

#### Summary (2 slides)
23. Key Takeaways (4-5 bullet points + bottom line)
24. References and Q&A

### Step 3: Write the Kimi Prompt

Each slide must contain:
- **Heading** (slide title)
- **Bullet points**: not paragraphs
- **Specific numbers**: no approximations
- **Data tables**: where comparisons are needed
- **Application to case**: for every discussion slide
- **Visual suggestions**: for algorithm figures (e.g., "Visual: Gambar 3.1 from ESC 2021")

Format:
```markdown
### Slide N: Slide Title
- Bullet point with data
- Another bullet
- Visual: description
```

### Step 4: Final Prompt Header

Every Kimi prompt starts with:
```markdown
# KIMI SLIDES PROMPT: ADAPTIVE MODE

Buat presentasi dalam Bahasa Inggris menggunakan mode Adaptive dengan skenario academic research. Judul presentasi:

"[TITLE]"

Total slide: 22-24 slide. Bahasa: English. Gaya: Formal akademik, bullet points bukan paragraf panjang, sertakan angka dan data spesifik.
```

## Pitfalls

### Too Much Data Per Slide
Each slide should have 3-6 bullet points max. Move detailed data to appendix or additional slides. The Kimi Visual mode has template limits: Adaptive mode can handle more text but readability suffers.

### Forgetting the Application-to-Case Hook
Every Discussion slide must tie back to the patient. A slide about CAN without mentioning "DM 15 yrs + HbA1c 9.6% + retinopathy: very high CAN probability" is just a textbook review.

### Prolog Too Vague
The teaser slide must contain: a striking clinical discrepancy (e.g., "SpO2 81% vs SaO2 99.5%"), the explicit question, and a preview sentence. Without this, the audience has no reason to care.

### Missing Guideline Visual References
Kimi can reference uploaded images. Include visual suggestions like "Visual: Gambar 3.1 from ESC 2021 (bradyarrhythmia algorithm)" so the user knows which figures to upload.

### CHA2DS2-VA vs CHA2DS2-VASc
ESC 2024 AF Guidelines use CHA2DS2-VA (without sex category). Double-check which scoring system the document uses.

## Verification Checklist

Before delivering the prompt:
- [ ] Title + authors + affiliation correct
- [ ] Prolog has hook, question, and preview
- [ ] Case illustration: 4 slides max, data-driven
- [ ] Discussion has application-to-case per slide
- [ ] Key references included (max 6 on final slide)
- [ ] All numbers match source document
- [ ] Bottom line / takeaway punchy and memorable
- [ ] Kimi mode specified (Adaptive to Academic Research)
- [ ] Total slide count: 22-24
