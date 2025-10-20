# Career Opportunities: Product Development Team at Realnaps

Welcome to the **Realnaps Brand** GitHub organization (`realnaps-brand`)! If you're a developer eager to join our Product Development Team and contribute to AI-driven sports predictions and automated betting tools, this guide is for you. Realnaps is part of the Danny Okec Group, specializing in sports information and solutions with a focus on intelligent prediction and automation. Our mission is to empower users with systems that simplify decision-making in virtual sports betting, positioning us as Africa's leading AI-powered provider.

As a new team member, you'll help build and maintain our core products: the **Realnaps Prediction Bot** (a real-time web app delivering sports insights by analyzing patterns, odds, and history) and the **Realnaps Outcome-Staker Bot** (a desktop app for macOS and Windows that automates stakes based on strategies, limits, and conditions—running 24/7). Our architecture follows a decoupled microservices model (see [ARCHITECTURE.md](https://github.com/realnaps-brand/knowledgebase/blob/main/ARCHITECTURE.md)), with repositories like `realnaps-bet-data-scrapper` (Node.js/Puppeteer for data gathering), `realnaps-data-scrapped-router` (lightweight routing), `realnaps-server` (Node.js/Express/MySQL for API and persistence), `realnaps-web-client` (PHP OOP for the web app), and `realnaps-desktop-client` (Electron for desktop automation). We integrate an external n8n workflow for predictions, emphasizing scalability, resilience, and real-time data flows.

Our Product Development Team is remote-first, collaborative, and asynchronous by default. We use GitHub for issue tracking, PRs, and project boards; prioritize clear, concise communication; and focus on data-driven innovation, transparency, and user empowerment. Team members are provisioned into GitHub teams for role-based access:
- **Code and Security Developers**: Write access to assigned repos.
- **Head of AI Platform**: Maintain access to n8n/router-related repos.
- **Product Leads**: Maintain access to all repos, with assignments to lead specific ones (e.g., one for server/client, another for scraper/router).
- **Test and Quality Assurance**: Triage access for issue management.

Roles are scalable—we have multiple Product Leads (each assigned to lead specific repos based on expertise and needs), Heads of AI, Developers, and QA Specialists, all collaborating on assigned areas while sharing knowledge across the team. Below, we detail each role to give you a clear picture of what joining means. Explore our repos, tackle an open Issue, or connect via email (careers@realnaps.com) to get started.

## Product Lead
Product Leads are the strategic drivers of our tech ecosystem, each assigned to lead one or more specific repositories (e.g., one might own `realnaps-server` and `realnaps-web-client`, while another focuses on `realnaps-bet-data-scrapper` and router). You'll guide development, align with business goals, and mentor your assigned sub-team. This role suits experienced full-stack leaders who thrive on ownership in a dynamic, repo-specific context.

### Core Responsibilities
- **Repo-Specific Roadmap**: For your assigned repos, define priorities, scope features (e.g., enhancing prediction accuracy or scraper resilience), and track progress via GitHub Milestones and Epics.
- **Team Leadership**: Coordinate developers and QA on your repos, assigning tasks through Issues and facilitating async check-ins. Escalate cross-repo issues to collaborate with other Leads.
- **Triage and Oversight**: Prioritize bugs/features in your area (e.g., XPath updates for scraping), review PRs, and oversee merges/deployments to staging/production.
- **Cross-Team Sync**: Align with other Leads on integrations (e.g., data flows between scraper and n8n), incorporate user feedback, and monitor KPIs like uptime and accuracy.
- **Innovation Push**: Propose repo enhancements tied to user needs, ensuring your slice of the system scales for high-traffic betting peaks.

### Key Skills & Tools
- **Tech Stack**: Node.js, PHP OOP, MySQL, GitHub workflows, microservices, and real-time integrations (e.g., webhooks).
- **Soft Skills**: Leadership, strategic planning, and cross-functional collaboration in remote settings.
- **Daily Workflow Example**: Triage Issues in your repo's Project board, review code/PRs, sync async with your sub-team, and validate deployments.

### Qualifications
- Bachelor's in Computer Science or related (Master's preferred).
- 5+ years in product leadership, with full-stack experience in AI/ML or fintech/betting.
- Track record scaling systems; bonus for Puppeteer, Electron, or sports data.
- GitHub: Maintain access across all repos, with primary leadership on assigned ones.

### What Success Looks Like
On-time deliveries for your repos (e.g., 90% velocity), seamless integrations, and direct impact on user growth. With multiple Leads, success includes knowledge-sharing to elevate the whole team.

## Head of AI Platform
Heads of AI Platform own the predictive intelligence, with multiple specialists each focusing on aspects like model tuning or data pipelines—often tied to specific repos like the n8n engine or router. You'll refine algorithms for accurate, real-time sports predictions in virtual betting scenarios. Ideal for ML experts passionate about dynamic data in high-stakes environments.

### Core Responsibilities
- **Model Ownership**: Develop/tune ML models in n8n for your assigned focus (e.g., fixture predictions using odds/history), processing data from scrapers.
- **Pipeline Management**: Ensure clean data flows (e.g., from router to n8n, results back to server) and log outcomes for accuracy tracking and model updates.
- **Optimization and Experimentation**: Analyze post-game results, reduce duplicates, and test advancements like strategy automation—scoped to your repo assignments.
- **Collaboration**: Partner with Developers on integrations; contribute to Epics under Product Leads for your areas.
- **Performance Tracking**: Maintain >70% accuracy, iterating based on real-world betting data.

### Key Skills & Tools
- **Tech Stack**: n8n workflows, Python/ML tools (via nodes), JSON handling, basic Node.js.
- **Soft Skills**: Analytical depth, sports data curiosity, and clear model communication.
- **Daily Workflow Example**: Ingest fixture data, run prediction runs, tweak models from results, and update repo docs.

### Qualifications
- Bachelor's/Master's in AI, Data Science, or Statistics.
- 4+ years in ML, focused on predictions (e.g., time-series or analytics).
- n8n or automation experience; betting knowledge a plus.
- GitHub: Maintain access to n8n/router repos, aligned with your assignments.

### What Success Looks Like
Sustained accuracy gains, minimal drift, and reliable predictions powering automation. As one of multiple Heads, you'll collaborate to compound team-wide AI strength.

## Code and Security Developer
Code and Security Developers are our hands-on builders, with multiple members each assigned to specific repos (e.g., one on desktop client, others on server/scraper). You'll implement features, squash bugs, and secure code—keeping our system resilient for 24/7 betting. Perfect for full-stack pros who love clean, secure code in distributed setups.

### Core Responsibilities
- **Assigned Repo Development**: Code features/fixes in your repos (e.g., Puppeteer scripts for scraping, API endpoints in server, or Electron automation).
- **Bug Handling**: Branch from Issues, implement with tests (OOP standards), create PRs with references (e.g., "fix: XPath update, closes #123"), and collaborate on reviews.
- **Security Integration**: Apply best practices (e.g., validation, encryption) across your assignments; respond to incidents promptly.
- **Maintenance and Reviews**: Keep codebases tidy, review peer PRs, and ensure inter-repo compatibility (e.g., router to n8n).
- **Testing Support**: Aid in integration checks for data flows.

### Key Skills & Tools
- **Tech Stack**: Node.js/Express, PHP OOP, Puppeteer, Electron, MySQL, Git; OWASP security knowledge.
- **Soft Skills**: Detail-focused, collaborative debugging.
- **Daily Workflow Example**: Code from assigned Issues, push PRs for review, test in staging, monitor logs.

### Qualifications
- Bachelor's in Computer Science or equivalent.
- 3+ years full-stack; scraping/automation essential.
- Security awareness (e.g., certs); fintech bonus.
- GitHub: Write access to assigned repos for direct contributions.

### What Success Looks Like
Rapid resolutions (<24h for criticals), high code coverage (>80%), and vulnerability-free audits. Multiple Developers mean shared load and faster innovation across repos.

## Test and Quality Assurance Specialist
Test and QA Specialists ensure reliability, with multiple members handling testing for assigned repos (e.g., one for web/client, another for scraper/server). You'll design tests, validate releases, and prevent issues—safeguarding user trust in our real-time tools. Suited for methodical testers blending manual and automated approaches.

### Core Responsibilities
- **Repo-Specific Testing**: Build/execute plans for your assignments (e.g., regression on predictions, load tests for automation).
- **PR Validation**: Deploy branches to staging, run suites, approve with feedback, and log defects as Issues.
- **Automation Builds**: Create scripts for key paths (e.g., end-to-end flows like scraper-to-display).
- **Triage and Reporting**: Prioritize bugs, escalate in team syncs, and check compliance (e.g., resilience).
- **Coverage Monitoring**: Aim for comprehensive testing in high-stakes areas.

### Key Skills & Tools
- **Tech Stack**: Jest/PHPUnit, CI/CD basics, our core languages.
- **Soft Skills**: Systematic, user-focused communication.
- **Daily Workflow Example**: Review PRs, test in staging, file Issues, report status async.

### Qualifications
- Bachelor's in CS/QA or related.
- 2+ years testing; automation experience.
- Agile familiarity; real-time app bonus.
- GitHub: Triage access to manage/assign Issues repo-wide.

### What Success Looks Like
Low defect rates (<1% post-release), full critical-path coverage, and quicker cycles. With multiple Specialists, you'll distribute expertise for robust, team-wide quality.

---

Excited to join our Product Development Team? Dive into [our repos](https://github.com/realnaps-brand), contribute to Issues, or apply at [realnaps.com/careers](https://realnaps.com/careers). We value diverse perspectives and are growing—roles open for all levels.

*Last updated: October 19, 2025*  
*Realnaps Brand | Abuja, Nigeria | RC: 1634076*
