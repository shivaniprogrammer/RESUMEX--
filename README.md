
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>AI Resume & Tech Career Portal</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link href="https://fonts.googleapis.com/css?family=Inter:400,700&display=swap" rel="stylesheet">
  <style>
    :root {
      --color-bg: #f8f9fb;
      --color-fg: #222;
      --color-accent: #6366f1;
      --color-card: #fff;
      --color-border: #e5e7eb;
      --color-btn: #6366f1;
      --color-btn-txt: #fff;
      --shadow-card: 0 2px 18px 0 rgba(100,100,150,0.08);
    }
    [data-theme="dark"] {
      --color-bg: #181826;
      --color-fg: #f4f4f9;
      --color-accent: #8b5cf6;
      --color-card: #232338;
      --color-border: #353663;
      --color-btn: #8b5cf6;
      --color-btn-txt: #f4f4f9;
      --shadow-card: 0 2px 18px 0 rgba(100,100,150,0.18);
    }
    html, body {
      height: 100%;
      margin: 0;
    }
    body {
      font-family: 'Inter', sans-serif;
      background: var(--color-bg);
      color: var(--color-fg);
      transition: background 0.4s, color 0.4s;
      min-height: 100vh;
    }
    header {
      background: var(--color-accent);
      color: #fff;
      padding: 1.2rem 0 0.8rem 0;
      text-align: center;
      position: relative;
      transition: background 0.4s;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 0.7em;
    }
    .theme-toggle-container {
      width: 100%;
      display: flex;
      justify-content: flex-end;
      padding-right: 2.2rem;
      margin-bottom: 0.3em;
    }
    .toggle-mode {
      background: transparent;
      color: #fff;
      border: 2px solid #fff;
      font-size: 1em;
      font-weight: 700;
      padding: 0.35em 1.2em;
      border-radius: 8px;
      transition: background 0.2s, color 0.2s;
    }
    .toggle-mode.light-mode {
      color: var(--color-accent);
      border-color: var(--color-accent);
      background: #fff;
    }
    main {
      max-width: 900px;
      margin: 2.5rem auto 1.5rem auto;
      background: var(--color-card);
      border-radius: 12px;
      box-shadow: var(--shadow-card);
      padding: 2rem;
      border: 1px solid var(--color-border);
      text-align: center;
      animation: fadeInUp 1.1s cubic-bezier(.4,0,.2,1);
    }
    @keyframes fadeInUp{
      from{opacity:0; transform:translateY(40px);}
      to{opacity:1; transform:translateY(0);}
    }
    h1, h2, h3, h4 {
      margin-top: 0;
      text-align: center;
      letter-spacing: 0.01em;
    }
    section {
      margin-bottom: 2.5rem;
      animation: fadeIn 1.1s cubic-bezier(.4,0,.2,1);
      position: relative;
    }
    @keyframes fadeIn {
      from{opacity:0;}
      to{opacity:1;}
    }
    hr.section-divider {
      border: none;
      border-top: 2px solid var(--color-border);
      margin: 2.5rem 0 2rem 0;
      width: 90%;
      animation: fadeIn 1.1s;
    }
    .card {
      background: var(--color-bg);
      border-radius: 10px;
      padding: 1.2rem 1.5rem;
      margin-bottom: 1.2rem;
      border-left: 4px solid var(--color-accent);
      box-shadow: var(--shadow-card);
      display: inline-block;
      min-width: 60%;
      text-align: center;
      animation: popCard 0.7s;
    }
    @keyframes popCard {
      0% {transform: scale(0.9);}
      80% {transform: scale(1.05);}
      100% {transform: scale(1);}
    }
    button, select, .option-btn {
      background: var(--color-btn);
      color: var(--color-btn-txt);
      border: none;
      border-radius: 5px;
      padding: 0.7em 1.5em;
      font-weight: 600;
      margin-top: 0.6em;
      margin-right: 0.6em;
      font-size: 1em;
      cursor: pointer;
      transition: background 0.18s, color 0.18s, box-shadow 0.2s;
      box-shadow: 0 2px 8px rgba(99,102,241,0.03);
      outline: none;
      text-align: center;
    }
    button:active, .option-btn:active {
      box-shadow: 0 1px 4px rgba(99,102,241,0.09);
      transform: scale(0.97);
    }
    button:hover, .option-btn:hover {
      background: #3730a3;
    }
    .resume-upload {
      display: flex;
      flex-direction: column;
      gap: 0.7em;
      align-items: center;
      justify-content: center;
    }
    .resume-score {
      background: #e0e7ff;
      color: #3730a3;
      border-radius: 7px;
      padding: 1.2em 2em;
      margin-top: 1.1em;
      display: none;
      font-size: 1.08em;
      text-align: center;
      box-shadow: var(--shadow-card);
      animation: fadeIn 0.7s;
    }
    [data-theme="dark"] .resume-score {
      background: #28285e;
      color: #c7d0ff;
    }
    .select-job, .select-edu {
      width: 80%;
      max-width: 350px;
      margin-bottom: 0.8em;
      margin-top: 1em;
      font-size: 1.05em;
      padding: 0.5em;
      border-radius: 6px;
      border: 1.5px solid var(--color-accent);
      text-align: center;
    }
    .skills-list {
      display: flex;
      flex-wrap: wrap;
      gap: 0.6em;
      margin-bottom: 1em;
      justify-content: center;
      align-items: center;
    }
    .skill-chip {
      background: var(--color-accent);
      color: #fff;
      border-radius: 16px;
      padding: 0.4em 1em;
      font-size: 0.98em;
      margin-bottom: 0.3em;
      margin-top: 0.3em;
      box-shadow: 0 1px 4px rgba(99,102,241,0.06);
      animation: slideInSkill 0.7s;
      opacity: 0;
      animation-fill-mode: forwards;
    }
    @keyframes slideInSkill {
      0% {transform: translateY(30px); opacity:0;}
      100% {transform: translateY(0); opacity:1;}
    }
    .hidden { display: none !important; }
    .quiz-section {
      background: #f3f4f6;
      padding: 2em 0.5em 2.5em 0.5em;
      border-radius: 12px;
      margin: 0 auto 2em auto;
      box-shadow: var(--shadow-card);
      max-width: 700px;
      animation: fadeInUp 1.1s;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      min-height: 280px;
    }
    [data-theme="dark"] .quiz-section {
      background: #232338;
    }
    .quiz-options {
      display: flex;
      flex-direction: column;
      gap: 0.5em;
      margin: 1.2em 0 0.7em 0;
      align-items: center;
      width: 100%;
    }
    .quiz-progress{
      margin-top: 1em;
      color: var(--color-accent);
      font-weight: 600;
      font-size: 1.1em;
    }
    .piechart-container {
      width: 100%;
      max-width: 400px;
      margin: 1em auto 0 auto;
      background: var(--color-bg);
      border-radius: 8px;
      padding: 1.5em;
      box-shadow: var(--shadow-card);
      text-align: center;
      animation: fadeIn 0.9s;
    }
    canvas { margin-top: 1em; }
    .mode-label {
      color: #fff;
      font-size: 1em;
      background: #3730a3;
      border-radius: 0 0 8px 8px;
      padding: 0.2em 1.6em;
      display: inline-block;
      margin-bottom: 1em;
      text-align: center;
    }
    [data-theme="dark"] .mode-label {
      background: #fff;
      color: var(--color-accent);
    }
    /* Recommended Jobs Animations */
    .job-role-anim {
      background: var(--color-accent);
      color: #fff;
      border-radius: 16px;
      padding: 0.4em 1em;
      font-size: 0.98em;
      margin-bottom: 0.3em;
      margin-top: 0.3em;
      margin-right: 0.35em;
      margin-left: 0.35em;
      box-shadow: 0 1px 4px rgba(99,102,241,0.12);
      opacity: 0;
      display: inline-block;
      animation: popJob 0.9s forwards;
    }
    @keyframes popJob {
      0% {transform: scale(0.8) translateY(30px); opacity:0;}
      60% {transform: scale(1.08) translateY(-5px); opacity:0.7;}
      100% {transform: scale(1) translateY(0); opacity:1;}
    }
    @media (max-width: 700px) {
      main { padding: 1rem; }
      .piechart-container { max-width: 100%; }
      .card { padding: 0.8em 0.5em; min-width: 90%; }
      .quiz-section{ padding: 1.2em 0.2em 1.8em 0.2em;}
      .theme-toggle-container {padding-right: 1em;}
    }
  </style>
</head>
<body data-theme="light">
  <header>
    <div class="theme-toggle-container">
      <button class="toggle-mode" onclick="toggleMode()" id="modeBtn">Dark Mode</button>
    </div>
    <h1>AI Resume & Tech Career Portal</h1>
    <div class="mode-label" id="modeLabel">Current: Light Mode</div>
  </header>
  <main>
    <!-- Resume Score Section -->
    <section>
      <h2>AI Resume Score</h2>
      <div class="resume-upload">
        <label for="resumeInput"><b>Upload your resume (PDF or DOCX):</b></label>
        <input type="file" id="resumeInput" accept=".pdf,.doc,.docx">
        <button onclick="scoreResume()" id="scoreBtn" disabled>Score Resume</button>
      </div>
      <div class="resume-score" id="resumeScore"></div>
    </section>

    <hr class="section-divider">

    <!-- Job Skills Info Section -->
    <section>
      <h2>Explore Tech Careers & Skills</h2>
      <select class="select-job" id="jobSelect">
        <option value="" disabled selected>Select a job role</option>
        <option value="fullstack">Full Stack Developer</option>
        <option value="frontend">Frontend Developer</option>
        <option value="backend">Backend Developer</option>
        <option value="datasci">Data Scientist</option>
        <option value="ai">AI/ML Engineer</option>
        <option value="cloud">Cloud Engineer</option>
        <option value="devops">DevOps Engineer</option>
        <option value="cyber">Cybersecurity Analyst</option>
        <option value="qa">QA Engineer</option>
      </select>
      <button onclick="showSkills()">Show Skills</button>
      <div class="card hidden" id="skillsCard">
        <h3 id="skillsTitle"></h3>
        <div class="skills-list" id="skillsList"></div>
      </div>
    </section>

    <hr class="section-divider">

    <!-- Education to Job Section -->
    <section>
      <h2>Find Suitable Jobs by Education</h2>
      <select class="select-edu" id="eduSelect">
        <option value="" disabled selected>Select your education</option>
        <option value="btechcs">B.Tech in Computer Science</option>
        <option value="bscit">B.Sc. IT/CS</option>
        <option value="mscai">M.Sc. AI/ML/Data Science</option>
        <option value="mca">MCA</option>
        <option value="btechother">B.Tech Other</option>
        <option value="diploma">Diploma in Engg/IT</option>
        <option value="nontech">Non-Tech Graduate</option>
      </select>
      <button onclick="suggestJob()">Suggest Jobs</button>
      <div class="card hidden" id="eduJobsCard">
        <h3>Recommended Job Roles</h3>
        <div id="eduJobsList" style="text-align:center; margin-top:0.3em;"></div>
      </div>
    </section>

    <hr class="section-divider">

    <!-- Pie Chart Section -->
    <section>
      <h2>Recent Job Market Trends</h2>
      <div class="piechart-container">
        <canvas id="jobPieChart" width="320" height="320"></canvas>
        <div style="font-size:0.95em;margin-top:0.7em;">Distribution of recent job postings by field</div>
      </div>
    </section>

    <hr class="section-divider">

    <!-- Quiz Section (expanded at bottom, always visible) -->
    <section class="quiz-section" id="quizSection">
      <h3 id="quizTitle" style="margin-bottom:0.5em;">Quiz</h3>
      <div id="quizQuestion" style="font-size:1.1em;"></div>
      <div class="quiz-options" id="quizOptions"></div>
      <div class="quiz-progress" id="quizProgress"></div>
      <button onclick="startQuiz()" id="startQuizBtn" style="margin-bottom:1em;">Take a Knowledge Quiz</button>
      <button onclick="nextQuizQuestion()" id="nextQuizBtn" class="hidden">Next</button>
      <div id="quizResult" style="margin-top:1em; font-weight:bold;"></div>
    </section>
  </main>
  <footer style="text-align:center; color:#888; padding:1.5rem 0;">&copy; 2025 Tech Career AI Portal</footer>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script>
    // Light/Dark Mode
    function toggleMode() {
      const body = document.body;
      const current = body.getAttribute('data-theme');
      const modeBtn = document.getElementById('modeBtn');
      const modeLabel = document.getElementById('modeLabel');
      if (current === 'light') {
        body.setAttribute('data-theme', 'dark');
        modeBtn.innerHTML = 'Light Mode';
        modeBtn.classList.add('light-mode');
        modeLabel.textContent = 'Current: Dark Mode';
      } else {
        body.setAttribute('data-theme', 'light');
        modeBtn.innerHTML = 'Dark Mode';
        modeBtn.classList.remove('light-mode');
        modeLabel.textContent = 'Current: Light Mode';
      }
    }

    // Resume Score AI (Simulated)
    const resumeInput = document.getElementById('resumeInput');
    resumeInput.addEventListener('change', function() {
      document.getElementById('scoreBtn').disabled = !this.files.length;
      document.getElementById('resumeScore').style.display = 'none';
    });
    function scoreResume() {
      const file = resumeInput.files[0];
      if (!file) return;
      const ext = file.name.split('.').pop().toLowerCase();
      let base = ext === 'pdf' ? 70 : 60;
      if (file.size > 300000) base += 10;
      if (file.size > 600000) base += 10;
      let score = Math.min(100, Math.floor(base + Math.random() * 20));

      let feedback = 'Very Good! Resume covers most essential sections.';
      if (score < 70) feedback = 'Needs Improvement. Try adding relevant skills and achievements!';
      else if (score < 85) feedback = 'Good. Add more details and tailor for the job role.';

      const out = `<b>Resume Score:</b> <span style="font-size:1.3em">${score}/100</span><br>
        <b>Feedback:</b> ${feedback}<br>
        <b>Tips:</b> Use clear sections (Summary, Skills, Experience, Education). Highlight measurable achievements.`;

      const box = document.getElementById('resumeScore');
      box.innerHTML = out;
      box.style.display = 'block';
      box.style.animation = "fadeIn 0.7s";
    }

    // Skills per job role
    // Each quiz now has at least 5 questions
    const SKILLS = {
      fullstack: {
        title: "Full Stack Developer",
        skills: [
          "HTML5/CSS3/JavaScript", "React or Angular", "Node.js / Express.js",
          "APIs (REST/GraphQL)", "Databases (SQL/NoSQL)", "Git & Version Control",
          "Testing (Jest/Mocha)", "CI/CD", "Cloud Platforms", "Problem Solving"
        ],
        quiz: [
          {
            q: "Which language is commonly used for both frontend and backend in web development?",
            options: ["Python", "JavaScript", "PHP", "Ruby"],
            a: 1
          },
          {
            q: "Which database is NoSQL?",
            options: ["MySQL", "MongoDB", "PostgreSQL", "SQLite"],
            a: 1
          },
          {
            q: "What does REST stand for?",
            options: ["Representational State Transfer", "Remote Execution Standard Transfer", "Rapid System Test", "Relational Structured Table"],
            a: 0
          },
          {
            q: "Which tool is commonly used for version control?",
            options: ["Git", "Figma", "Jira", "Slack"],
            a: 0
          },
          {
            q: "Which of the following is a popular backend JavaScript runtime?",
            options: ["Node.js", "Laravel", "Django", "Spring"],
            a: 0
          }
        ]
      },
      frontend: {
        title: "Frontend Developer",
        skills: [
          "HTML5/CSS3", "React.js", "JavaScript/TypeScript", "Responsive Design",
          "CSS Frameworks (Tailwind, Bootstrap)", "Figma/Design Tools", "Performance Optimization",
          "Accessibility (a11y)", "Testing (Jest/RTL)"
        ],
        quiz: [
          {
            q: "Which technology is used for responsive web layouts?",
            options: ["Flexbox", "C++", "MongoDB", "Docker"],
            a: 0
          },
          {
            q: "What does a11y stand for?",
            options: ["Accessibility", "Agility", "Array", "Algorithm"],
            a: 0
          },
          {
            q: "Which is a CSS framework?",
            options: ["Bootstrap", "Express", "Java", "NumPy"],
            a: 0
          },
          {
            q: "Which is a UI design tool?",
            options: ["Figma", "Node.js", "Nginx", "MySQL"],
            a: 0
          },
          {
            q: "Which language is used for DOM manipulation?",
            options: ["JavaScript", "Python", "C#", "PHP"],
            a: 0
          }
        ]
      },
      backend: {
        title: "Backend Developer",
        skills: [
          "Node.js / Express", "Python / Django", "Java / Spring", "APIs", "Databases",
          "Authentication & Security", "Containerization (Docker)", "Testing", "Design Patterns"
        ],
        quiz: [
          {
            q: "Which protocol is commonly used for APIs?",
            options: ["HTTP", "FTP", "SMTP", "SSH"],
            a: 0
          },
          {
            q: "Which tool is used for containerization?",
            options: ["Git", "Docker", "npm", "Webpack"],
            a: 1
          },
          {
            q: "Which is a Python web framework?",
            options: ["Django", "React", "Vue", "Angular"],
            a: 0
          },
          {
            q: "Which SQL command is used to fetch data?",
            options: ["SELECT", "INSERT", "UPDATE", "DELETE"],
            a: 0
          },
          {
            q: "Which is an example of authentication?",
            options: ["Login with password", "Data backup", "Load balancing", "Caching"],
            a: 0
          }
        ]
      },
      datasci: {
        title: "Data Scientist",
        skills: [
          "Python/R", "Pandas/Numpy", "Machine Learning", "Data Visualization", "Statistics",
          "SQL", "Deep Learning", "Model Deployment", "Big Data Tools (Spark, Hadoop)"
        ],
        quiz: [
          {
            q: "Which library is used for data manipulation in Python?",
            options: ["Pandas", "TensorFlow", "Flask", "Django"],
            a: 0
          },
          {
            q: "Which term refers to the process of splitting data for model evaluation?",
            options: ["Normalization", "Feature Engineering", "Cross-validation", "Tokenization"],
            a: 2
          },
          {
            q: "Which tool is used for big data processing?",
            options: ["Spark", "React", "Redis", "Docker"],
            a: 0
          },
          {
            q: "Which is a data visualization library?",
            options: ["Matplotlib", "NumPy", "Express", "FastAPI"],
            a: 0
          },
          {
            q: "Which concept is essential for supervised learning?",
            options: ["Labeled data", "No data", "Encrypted data", "Unstructured data"],
            a: 0
          }
        ]
      },
      ai: {
        title: "AI/ML Engineer",
        skills: [
          "Python", "TensorFlow/PyTorch", "Machine Learning Algorithms", "Data Preprocessing",
          "Model Training & Tuning", "Deployment (TF Serving, ONNX)", "Cloud ML Services"
        ],
        quiz: [
          {
            q: "Which framework is popular for deep learning?",
            options: ["React", "PyTorch", "Bootstrap", "Deno"],
            a: 1
          },
          {
            q: "What does 'overfitting' mean?",
            options: [
              "Model fits training data too well, poor on new data.",
              "Model is too simple.",
              "Model runs too fast.",
              "Model does not compile."
            ],
            a: 0
          },
          {
            q: "Which is a cloud-based ML service?",
            options: ["AWS SageMaker", "Express.js", "Jira", "Tailwind"],
            a: 0
          },
          {
            q: "Which library is used for neural networks in Python?",
            options: ["TensorFlow", "BeautifulSoup", "Pandas", "Scikit-learn"],
            a: 0
          },
          {
            q: "Which metric is used for classification accuracy?",
            options: ["Precision", "Sorting", "Clustering", "Parsing"],
            a: 0
          }
        ]
      },
      cloud: {
        title: "Cloud Engineer",
        skills: [
          "AWS/GCP/Azure", "Cloud Networking", "Serverless", "Containers (Docker, K8s)",
          "Infrastructure as Code (Terraform)", "Monitoring & Logging", "CI/CD in Cloud"
        ],
        quiz: [
          {
            q: "Which is a cloud provider?",
            options: ["AWS", "Redux", "Jest", "Figma"],
            a: 0
          },
          {
            q: "What does IaC stand for?",
            options: ["Infrastructure as Code", "Image and Cache", "Index and Compute", "Instance and Cluster"],
            a: 0
          },
          {
            q: "Which tool is used for cloud infrastructure automation?",
            options: ["Terraform", "React", "Express", "Redis"],
            a: 0
          },
          {
            q: "Which is a serverless offering?",
            options: ["AWS Lambda", "MySQL", "Webpack", "PostgreSQL"],
            a: 0
          },
          {
            q: "Which is a container orchestration system?",
            options: ["Kubernetes", "GitHub", "Numpy", "Figma"],
            a: 0
          }
        ]
      },
      devops: {
        title: "DevOps Engineer",
        skills: [
          "CI/CD Pipelines", "Docker/Kubernetes", "Cloud Platforms", "Monitoring", "Infrastructure as Code",
          "Linux", "Automation (Scripting)", "Version Control"
        ],
        quiz: [
          {
            q: "What tool is used for container orchestration?",
            options: ["Webpack", "Kubernetes", "Redux", "Flask"],
            a: 1
          },
          {
            q: "Which is a common CI/CD tool?",
            options: ["Jenkins", "React", "Photoshop", "Sass"],
            a: 0
          },
          {
            q: "Which language is often used for scripting in DevOps?",
            options: ["Bash", "CSS", "HTML", "Photoshop"],
            a: 0
          },
          {
            q: "Which OS is widely used in servers?",
            options: ["Linux", "Windows ME", "Android", "iOS"],
            a: 0
          },
          {
            q: "Which is a monitoring tool?",
            options: ["Prometheus", "Bootstrap", "Redux", "NumPy"],
            a: 0
          }
        ]
      },
      cyber: {
        title: "Cybersecurity Analyst",
        skills: [
          "Network Security", "Risk Assessment", "Vulnerability Scanning", "Incident Response",
          "Encryption", "Firewalls", "SIEM Tools"
        ],
        quiz: [
          {
            q: "What is the purpose of a firewall?",
            options: [
              "Block unauthorized access",
              "Render web pages",
              "Store passwords",
              "Compress images"
            ],
            a: 0
          },
          {
            q: "Which term means scrambling data to protect it?",
            options: ["Encryption", "Indexing", "Sorting", "Parsing"],
            a: 0
          },
          {
            q: "Which is a cyber attack type?",
            options: ["Phishing", "Rendering", "Compiling", "Parsing"],
            a: 0
          },
          {
            q: "What does SIEM stand for?",
            options: ["Security Information and Event Management", "Software Integration and Email Management", "System Information and Email Management", "Security Integration and Event Manager"],
            a: 0
          },
          {
            q: "Which is a vulnerability scanning tool?",
            options: ["Nessus", "Express", "TensorFlow", "Redux"],
            a: 0
          }
        ]
      },
      qa: {
        title: "QA Engineer",
        skills: [
          "Manual Testing", "Automated Testing (Selenium)", "Bug Tracking", "Test Case Design",
          "Regression Testing", "Performance Testing", "CI/CD Integration"
        ],
        quiz: [
          {
            q: "Which tool automates browser testing?",
            options: ["Selenium", "Figma", "Git", "TensorFlow"],
            a: 0
          },
          {
            q: "What is regression testing?",
            options: [
              "Testing after changes to ensure existing features work",
              "Testing user experience",
              "Testing security only",
              "Testing code style"
            ],
            a: 0
          },
          {
            q: "Which is a bug tracking system?",
            options: ["Jira", "Figma", "Slack", "Webpack"],
            a: 0
          },
          {
            q: "Which is a type of performance testing?",
            options: ["Load Testing", "Manual Testing", "Unit Testing", "Integration Testing"],
            a: 0
          },
          {
            q: "Which language is used in Selenium scripting?",
            options: ["Java", "HTML", "CSS", "SQL"],
            a: 0
          }
        ]
      }
    };

    function showSkills() {
      const sel = document.getElementById('jobSelect');
      const val = sel.value;
      if (!val || !SKILLS[val]) return;
      const card = document.getElementById('skillsCard');
      card.classList.remove('hidden');
      document.getElementById('skillsTitle').textContent = SKILLS[val].title + " - Key Skills:";

      const skillsArr = SKILLS[val].skills;
      let html = '';
      for (let i = 0; i < skillsArr.length; ++i) {
        html += `<span class="skill-chip" style="animation-delay:${i*0.07}s">${skillsArr[i]}</span>`;
      }
      document.getElementById('skillsList').innerHTML = html;
      document.getElementById('quizResult').textContent = '';
      document.getElementById('startQuizBtn').disabled = false;
    }

    let quizState = { job: null, idx: 0, score: 0, questions: [] };
    function startQuiz() {
      const sel = document.getElementById('jobSelect');
      const val = sel.value;
      if (!val || !SKILLS[val]) return;
      quizState = {
        job: val,
        idx: 0,
        score: 0,
        questions: shuffle(SKILLS[val].quiz)
      };
      showQuizQuestion();
      document.getElementById('quizResult').textContent = '';
    }
    function showQuizQuestion() {
      const { idx, questions } = quizState;
      const q = questions[idx];
      document.getElementById('quizTitle').textContent = `Quiz: ${SKILLS[quizState.job].title}`;
      document.getElementById('quizQuestion').textContent = q.q;
      const opts = q.options.map((opt, i) =>
        `<button class="option-btn" onclick="selectQuizOption(${i})">${opt}</button>`
      ).join('');
      document.getElementById('quizOptions').innerHTML = opts;
      document.getElementById('nextQuizBtn').classList.add('hidden');
      document.getElementById('quizProgress').textContent =
        `Question ${quizState.idx+1} of ${quizState.questions.length}`;
    }
    function selectQuizOption(selIdx) {
      const { idx, questions } = quizState;
      const q = questions[idx];
      const correct = q.a === selIdx;
      if (correct) quizState.score++;
      const btns = document.querySelectorAll('.quiz-section .option-btn');
      btns.forEach((btn, i) => {
        btn.disabled = true;
        btn.style.transition = "background 0.15s, color 0.15s";
        if (i === q.a) btn.style.background = '#22c55e';
        else if (i === selIdx) btn.style.background = '#ef4444';
        else btn.style.background = '#a1a1aa';
      });
      document.getElementById('nextQuizBtn').classList.remove('hidden');
    }
    function nextQuizQuestion() {
      quizState.idx++;
      if (quizState.idx < quizState.questions.length) {
        showQuizQuestion();
      } else {
        document.getElementById('quizQuestion').textContent = '';
        document.getElementById('quizOptions').innerHTML = '';
        document.getElementById('nextQuizBtn').classList.add('hidden');
        document.getElementById('quizProgress').textContent = '';
        document.getElementById('quizResult').textContent =
          `Your Score: ${quizState.score} / ${quizState.questions.length}`;
      }
    }
    function shuffle(arr){
      let a = arr.slice();
      for(let i=a.length-1;i>0;i--){
        let j=Math.floor(Math.random()*(i+1));
        [a[i],a[j]]=[a[j],a[i]];
      }
      return a;
    }

    const EDUJOBS = {
      btechcs: [
        "Full Stack Developer", "Backend Developer", "Frontend Developer", "Data Scientist",
        "AI/ML Engineer", "Cloud Engineer", "DevOps Engineer", "Cybersecurity Analyst", "QA Engineer"
      ],
      bscit: [
        "Frontend Developer", "QA Engineer", "Backend Developer", "Data Scientist", "Cloud Engineer"
      ],
      mscai: [
        "AI/ML Engineer", "Data Scientist", "Backend Developer", "Cloud Engineer"
      ],
      mca: [
        "Full Stack Developer", "Backend Developer", "Frontend Developer", "QA Engineer", "Cloud Engineer"
      ],
      btechother: [
        "QA Engineer", "Frontend Developer", "Cloud Engineer", "DevOps Engineer"
      ],
      diploma: [
        "QA Engineer", "Frontend Developer", "Cloud Support", "IT Support"
      ],
      nontech: [
        "QA Engineer", "IT Support", "Technical Writer"
      ]
    };
    function suggestJob() {
      const sel = document.getElementById('eduSelect');
      const val = sel.value;
      const card = document.getElementById('eduJobsCard');
      const listDiv = document.getElementById('eduJobsList');
      if (!val || !EDUJOBS[val]) {
        card.classList.add('hidden');
        return;
      }
      card.classList.remove('hidden');
      listDiv.innerHTML = '';
      const jobs = EDUJOBS[val];
      jobs.forEach((j, idx) => {
        const span = document.createElement('span');
        span.className = 'job-role-anim';
        span.textContent = j;
        span.style.animationDelay = (idx * 0.09) + "s";
        listDiv.appendChild(span);
      });
      card.style.animation = "popCard 0.7s";
    }

    const PIE_CHART_DATA = {
      labels: [
        "Full Stack Dev", "Frontend Dev", "Backend Dev", "Data Science", "AI/ML", "Cloud", "DevOps", "Cybersecurity", "QA"
      ],
      datasets: [{
        data: [20, 14, 16, 12, 10, 8, 10, 5, 5],
        backgroundColor: [
          "#6366f1","#22c55e","#f59e42","#38bdf8","#c026d3","#f43f5e","#a3e635","#fbbf24","#818cf8"
        ]
      }]
    };
    let jobPieChart = null;
    function renderPieChart() {
      const ctx = document.getElementById('jobPieChart').getContext('2d');
      if (jobPieChart) jobPieChart.destroy();
      jobPieChart = new Chart(ctx, {
        type: 'pie',
        data: PIE_CHART_DATA,
        options: {
          plugins: {
            legend: {
              labels: { color: document.body.getAttribute('data-theme') === 'dark' ? '#fff' : '#222' }
            }
          }
        }
      });
    }
    const observer = new MutationObserver(renderPieChart);
    observer.observe(document.body, { attributes: true, attributeFilter: ['data-theme'] });

    window.onload = function() {
      renderPieChart();
      document.getElementById('quizSection').classList.remove('hidden');
      document.getElementById('quizTitle').textContent = "Quiz";
      document.getElementById('quizQuestion').textContent = "Choose a job from above and click 'Take a Knowledge Quiz'!";
      document.getElementById('quizOptions').innerHTML = "";
      document.getElementById('quizProgress').textContent = "";
      document.getElementById('quizResult').textContent = "";
      document.getElementById('startQuizBtn').disabled = true;
    };

    document.getElementById('jobSelect').addEventListener('keydown', e => e.preventDefault());
    document.getElementById('eduSelect').addEventListener('keydown', e => e.preventDefault());
  </script>
</body>
</html>
