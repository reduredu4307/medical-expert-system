# Medical Diagnostic Expert System

This project is an educational **rule-based medical diagnostic expert system** built in a Jupyter Notebook. It demonstrates knowledge representation, backward chaining, explanation facilities, automated testing, and simple visualization for a symptom-based diagnostic assistant.

> **Important disclaimer:** This system is for learning and demonstration only. It is not a medical device and must not be used as a substitute for diagnosis or advice from a qualified healthcare professional.

## Project Files

| File | Description |
| --- | --- |
| `Medical_Diagnostic_Expert_System (2).ipynb` | Main uploaded notebook containing the expert system code. |
| `main.tex` | LaTeX project report prepared for the notebook. |
| `main.pdf` | Compiled PDF version of the report. |
| `knowledge_base_overview.png` | Visualization generated from the disease-symptom knowledge base. |

## Main Features

- Represents medical knowledge as disease-to-symptom rules.
- Uses **backward chaining** to test whether selected symptoms prove a target disease.
- Supports diagnosis for all diseases or one selected target disease.
- Shows confirmed diagnoses and close partial matches.
- Provides **HOW explanations** that show the proof trace for a disease.
- Provides **WHY explanations** that list diseases linked to a symptom.
- Includes an interactive Jupyter widget interface.
- Includes an automated test suite with 10 test cases.
- Generates a heatmap and bar chart for knowledge-base coverage.

## Knowledge Base Summary

The notebook contains:

- **12 diseases**: Malaria, Typhoid, Influenza, Tuberculosis, Pneumonia, Dengue, COVID-19, Cholera, Meningitis, Hepatitis B, Diabetes, and Hypertension.
- **40 unique symptom labels**.
- Disease rules that require all listed symptoms to be present before a disease is fully confirmed.
- Partial-match scoring for diseases that share some, but not all, selected symptoms.

## How the System Works

The system uses a simple rule format:

```text
Disease -> required symptoms
```

When the user selects symptoms, the system stores them as Boolean facts:

```text
symptom -> True or False
```

The inference engine then treats each disease as a goal. For each disease, it checks every required symptom. A disease is confirmed only when all required symptoms are present.

Example:

```text
Malaria -> fever, chills, sweating, headache, nausea, muscle_pain
```

If all six symptoms are selected, Malaria is confirmed. If one symptom is missing, Malaria is not confirmed, but it may appear as a partial match.

## Requirements

Use a Python/Jupyter environment with these packages available:

- `ipykernel` or Jupyter Notebook/JupyterLab
- `ipywidgets`
- `numpy`
- `matplotlib`
- `IPython`

The workspace already provides the packages needed for this project. If running on another computer, use a Python environment that includes the packages above.

## How to Run

1. Open the notebook:

   ```bash
   jupyter notebook "Medical_Diagnostic_Expert_System (2).ipynb"
   ```

2. Run the notebook cells in order:

   - Knowledge Base
   - Inference Engine
   - Interactive Diagnosis UI
   - Automated Test Suite
   - Visualisations

3. In the interactive UI:

   - Select symptoms using the checkboxes.
   - Choose `All diseases` or a specific target disease.
   - Click `Run Diagnosis`.
   - Review confirmed diagnoses and close partial matches.
   - Use the HOW dropdown to view explanation traces.
   - Click `Reset` to clear the session.

## Expected Startup Messages

After running the first two code cells, the notebook should print:

```text
Knowledge base loaded: 12 diseases, 40 symptoms.
InferenceEngine class defined.
```

## Running the Tests

Run the automated test suite cell after running the knowledge base and inference engine cells.

Expected result:

```text
Medical Diagnostic Expert System — Test Suite
-------------------------------------------------------
Results: 10 passed, 0 failed out of 10 tests.
```

The tests cover:

- Full disease confirmation.
- Missing-symptom rejection.
- No-symptom behavior.
- Multiple simultaneous diagnoses.
- Partial-match counting.
- HOW explanation output.
- WHY explanation output.
- Reset behavior.

## Example Inputs and Outputs

### Example 1: Confirmed Malaria

Input symptoms:

```text
Fever, chills, sweating, headache, nausea, muscle pain
```

Expected output:

```text
Malaria confirmed
```

### Example 2: Partial Malaria Match

Input symptoms:

```text
Fever, sweating, headache, nausea, muscle pain
```

Expected output:

```text
Malaria is not fully confirmed, but appears as a close partial match.
```

### Example 3: No Diagnosis

Input symptoms:

```text
No symptoms selected
```

Expected output:

```text
No disease fully confirmed based on reported symptoms.
```

## Code Structure

The notebook is organized into five main parts:

1. **Knowledge Base**
   - Defines `DISEASE_RULES`.
   - Defines `SYMPTOM_LABELS`.

2. **Inference Engine**
   - Defines the `InferenceEngine` class.
   - Stores facts, proof traces, confirmed matches, and partial matches.
   - Implements `diagnose()`, `_prove_goal()`, `_check_symptom()`, `explain_how()`, `explain_why()`, and `reset()`.

3. **Interactive UI**
   - Uses `ipywidgets` checkboxes, buttons, and dropdowns.
   - Collects user-selected symptoms.
   - Displays confirmed and partial results.

4. **Automated Test Suite**
   - Uses direct fact injection.
   - Runs 10 assertion-based test cases.

5. **Visualisations**
   - Builds a binary disease-symptom matrix.
   - Generates a symptom-disease heatmap.
   - Generates a required-symptom count chart.

## Confidence Claim

The project has **high implementation confidence** for the tested scenarios because all 10 automated tests pass. This means the rule engine, partial-match tracking, explanation output, and reset behavior work as expected in the notebook tests.

This confidence does **not** mean the system is clinically validated. The rules are simplified for an artificial intelligence coursework prototype and should be reviewed by medical experts before any real-world use.

## Future Improvements

Possible extensions include:

- Add confidence factors or weighted symptoms.
- Represent unknown symptoms separately from negative symptoms.
- Ask follow-up questions dynamically.
- Expand the disease and symptom knowledge base.
- Validate rules against expert-reviewed clinical sources.
- Convert the notebook interface into a web application.
- Add exportable diagnosis reports.

## Author and Course

**Author:** Rediet Samuel  
**ID:** MTUPR/2032/18  
**Course:** MSIT5205 – Advanced Artificial Intelligence  
**Track:** B – Knowledge Representation