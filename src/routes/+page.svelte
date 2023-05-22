<script lang="ts">
    let choice = '';
    let speciesCapitalized = '';
    let frontDefault = '';
    let hp = 0;
    let atk = 0;
    let def = 0;
    let spa = 0;
    let spd = 0;
    let spe = 0;
    let bst = 0;
  
    function getFetch() {
      const url = `https://pokeapi.co/api/v2/pokemon/${choice.toLowerCase()}`;
  
      fetch(url)
        .then((res) => res.json())
        .then((data) => {
          console.log(data);
          console.log(data.sprites['front_default']);
          console.log(data.species.name);
          speciesCapitalized =
            data.species.name[0].toUpperCase() + data.species.name.slice(1);
          frontDefault = data.sprites['front_default'];
          hp = data.stats[0].base_stat;
          atk = data.stats[1].base_stat;
          def = data.stats[2].base_stat;
          spa = data.stats[3].base_stat;
          spd = data.stats[4].base_stat;
          spe = data.stats[5].base_stat;
          bst =
            data.stats[0].base_stat +
            data.stats[1].base_stat +
            data.stats[2].base_stat +
            data.stats[3].base_stat +
            data.stats[4].base_stat +
            data.stats[5].base_stat;
        })
        .catch((err) => {
          console.log(`${err}`);
        });
    }
  </script>
  
  <main>
    <h1>Pokemon Base Stat Totals</h1>
    <input bind:value={choice} type="text" />
    <button on:click={getFetch} type="button">Get Pokemon</button>
  
    <h2>{speciesCapitalized}</h2>
    <img src={frontDefault} alt="" />
  
    <h3>Base Stat Total:</h3>
    <h4 id="hp">HP: {hp}</h4>
    <h4 id="atk">Attack: {atk}</h4>
    <h4 id="def">Defense: {def}</h4>
    <h4 id="spa">Special Attack: {spa}</h4>
    <h4 id="spd">Special Defense: {spd}</h4>
    <h4 id="spe">Speed: {spe}</h4>
    <h4 id="bst">Total: {bst}</h4>
  </main>
  
  <style lang="scss">
    /* SCSS styles for the win */
    h1 {color: $color}
  </style>
  