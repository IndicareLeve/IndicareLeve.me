<script lang="ts">
	import { onMount } from 'svelte';

	const text = [
		{
			position: 0,
			from: {
				letter: 'i',
				class: 'magenta'
			},
			to: {
				letter: 'D',
				class: 'yellow'
			}
		},
		{
			position: 1,
			from: {
				letter: 'n',
				class: 'yellow'
			},
			to: {
				letter: 'a',
				class: ''
			}
		},
		{
			position: 2,
			from: {
				letter: 'D',
				class: 'yellow'
			},
			to: {
				letter: 'n',
				class: 'yellow'
			}
		},
		{
			position: 4,
			from: {
				letter: 'C',
				class: 'magenta'
			},
			to: {
				letter: 'e',
				class: 'yellow'
			}
		},
		{
			position: 5,
			from: {
				letter: 'a',
				class: 'yellow'
			},
			to: {
				letter: 'l',
				class: 'yellow'
			}
		},
		{
			position: 6,
			from: {
				letter: 'r',
				class: 'magenta'
			},
			to: {
				letter: 'e',
				class: 'yellow'
			}
		},
		{
			position: 7,
			from: {
				letter: 'e',
				class: 'magenta'
			},
			to: {
				letter: 'C',
				class: 'magenta'
			}
		},
		{
			position: 8,
			from: {
				letter: 'l',
				class: 'yellow'
			},
			to: {
				letter: 'e',
				class: 'magenta'
			}
		},
		{
			position: 9,
			from: {
				letter: 'e',
				class: 'yellow'
			},
			to: {
				letter: 'r',
				class: 'magenta'
			}
		},
		{
			position: 11,
			from: {
				letter: 'e',
				class: 'yellow'
			},
			to: {
				letter: 'i',
				class: 'magenta'
			}
		}
	];

	const chars = '!<>-_\\/[]{}—=+*^?#________';

	async function switchName(realName: boolean) {
		let items = Array.from(document.querySelectorAll('.flex div'));
		let toSwitch = text;
		while (toSwitch.length > 0) {
			let rnd = Math.floor(Math.random() * toSwitch.length);
			let item = toSwitch[rnd];
			toSwitch = toSwitch.filter((i) => i.position !== item.position);

			//make it gray and scramble the chars
			let name = realName ? item.to : item.from;
			setTimeout(async () => {
				await scrambleChar(items[item.position], name.letter, name.class);
			}, Math.random() * 2000);
		}
	}

	async function scrambleChar(el: Element, to: string, className: string) {
		el.className = 'gray';
		let iterations = Math.random() * chars.length;
		for (let i = 0; i < iterations; i++) {
			el.innerHTML = await getNextLetter(Math.random() * 250);
		}

		el.innerHTML = to;
		el.className = className;
	}

	function getNextLetter(delay: number): Promise<string> {
		return new Promise((resolve) => {
			let letter = '';
			setTimeout(() => {
				letter = chars[Math.floor(Math.random() * chars.length)];
				resolve(letter);
			}, delay);
		});
	}

	onMount(async () => {
		let realName = true;
		setTimeout(() => {
			switchName(true);
			realName = !realName;
		}, 2000);
		setInterval(() => {
			switchName(false);
			realName = !realName;
		}, 10000);
	});

	console.log('made with just a few swears by a backend guy :)');
</script>

<main class="grid">
	<div class="header">
		<h1 class="flex">
			<div class="magenta">i</div>
			<div class="yellow">n</div>
			<div class="yellow">D</div>
			<div class="yellow">i</div>
			<div class="magenta">C</div>
			<div class="yellow">a</div>
			<div class="magenta">r</div>
			<div class="magenta">e</div>
			<div class="yellow">l</div>
			<div class="yellow">e</div>
			<div class="magenta">v</div>
			<div class="yellow">e</div>
			<div class="yellow">.</div>
		</h1>
	</div>
	<div class="intro">
		<p class="intro">GeEk • deVelOpeR • PetroLhead • mecH keyBoArd lover • crypto eNthusiasT</p>
		<p>Not necessArilY in this oRDer.</p>
	</div>
	<div class="work">
		<p>
			if you'd like to collaborate on websites, integrations or anything code-related please <a
				class="magenta"
				href="mailto:dan@indicareleve.me">drop me a line</a
			>!
		</p>
		<p class="mt-1">
			if you are a recruiter, you might want to <a
				class="magenta"
				href="https://raw.githubusercontent.com/IndicareLeve/resume/master/resume.pdf"
				>take a look at my cv</a
			>.
		</p>
	</div>
	<div class="social">
		<a href="https://github.com/IndicareLeve" target="_blank">
			<svg
				class="social-icon from-bottom github yellow"
				height="24"
				role="img"
				viewBox="0 0 24 24"
				xmlns="http://www.w3.org/2000/svg"
				><title>GitHub</title><path
					d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"
				/></svg
			>
		</a>
		<a href="https://www.linkedin.com/in/danielecervi/" target="_blank">
			<svg
				class="social-icon from-bottom linkedin yellow"
				height="24"
				role="img"
				viewBox="0 0 24 24"
				xmlns="http://www.w3.org/2000/svg"
				><title>LinkedIn</title><path
					d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"
				/></svg
			>
		</a>
		<a href="https://www.reddit.com/u/salamadonna" target="_blank">
			<svg
				class="social-icon from-bottom reddit yellow"
				xmlns="http://www.w3.org/2000/svg"
				width="24"
				viewBox="0 0 24 24"
				><path
					d="M14.238 15.348c.085.084.085.221 0 .306-.465.462-1.194.687-2.231.687l-.008-.002-.008.002c-1.036 0-1.766-.225-2.231-.688-.085-.084-.085-.221 0-.305.084-.084.222-.084.307 0 .379.377 1.008.561 1.924.561l.008.002.008-.002c.915 0 1.544-.184 1.924-.561.085-.084.223-.084.307 0zm-3.44-2.418c0-.507-.414-.919-.922-.919-.509 0-.923.412-.923.919 0 .506.414.918.923.918.508.001.922-.411.922-.918zm13.202-.93c0 6.627-5.373 12-12 12s-12-5.373-12-12 5.373-12 12-12 12 5.373 12 12zm-5-.129c0-.851-.695-1.543-1.55-1.543-.417 0-.795.167-1.074.435-1.056-.695-2.485-1.137-4.066-1.194l.865-2.724 2.343.549-.003.034c0 .696.569 1.262 1.268 1.262.699 0 1.267-.566 1.267-1.262s-.568-1.262-1.267-1.262c-.537 0-.994.335-1.179.804l-2.525-.592c-.11-.027-.223.037-.257.145l-.965 3.038c-1.656.02-3.155.466-4.258 1.181-.277-.255-.644-.415-1.05-.415-.854.001-1.549.693-1.549 1.544 0 .566.311 1.056.768 1.325-.03.164-.05.331-.05.5 0 2.281 2.805 4.137 6.253 4.137s6.253-1.856 6.253-4.137c0-.16-.017-.317-.044-.472.486-.261.82-.766.82-1.353zm-4.872.141c-.509 0-.922.412-.922.919 0 .506.414.918.922.918s.922-.412.922-.918c0-.507-.413-.919-.922-.919z"
				/></svg
			>
		</a>
		<a href="https://www.facebook.com/IndicareLeve" target="_blank">
			<svg
				class="social-icon from-bottom facebook yellow"
				height="24"
				role="img"
				viewBox="0 0 24 24"
				xmlns="http://www.w3.org/2000/svg"
				><title>Facebook</title><path
					d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"
				/></svg
			>
		</a>
	</div>
</main>
