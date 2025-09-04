<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <title>Student Portfolio</title>
  <style>
    *{margin:0;padding:0;box-sizing:border-box;font-family:Arial,sans-serif;}
    body{line-height:1.6;background:#f4f4f4;color:#333;}

    /* Navbar */
    header{background:#333;color:#fff;padding:1rem;}
    .navbar{display:flex;justify-content:space-between;align-items:center;}
    .logo{font-size:1.5rem;font-weight:bold;}
    .nav-links{list-style:none;display:flex;}
    .nav-links li{margin:0 10px;}
    .nav-links a{color:white;text-decoration:none;padding:5px 10px;}
    .nav-links a:hover{background:#555;border-radius:5px;}

    /* Hero */
    .hero{display:flex;justify-content:center;align-items:center;height:80vh;text-align:center;background:#222;color:white;}
    .hero h1{font-size:2.5rem;}
    .hero span{color:#00adb5;}
    .btn{display:inline-block;margin-top:15px;padding:10px 20px;background:#00adb5;color:white;text-decoration:none;border-radius:5px;}

    /* About */
    .about{padding:2rem;text-align:center;background:white;}
    .about-content{max-width:800px;margin:auto;}
    .about img{width:150px;border-radius:50%;margin-bottom:15px;}

    /* Projects */
    .projects{padding:2rem;background:#f9f9f9;}
    .project-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:1rem;}
    .project-card{background:white;padding:1rem;border-radius:8px;box-shadow:0 0 5px rgba(0,0,0,0.1);}
    .project-card h3{margin-bottom:10px;}

    /* Quiz App */
    .quiz-container{background:white;padding:20px;border-radius:10px;box-shadow:0 0 10px rgba(0,0,0,0.2);max-width:500px;margin:10px auto;}
    .quiz-container ul{list-style:none;margin-bottom:20px;}
    .quiz-container li{margin:10px 0;}
    .quiz-container button{background:#333;color:white;padding:10px 15px;border:none;border-radius:5px;cursor:pointer;}
    .quiz-container button:hover{background:#555;}
    .result{font-size:18px;font-weight:bold;text-align:center;}

    /* Blog */
    .blog-container{max-width:800px;margin:20px auto;padding:10px;}
    .post{background:white;padding:15px;margin-bottom:20px;border-radius:8px;box-shadow:0 0 5px rgba(0,0,0,0.1);}
    .post h2{margin:0 0 10px;}
    .post small{color:gray;font-size:12px;}

    /* Contact */
    .contact{padding:2rem;text-align:center;background:white;}
    .contact form{display:flex;flex-direction:column;gap:10px;max-width:400px;margin:auto;}
    .contact input,.contact textarea{padding:10px;border:1px solid #ccc;border-radius:5px;}
    .contact button{padding:10px;background:#00adb5;color:white;border:none;border-radius:5px;cursor:pointer;}
    .contact button:hover{background:#007a7e;}

    footer{text-align:center;background:#333;color:white;padding:1rem;margin-top:1rem;}
  </style>
</head>
<body>

  <!-- Navbar -->
  <header>
    <nav class="navbar">
      <div class="logo">MyPortfolio</div>
      <ul class="nav-links">
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#projects">Projects</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <!-- Hero -->
  <section id="home" class="hero">
    <div class="hero-content">
      <h1>Hello, I'm <span>MR Sunil Kumar</span></h1>
      <p>I am the student</p>
      <a href="#projects" class="btn">View My Work</a>
    </div>
  </section>

  <!-- About -->
  <section id="about" class="about">
    <h2>About Me</h2>
    <div class="about-content">
      <img src="IMG_20250301_123505.jpg" alt="Profile Photo">
      <p>I am a student enthusiastic about technology and design. I love building interactive,
        user-friendly web applications and exploring new tools in the tech world.</p>
    </div>
  </section>

  <!-- Projects -->
  <section id="projects" class="projects">
    <h2>My Projects</h2>
    <div class="project-grid">

      <!-- Project 1 -->
      <div class="project-card">
        <h3>Project 1</h3>
        <p>A simple responsive website.</p>
        <p>(Demo site placeholder)</p>
      </div>

      <!-- Project 2 - Quiz App -->
      <div class="project-card">
        <h3>Project 2</h3>
        <p>JavaScript-based quiz app.</p>
        <div class="quiz-container" id="quiz">
          <h2 id="question">Question text</h2>
          <ul>
            <li><label><input type="radio" name="answer" class="answer" id="a"> <span id="a_text">Answer A</span></label></li>
            <li><label><input type="radio" name="answer" class="answer" id="b"> <span id="b_text">Answer B</span></label></li>
            <li><label><input type="radio" name="answer" class="answer" id="c"> <span id="c_text">Answer C</span></label></li>
            <li><label><input type="radio" name="answer" class="answer" id="d"> <span id="d_text">Answer D</span></label></li>
          </ul>
          <button id="submit">Submit</button>
          <div class="result" id="result"></div>
        </div>
      </div>

      <!-- Project 3 - Blog -->
      <div class="project-card">
        <h3>Project 3</h3>
        <p>Personal blog with CMS.</p>
        <div class="blog-container" id="postsContainer"></div>
      </div>

    </div>
  </section>

  <!-- Contact -->
  <section id="contact" class="contact">
    <h2>Contact Me</h2>
    <form id="contact-form">
      <input type="text" id="name" name="user_name" placeholder="Your Name" required>
      <input type="email" id="email" name="user_email" placeholder="Your Email" required>
      <textarea id="message" name="message" placeholder="Your Message" required></textarea>
      <button type="submit">Send</button>
    </form>
    <p id="form-status"></p>
  </section>

  <!-- Footer -->
  <footer>
    <p>&copy; 2025 MR Sunil Kumar | All rights reserved</p>
  </footer>

  <!-- Quiz Script -->
  <script>
    const quizData = [
      { question: "What does HTML stand for?", a: "Hyper Text Markup Language", b: "High Text Markup Language", c: "Hyperlinks and Text Markup Language", d: "Home Tool Markup Language", correct: "a" },
      { question: "Which language is used for styling web pages?", a: "HTML", b: "JQuery", c: "CSS", d: "XML", correct: "c" },
      { question: "Which is not a JavaScript Framework?", a: "React", b: "Angular", c: "Vue", d: "Django", correct: "d" },
      { question: "Which is used for database?", a: "PHP", b: "MySQL", c: "HTML", d: "CSS", correct: "b" }
    ];

    const quiz = document.getElementById("quiz");
    const answerEls = document.querySelectorAll(".answer");
    const questionEl = document.getElementById("question");
    const a_text = document.getElementById("a_text");
    const b_text = document.getElementById("b_text");
    const c_text = document.getElementById("c_text");
    const d_text = document.getElementById("d_text");
    const submitBtn = document.getElementById("submit");

    let currentQuiz = 0;
    let score = 0;

    loadQuiz();

    function loadQuiz() {
      deselectAnswers();
      const currentQuizData = quizData[currentQuiz];
      questionEl.innerText = currentQuizData.question;
      a_text.innerText = currentQuizData.a;
      b_text.innerText = currentQuizData.b;
      c_text.innerText = currentQuizData.c;
      d_text.innerText = currentQuizData.d;
    }

    function getSelected() {
      let answer;
      answerEls.forEach(el => { if (el.checked) answer = el.id; });
      return answer;
    }

    function deselectAnswers() { answerEls.forEach(el => el.checked = false); }

    submitBtn.addEventListener("click", () => {
      const answer = getSelected();
      if (answer) {
        if (answer === quizData[currentQuiz].correct) score++;
        currentQuiz++;
        if (currentQuiz < quizData.length) {
          loadQuiz();
        } else {
          quiz.innerHTML = `<h2 class="result">You answered correctly ${score}/${quizData.length} questions.</h2>
                            <button onclick="location.reload()">Restart</button>`;
        }
      }
    });

    // Blog Script
    function loadPosts() {
      const postsContainer = document.getElementById("postsContainer");
      const posts = JSON.parse(localStorage.getItem("blogPosts")) || [
        { title: "My First Post", date: new Date(), content: "Welcome to my new blog!" }
      ];
      postsContainer.innerHTML = "";
      posts.reverse().forEach(post => {
        const postEl = document.createElement("div");
        postEl.classList.add("post");
        postEl.innerHTML = `<h2>${post.title}</h2>
          <small>${new Date(post.date).toLocaleString()}</small>
          <p>${post.content}</p>`;
        postsContainer.appendChild(postEl);
      });
    }
    loadPosts();
  </script>
</body>
</html>
