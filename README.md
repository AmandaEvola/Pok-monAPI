# Pok-monAPI
The Pokémon Display Web App is a simple, front-end web application that fetches and displays information about Pokémon using the PokéAPI. This project aims to provide a user-friendly interface where users can view details of various Pokémon, including their names and images.

![Screenshot (38286)](https://github.com/user-attachments/assets/3a99d58d-24d2-4680-9571-46caf7994564)

## Objectives
To create a web application that interacts with an external API (PokéAPI) to fetch data.
To display Pokémon information in a visually appealing and responsive layout.
To enhance understanding and skills in HTML, CSS, and JavaScript.
To practice fetching and handling data from a RESTful API.
Technologies Used
HTML5: For the structure and layout of the web page.
CSS3: For styling and responsive design.
JavaScript: For fetching data from the PokéAPI and dynamically updating the web page.
PokéAPI: A RESTful API providing Pokémon data.

## Key Features
Fetch Pokémon Data: The application fetches data for the first 10 Pokémon using the PokéAPI.
Dynamic Content Display: Pokémon names and images are dynamically inserted into the web page.
Responsive Design: The application features a responsive design to ensure it looks good on various devices.
Simple and Clean UI: The user interface is straightforward, making it easy for users to navigate and view Pokémon information.

## How It Works
HTML Structure: The HTML file sets up the basic structure of the web page, including a container for displaying Pokémon.
CSS Styling: The embedded CSS styles the Pokémon cards and ensures a clean and consistent look.
JavaScript Functionality:
When the page loads, JavaScript fetches data for the first 10 Pokémon from the PokéAPI.
Each Pokémon's name and image are extracted and displayed in a styled card format on the web page.

# Example Code
Here's a snippet of the core JavaScript functionality used in the project:

javascript
Copy code
document.addEventListener('DOMContentLoaded', () => {
    const pokemonContainer = document.getElementById('pokemon-container');

    const fetchPokemon = async (id) => {
        const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${id}`);
        const pokemon = await response.json();
        return pokemon;
    };

    const displayPokemon = (pokemon) => {
        const pokemonElement = document.createElement('div');
        pokemonElement.classList.add('pokemon');
        pokemonElement.innerHTML = `
            <h3>${pokemon.name.charAt(0).toUpperCase() + pokemon.name.slice(1)}</h3>
            <img src="${pokemon.sprites.front_default}" alt="${pokemon.name}">
        `;
        pokemonContainer.appendChild(pokemonElement);
    };

    const loadPokemons = async () => {
        for (let i = 1; i <= 10; i++) { // Display first 10 Pokémon
            const pokemon = await fetchPokemon(i);
            displayPokemon(pokemon);
        }

       
       
