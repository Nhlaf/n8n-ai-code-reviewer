# AI Code Reviewer Agent — n8n

An AI-powered Java code review workflow built with n8n, Groq, and email automation. The project analyzes Java source code and generates a structured review with code-quality scores, actionable recommendations, and an overall assessment.

## Project Overview

The AI Code Reviewer Agent automates part of the software code review process. It retrieves Java source code, passes it to a large language model for analysis, and emails the generated review to the configured recipient.

The goal is to demonstrate how AI and workflow automation can support software development and improve code review efficiency.

## Features

- **Form-based input:** Collects a GitHub Java file URL.
- **HTTP requests:** Retrieves source code from a configured URL.
- **AI-powered code analysis:** Uses a Groq-hosted language model through an n8n LLM chain.
- **Five code-quality criteria:** Evaluates readability, efficiency, error handling, maintainability, and Java best practices.
- **Scoring:** Requests individual scores out of 20 and an overall score out of 100.
- **Actionable recommendations:** Generates suggested improvements and a review summary.
- **Email integration:** Sends the generated review to a configured recipient.

## Workflow

1. The user submits the form.
2. The HTTP Request node retrieves the Java source code.
3. The LLM chain passes the code and review instructions to the language model.
4. The model generates a structured code review.
5. The email node sends the review to the configured recipient.

## Technologies Used

- n8n — Workflow automation
- Groq — Language model inference
- Large Language Models (LLMs) — Code analysis and feedback generation
- HTTP Request — Source-code retrieval
- Email/SMTP — Review delivery
- JSON — Workflow export and sharing

## Screenshots
-n8n:
<img width="1601" height="816" alt="Screenshot 2026-10-28 211049" src="https://github.com/user-attachments/assets/95e13f28-e7dc-49cf-8e26-50f744aa4e40" />

-email:
<img width="1491" height="606" alt="Screenshot 2026-10-28 215050" src="https://github.com/user-attachments/assets/951e0345-685a-4174-8a02-12c571ab0a77" />


## Code Review Criteria

| Criterion | Maximum score |
|---|---:|
| Code Readability | 20 |
| Code Efficiency | 20 |
| Error Handling | 20 |
| Maintainability | 20 |
| Best Practices & Standards | 20 |
| **Total** | **100** |

The scores and recommendations are AI-generated and should be validated by a developer before being used in a formal code review.

## Repository Structure

```text
n8n-ai-code-reviewer/
├── workflows/
│   └── ai-code-reviewer.json
├── screenshots/
└── README.md
```

## Prerequisites

- An n8n instance
- A Groq API key
- An SMTP account or compatible email service
- Access to the Java source code being reviewed

## Setup Instructions

1. Clone or download this repository.
2. Open your n8n instance.
3. Import `workflows/ai-code-reviewer.json`.
4. Configure the Groq credentials in n8n.
5. Configure the SMTP credentials and recipient email.
6. Verify the HTTP Request URL and ensure it retrieves the intended Java source code.
7. Test the workflow with a Java file you are authorized to access.
8. Review the execution results and confirm that the email is delivered.

**Important:** The current workflow export uses a configured source URL. Configure the HTTP Request node to use the submitted form value if you want users to select different files dynamically. Validate submitted URLs before making requests.

## Security Considerations

- Never commit API keys, SMTP passwords, access tokens, or private credentials.
- Keep credentials in n8n's credential manager.
- Review exported workflow JSON before publishing it.
- Restrict URL inputs to approved GitHub raw-content URLs to reduce server-side request forgery (SSRF) risks.
- Do not submit proprietary or confidential source code to an external AI provider without authorization.

## Limitations

- AI-generated scores are subjective and may vary between runs.
- The workflow does not replace human code review, testing, static analysis, or security scanning.
- The current HTTP Request configuration must be updated to support dynamic form URLs.
- The email recipient and SMTP configuration must be configured for your own environment.

## Future Improvements

- Support dynamic GitHub raw file URLs with validation.
- Add support for additional programming languages.
- Generate more structured review reports.
- Add automated tests and static-analysis integrations.
- Introduce a human approval step before distributing reviews.

## Disclaimer

This project is intended for learning and demonstration purposes. AI-generated feedback may be incomplete or incorrect and should not be treated as a guarantee of code quality or security.
