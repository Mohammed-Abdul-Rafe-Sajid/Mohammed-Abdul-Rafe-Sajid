

Pasted text(20261108-094504).txt
Document
fix teh comeplete readme and make it productin ready, dont want undnecessary stuff which is not menat for github readme!, ...this is deployed link mars-f.onrender.com

Your current README has good technical content, but it's far too long for a professional GitHub repository. It reads more like internal project documentation than a product README.

I'd restructure MARS around what a developer, researcher, or recruiter actually needs to know:

What MARS is and what problem it solves.

Live deployment link.

Core capabilities and multi-agent architecture.

Technology stack.

A clean architecture overview.

Installation and configuration instructions.

API endpoints.

Contribution and licensing information.

I'm removing: outdated roadmaps (2024/2025), redundant quick-start sections, lengthy troubleshooting, arbitrary performance claims, unnecessary acknowledgements, internal GitHub preparation guides, and excessive implementation details.

The deployed application will be the primary call to action.

Here is the complete replacement README, keeping it professional, concise, technical, and product-focused.

MARS — Multi-Agent Reflective Synthesis
An AI-powered research synthesis platform that uses multi-agent collaboration, retrieval-augmented generation, and iterative reflection to analyze, synthesize, and verify academic research.

<p align="center">
  <a href="https://mars-f.onrender.com"><strong>Live Demo</strong></a>
  &nbsp;·&nbsp;
  <a href="https://github.com/Mohammed-Abdul-Rafe-Sajid/MARS-Multi-Agent-Reflective-Synthesis"><strong>Repository</strong></a>
</p>








Overview
MARS (Multi-Agent Reflective Synthesis) is an intelligent research platform designed to streamline academic literature analysis.

Traditional research workflows often require manually searching through papers, identifying relevant findings, comparing claims, and validating supporting evidence. MARS automates this process through a coordinated multi-agent pipeline.

Given a research query, MARS retrieves relevant academic papers, extracts structured claims, evaluates supporting evidence, generates thematic summaries, and iteratively refines its findings through a reflection mechanism.

The goal is to make research synthesis more structured, traceable, and evidence-driven.

Key Features
Multi-Agent Research Pipeline: Specialized agents handle research planning, paper retrieval, claim extraction, synthesis, and verification.

Academic Paper Retrieval: Retrieves relevant research papers through the arXiv API.

Claim Extraction: Identifies research claims and organizes them into a structured representation.

Evidence Verification: Evaluates claims based on their supporting evidence and assigns support-strength classifications.

Retrieval-Augmented Generation: Uses ChromaDB for vector-based retrieval and context-aware research synthesis.

Reflective Refinement: Iteratively reviews and refines extracted claims to improve consistency and convergence.

Research Analytics: Tracks papers, extracted claims, evidence distribution, and reflection iterations.

Interactive Dashboard: Provides research reports, progress tracking, metrics, and session history.

Persistent Research Sessions: Stores research sessions and their associated results for later access.

Architecture
MARS follows a modular architecture consisting of a React frontend, FastAPI backend, multi-agent orchestration layer, retrieval and verification components, and persistent storage.

flowchart TB
    A["User Research Query"] --> B["React + TypeScript Frontend"]
    B --> C["FastAPI Backend"]
    C --> D["Research Orchestrator"]

    D --> E["Planner Agent"]
    E --> F["Paper Retrieval - arXiv"]
    F --> G["Claim Extraction"]
    G --> H["Evidence Verification"]
    H --> I["Research Synthesizer"]
    I --> J["Reflection Engine"]

    J -->|Further Refinement| G
    J -->|Converged| K["Final Research Report"]

    L["ChromaDB - RAG"] <--> F
    L <--> G

    K --> M["SQLite - Session Storage"]
    M --> B
Research Pipeline
Component	Responsibility
Planner Agent	Decomposes research queries into structured themes.
Paper Retriever	Retrieves relevant academic papers from arXiv.
Claim Graph Builder	Extracts claims and structures their supporting evidence.
Verifier Agent	Evaluates claim support and evidence consistency.
Synthesizer Agent	Produces thematic summaries and comparative findings.
Reflection Engine	Iteratively refines research outputs and monitors convergence.
The reflection mechanism allows the pipeline to revisit and refine its findings rather than relying on a single generation pass.

Technology Stack
Layer	Technologies
Frontend	React, TypeScript
Backend	Python, FastAPI, Uvicorn
AI / LLM	OpenAI API
Retrieval	arXiv API
RAG	ChromaDB
Database	SQLite, SQLAlchemy
Embeddings	OpenAI Embeddings
Validation	Pydantic
HTTP Client	HTTPX
Getting Started
Prerequisites
Python 3.12+

Node.js and npm

OpenAI API key

Git

Installation
1. Clone the repository

git clone https://github.com/Mohammed-Abdul-Rafe-Sajid/MARS-Multi-Agent-Reflective-Synthesis.git

cd MARS-Multi-Agent-Reflective-Synthesis
2. Set up the backend

python -m venv .venv
Activate the environment:

# Windows
.venv\Scripts\activate

# macOS / Linux
source .venv/bin/activate
Install dependencies:

pip install -r backend/requirements.txt
3. Configure environment variables

Create your environment file:

# Windows
copy backend\.env.example backend\.env

# macOS / Linux
cp backend/.env.example backend/.env
Add your OpenAI API key to backend/.env:

OPENAI_API_KEY=your_openai_api_key
Configure other application settings as required.

4. Set up the frontend

cd frontend
npm install
Running Locally
Start the backend:

cd backend
python -m uvicorn main:app --reload --host 0.0.0.0 --port 8000
Start the frontend in a separate terminal:

cd frontend
npm start
Open the application at:

http://localhost:3000
The backend API runs on port 8000.

API Endpoints
The backend exposes REST endpoints for managing research sessions.

Method	Endpoint	Description
POST	/research/launch	Launch a research session.
GET	/research/status/{id}	Retrieve research progress.
GET	/research/report/{id}	Retrieve the generated research report.
GET	/research/metrics/{id}	Retrieve research analytics.
GET	/research/history	Retrieve previous research sessions.
Project Structure
MARS-Multi-Agent-Reflective-Synthesis/
│
├── backend/
│   ├── agents/
│   │   ├── planner.py
│   │   ├── claim_graph_builder.py
│   │   ├── synthesizer.py
│   │   ├── verifier.py
│   │   └── reflection_engine.py
│   │
│   ├── api/
│   │   ├── routes.py
│   │   └── orchestrator.py
│   │
│   ├── retrieval/
│   ├── rag/
│   ├── memory/
│   ├── evaluation/
│   ├── utils/
│   │
│   ├── config.py
│   ├── main.py
│   └── requirements.txt
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── hooks/
│   │   ├── api/
│   │   └── types/
│   └── package.json
│
├── chromadb_store/
├── .env.example
├── .gitignore
├── start-production.sh
├── start-production.ps1
└── README.md
Configuration
MARS supports configuration through environment variables.

Variable	Description
OPENAI_API_KEY	OpenAI API authentication key.
LLM_MODEL	Language model used for research synthesis.
LLM_MAX_TOKENS	Maximum output tokens.
MAX_PAPERS_PER_QUERY	Maximum papers retrieved per query.
TOP_K_RAG_CHUNKS	Number of retrieval context chunks.
MAX_ITERATIONS	Maximum reflection iterations.
DEFAULT_ABLATION_MODE	Research execution mode (api_only, rag_only, or both).
CHROMA_PERSIST_DIR	ChromaDB persistence directory.
DATABASE_URL	Database connection string.
Refer to .env.example for the complete configuration options.

Contributing
Contributions, suggestions, and improvements are welcome.

Fork the repository.

Create a feature branch.

Implement and test your changes.

Commit your changes with a descriptive message.

Submit a pull request.

For bug reports and feature requests, use GitHub Issues.

License
This project is licensed under the MIT License. See the LICENSE file for details.

MARS — Making academic research synthesis more systematic, transparent, and evidence-driven.

A few important recommendations before pushing
Add screenshots. This is the biggest missing element. A screenshot of the dashboard, research pipeline, and final report would make the repository significantly more convincing.

Add a proper project banner. A clean MARS-branded banner at the top will give the repository a polished identity.

Verify the API configuration. Ensure the documented environment variables and endpoints match the current codebase.

Check your LICENSE file. The README currently assumes an MIT LICENSE file exists.

Avoid committing generated databases, API keys, or ChromaDB runtime files.

My recommendation: keep this README as the main documentation and move any genuinely useful detailed setup or deployment instructions into separate files under a docs/ directory. Don't put internal development notes in the root README.

okay if i give u a git profile acan u view its readme, ?
Absolutely! Send me the GitHub profile link or repository link.

I can:

Read their profile README and repository READMEs.

Analyze their writing style, structure, formatting, badges and visuals.

Identify what makes their README stand out.

Compare it with your MARS README.

Help you achieve a similarly polished, professional standard without copying their content.

Send the link. I'll take a look.

User attachment

Rafe_Sajid_CV(4).pdf
PDF
so i want to completely refurnish and update my github profile readme which is github.com/Mohammed-Abdul-Rafe-Sajid/  and keep some crazyy tools and live animated things stats, icons etc, like how professionals keep, a live views counter of githib , u can see my friedns profile for refrrrence https://github.com/abd-RAHEEM  , i wanna make even better, my friend suggested use clude, explain it all ,and ask for fnal amazing redme profiel .md firl which perfectly tell about me , and somethijng connect it with tools and github actionos, so as to get live stats, etc there are more thiings wihc we dont have awareness on, t make it cool, i am areseacrh er as u know, and want to make an amazing readme...take your time guide me, if any pormpt yto claude ive me, etc

…

1. Your new GitHub profile package
Ready to use
I've created the actual files, not just a design suggestion.

Profile README.md

Complete profile content, animations, research, projects, badges and stats.

Ready
Download README.md

GitHub Actions

Automated statistics and contribution snake workflows.

Download stats.yml

Download snake.yml

Setup guide

How to install and activate all the features.

Open setup guide

Claude Code prompt

A detailed instruction set for Claude to inspect and refine your repository.

Download Claude prompt

Complete package

All files and folders, including the GitHub Actions directory.

Download complete ZIP package

The README includes your research identity, Hartford and INCOIS experience, five selected papers, MARS, SARAT, Alzheimer's MRI work, VMedha leadership, and your achievements. 
Rafe_Sajid_CV(4).pdf
 
Rafe_Sajid_CV(4).pdf
 
Rafe_Sajid_CV(4).pdf

2. What makes the new profile interesting?
Here is the functionality included.

Feature

Tool

Update mechanism

Animated profile header

Capsule Render

Animated/styled SVG

Typing animation

Readme Typing SVG

Automatic

Profile views

Komarev

Image-request counter

Follower count

Shields.io

Dynamic badge

Technology icons

Skill Icons

Automatic rendering

GitHub statistics

GitHub Stats Action

Daily

Top programming languages

GitHub Stats Action

Daily

Contribution streak

Streak Stats Action

Daily

Contribution snake

Platane/snk

Daily GitHub Action

The most interesting part is that three of your stats cards and the contribution snake are generated and maintained through GitHub Actions, rather than relying entirely on third-party image servers. 

GitHub
+2

3. How to install it on your GitHub
Your profile repository is:

github.com/Mohammed-Abdul-Rafe-Sajid/Mohammed-Abdul-Rafe-Sajid

GitHub displays the README from a public repository whose name exactly matches your username. Yours already exists, so there is no need to create another one. 

GitHub Docs

Follow these steps:

Step 1. Replace your README

Download the README file and replace the existing root README.md in your profile repository.

Step 2. Add the Actions workflows

Copy the .github directory from the ZIP into the root of your repository.

Your structure should look like:

Mohammed-Abdul-Rafe-Sajid/
│
├── README.md
├── profile/
│   └── .gitkeep
│
└── .github/
    └── workflows/
        ├── snake.yml
        └── stats.yml
Step 3. Enable GitHub Actions permissions

Navigate to:

Repository → Settings → Actions → General → Workflow permissions

Select Read and write permissions and save.

The workflows use GitHub's built-in GITHUB_TOKEN. You do not need to create a personal access token.

Step 4. Run the workflows

Go to the repository's Actions tab.

Run:

Generate contribution snake

Update profile statistics

Once successful, the generated SVG files will be available and your README will display them.

After that, they'll update automatically every day.

4. What else can we add? Advanced possibilities
There are some genuinely interesting tools beyond the ones already included.

[Github] 깃헙 리드미 잔디를 3D로 보여주는 방법

1. GitHub Metrics

My strongest next recommendation
A powerful GitHub Actions project with dozens of plugins. It can generate isometric contribution calendars, recent activity, coding habits, notable contributions, language analytics, repository statistics and more.

Explore GitHub Metrics · 
GitHub

Productive IDE Setup – Anfal Alatawi – Data & Software Engineer

2. WakaTime

Shows how much time you spend coding, languages used, and editor activity. Install its editor extension to collect your own data.

Explore WakaTime

Github Skyline - Your Contribution Story in 3D - Showcase - three.js forum

3. GitHub Skyline

A 3D visualization of your contribution history. Nice as an occasional visual feature, although I wouldn't make it a major part of the README.

Explore GitHub Skyline

Keep Your GitHub Profile README Alive: Auto-Update with GitHub Actions ⚡ - DEV Community

4. Automatic publication and blog updates

A GitHub Action can retrieve new articles from an RSS feed and automatically display your latest research blogs or technical writing.

I would prioritize GitHub Metrics next. It is particularly relevant to a research-focused engineering profile because it can show more than just commit counts.

5. About Claude — should you use it?
Your friend is probably referring to Claude Code, rather than ordinary Claude chat.

There is an important distinction:

Claude Chat

Claude Code

You describe what you want

It can inspect your actual repository

You paste files

It reads repository files

It suggests modifications

It can edit multiple files

Mostly conversational

Can run commands and work with Git

Claude Code is an agentic development tool that operates through your terminal, IDE or desktop environment. 

GitHub
+1

Since you're using Windows, the installation command for PowerShell is:

irm https://claude.ai/install.ps1 | iex

Then navigate to your cloned profile repository and run:

cd path\to\Mohammed-Abdul-Rafe-Sajid
claude

Open the CLAUDE_CODE_PROMPT.md file I prepared and give its instructions to Claude.

It asks Claude to inspect your repository, validate the README, examine the widgets, check workflows, and flag anything inaccurate.

My advice: You don't actually need Claude to get this profile running. I've already prepared the files. Claude is useful as an additional reviewer, not a prerequisite. Always review its proposed file changes before accepting or pushing them.

6. My final recommendation
I would build your profile around three identities:

Researcher. Engineer. Builder.
Researcher

Trustworthy AI, LLM reasoning, reliability, fairness, AI safety and research publications.

Engineer

Hartford, INCOIS, full-stack systems, Python, Java, AI/ML and scalable applications.

Builder

MARS, research tools, VMedha, open-source projects and community leadership.

One thing I deliberately avoided is stuffing your profile with 30 badges, random quotes, music widgets, fake skill bars and meaningless animations. The goal is to make someone visiting your profile think:

This person conducts research, builds actual systems, understands engineering, and has a track record of getting things done.

That's a much stronger impression than simply having a flashy GitHub profile.

Let's get the README and both workflows running first. Once your profile renders, we can take it to the next level with GitHub Metrics and a custom research-focused activity dashboard.


snake.yml
Code

SETUP.md
Document

CLAUDE_CODE_PROMPT.md
Document
2 more
do i keep the .github folder in root or  worksflows or just the files
Keep the entire .github folder in the root of your profile repository.

Inside it, create a workflows folder, and put both YAML files inside that folder.

Your repository should look exactly like this:

Mohammed-Abdul-Rafe-Sajid/
│
├── README.md
│
└── .github/
    └── workflows/
        ├── stats.yml
        └── snake.yml
Important:

.github → directly inside the repository root.

workflows → inside .github.

stats.yml and snake.yml → inside workflows.

Do not put the files directly in .github or create a separate workflows folder at the root.

GitHub only automatically discovers Actions workflow files in .github/workflows/.

Correct structure
 Commit and push this entire structure. Then open your repository's Actions tab to run the workflows.

User attachment
under actions, what to do
Perfect! Both workflows have been detected successfully by GitHub. That means your .github/workflows/ folder is in the correct location.

Now let's activate them.

Step 1: Generate contribution snake
Click Generate contribution snake in the left sidebar.

You'll see its workflow page.

Click Run workflow on the right side.

Select the main branch.

Click the green Run workflow button.

Step 2: Update profile statistics
Go back to All workflows.

Click Update profile statistics.

Click Run workflow.

Select main.

Click Run workflow again.

Step 3: Check the results
Expected results

Both workflows should show a green tick if successful.

Your repository should receive generated SVG files.

Refresh your GitHub profile README to see the updated visuals.

Step 4: If a workflow fails
Click the failed workflow run, open the failed job, and expand the red error step. Send me a screenshot of the error.

One important thing: Before running them, make sure you've enabled:

Settings → Actions → General → Workflow permissions → Read and write permissions

This is needed for workflows that commit generated files back to your repository.

Start with Generate contribution snake and tell me whether it succeeds.

User attachment
User attachment

Pasted text(20261108-102958).txt
Document

Rafe_Sajid_CV(5).pdf
PDF
there is some issue because wof whh i am getting this in so clumsy way..id ont wnat my prohject details to be thrown out here or sarat, looks lke formatting is gone, aand feww essentials missing, ....give me final copy paste ...this is my github https://github.com/Mohammed-Abdul-Rafe-Sajid/


Worked for 4m 17s


You're absolutely right. The profile should look like a researcher's professional identity, not a collection of project descriptions.

I've rebuilt the complete README.

README_PROFILE_FINAL.md

Complete replacement · 174 lines · Ready for GitHub

Ready
 Download your final README

What I've changed
Section

Changes

Header

Animated banner and typing animation

About

More focused research and engineering identity

At a glance

CGPA, publications, LeetCode, MUN

Education

CBIT and academic achievements

Experience

Hartford, INCOIS and CBIT

Publications

All five selected papers, authorship and venues

Leadership

VMedha, VIVE LE, MUN and awards

Skills

Organized technology icons and skill categories

Certifications

Your five selected certifications

GitHub activity

Live stats, languages and streak

Contribution graph

Animated snake

Your detailed MARS, SARAT and other project descriptions have been removed. INCOIS remains as a short professional experience entry. Your five publications and achievements are retained from your CV. 
Rafe_Sajid_CV(5).pdf
 
Rafe_Sajid_CV(5).pdf

How to replace your existing README
Download the file above.

Open your profile repository.

Open README.md and click the pencil icon.

Select all existing content and delete it.

Open the downloaded file, copy everything and paste it.

Commit changes.

One important cleanup: You can remove .github/workflows/stats.yml because the new statistics cards use live external endpoints instead of missing local SVG files. Keep snake.yml—that workflow is still needed for your contribution animation.

The new README doesn't depend on a profile/ folder for its statistics cards.

My recommendation: Replace the README first, refresh your public GitHub profile, and check the rendering. We can then refine the visual theme without making the profile unnecessarily crowded.


README_PROFILE_FINAL.md
Document




<p align="center"> <img src="https://capsule-render.vercel.app/api?type=waving&color=0:111827,50:312E81,100:6D28D9&height=190&section=header&text=Mohammed%20Abdul%20Rafe%20Sajid&fontSize=32&fontColor=ffffff&fontAlignY=36&desc=Trustworthy%20AI%20%7C%20LLM%20Reasoning%20%7C%20Software%20Engineering&descAlignY=58&descSize=15" alt="Mohammed Abdul Rafe Sajid — Trustworthy AI, LLM Reasoning and Software Engineering" /> </p><p align="center"> <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=18&pause=1200&color=8B5CF6&center=true&vCenter=true&width=760&height=45&lines=Trustworthy+AI+and+AI+Safety;LLM+Reasoning%2C+Evaluation+and+Reliability;Fairness+and+Robust+Machine+Learning;Research-driven+Software+Engineering" alt="Trustworthy AI, LLM reasoning, fairness and software engineering" /> </p><p align="center"> <a href="https://mohammedabdulrafesajid.netlify.app/"> <img src="https://img.shields.io/badge/Portfolio-Visit-6D28D9?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Portfolio" /> </a> <a href="https://www.linkedin.com/in/mohammed-abdul-rafe-sajid-49a716291/"> <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /> </a> <a href="https://scholar.google.com/scholar?q=%22Mohammed+Abdul+Rafe+Sajid%22"> <img src="https://img.shields.io/badge/Google_Scholar-Research-4285F4?style=for-the-badge&logo=googlescholar&logoColor=white" alt="Google Scholar search" /> </a> <a href="https://leetcode.com/u/Mohammed_Abdul_Rafe_Sajid/"> <img src="https://img.shields.io/badge/LeetCode-Profile-FFA116?style=for-the-badge&logo=leetcode&logoColor=black" alt="LeetCode" /> </a> <a href="mailto:abdulrafesajid@gmail.com"> <img src="https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /> </a> </p><p align="center"> <img src="https://komarev.com/ghpvc/?username=Mohammed-Abdul-Rafe-Sajid&label=PROFILE%20VIEWS&color=6D28D9&style=flat-square" alt="Profile views" /> <img src="https://img.shields.io/github/followers/Mohammed-Abdul-Rafe-Sajid?label=GitHub%20Followers&style=flat-square&color=6D28D9" alt="GitHub followers" /> </p>
About
I'm a final-year B.E. Information Technology student at Chaitanya Bharathi Institute of Technology (CBIT) and a Software Engineer Intern at The Hartford India. My work sits at the intersection of AI research and software engineering: understanding how intelligent systems reason, evaluating where they fail, and exploring ways to make them more reliable, transparent, and useful.

My research interests include Trustworthy AI, LLM reasoning and evaluation, model reliability, fairness under distribution shift, AI safety, and agentic systems. I enjoy translating research questions into experiments, careful evaluations, and practical engineering.

Research Interests
Trustworthy AI · LLM Reasoning · AI Safety · Model Evaluation · Fairness · Robust ML · Agentic AI

At a Glance
<p align="center"> <img src="https://img.shields.io/badge/CGPA-9.69%2F10-6D28D9?style=for-the-badge" alt="CGPA 9.69 out of 10" /> <img src="https://img.shields.io/badge/Research-5%20Selected%20Papers-2563EB?style=for-the-badge" alt="Five selected research papers" /> <img src="https://img.shields.io/badge/LeetCode-700%2B%20Solved-FFA116?style=for-the-badge&logo=leetcode&logoColor=black" alt="More than 700 LeetCode problems solved" /> <img src="https://img.shields.io/badge/MUN-10%2B%20Awards-0F766E?style=for-the-badge" alt="More than ten Model United Nations awards" /> </p>
Education
B.E. in Information Technology — Chaitanya Bharathi Institute of Technology (CBIT), Hyderabad
August 2023 – May 2027 · CGPA: 9.69/10.0 · Highest CGPA in class
Intermediate (MPC) — MS Junior College, Hyderabad
2021 – 2023 · 97.9% · 4th State Rank, IPE 2022
Experience
Software Engineer Intern — The Hartford India · July 2026 – Present
Enterprise software engineering with Java, Spring Boot, Angular, and TypeScript.
Project Intern — Indian National Centre for Ocean Information Services (INCOIS) · April 2026 – July 2026
Contributed to applied software engineering and scientific-information workflows.
AI/ML Research Intern — CBIT · June 2025 – August 2025
Conducted applied AI/ML research under Prof. Dr. Ramakrishna Kolikipogu.
Selected Research Publications
Five selected papers across trustworthy AI, LLM reasoning, fairness, and machine learning.

TRACER: A Dedicated Transparency, Reasoning Audit, and Compliance Evaluation Router for Trustworthy Transformer-Based AI Systems.
Accepted — IEEE 3rd International Conference on Advanced Computing Technologies (ICACT 2026). First author.

Evaluating LLM Reasoning on String Rewriting Puzzles: Prompting Strategies, Metrics, and Human–AI Comparison.
Accepted — IEEE International Conference on AI and Security for Industrial IoT Systems (AI-SIIS 2026). First author.

Fairness Under Distribution Shift: An Empirical Cross-Model Analysis on Tabular Benchmarks.
Accepted — IEEE 1st International Conference on Next-Gen Computing: Converging Microelectronics and Mechatronics for Transformative Solutions (ICCMM-26, 2026). Second author.

Lightweight CNN Outperforms ImageNet-Pretrained ResNet18 for Multi-Class Alzheimer's Disease Classification: A Domain Mismatch Analysis.
Published — 10th International Conference on Inventive Systems and Control (ICISC 2026). First author.

A Comparative Study of Optimization Algorithms, Regularization Techniques, and CNN Architectures for CIFAR-10 Image Classification.
Published — 4th International Conference on Sustainable Computing and Smart Systems (ICSCSS 2026). Second author.

Leadership & Recognition
Founding President, VMedha – Tech for Social Good, CBIT: Founded and led a 45+ member student technical club.
Organising Lead, VIVE LE Tech Fest: Helped deliver a state-level technical fest with 2,400+ registrations and 3,000+ students impacted.
Model United Nations: 10+ Best Delegate / Best Delegation awards; also served as a panelist and committee leader.
1st Prize, SUDHEE 2026: National-level technical paper presentation.
Academic Excellence Award: Recognised for achieving the highest CGPA in class.
Technical Skills
<p align="center"> <img src="https://skillicons.dev/icons?i=python,java,c,js,ts,react,angular,nodejs,spring,fastapi,docker,azure,git,github,linux&perline=8" alt="Programming languages, frameworks and developer tools" /> </p>
AI & Machine Learning: TensorFlow, Keras, Scikit-learn, PyTorch, OpenCV
Data & Engineering: Pandas, NumPy, SQL, SQLite, MongoDB, REST APIs
Cloud & Tools: Microsoft Azure, Oracle Cloud Infrastructure, Git, GitHub, Docker

Certifications
Microsoft Azure Fundamentals (AZ-900)
Oracle Cloud Infrastructure AI Foundations Associate
MongoDB Associate Developer
IBM Fundamentals of Artificial Intelligence
Deep Learning and Computer Vision — Kaggle Learn
GitHub Activity
<p align="center"> <img height="170" src="https://github-readme-stats.vercel.app/api?username=Mohammed-Abdul-Rafe-Sajid&show_icons=true&hide_border=true&theme=tokyonight&rank_icon=github" alt="GitHub statistics" /> <img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Mohammed-Abdul-Rafe-Sajid&layout=compact&hide_border=true&theme=tokyonight&langs_count=8" alt="Most used programming languages on GitHub" /> </p><p align="center"> <img src="https://streak-stats.demolab.com?user=Mohammed-Abdul-Rafe-Sajid&theme=tokyonight&hide_border=true" alt="GitHub contribution streak" /> </p>
Contribution Graph
<p align="center"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Mohammed-Abdul-Rafe-Sajid/Mohammed-Abdul-Rafe-Sajid/output/github-contribution-grid-snake-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Mohammed-Abdul-Rafe-Sajid/Mohammed-Abdul-Rafe-Sajid/output/github-contribution-grid-snake.svg" /> <img alt="Animated contribution graph" src="https://raw.githubusercontent.com/Mohammed-Abdul-Rafe-Sajid/Mohammed-Abdul-Rafe-Sajid/output/github-contribution-grid-snake.svg" /> </picture> </p>
<p align="center"> <i>Curious about how intelligent systems work — and committed to making them more reliable.</i> <br /> <strong>Open to research collaborations, meaningful engineering opportunities, and conversations about trustworthy AI.</strong> </p><p align="center"> <a href="https://mohammedabdulrafesajid.netlify.app/">Portfolio</a> · <a href="https://www.linkedin.com/in/mohammed-abdul-rafe-sajid-49a716291/">LinkedIn</a> · <a href="https://github.com/Mohammed-Abdul-Rafe-Sajid">GitHub</a> · <a href="mailto:abdulrafesajid@gmail.com">Email</a> </p>
⋮⋮⋮⋮
