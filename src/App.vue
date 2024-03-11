<script setup>
  import { ref } from 'vue'
  const modal = ref(false)
</script>

<template>
  <div class="modal" v-if="modal">
    <div class="content">
      <div class="close" @click="modal = false">
       <div class="cross"></div>
      </div>
      <input type="text">
      <textarea name="" id="" cols="30" rows="10"></textarea>
      <button>Add Note</button>
    </div>
  </div>
  <main>
    <div class="container">
      <div class="header">
        <h1 class="title">All Notes</h1>
        <button class="new" @click="modal=true">+ Add New</button>
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
  .modal {
    background: rgba(0, 0, 0, 0.9);
    position: absolute;
    height: 100vh;
    width: 100vw;
    z-index: 5;
    display: flex;
    justify-content: center;
    align-items: center;
    .content {
      position: relative;
      background: white;
      padding: 40px 30px;
      border-radius: 10px;
      display: flex;
      flex-direction: column;
      gap: 10px;
      .close {
        position: absolute;
        top: -15px;
        right: -15px;
        background: rgba(255, 75, 129, 0.9);
        height: 30px;
        width: 30px;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        color: white;
        cursor: pointer;
        .cross {
          position: relative;
          display: flex;
          justify-content: center;
          align-items: center;
        }
        .cross::before, .cross::after {
          position: absolute;
          content: "";
          width: 17px;
          height: 3px;
          background: white;
          border-radius: 5px;
        }
        .cross::before {
          transform: rotate(-45deg);
        }
        .cross::after {
          transform: rotate(45deg);
        }
      }
      .close:hover {
        transition: all 0.3s ease-in;
        background: rgb(255, 75, 129);
        transform: scale(1.2);
      }
      input, textarea {
        border-radius: 5px;
        outline: none;
        border: 1px solid #d7d7d7;
        padding: 5px 10px;
      }
      button {
        background: #00c2c4;
        color: white;
        border: none;
        border-radius: 6px;
        display: flex;
        width: max-content;
        padding: 5px 10px;
        cursor: pointer;
      }
    }
  }
  main {
    padding: 50px;
    .container {
      max-width: 1300px;
      margin: 0px auto;
      background: white;
      padding: 30px;
      border-radius: 15px;
      .header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 30px;
        .title {
          font-weight: 300;
        }
        .new {
          background: #00c2c4;
          color: white;
          border: none;
          border-radius: 7px;
          padding: 5px 12px;
          display: flex;
          align-items: center;
          cursor: pointer;
        }
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
