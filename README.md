[![Download Releases](https://img.shields.io/badge/Downloads-Releases-blue?logo=github)](https://github.com/Grafello/autojd/releases)

AutoJD — AI Job Email Generator for Faster Applications Now
===========================================================

![Hero image](https://source.unsplash.com/1600x900/?job,email,ai)

Aut oJD (autojd) is an AI-powered tool that generates personalized job application emails in seconds. It helps job seekers compose tailored messages, highlight relevant skills, and match tone to the company. Built with Next.js, TypeScript, Tailwind CSS and OpenAI, AutoJD reduces time spent on applications and improves response rates.

Badges
------
- ![License](https://img.shields.io/badge/license-MIT-green)  
- ![TypeScript](https://img.shields.io/badge/TS-TypeScript-blue)  
- ![Next.js](https://img.shields.io/badge/Framework-Next.js-black)  
- ![OpenAI](https://img.shields.io/badge/AI-OpenAI-purple)  
- Topics: ai • automation • career • job-applications • job-search • nextjs • openai • productivity • tailwindcss • typescript

Quick links
-----------
- Releases (download and run): https://github.com/Grafello/autojd/releases  
  Download the release archive from the Releases page and execute the installer or binary included in that release.
- Source: https://github.com/Grafello/autojd

Key features
------------
- Fast personalized emails: Generate a tailored email in seconds using role, company, and your profile.
- Tone control: Choose formal, friendly, or creative tone.
- Skill matching: AutoJD extracts and highlights the skills that match the job description.
- Templates: Save and reuse templates for different application types.
- Multi-channel export: Copy to clipboard, download as text or PDF, or send via configured SMTP.
- CLI and Web UI: Use a simple command line tool or the web interface built with Next.js.
- Privacy-first: Local caching and optional encryption for stored profiles.

How it works
------------
1. You give AutoJD a job posting link or job description.
2. You provide a short profile or link to your resume.
3. AutoJD parses the job text and maps required skills to your profile.
4. The AI generates multiple email drafts with suggested subject lines and openings.
5. You pick a draft, tweak it, and export or send.

Install (local / production)
----------------------------
1. Download the latest release bundle from the Releases page and run the included installer:
   - Visit: https://github.com/Grafello/autojd/releases
   - Download the archive that matches your OS (autojd-vX.Y.Z-<os>.tar.gz or autojd-vX.Y.Z-<os>.zip).
   - Extract and run the installer or binary inside the archive.
2. Or clone and run from source:

```bash
git clone https://github.com/Grafello/autojd.git
cd autojd
pnpm install
pnpm run build
pnpm run start
```

3. For development:

```bash
pnpm run dev
# then open http://localhost:3000
```

System requirements
-------------------
- Node.js 18+ (for local web UI)
- Yarn or pnpm preferred
- An OpenAI API key for AI features (set in env)
- For CLI-only usage, a compiled binary exists in Releases for macOS, Linux, and Windows.

Configuration
-------------
Set environment variables in a .env file at the project root or system environment:

- OPENAI_API_KEY=<your_api_key>
- NEXT_PUBLIC_APP_NAME=AutoJD
- SMTP_HOST=smtp.example.com
- SMTP_PORT=587
- SMTP_USER=<user>
- SMTP_PASS=<pass>

Example .env:

```env
OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxx
NEXT_PUBLIC_APP_NAME=AutoJD
SMTP_HOST=smtp.mail.example
SMTP_PORT=587
SMTP_USER=me@example.com
SMTP_PASS=supersecret
```

Usage: Web UI
-------------
- Start the app: pnpm run dev
- Open http://localhost:3000
- Fill in the profile section or upload a resume.
- Paste a job description or a job URL.
- Choose tone and length.
- Click Generate.
- Review drafts. Edit and export.

Usage: CLI
---------
Commands follow a small, simple CLI. Examples:

Generate a draft from a job description file:

```bash
autojd generate --job-file ./job.txt --profile ./profile.json --tone friendly --output draft1.txt
```

Generate and send via SMTP:

```bash
autojd send --job-file ./job.txt --profile ./profile.json --to hr@company.com --from me@example.com --subject "Application for Product Designer"
```

Commands
- autojd generate — Produce drafts.
- autojd list-templates — Show saved templates.
- autojd add-template — Save a template.
- autojd send — Send a selected draft via SMTP.
- autojd export — Export to PDF or text.

Examples
--------
1) Generate multiple subject lines:

```bash
autojd generate --job-file ./job.txt --profile ./profile.json --subjects 5
```

2) Quick generate from a URL (web UI or CLI):

- Web: Paste the URL and click generate.
- CLI:

```bash
autojd generate --job-url "https://company.example/careers/1234" --profile ./profile.json
```

Best practices
--------------
- Keep your profile short and factual. Include role, core skills, and recent achievements.
- Provide full job text or a job posting URL. More context yields better drafts.
- Review suggested skills. Remove mismatches to avoid overclaiming.
- Use different tones for different companies. Match the company voice.

Data flow and privacy
---------------------
- Job text and profile data go to the AI provider only when you enable cloud mode.
- For local mode, AutoJD runs model calls through your local agent or a private endpoint.
- You can clear local caches from Settings in the web UI or by removing the .autojd local folder.

Advanced: Templates and variables
---------------------------------
Templates use simple variables:

- {{name}} — your full name
- {{role}} — target role
- {{company}} — company name
- {{skills}} — matched skills

Example template:

"Hi {{hiring_manager}},\n\nI’m {{name}}, a {{role}} with experience in {{skills}}. I’d like to apply to {{company}}."

Integrations
------------
- OpenAI for generation.
- Optional Google Drive export for saved drafts.
- SMTP for direct sending.
- Zapier webhook support for automating job-to-draft flows.

Performance notes
-----------------
- The web UI caches parsed job data to speed repeated requests.
- Large job descriptions may take longer to parse. The UI shows progress.
- Use the CLI for batch generation when processing many jobs.

Troubleshooting
---------------
- If the AI API returns rate-limit errors, reduce concurrency or upgrade your plan.
- If generation fails without a clear message, check OPENAI_API_KEY and network access.
- If SMTP fails, verify host, port, and credentials.

FAQ
---
Q: Can AutoJD apply to jobs automatically?  
A: AutoJD can send email applications via SMTP when you authorize it. It does not apply through proprietary job portals automatically.

Q: Does AutoJD store my resume?  
A: You can opt to store your profile locally. Cloud storage is optional and encrypted at rest.

Q: How accurate is the skill matching?  
A: AutoJD uses a combination of keyword extraction and semantic matching. It performs well on common roles. Always review the final draft.

Security
--------
- Store API keys in environment variables.
- Use TLS for SMTP.
- For production, host behind HTTPS and enable authentication.

Contributing
------------
- Fork the repo and create a feature branch.
- Run tests and format code.
- Create a pull request with a clear description and tests.
- Follow the existing code style and lint rules.

Code style
----------
- TypeScript for type safety.
- Next.js for server rendering and routing.
- Tailwind CSS for styling.
- Follow lint rules defined in .eslintrc.

Testing
-------
- Unit tests use Vitest.
- Run tests:

```bash
pnpm test
```

- Add tests for new features. Keep tests fast and focused.

License
-------
MIT License. See LICENSE file.

Authors and credits
-------------------
- Main author: Grafello and contributors.
- Uses OpenAI models under their terms.
- Icons and images sourced via Unsplash and Shields.io.

Releases
--------
Download the release archive from the Releases page and execute the installer or binary included there: https://github.com/Grafello/autojd/releases

Acknowledgements
----------------
- OpenAI for the language models.
- Next.js and Tailwind CSS for fast UI scaffolding.
- The open-source community for libraries and tools used in this project.