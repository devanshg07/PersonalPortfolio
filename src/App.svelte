<script>
	import { onMount } from 'svelte';
	// No props needed for now
	const sections = [
		{ id: 'about', label: 'About' },
		{ id: 'skills', label: 'Skills' },
		{ id: 'experience', label: 'Experience' },
		{ id: 'projects', label: 'Projects' },
		{ id: 'hobbies', label: 'Hobbies' },
		{ id: 'reachout', label: 'Reach Out!' },
		{ id: 'resume', label: 'Resume', external: true, url: 'https://docs.google.com/document/d/1ENQE7DyKBycYKb27E80NPjzEqrZV9eyk/edit' }
	];

	// Typewriter effect
	const phrases = [
		"My name is Devansh Goyal",
		"I'm an avid machine learning devotee",
		"I am a fullstack developer",
		"I'm a computer engineering student",
		"I am an aspiring business leader",
		"I enjoy working in collaborative environments"
	];

	let currentPhraseIndex = 0;
	let displayText = '';
	let isDeleting = false;
	let typingSpeed = 60;
	let pauseTime = 1200;

	function typeWriter() {
		const currentPhrase = phrases[currentPhraseIndex];
		if (isDeleting) {
			displayText = currentPhrase.substring(0, displayText.length - 1);
			if (displayText === '') {
				isDeleting = false;
				currentPhraseIndex = (currentPhraseIndex + 1) % phrases.length;
				setTimeout(typeWriter, 400);
				return;
			}
			setTimeout(typeWriter, typingSpeed / 2);
		} else {
			displayText = currentPhrase.substring(0, displayText.length + 1);
			if (displayText === currentPhrase) {
				isDeleting = true;
				setTimeout(typeWriter, pauseTime);
				return;
			}
			setTimeout(typeWriter, typingSpeed);
		}
	}

	let darkMode = false;

	onMount(() => {
		darkMode = localStorage.getItem('darkMode') === 'true';
		if (darkMode) document.body.classList.add('dark-mode');
		typeWriter();
	});

	function toggleDarkMode() {
		darkMode = !darkMode;
		if (darkMode) {
			document.body.classList.add('dark-mode');
			localStorage.setItem('darkMode', 'true');
		} else {
			document.body.classList.remove('dark-mode');
			localStorage.setItem('darkMode', 'false');
		}
	}
</script>

<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;700;900&display=swap" rel="stylesheet">
<!-- Font Awesome CDN -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css" />

<nav>
	<ul>
		{#each sections as section}
			<li>
				{#if section.external}
					<a href={section.url} target="_blank" rel="noopener">{section.label}</a>
				{:else}
					<a href={'#' + section.id}>{section.label}</a>
				{/if}
			</li>
		{/each}
	</ul>
	<button class="theme-toggle" on:click={toggleDarkMode} aria-label="Toggle light/dark mode">
		{#if darkMode}
			<i class="fa-solid fa-sun"></i>
		{:else}
			<i class="fa-solid fa-moon"></i>
		{/if}
	</button>
</nav>

<main>
	<section id="about">
		<h2><i class="fa-solid fa-user fa-fw section-icon"></i> About</h2>
		<div class="about-flex">
			<div class="about-left">
				<p class="typewriter">{displayText}<span class="cursor">|</span></p>
				<p>Hey! My name is Devansh Goyal, and welcome to my site! I study Computer Engineering at Queen's University and am originally from Mississauga, Ontario. I have experience in software development, with an aptitude in the field of machine learning. I have an ever-growing interest in hardware, and I aspire to build technical projects that integrate both fields of hardware and software. I enjoy experimenting with new technologies in the world of engineering and building impactful projects that have a positive impact on society. I am always interested in collaboration-based projects, which is why I consistently attend hackathons. I love visiting hackathons as it pushes me to my utter limits while making new, long-lasting friends and memories. I'm always down to working with new people, if you are interested in collaborating or simply want to have a chat, please reach out!</p>
			</div>
			<div class="about-right">
				<img class="profile-pic" src="/devanshpic.png" alt="Profile Picture" />
			</div>
		</div>
	</section>
	<section id="skills">
		<h2><i class="fa-solid fa-lightbulb fa-fw section-icon"></i> Technical Skills</h2>
		<div class="skills-belt">
			<div class="bubble-belt-inner">
				<span class="bubble"><i class="fa-brands fa-python"></i> Python</span>
				<span class="bubble"><i class="fa-brands fa-html5"></i> HTML</span>
				<span class="bubble"><i class="fa-brands fa-css3-alt"></i> CSS</span>
				<span class="bubble"><i class="fa-solid fa-brain"></i> Critical Thinking</span>
				<span class="bubble"><i class="fa-solid fa-code"></i> Problem Solving</span>
				<span class="bubble"><i class="fa-solid fa-lightbulb"></i> Curiousity</span>
				<span class="bubble"><i class="fa-solid fa-users"></i> Collaboration</span>
				<span class="bubble"><i class="fa-brands fa-react"></i> React.js</span>
				<span class="bubble"><i class="fa-brands fa-node-js"></i> Node.js</span>
				<span class="bubble"><i class="fa-brands fa-svelte"></i> Svelte.js</span>
				<span class="bubble"><i class="fa-brands fa-tensorflow"></i> TensorFlow</span>
				<span class="bubble"><i class="fa-brands fa-pytorch"></i> PyTorch</span>
				<span class="bubble"><i class="fa-brands fa-numpy"></i> NumPy</span>
				<span class="bubble"><i class="fa-brands fa-flask"></i> Flask</span>
				<span class="bubble"><i class="fa-brands fa-git-alt"></i> Git</span>
				<span class="bubble"><i class="fa-brands fa-opencv"></i> OpenCV</span>
				<span class="bubble"><i class="fa-brands fa-pandas"></i> Pandas</span>
			</div>
		</div>
	</section>
	<section id="experience">
		<h2><i class="fa-solid fa-briefcase fa-fw section-icon"></i> Experience</h2>
		<div class="experience-flex">
			<div class="exp-card">
				<div class="exp-header">
					<h3 class="exp-title">Machine Learning Intern</h3>
					<span class="exp-dates">Jul 2024 - Aug 2024</span>
				</div>
				<h4 class="exp-company">CoolR Group</h4>
				<ul class="exp-list">
					<li>Effectively built a machine learning model to detect real-time empty industrial shelves by processing a visual dataset from an IoT sensor.</li>
					<li>Cleaned a labeled dataset using Pandas and then applied data augmentation to train a YOLOv5 model by integrating PyTorch and OpenCV modules.</li>
					<li>Successfully automated empty stock detection, hence decreasing shelf inspection by &gt;20% and increasing product availability.</li>
				</ul>
				<div class="exp-bubbles">
					<span class="exp-bubble">PyTorch</span>
					<span class="exp-bubble">NumPy</span>
					<span class="exp-bubble">TensorFlow</span>
					<span class="exp-bubble">Python</span>
				</div>
				<a class="exp-link" href="https://coolrgroup.com" target="_blank" rel="noopener">Visit Website &rarr;</a>
			</div>
			<div class="exp-card shad-card right-card">
				<div class="exp-header">
					<h3 class="exp-title shad-title">Shad TMU Alum</h3>
					<span class="exp-dates">July 2024</span>
				</div>
				<h4 class="exp-company">Shad Canada @ Toronto Metropolitan University</h4>
				<ul class="exp-list">
					<li>Designed and prototyped TempoBOT, a green energy thermostat system that reduces AC emissions and expenses by using outside air for cooling.</li>
					<li>Gained hands-on experience in collaborative project development, technical design, and public speaking at a national STEM boot camp.</li>
				</ul>
				<div class="exp-bubbles">
					<span class="exp-bubble">Collaboration</span>
					<span class="exp-bubble">Leadership</span>
					<span class="exp-bubble">Public Speaking</span>
				</div>
				<a class="exp-link" href="https://www.shad.ca/" target="_blank" rel="noopener">Visit Website &rarr;</a>
			</div>
		</div>
	</section>
	<section id="projects">
		<h2><i class="fa-solid fa-code fa-fw section-icon"></i> Projects</h2>
		<div class="projects-flex">
			<div class="exp-card project-card">
				<div class="exp-header">
					<h3 class="exp-title project-title">Vanilla Neural Network</h3>
				</div>
				<ul class="exp-list">
					<li>Computed a neural network to make predictions of a student’s GPA using 4 different independent variables without any external machine learning libraries.</li>
					<li>Applied calculus and linear algebra concepts to implement the movement of neurons manually and calculate gradients and change network weights using optimization.</li>
					<li>Received a final validation error of &lt;0.5, resulting in feasible and precise predictions of a student’s GPA.</li>
				</ul>
				<div class="exp-bubbles">
					<span class="exp-bubble">Python</span>
					<span class="exp-bubble">Math</span>
					<span class="exp-bubble">Problem Solving</span>
				</div>
				<a class="exp-link" href="https://github.com/devanshg07/Vanilla-Neural-Network" target="_blank" rel="noopener">Visit Website &rarr;</a>
			</div>
			<div class="exp-card project-card">
				<div class="exp-header">
					<h3 class="exp-title project-title">LLM from Scratch</h3>
				</div>
				<ul class="exp-list">
					<li>Built a large language model from scratch using PyTorch, covering custom tokenization, model architecture, training, and text generation.</li>
					<li>Faced challenges with data quality and model output, but learned a lot about the intricacies of LLMs and enjoyed the process.</li>
				</ul>
				<div class="exp-bubbles">
					<span class="exp-bubble">PyTorch</span>
					<span class="exp-bubble">Python</span>
					<span class="exp-bubble">NLP</span>
				</div>
				<a class="exp-link" href="https://github.com/devanshg07/LLM" target="_blank" rel="noopener">Visit Website &rarr;</a>
			</div>
			<div class="exp-card project-card">
				<div class="exp-header">
					<h3 class="exp-title project-title">CiviClinic</h3>
				</div>
				<ul class="exp-list">
					<li>Created CiviClinic, an AI-powered web app designed to improve Canada’s healthcare system by reducing the number of unnecessary ER visits through machine learning based diagnosis and intelligent doctor matching.</li>
					<li>Used TensorFlow and PyTorch libraries to diagnose a patient using image processing and NLP, and the OpenAI API Key to match patients with the correct doctors, and provide medical advice.</li>
					<li>Reduced ER wait times by classifying non-critical patients using AI, ensuring that 1 in 7 unnecessary ER patients can take care of themselves without the need for medical support.</li>
				</ul>
				<div class="exp-bubbles">
					<span class="exp-bubble">TensorFlow</span>
					<span class="exp-bubble">PyTorch</span>
					<span class="exp-bubble">HTML</span>
					<span class="exp-bubble">Python</span>
					<span class="exp-bubble">SQL</span>
					<span class="exp-bubble">APIs</span>
					<span class="exp-bubble">Critical Thinking</span>
				</div>
				<a class="exp-link" href="https://github.com/devanshg07/CiviClinic" target="_blank" rel="noopener">Visit Website &rarr;</a>
			</div>
			<div class="exp-card project-card">
				<div class="exp-header">
					<h3 class="exp-title project-title">GrowTogether</h3>
				</div>
				<ul class="exp-list">
					<li>Developed a gamified urban gardening app that lets users track, update, and donate plants, earn points, and get AI-powered crop recommendations.</li>
					<li>Built a modern Flask app with leaderboard, map, and community features using Python, SQLAlchemy, and real gardening data.</li>
				</ul>
				<div class="exp-bubbles">
					<span class="exp-bubble">Python</span>
					<span class="exp-bubble">HTML</span>
					<span class="exp-bubble">CSS</span>
					<span class="exp-bubble">SQL</span>
				</div>
				<a class="exp-link" href="https://github.com/devanshg07/GrowTogether" target="_blank" rel="noopener">Visit Website &rarr;</a>
			</div>
		</div>
	</section>
	<section id="hobbies">
		<h2><i class="fa-solid fa-heart fa-fw section-icon"></i> Hobbies</h2>
		<div class="hobbies-belt">
			<div class="bubble-belt-inner hobbies-belt-inner">
				<span class="bubble"><i class="fa-solid fa-music"></i> Music</span>
				<span class="bubble"><i class="fa-solid fa-futbol"></i> Soccer</span>
				<span class="bubble"><i class="fa-solid fa-code"></i> Coding</span>
				<span class="bubble"><i class="fa-solid fa-palette"></i> Origami</span>
				<span class="bubble"><i class="fa-solid fa-dumbbell"></i> Badminton</span>
				<span class="bubble"><i class="fa-solid fa-gamepad"></i> Doomscrolling</span>
				<span class="bubble"><i class="fa-solid fa-utensils"></i> Cooking</span>
			</div>
		</div>
	</section>
	<section id="reachout">
		<h2><i class="fa-solid fa-paper-plane fa-fw section-icon"></i> Reach Out!</h2>
		<div class="reachout-links">
			<a class="insta-link" href="https://instagram.com/devanshg07" target="_blank" rel="noopener">Instagram: @devanshg07</a>
			<a class="github-link" href="https://github.com/devanshg07" target="_blank" rel="noopener">GitHub: devanshg07</a>
			<a class="linkedin-link" href="https://www.linkedin.com/in/devanshg07" target="_blank" rel="noopener">LinkedIn: Devanshg07</a>
			<a class="email-link" href="https://mail.google.com/mail/?view=cm&to=devanshgoyal087@gmail.com" target="_blank" rel="noopener">Email: devanshgoyal087@gmail.com</a>
		</div>
	</section>
</main>

<style>
nav {
	display: flex;
	justify-content: center;
	background: #fff;
	box-shadow: 0 2px 8px rgba(0,0,0,0.04);
	padding: 1em 0;
	margin-bottom: 2em;
	position: sticky;
	top: 0;
	z-index: 10;
}
nav ul {
	display: flex;
	gap: 2em;
	list-style: none;
	margin: 0;
	padding: 0;
}
nav a {
	color: #ff3e00;
	font-weight: bold;
	text-decoration: none;
	font-size: 2.5em;
	transition: color 0.2s, box-shadow 0.22s, transform 0.22s, background 0.22s;
	border-radius: 0.5em;
	padding: 0.1em 0.4em;
}
nav a:hover, nav a:focus {
	color: #a259e6;
	background: #fff6;
	box-shadow: 0 4px 24px #a259e644;
	transform: scale(1.08) rotate(-2deg);
}
main {
	max-width: none;
	margin-left: 20px;
	margin-right: 0;
	padding: 2em 1em;
}
.about-flex {
	display: flex;
	flex-direction: row;
	align-items: center;
	gap: 1em;
}
.about-left {
	flex: 2;
}
.about-right {
	flex: 0 0 280px;
	display: flex;
	justify-content: flex-end;
	align-items: center;
}
.profile-pic {
	width: 280px;
	height: 280px;
	object-fit: cover;
	border-radius: 50%;
	border: 3px solid #ff3e00;
	box-shadow: 0 2px 24px 0 #ff3e0044, 0 0 0 0 #a259e644;
	margin-left: -40px;
	animation: profile-float 4.5s ease-in-out infinite alternate, profile-glow 2.5s ease-in-out infinite alternate;
}
@keyframes profile-float {
	0% { transform: translateY(0); }
	100% { transform: translateY(-18px); }
}
@keyframes profile-glow {
	0% { box-shadow: 0 2px 24px 0 #ff3e0044, 0 0 0 0 #a259e644; }
	100% { box-shadow: 0 8px 48px 0 #ff3e00aa, 0 0 32px 8px #a259e688; }
}
.typewriter {
	font-size: 1.2em;
	font-family: 'Fira Mono', 'Consolas', monospace;
	color: #333;
	margin-bottom: 0.5em;
	min-height: 1.5em;
}
.cursor {
	display: inline-block;
	width: 1ch;
	animation: blink 1s steps(1) infinite, bounce 0.7s cubic-bezier(0.4,0.2,0.2,1) infinite alternate;
	vertical-align: bottom;
}
@keyframes blink {
	0%, 50% { opacity: 1; }
	51%, 100% { opacity: 0; }
}
@keyframes bounce {
	0% { transform: translateY(0); }
	100% { transform: translateY(-0.25em); }
}
section {
	margin-bottom: 3em;
	padding-bottom: 2em;
	border-bottom: 1px solid #eee;
}
section:last-child {
	border-bottom: none;
}
h2 {
	color: #ff3e00;
	margin-top: 0;
	font-size: 3em;
}
.about-left h2 {
	font-size: 3em;
}
.about-left .typewriter {
	font-size: 2em;
}
.about-left p {
	font-size: 1.5em;
}
#skills h3 {
	font-size: 2.2em;
}
.frontend-label {
	font-size: 2em;
}
#skills h5 {
	font-size: 1.2em;
}
.bubble-container {
	display: grid;
	grid-template-columns: repeat(8, 1fr);
	gap: 2em;
	margin-bottom: 1em;
	width: 100%;
	max-width: 100vw;
}
.bubble {
	display: flex;
	align-items: center;
	justify-content: center;
	padding: 1.2em 0;
	border-radius: 1.2em;
	font-size: 1.3em;
	font-weight: bold;
	width: 220px;
	min-height: 2.2em;
	transition: transform 0.18s cubic-bezier(0.4, 0.2, 0.2, 1), box-shadow 0.18s cubic-bezier(0.4, 0.2, 0.2, 1), background 0.18s;
	box-shadow: 0 2px 16px 0 rgba(31,38,135,0.13);
	background: rgba(255,255,255,0.85);
	backdrop-filter: blur(8px) saturate(1.2);
	border: 2.5px solid #fff6;
	margin-bottom: 0.5em;
}
.bubble:hover {
	transform: scale(1.13) rotate(-3deg);
	z-index: 2;
	box-shadow: 0 8px 32px 0 #a259e644, 0 2px 16px 0 #ff3e0044;
	background: linear-gradient(120deg, #fff6, #ffd6ba 80%);
}
.exp-card, .project-card, .shad-card {
	background: rgba(255,255,255,0.82);
	backdrop-filter: blur(16px) saturate(1.2);
	box-shadow: 0 8px 32px 0 rgba(31,38,135,0.13), 0 2px 8px 0 #a259e622;
	border-radius: 28px;
	border: 1.5px solid #e0e0e0;
	padding: 2.2em 2em 2em 2em;
	margin: 2em 0 2.5em 0;
	width: 500px;
	max-width: 90vw;
	transition: box-shadow 0.25s, transform 0.22s;
}
.exp-card:hover, .project-card:hover, .shad-card:hover {
	box-shadow: 0 16px 48px 0 rgba(31,38,135,0.22), 0 4px 24px 0 #a259e644;
	transform: translateY(-8px) scale(1.025) rotate(-1deg);
}
.exp-header {
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin-bottom: 0.2em;
}
.exp-title { color: #1976d2; }
.exp-company, .exp-dates { color: #555; }
.exp-desc, .exp-list {
	color: #222;
}
.exp-bubbles {
	display: flex;
	gap: 1em;
	margin-bottom: 1.2em;
	flex-wrap: wrap;
}
.exp-bubble {
	background: #e3e8f0;
	color: #1976d2;
	padding: 0.45em 1.3em;
	border-radius: 2em;
	font-size: 1em;
	font-weight: 600;
	border: 1.5px solid #1976d2;
	box-shadow: 0 1px 4px #e0e0e0;
	transition: background 0.2s, color 0.2s;
}
.exp-bubble:hover {
	background: #1976d2;
	color: #fff;
}
.exp-link {
	display: inline-block;
	margin-top: 0.5em;
	color: #1976d2;
	font-weight: 500;
	font-size: 1.1em;
	text-decoration: none;
	transition: color 0.18s;
}
.exp-link:hover {
	color: #1565c0;
	text-decoration: underline;
}
.exp-list {
	margin: 0 0 1em 1.2em;
	padding: 0;
	color: #e6e6f0;
	font-size: 1.15em;
	line-height: 1.5;
}
.exp-list li {
	margin-bottom: 0.5em;
}
body {
	font-family: 'Nunito', Arial, sans-serif;
	font-size: 1.1em;
	line-height: 1.7;
	margin: 0;
	padding: 0;
	background: linear-gradient(120deg, #f8fafc 0%, #fbeee6 100%);
	min-height: 100vh;
	position: relative;
	overflow-x: hidden;
}
body::before {
	content: '';
	position: fixed;
	top: -200px;
	left: -200px;
	width: 600px;
	height: 600px;
	background: radial-gradient(circle at 30% 30%, #a259e6 0%, transparent 70%);
	z-index: 0;
	filter: blur(60px);
	animation: float1 18s ease-in-out infinite alternate;
	pointer-events: none;
}
body::after {
	content: '';
	position: fixed;
	bottom: -200px;
	right: -200px;
	width: 600px;
	height: 600px;
	background: radial-gradient(circle at 70% 70%, #ff3e00 0%, transparent 70%);
	z-index: 0;
	filter: blur(60px);
	animation: float2 22s ease-in-out infinite alternate;
	pointer-events: none;
}
@keyframes float1 {
	0% { transform: translateY(0) scale(1); }
	100% { transform: translateY(80px) scale(1.08); }
}
@keyframes float2 {
	0% { transform: translateY(0) scale(1); }
	100% { transform: translateY(-80px) scale(1.08); }
}
h1, h2, h3, h4, h5, h6 {
	font-family: 'Nunito', Arial, sans-serif;
	font-weight: 900;
	margin-top: 0.7em;
	margin-bottom: 0.5em;
	letter-spacing: 0.01em;
}
p, li {
	font-family: 'Nunito', Arial, sans-serif;
	font-size: 1.1em;
	margin-bottom: 1em;
	color: #222;
}

/* Section heading colors */
section h2 {
	background: linear-gradient(90deg, #ff3e00 0%, #ffd6ba 20%, #1976d2 40%, #bae1ff 50%, #a259e6 60%, #f3e0ff 70%, #2ecc40 80%, #baffc9 90%, #f7b731 95%, #e17055 100%);
	-webkit-background-clip: text;
	-webkit-text-fill-color: transparent;
	font-size: 3em;
	font-weight: 900;
	margin-bottom: 0.5em;
}

/* Experience card tweaks for fun */
.exp-card {
	background: #f5f6fa;
	color: #222;
	border-radius: 16px;
	border: 1.5px solid #d1d5db;
	box-shadow: 0 0 16px 0 #e0e0e0;
	padding: 2.2em 2em 2em 2em;
	margin: 2em 0 2.5em 0;
	max-width: 600px;
}
.exp-title { color: #1976d2; }
.exp-company, .exp-dates { color: #555; }
.exp-bubble {
	background: #e3e8f0;
	color: #1976d2;
	padding: 0.45em 1.3em;
	border-radius: 2em;
	font-size: 1em;
	font-weight: 600;
	border: 1.5px solid #1976d2;
	box-shadow: 0 1px 4px #e0e0e0;
	transition: background 0.2s, color 0.2s;
}
.exp-bubble:hover {
	background: #1976d2;
	color: #fff;
}
.shad-title {
	color: #e17055;
}
.shad-card {
	border-left: 6px solid #e17055;
}

/* Fun, multi-colored skill bubbles for the belt */
.bubble-belt-inner .bubble:nth-child(8n+1), .hobbies-belt-inner .bubble:nth-child(7n+1) {
	background: linear-gradient(135deg, #ffb3ba 0%, #ffd6ba 100%);
	color: #ff3e00;
	border-color: #ff3e00;
}
.bubble-belt-inner .bubble:nth-child(8n+2), .hobbies-belt-inner .bubble:nth-child(7n+2) {
	background: linear-gradient(135deg, #bae1ff 0%, #e0f0ff 100%);
	color: #1976d2;
	border-color: #1976d2;
}
.bubble-belt-inner .bubble:nth-child(8n+3), .hobbies-belt-inner .bubble:nth-child(7n+3) {
	background: linear-gradient(135deg, #baffc9 0%, #eaffea 100%);
	color: #2ecc40;
	border-color: #2ecc40;
}
.bubble-belt-inner .bubble:nth-child(8n+4), .hobbies-belt-inner .bubble:nth-child(7n+4) {
	background: linear-gradient(135deg, #ffffba 0%, #fff6 100%);
	color: #e17055;
	border-color: #e17055;
}
.bubble-belt-inner .bubble:nth-child(8n+5), .hobbies-belt-inner .bubble:nth-child(7n+5) {
	background: linear-gradient(135deg, #e0bbff 0%, #f3e0ff 100%);
	color: #a259e6;
	border-color: #a259e6;
}
.bubble-belt-inner .bubble:nth-child(8n+6), .hobbies-belt-inner .bubble:nth-child(7n+6) {
	background: linear-gradient(135deg, #ffd6ba 0%, #ffe5e0 100%);
	color: #ff3e00;
	border-color: #ff3e00;
}
.bubble-belt-inner .bubble:nth-child(8n+7), .hobbies-belt-inner .bubble:nth-child(7n) {
	background: linear-gradient(135deg, #c9fff4 0%, #e0f0ff 100%);
	color: #00b894;
	border-color: #00b894;
}
.bubble-belt-inner .bubble:nth-child(8n), .hobbies-belt-inner .bubble:nth-child(7n+7) {
	background: linear-gradient(135deg, #f7b731 0%, #fff6 100%);
	color: #fff;
	border-color: #f7b731;
}
.skills-belt {
	overflow: hidden;
	width: 100%;
	margin: 2em 0 2.5em 0;
	background: transparent;
}
.bubble-belt-inner {
	display: flex;
	gap: 2em;
	animation: conveyor-belt 22s linear infinite;
	width: max-content;
}
@keyframes conveyor-belt {
	0% { transform: translateX(0); }
	100% { transform: translateX(-50%); }
}

/* Keep text readable */
p, li, .exp-list, .exp-desc {
	color: #222;
}
.experience-flex {
	display: flex;
	gap: 2em;
	flex-wrap: wrap;
	align-items: flex-start;
	justify-content: center;
}
.right-card {
	/* margin-left: auto; removed for alignment */
}
@media (max-width: 1100px) {
	.experience-flex, .projects-flex {
		flex-direction: column;
		align-items: center;
	}
	.exp-card, .project-card, .shad-card {
		width: 95vw;
		max-width: 600px;
	}
}
@media (max-width: 800px) {
	nav ul {
		gap: 1.2em;
	}
	nav a {
		font-size: 1.3em;
	}
	.exp-card, .project-card, .shad-card {
		padding: 1.2em 0.7em 1.2em 0.7em;
		width: 98vw;
		max-width: 99vw;
	}
	.bubble {
		font-size: 1em;
		width: 140px;
		padding: 0.7em 0;
	}
	.bubble-belt-inner, .hobbies-belt-inner {
		gap: 0.7em;
	}
	.skills-belt, .hobbies-belt {
		margin: 1em 0 1.5em 0;
	}
	.profile-pic {
		width: 120px;
		height: 120px;
		margin-left: 0;
	}
	.about-flex {
		flex-direction: column;
		align-items: center;
		gap: 1.2em;
	}
	section h2 {
		font-size: 2em;
	}
}
@media (max-width: 500px) {
	.exp-card, .project-card, .shad-card {
		padding: 0.7em 0.2em 0.7em 0.2em;
		width: 99vw;
		max-width: 100vw;
	}
	.bubble {
		font-size: 0.85em;
		width: 90px;
		padding: 0.4em 0;
	}
	.profile-pic {
		width: 70px;
		height: 70px;
	}
	section h2 {
		font-size: 1.2em;
	}
}
.projects-flex {
	display: flex;
	gap: 2em;
	flex-wrap: wrap;
	align-items: flex-start;
	justify-content: center;
}
.project-title {
	color: #2ecc40;
}
.project-card {
	border-left: 6px solid #2ecc40;
}
.hobbies-belt {
	overflow: hidden;
	width: 100%;
	margin: 2em 0 2.5em 0;
	background: transparent;
}
.hobbies-belt-inner {
	display: flex;
	gap: 2em;
	animation: conveyor-belt 18s linear infinite;
	width: max-content;
}
.reachout-links {
	margin-top: 1.5em;
}
.insta-link, .github-link, .linkedin-link, .email-link {
	display: inline-block;
	margin-left: 1em;
	padding: 0.7em 1.5em;
	color: #fff;
	font-weight: bold;
	border-radius: 2em;
	text-decoration: none;
	font-size: 1.2em;
	transition: box-shadow 0.22s, transform 0.22s, background 0.22s, color 0.22s;
	box-shadow: 0 2px 8px rgba(0,0,0,0.10);
	cursor: pointer;
}
.insta-link {
	background: linear-gradient(90deg, #fd5949 0%, #d6249f 50%, #285AEB 100%);
}
.insta-link:hover, .insta-link:focus {
	box-shadow: 0 6px 24px rgba(253,89,73,0.18), 0 1.5px 8px rgba(0,0,0,0.10);
	transform: scale(1.08) rotate(-2deg);
	background: linear-gradient(90deg, #285AEB 0%, #fd5949 100%);
}
.github-link {
	background: linear-gradient(90deg, #333 0%, #6e5494 100%);
}
.github-link:hover, .github-link:focus {
	box-shadow: 0 6px 24px rgba(110,84,148,0.18), 0 1.5px 8px rgba(0,0,0,0.10);
	transform: scale(1.08) rotate(-2deg);
	background: linear-gradient(90deg, #6e5494 0%, #333 100%);
}
.linkedin-link {
	background: linear-gradient(90deg, #0077b5 0%, #00c6ff 100%);
}
.linkedin-link:hover, .linkedin-link:focus {
	box-shadow: 0 6px 24px rgba(0,119,181,0.18), 0 1.5px 8px rgba(0,0,0,0.10);
	transform: scale(1.08) rotate(-2deg);
	background: linear-gradient(90deg, #00c6ff 0%, #0077b5 100%);
}
.email-link {
	background: linear-gradient(90deg, #ff5858 0%, #ffc371 100%);
}
.email-link:hover, .email-link:focus {
	box-shadow: 0 6px 24px rgba(255,88,88,0.18), 0 1.5px 8px rgba(0,0,0,0.10);
	transform: scale(1.08) rotate(-2deg);
	background: linear-gradient(90deg, #ffc371 0%, #ff5858 100%);
}
.section-icon {
	margin-right: 0.4em;
	color: inherit;
	font-size: 1.1em;
	vertical-align: middle;
	filter: drop-shadow(0 2px 4px #0001);
}
.bubble i {
	margin-right: 0.4em;
	font-size: 1em;
	vertical-align: middle;
}
:root {
	--bg: #f8fafc;
	--bg-gradient: linear-gradient(120deg, #f8fafc 0%, #fbeee6 100%);
	--card-bg: rgba(255,255,255,0.82);
	--card-border: #e0e0e0;
	--text: #222;
	--accent: #ff3e00;
	--bubble-bg: rgba(255,255,255,0.85);
	--bubble-shadow: 0 2px 16px 0 rgba(31,38,135,0.13);
}
body {
	background: var(--bg-gradient);
	color: var(--text);
}
.dark-mode {
	--bg: #181c24;
	--bg-gradient: linear-gradient(120deg, #181c24 0%, #232946 100%);
	--card-bg: rgba(30,34,44,0.92);
	--card-border: #232946;
	--text: #f8fafc;
	--accent: #ffb86c;
	--bubble-bg: rgba(30,34,44,0.92);
	--bubble-shadow: 0 2px 16px 0 #0008;
}
body, .dark-mode {
	background: var(--bg-gradient);
	color: var(--text);
}
.exp-card, .project-card, .shad-card {
	background: var(--card-bg);
	border: 1.5px solid var(--card-border);
	color: var(--text);
}
.bubble {
	background: var(--bubble-bg);
	box-shadow: var(--bubble-shadow);
	color: var(--text);
}
.theme-toggle {
	background: none;
	border: none;
	outline: none;
	cursor: pointer;
	font-size: 2em;
	margin-left: 1.5em;
	color: var(--accent);
	transition: color 0.2s, transform 0.2s;
	vertical-align: middle;
}
.theme-toggle:hover {
	color: #a259e6;
	transform: scale(1.15) rotate(-10deg);
}
</style>