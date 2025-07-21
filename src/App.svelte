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
		<div class="bubble-container">
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
	</section>
	<section id="experience">
		<h2>Experience</h2>
		<div class="exp-card">
			<div class="exp-header">
				<h3 class="exp-title">Software Engineer Intern</h3>
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
	</section>
	<section id="projects">
		<h2>Projects</h2>
		<p>Showcase your favorite or most impressive projects here.</p>
	</section>
	<section id="hobbies">
		<h2>Hobbies</h2>
		<p>Share your hobbies and interests here.</p>
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
	width: 100%;
	min-height: 2.2em;
	transition: transform 0.18s cubic-bezier(0.4, 0.2, 0.2, 1), box-shadow 0.18s cubic-bezier(0.4, 0.2, 0.2, 1);
	animation: bubble-rotate 4s linear infinite;
	box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
.bubble.reverse {
	animation: bubble-rotate-reverse 4s linear infinite;
}
@keyframes bubble-rotate {
	0% { transform: rotate(0deg); }
	100% { transform: rotate(360deg); }
}
@keyframes bubble-rotate-reverse {
	0% { transform: rotate(0deg); }
	100% { transform: rotate(-360deg); }
}
.bubble:hover {
	transform: scale(1.15) rotate(0deg) !important;
	box-shadow: 0 6px 24px rgba(255,62,0,0.18), 0 1.5px 8px rgba(0,0,0,0.10);
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
	max-width: 600px;
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

/* Fun, multi-colored skill bubbles */
.bubble-container .bubble:nth-child(4n+1) {
	background: #ffe5e0;
	color: #ff3e00;
	border-color: #ff3e00;
}
.bubble-container .bubble:nth-child(4n+2) {
	background: #e0f0ff;
	color: #1976d2;
	border-color: #1976d2;
}
.bubble-container .bubble:nth-child(4n+3) {
	background: #f3e0ff;
	color: #a259e6;
	border-color: #a259e6;
}
.bubble-container .bubble:nth-child(4n) {
	background: #eaffea;
	color: #2ecc40;
	border-color: #2ecc40;
}
.bubble {
	display: flex;
	align-items: center;
	justify-content: center;
	padding: 1.2em 0;
	border-radius: 0.18em;
	font-size: 2em;
	font-weight: bold;
	width: 100%;
	min-height: 2.2em;
	transition: transform 0.18s cubic-bezier(0.4, 0.2, 0.2, 1), box-shadow 0.18s cubic-bezier(0.4, 0.2, 0.2, 1);
	animation: bubble-rotate 4s linear infinite;
	box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
.bubble:hover {
	transform: scale(1.15) rotate(0deg) !important;
	box-shadow: 0 6px 24px rgba(255,62,0,0.18), 0 1.5px 8px rgba(0,0,0,0.10);
	z-index: 2;
}

/* Keep text readable */
p, li, .exp-list, .exp-desc {
	color: #222;
}
</style>