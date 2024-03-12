<script setup>
  import { ref } from 'vue'
  const modal = ref(false)

  const notes = ref([])
  const title = ref("")
  const body = ref("")
  const errorMessageForTitle = ref("")
  const errorMessageForBody = ref("")

  function getRandomColor() {
    return "hsl(" + Math.random() * 360 + ", 100%, 75%)"
  }

  const titleHandle = () => {
    console.log(title.value)
  }

  const addNote = () => {
    if(title.value.length < 5 || body.value.length < 10){
      return
    } else {
      notes.value.push({
        id: Math.floor(Math.random() * 1000000),
        title: title.value,
        body: body.value,
        time: new Date(),
        color: getRandomColor()
      })
      modal.value = false
      title.value = ""
      body.value = ""
    }
  }
</script>

<template>
  <div class="modal" v-if="modal">
    <div class="content">
      <div class="close" @click="modal = false">
       <div class="cross"></div>
      </div>

      <input @change="titleHandle()" v-model="title" type="text" placeholder="Note title">
      <p v-if="title.length < 5" class="errorMessage">
        <div v-if="!title">
          Tittle should be minimum in 5 characters!
        </div>
        <div v-else>
          {{ 5 - title.length }} characters left!
        </div>
      </p>
      <textarea v-model="body" cols="30" rows="10" placeholder="Your note"></textarea>
      <p v-if="body.length < 10" class="errorMessage">
        <div v-if="!body">
          Body should be minimum in 10 characters!
        </div>
        <div v-else>
          {{ 10 - body.length }} characters left!
        </div>
      </p>
      <button @click="addNote">Add Note</button>
    </div>
  </div>
  <main>
    <div class="container">
      <div class="header">
        <h1 class="title">All Notes</h1>
        <button class="new" @click="modal=true">+ Add New</button>
      </div>
      <div class="notes">
        <div v-for="note in notes" class="note" :style="{backgroundColor: note.color}">
          <h1 class="title">{{ note.title }}</h1>
          <!-- <h4 class="time">{{ note.time.toLocaleDateString("bn-BD") }}</h4> -->
          <h4 class="time">{{ note.time.toDateString() }}</h4>
          <p class="body">{{ note.body }}</p>
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
        gap: 10px;
        .note {
          padding: 15px;
          border-radius: 10px;
          .title {
            font-size: 18px;
            color: #777;
          }
          .time {
            font-size: 10px;
            font-weight: 100;
            color: #777;
            padding: 3px 0 7px;
          }
          .body {
            color: #777;
            line-height: 1;
          }
        }
      }
    }
  }
</style>
