<script>
	import RichPresence from '../molecules/RichPresence.svelte';
	import Tooltip from '../atoms/Tooltip.svelte';

	// i didnt write this idk
	let getAge = () => {
		let birthDate = new Date('2000/01/01');
		const ageMs = Date.now() - birthDate.getTime();
		const preciseAge = (ageMs / 31536000000).toFixed(10);
		return preciseAge;
	};

	let age = getAge();
	setInterval(() => {
		age = getAge();
	}, 1000);
</script>

<section id="about" class="wrapper">
	<div>
		<RichPresence />
	</div>
	<div class="text">
		<h2>bio</h2>
		<p>
			Hey there, I'm Gökhan. I'm a <Tooltip tip={age}
				><span>{Math.floor(Number(age))}</span></Tooltip
			>
			year old student and amateur guitarist based in Turkey. I’ve loved music and art since
			my childhood, I have experience with piano and singing. <span>and have been playing the electric guitar since 15/05/2024.</span>
			Recently, I’ve been a big fan of thrash metal. I like listening and playing
			<Tooltip tip="🤓">
				<a href="https://open.spotify.com/user/31owo5mukrfbj6cdlmbj6k2hovsy" target="_blank" rel="noreferrer">
					<span>old-school thrash and crossover thrash.</span>
				</a>
			</Tooltip>
			I'm inspired by Cliff Burton, John Connelly and Dave Mustaine, I've also built a decent repertory, actively learning new songs. <span>Currently struggling
			with songwriting and producing my own short demo album.</span> I will link my music to this website when it's done.
		</p>
	</div>
</section>

<style lang="scss">
	@import '../../styles/mixins.scss';

	section {
		margin-bottom: 6rem;
		display: grid;
		gap: 4.5rem;
		grid-template-columns: 1fr 1fr;
		align-items: center;
	}

	.text {
		position: relative;
		line-height: 1.75rem;
	}

	span {
		font-weight: 400;
		font-family: var(--font-two);
		font-size: 0.9rem;
		background-color: var(--elevation-one);
		border-radius: 7px;
		color: var(--accent);
		padding: 0.2rem 0.5rem 0.2rem;
		width: fit-content;
	}

	a {
		text-decoration: none;
	}

	.text::before {
		@include outlineText(
			$content: 'afn',
			$translateX: 97%,
			$translateY: -5%,
			$fontSize: 300px,
			$opacity: 0.22
		);
	}

	h2 {
		display: none;
		margin-top: 1rem;
	}

	@media (max-width: 868px) {
		section {
			display: flex;
			flex-direction: column;
			align-items: normal;
		}

		h2 {
			display: block;
			margin-bottom: 1rem;
		}
	}
</style>
