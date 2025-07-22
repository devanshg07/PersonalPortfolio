<script>
	import { onMount } from 'svelte';
	// No props needed for now
	const sections = [
		{ id: 'about', label: 'About' },
		{ id: 'skills', label: 'Technical Skills' },
		{ id: 'experience', label: 'Experience' },
		{ id: 'projects', label: 'Projects' },
		{ id: 'hobbies', label: 'Hobbies' },
		{ id: 'reachout', label: 'Reach Out!' }
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

	onMount(() => {
		typeWriter();
	});
</script>

<nav>
	<ul>
		{#each sections as section}
			<li><a href={'#' + section.id}>{section.label}</a></li>
		{/each}
	</ul>
</nav>

<main>
	<section id="about" class="about-flex">
		<div class="about-left">
			<h2>About</h2>
			<p class="typewriter">{displayText}<span class="cursor">|</span></p>
			<p>Hey! My name is Devansh Goyal, and welcome to my site! I study Computer Engineering at Queen's University and am originally from Mississauga, Ontario. I have experience in software development, with an aptitude in the field of machine learning. I have an ever-growing interest in hardware, and I aspire to build technical projects that integrate both fields of hardware and software. I enjoy experimenting with new technologies in the world of engineering and building impactful projects that have a positive impact on society. I am always interested in collaboration-based projects, which is why I consistently attend hackathons. I love visiting hackathons as it pushes me to my utter limits while making new, long-lasting friends and memories. I'm always down to working with new people, if you are interested in collaborating or simply want to have a chat, please reach out!</p>
		</div>
		<div class="about-right">
			<img class="profile-pic" src="/devanshpic.png" alt="Profile Picture" />
		</div>
	</section>
	<section id="skills">
		<h2>Technical Skills</h2>
		<div class="skills-belt">
			<div class="bubble-belt-inner">
				<span class="bubble">HTML</span>
				<span class="bubble reverse">CSS</span>
				<span class="bubble">JavaScript</span>
				<span class="bubble reverse">Python</span>
				<span class="bubble">Java</span>
				<span class="bubble reverse">C++</span>
				<span class="bubble">React.js</span>
				<span class="bubble reverse">Node.js</span>
				<span class="bubble">Svelte.js</span>
				<span class="bubble reverse">TensorFlow</span>
				<span class="bubble">PyTorch</span>
				<span class="bubble reverse">NumPy</span>
				<span class="bubble">Flask</span>
				<span class="bubble reverse">Git</span>
				<span class="bubble">OpenCV</span>
				<span class="bubble reverse">Pandas</span>
				<!-- Duplicate for seamless loop -->
				<span class="bubble">HTML</span>
				<span class="bubble reverse">CSS</span>
				<span class="bubble">JavaScript</span>
				<span class="bubble reverse">Python</span>
				<span class="bubble">Java</span>
				<span class="bubble reverse">C++</span>
				<span class="bubble">React.js</span>
				<span class="bubble reverse">Node.js</span>
				<span class="bubble">Svelte.js</span>
				<span class="bubble reverse">TensorFlow</span>
				<span class="bubble">PyTorch</span>
				<span class="bubble reverse">NumPy</span>
				<span class="bubble">Flask</span>
				<span class="bubble reverse">Git</span>
				<span class="bubble">OpenCV</span>
				<span class="bubble reverse">Pandas</span>
			</div>
		</div>
	</section>
	<section id="experience">
		<h2>Experience</h2>
		<div class="experience-flex">
			<div class="exp-card">
				<div class="exp-header">
					<h3 class="exp-title">Machine Learning Intern</h3>
					<span class="exp-dates">Jul 2024 - Aug 2024</span>
				</div>
				<h4 class="exp-company">CoolR Group</h4>
				<ul class="exp-list">
					<li>Developed and fine-tuned deep learning models (using PyTorch and TensorFlow) to automatically detect out-of-stock products and optimize inventory from images captured by IoT cameras in retail stores.</li>
					<li>Collaborated with cross-functional teams to deploy ML models into production, integrating them with CoolR’s StoreAware SaaS platform for real-time analytics and actionable insight.</li>
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
		<h2>Projects</h2>
		<div class="projects-flex">
			<div class="exp-card project-card">
				<div class="exp-header">
					<h3 class="exp-title project-title">Vanilla Neural Network</h3>
				</div>
				<ul class="exp-list">
					<li>Built a neural network from scratch in Python using only basic math, without any machine learning libraries.</li>
					<li>Learned the fundamentals of forward/backward propagation and gradients by implementing all computations manually.</li>
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
					<h3 class="exp-title project-title">LLM</h3>
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
					<li>Developed an AI-powered healthcare app that lets users check symptoms with GPT, scan wounds using computer vision, and get matched to doctors or clinics nearby.</li>
					<li>Built a modern Flask app with instant health assessments, smart injury analysis, and an interactive care map using Python, machine learning, and real medical data.</li>
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
		<h2>Hobbies</h2>
		<div class="hobbies-belt">
			<div class="bubble-belt-inner hobbies-belt-inner">
				<span class="bubble">Coding</span>
				<span class="bubble">Music</span>
				<span class="bubble">Origami</span>
				<span class="bubble">Soccer</span>
				<span class="bubble">Badminton</span>
				<span class="bubble">Doomscrolling</span>
				<span class="bubble">Cooking</span>
				<!-- Duplicate for seamless loop -->
				<span class="bubble">Coding</span>
				<span class="bubble">Music</span>
				<span class="bubble">Origami</span>
				<span class="bubble">Soccer</span>
				<span class="bubble">Badminton</span>
				<span class="bubble">Doomscrolling</span>
				<span class="bubble">Cooking</span>
			</div>
		</div>
	</section>
	<section id="reachout">
		<h2>Reach Out!</h2>
		<p>Provide your contact info or a contact form here.</p>
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
	transition: color 0.2s;
}
nav a:hover {
	color: #333;
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
	box-shadow: 0 2px 8px rgba(0,0,0,0.08);
	margin-left: -40px;
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
	animation: blink 1s steps(1) infinite;
}
@keyframes blink {
	0%, 50% { opacity: 1; }
	51%, 100% { opacity: 0; }
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
	border-radius: 0.18em;
	font-size: 2em;
	font-weight: bold;
	width: 220px;
	min-height: 2.2em;
	transition: transform 0.18s cubic-bezier(0.4, 0.2, 0.2, 1), box-shadow 0.18s cubic-bezier(0.4, 0.2, 0.2, 1);
	box-shadow: 0 1px 8px rgba(0,0,0,0.10);
	/* Remove animation and rotation */
}
.bubble:hover {
	transform: scale(1.12);
	z-index: 2;
}
.exp-card {
	background: #f5f6fa;
	color: #222;
	border-radius: 16px;
	border: 1.5px solid #d1d5db;
	box-shadow: 0 0 16px 0 #e0e0e0;
	padding: 2.2em 2em 2em 2em;
	margin: 2em 0 2.5em 0;
	width: 500px;
	max-width: 90vw;
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
	background: linear-gradient(135deg, #f8fafc 0%, #fbeee6 100%);
}

/* Section heading colors */
#about h2 { color: #ff3e00; }
#skills h2 { color: #1976d2; }
#experience h2 { color: #a259e6; }
#projects h2 { color: #2ecc40; }
#hobbies h2 { color: #f7b731; }
#reachout h2 { color: #e17055; }

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
.bubble-belt-inner .bubble:nth-child(8n+1) {
	background: #ffb3ba;
	color: #fff;
	border: 2.5px solid #ff3e00;
}
.bubble-belt-inner .bubble:nth-child(8n+2) {
	background: #bae1ff;
	color: #1976d2;
	border: 2.5px solid #1976d2;
}
.bubble-belt-inner .bubble:nth-child(8n+3) {
	background: #baffc9;
	color: #2ecc40;
	border: 2.5px solid #2ecc40;
}
.bubble-belt-inner .bubble:nth-child(8n+4) {
	background: #ffffba;
	color: #e17055;
	border: 2.5px solid #e17055;
}
.bubble-belt-inner .bubble:nth-child(8n+5) {
	background: #e0bbff;
	color: #a259e6;
	border: 2.5px solid #a259e6;
}
.bubble-belt-inner .bubble:nth-child(8n+6) {
	background: #ffd6ba;
	color: #ff3e00;
	border: 2.5px solid #ff3e00;
}
.bubble-belt-inner .bubble:nth-child(8n+7) {
	background: #c9fff4;
	color: #00b894;
	border: 2.5px solid #00b894;
}
.bubble-belt-inner .bubble:nth-child(8n) {
	background: #f7b731;
	color: #fff;
	border: 2.5px solid #f7b731;
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
	.experience-flex {
		flex-direction: column;
		align-items: center;
	}
	.exp-card {
		width: 95vw;
		max-width: 600px;
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
</style>