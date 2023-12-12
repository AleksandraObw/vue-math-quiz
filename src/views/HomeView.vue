<script>
  
</script>

<template>
  <div class="home">
    <p class="home__greeting">Добро пожаловать! Сможешь ли ты решить все примеры кота-криппера? Если не боишься - вперед!</p>
    <button class="home__button"><RouterLink to="/quiz" class="home__link">Старт!</RouterLink></button> 
  </div>
</template>

<style scoped>
  .home {
    padding: 1em;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
  }
  .home__greeting {
    color: #032704;
    font-size: 1.5em;
    font-weight: 600;
    text-wrap: balance;
    text-align: center;
  }
  .home__button {
    padding: 1em 3em;
    background-color: #F7F7FF;
    border: 1px solid #EAEAEA;
    outline: 4px solid #EAEAEA;
    transition: all .5s ease-in-out;
  }
  .home__button:hover {
    outline-offset: 10px;
    cursor: pointer;
  }
  .home__link {
    color: #032704;
    font-size: 1.5em;
    font-weight: 800;
    text-decoration: none;
  }
</style>