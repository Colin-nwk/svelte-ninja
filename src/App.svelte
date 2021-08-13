<script>
  import Modal from "./Modal.svelte";

  let showModal = false;
  const toggleModal = () => {
    showModal = !showModal;
  };

  let people = [
    { name: "John", beltcolor: "black", age: 30, id: 1 },
    { name: "Mario", beltcolor: "red", age: 20, id: 2 },
    { name: "luigi", beltcolor: "green", age: 20, id: 3 },
  ];
  const handleClick = (id) => {
    console.log(id);
    people = people.filter((person) => person.id != id);
  };
  let num = 5;
</script>

<!-- 
{#if num > 20}
  <p>Greater than 20 people</p>
{:else if num > 5}
  <p>Greater than 5 people</p>
{:else}
  <p>Not greater than 5 people</p>
{/if} -->
<Modal
  message="Hey, I am a prop value"
  isPromo={true}
  {showModal}
  on:click={toggleModal}
/>
<main>
  <button on:click={toggleModal}>open modal</button>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltcolor === "black"}
        <p><strong>Master Ninja</strong></p>
      {/if}
      <h5>{person.beltcolor} belt</h5>
      <p>{person.age} years old</p>
      <button on:click={() => handleClick(person.id)}>delete</button>
    </div>
  {:else}
    <p>No person is available</p>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  /* h2 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 1em;
    font-weight: 100;
  } */

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
