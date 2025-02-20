<script lang="ts">
	import ArrowLeft from './icons/ArrowLeft.svelte';
	import Github from './icons/brand/Github.svelte';
	import HammerWrench from './icons/HammerWrench.svelte';

	interface ProjectHeaderProps {
		projectName: string;
		githubUrl: string;
	}

	let { projectName = 'Sample Title', githubUrl }: ProjectHeaderProps = $props();
</script>

<header>
	<div class="left">
		<div class="back">
			<ArrowLeft height={22} width={22} color={'#a0a0a0'} />
		</div>
		<HammerWrench height={22} width={22} color={'#919191'} />
		<h1>{projectName}</h1>
	</div>
	<div>
		<a class="github" href={githubUrl} target="_blank">
			<Github height={22} width={22} color={'#ffffff'} />
			<span>Source Code</span>
		</a>
	</div>
</header>

<style>
	header {
		/* 드래그 금지 */
		user-select: none;

		height: 70px;

		display: flex;
		align-items: center;
		justify-content: space-between;

		padding: 0 30px;

		background-color: white;
	}

	.left {
		display: flex;
		align-items: center;
		gap: 8px;

		.back {
			cursor: pointer;

			width: 35px;
			height: 35px;

			display: flex;
			justify-content: center;
			align-items: center;

			border-radius: 8px;
			border: 2px solid var(--color-border);

			box-shadow: 0 2px 3px #f2f2f2;

			margin-right: 10px;

			transition: all 0.1s ease-in-out;

			&:hover {
				background-color: #f2f2f2;
			}

			&:active {
				transform: translateY(2px);
				box-shadow: 0 1px 2px #f2f2f2;
			}
		}

		h1 {
			font-size: 18px;
			font-weight: 500;

			color: #000000;
		}
	}

	.github {
		background-color: black;
		color: white;

		padding: 7px 10px;

		border-radius: 8px;

		display: flex;
		align-items: center;
		gap: 5px;

		text-decoration: none;

		transition: all 0.1s ease-in-out;

		&:hover {
			background-color: #333333;
		}

		&:active {
			transform: scale(0.95);
		}

		span {
			font-size: 14px;
		}
	}
</style>
