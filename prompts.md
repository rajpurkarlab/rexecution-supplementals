# Supplementary Table 2

**Prompts in question generation, scoring and tagging pipelines emphasize interpretation, clinical reasoning, and integration of multiple imaging findings.**

<table>
  <thead>
    <tr>
      <th>Task</th>
      <th>Prompt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Question Generation</strong></td>
      <td>
        Generate high-level clinical questions about chest X-rays that require integration of multiple findings, beyond simple pattern matching.
        <br><br>
        <em>Example:</em> “List all indwelling tubes and lines visible on this frontal chest radiograph. Describe any evidence of complications related to each of them (e.g., malpositioning, pneumothorax or mediastinal emphysema). Box and label all findings. If there are no complications, say so.”
      </td>
    </tr>

    <tr>
      <td><strong>Question Scoring</strong></td>
      <td>
        You are a clinical radiologist evaluating the quality of high-level questions about chest X-rays. For each question, reason about the question and then provide a score for each criterion based on a Likert scale (1–5), along with a brief justification.
        <br><br>
        <strong>The scoring system is defined as follows:</strong>
        <ul>
          <li>1: Strongly disagree</li>
          <li>2: Disagree</li>
          <li>3: Neutral</li>
          <li>4: Agree</li>
          <li>5: Strongly agree</li>
        </ul>
        <strong>The metrics being evaluated are:</strong>
        <ul>
          <li>Clinical relevance</li>
          <li>Answerability from image</li>
          <li>Complexity/Reasoning</li>
          <li>Clarity/Precision</li>
          <li>Risk flag</li>
        </ul>
        <strong>Format:</strong>
        <pre>Scores:
- Clinical relevance: 5 - justification
- Answerability: 3 - justification
…
- Risk flag: No
Conclusion: 13
</pre>
        Question: {question}
      </td>
    </tr>

    <tr>
      <td><strong>Question Tagging</strong></td>
      <td>
        You are a classifier for high-level chest X-ray questions. For each question, assign it to these dimensions:
        <br>
        <code>tag_anatomical_region, tag_pathology_type, tag_imaging_finding, tag_laterality, tag_diagnostic_intent, tag_temporal_context, tag_question_type, tag_subtype</code>
        <br><br>
        List all plausible values separated by “–”. If more than four distinct values are plausible, use “Multiple”. Always output all eight dimensions, even if the answer is “None” or “Multiple.”
        <br><br>
        <strong>Format:</strong>
        <pre>- tag_anatomical_region: Lung fields - Pleura
- tag_pathology_type: Pneumonia
…
- tag_subtype: Descriptive
</pre>
      </td>
    </tr>
  </tbody>
</table>
