<script PokeAPI>
    export default{
        // make a request to PokeAPI
        data(){
            return {
                pokemonData: null,
            };
        },
        methods: {
            async fetchData() {
                const response = await fetch('https://pokeapi.co/api/v2/pokemon?limit=10000')
                    .then((response) => {
                        if (response.status != 200){
                            alert("Something Went Wrong!");
                            return;
                        }

                        response.json().then(data => {this.pokemonData = data.results})
                    }
                );

            }
        },


        mounted(){
            this.fetchData();
        },
    }
        
</script>

<template>
    <div>
        <li v-for="pokemon in pokemonData">
            {{ pokemon.name }}
        </li>
    </div>
</template>
