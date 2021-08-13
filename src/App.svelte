<script>
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

{#if num > 20}
  <p>Greater than 20 people</p>
{:else if num > 5}
  <p>Greater than 5 people</p>
{:else}
  <p>Not greater than 5 people</p>
{/if}
<main>
  {#each people as person (person.id)}
    <div>
      <h2>{person.name}</h2>
      {#if person.beltcolor === "black"}
        <p><strong>Master Ninja</strong></p>
      {/if}
      <h4>{person.beltcolor} belt</h4>
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

  h2 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 1em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
