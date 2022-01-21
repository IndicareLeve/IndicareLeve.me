<main class="grid">
	<div class="header">
		<h1>
			<span class="animate">I</span>
			<span transition:flip="{{delayInSec:2}}">n</span>
			<span transition:flip="{{delayInSec:3}}">d</span>
			<span transition:flip="{{delayInSec:4}}">i</span>
			<span transition:flip="{{delayInSec:5}}">c</span>
			<span transition:flip="{{delayInSec:6}}">a</span>
			<span transition:flip="{{delayInSec:7}}">r</span>
			<span transition:flip="{{delayInSec:8}}">e</span>
			<span transition:flip="{{delayInSec:9}}">L</span>
			<span transition:flip="{{delayInSec:10}}">e</span>
			<span transition:flip="{{delayInSec:11}}">v</span>
			<span transition:flip="{{delayInSec:12}}">e</span>
			<span transition:flip="{{delayInSec:13}}">.</span>
		</h1>
		<h6>aka Daniele Cervi</h6>
	</div>
	<div class="intro">
		<p class="intro">Geek, developer, motorcyclist, mech keyboard lover. Not necessarily in this order.</p>
	</div>
	<div class="under-construction">
		<p class="under-construction">🚧 This is under construction! 🚧</p>
	</div>
	<div class="work">
		<p class="collaborate">If you'd like to collaborate on websites, integrations or anything code-related please <a href="mailto:indicareleve@gmail.com">drop me a line</a>!</p>
		<p class="work">If you are a recruiter, you might want to <a href="https://raw.githubusercontent.com/IndicareLeve/resume/master/resume.pdf">take a look at my cv</a>.</p>
	</div>
</main>

<script lang="ts">
	import { elasticOut } from 'svelte/easing';

	function flip(node, {delayInSec}) {
		return {
			delay: delayInSec * 200,
			duration: 600,
			css: (t, u) => `
				transform: rotateY(${360*t*2}deg) 
			`
		};
	}

	function animationend(event) {
		console.log(event)
	}
</script>