<script>
	import ProjectHeader from '../../components/ProjectHeader.svelte';
</script>

<div class="main">
	<ProjectHeader projectName={'PI Visualization'} githubUrl={'https://github.com/iamfiro/lab'} />
	<div class="frame">
		<main>
			<slot />
		</main>
	</div>
</div>

<style>
	.main {
		width: 100%;
		height: 100%;

		display: flex;
		flex-direction: column;
	}

	.frame {
		width: 100%;
		height: 100%;

		overflow: hidden;

        padding: 5px 30px 30px 30px;
	}

    main {
        width: 100%;
        height: 100%;

        border: 10px;

        background-color: white;

        border: 1px solid #e0e0e0;
        border-radius: 14px;

        overflow: hidden;
    }
</style>
