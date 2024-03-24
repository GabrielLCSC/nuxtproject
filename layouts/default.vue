<template>
  <main role="main">
    <header>
      <nav>
        <h1>ChampRank.</h1>
      </nav>
    </header>
    <slot />
  </main>
</template>

<style scoped>
nav {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  background-color: #4c4e97;
}

nav h1 {
  color: white;
}
</style>
