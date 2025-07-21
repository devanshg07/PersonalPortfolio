<script>
	import { onMount } from 'svelte';
	// No props needed for now
	const sections = [
		{ id: 'about', label: 'About' },
		{ id: 'skills', label: 'Skills' },
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
		<h2>Skills</h2>
		<p>List your key skills and technologies here.</p>
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
</style>