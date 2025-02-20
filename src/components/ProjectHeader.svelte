<script>
  import ArrowLeft from './icons/ArrowLeft.svelte';
  import HammerWrench from './icons/HammerWrench.svelte';
</script>

<header>
  <div class="left">
    <div class="back">
      <ArrowLeft height={22} width={22} color={'#a0a0a0'} />
    </div>
    <HammerWrench height={22} width={22} color={'#919191'} />
    <h1>PI Visualization</h1>
  </div>
</header>

<style>
  header {
    height: 60px;

    display: flex;
    align-items: center;

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
        border: 2px solid #e1e1e1;

        box-shadow: 0 2px 3px #f2f2f2;
    }

    h1 {
      font-size: 18px;
      font-weight: 500;

      color: #000000;
    }
  }
</style>
