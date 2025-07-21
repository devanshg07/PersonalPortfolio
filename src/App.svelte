<script>
	// No props needed for now
	const sections = [
		{ id: 'about', label: 'About' },
		{ id: 'skills', label: 'Skills' },
		{ id: 'projects', label: 'Projects' },
		{ id: 'hobbies', label: 'Hobbies' },
		{ id: 'reachout', label: 'Reach Out!' }
	];
</script>

<nav>
	<ul>
		{#each sections as section}
			<li><a href={'#' + section.id}>{section.label}</a></li>
		{/each}
	</ul>
</nav>

<main>
	<section id="about">
		<h2>About</h2>
		<p>Write a short introduction about yourself here.</p>
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
	font-size: 1.1em;
	transition: color 0.2s;
}
nav a:hover {
	color: #333;
}
main {
	max-width: 700px;
	margin: 0 auto;
	padding: 2em 1em;
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
}
</style>