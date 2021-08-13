<script>
  let showModal = true;
  let isPromo = false;
</script>

{#if showModal}
  <div class="backdrop" class:promo={isPromo}>
    <div class="modal">
      <p>Sign up for offers</p>
    </div>
  </div>
{/if}

<main />

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0, 0, 0, 0.8);
  }
  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background-color: white;
  }

  .promo .modal {
    background-color: red;
    color: white;
  }
</style>
