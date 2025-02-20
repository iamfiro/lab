<script>

  import ProjectHeader from "../../components/ProjectHeader.svelte";

</script>

<div class="main">
    <ProjectHeader />
    <main>
        <slot />
    </main>
</div>

<style>
    .main {
        width: 100%;
        height: 100%;

        display: flex;
        flex-direction: column;
    }

    main {
        width: 100%;
        height: calc(100% - 60px);

        display: flex;
        flex-direction: column;

        overflow: hidden;

        background-color: blue;
    }
</style>