# Supplemental Table

**Table 1.** Prompts in question generation, scoring and tagging pipelines emphasize interpretation, clinical reasoning, and integration of multiple imaging findings.

| **Task** | **Prompt** |
|----------|------------|
| **Question Generation** | Generate high-level clinical questions about chest X-rays that require integration of multiple findings, beyond simple pattern matching.<br><br>Example: *“List all indwelling tubes and lines visible on this frontal chest radiograph. Describe any evidence of complications related to each of them (e.g., malpositioning, pneumothorax or mediastinal emphysema). Box and label all findings. If there are no complications, say so.”* |
| **Question Scoring** | You are a clinical radiologist evaluating the quality of high-level questions about chest X-rays. For each question, reason about the question and then provide a score for each criterion based on a Likert scale (1–5), along with a brief justification.<br><br>**The scoring system is defined as follows:**<br>• 1: Strongly disagree<br>• 2: Disagree<br>• 3: Neutral<br>• 4: Agree<br>• 5: Strongly agree<br><br>**The metrics being evaluated are:**<br>• Clinical relevance<br>• Answerability from image<br>• Complexity/Reasoning<br>• Clarity/Precision<br>• Risk flag<br><br>**Format:**<br><br>```text
Scores:
- Clinical relevance: 5 - justification
- Answerability: 3 - justification
…
- Risk flag: No
Conclusion: 13
Question: {question} |
| Question Tagging | You are a classifier for high-level chest X-ray questions. For each question, assign it to these dimensions:<br>tag_anatomical_region, tag_pathology_type, tag_imaging_finding, tag_laterality, tag_diagnostic_intent, tag_temporal_context, tag_question_type, tag_subtype<br><br>List all plausible values separated by “–”. If more than four distinct values are plausible, use “Multiple”. Always output all eight dimensions, even if the answer is “None” or “Multiple.”<br><br>Format:<br><br>```text

tag_anatomical_region: Lung fields - Pleura

tag_pathology_type: Pneumonia
…

tag_subtype: Descriptive
|
