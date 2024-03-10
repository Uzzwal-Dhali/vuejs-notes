<template>
  <main>
    <div class="container">
      <div class="header">
        <h1 class="title">All Notes</h1>
        <div class="new">+</div>
      </div>
      <div class="notes">
        <div class="note">
          <h1 class="title">Title</h1>
          <h4>12th March, 2024</h4>
          <p class="body">Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestiae, exercitationem commodi! Itaque ratione iste cum!</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
  main {
    .container {
      max-width: 1300px;
      margin: 40px auto;
      background: white;
      padding: 30px;
      border-radius: 15px;
      .header {
        display: flex;
        justify-content: space-between;
        margin-bottom: 30px;
      }
      .notes {
        display: grid;
        grid-template-columns: repeat(6, 1fr);
        .note {

        }
      }
    }
  }
</style>
