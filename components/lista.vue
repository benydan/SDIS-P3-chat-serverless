<template>
  <div class="wrapper">
    <header>
      <h1>Chat Serverless</h1>
      <button @click="logout">Logout!</button>
    </header>

    <section>
      <main>
        <div v-for="(item, index) of items" v-bind:key="'index-'+index"
             :class="['message', sentOrReceived()]">
          <p>{{ item.nick }}</p>
          <p>{{ item.msg }}</p>
          <p>{{ item.date }}</p>
        </div>

        <div ref="scrollable"></div>
      </main>
    </section>
  </div>
</template>


<script>
  export default {
    props: {items:{type: Array, default: ()=>[]} },///////???????????????????????????????

    methods: {
      logout() {
          this.$emit('input')
      },

      sentOrReceived(userUID) {
        return 'sent'
        //return userUID === this.user.uid ? 'sent' : 'received'
      }
    }    
  }
</script>

<style lang="scss">
  body {
    margin: 0;
    font-family: -apple-system,BlinkMacSystemFont,"Segoe UI","Roboto","Oxygen","Ubuntu","Cantarell","Fira Sans","Droid Sans","Helvetica Neue",sans-serif;
  }
  .wrapper {
    text-align: center;
    max-width: 728px;
    margin: 0 auto;
    header {
      background-color: #181717;
      height: 10vh;
      min-height: 50px;
      color: rgb(111, 5, 172);
      position: fixed;
      width: 100%;
      max-width: 728px;
      top: 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      z-index: 99;
      padding: 10px;
      box-sizing: border-box;
    }
    section {
      display: flex;
      flex-direction: column;
      justify-content: center;
      min-height: 100vh;
      background-color: rgb(40, 37, 53);
      main {
        padding: 10px;
        height: 75vh;
        margin: 10vh 0 10vh;
        overflow-y: scroll;
        display: flex;
        flex-direction: column;
        &::-webkit-scrollbar {
          width: 0.25rem;
        }
        &::-webkit-scrollbar-track {
          background: #1e1e24;
        }
        &::-webkit-scrollbar-thumb {
          background: #6649b8;
        }
      }
      form {
        height: 10vh;
        position: fixed;
        bottom: 0;
        background-color: rgb(24, 23, 23);
        width: 100%;
        max-width: 728px;
        display: flex;
        font-size: 1.5rem;
        button {
          width: 20%;
          background-color: rgb(56, 56, 143);
        }
        input {
          line-height: 1.5;
          width: 100%;
          font-size: 1.5rem;
          background: rgb(58, 58, 58);
          color: white;
          outline: none;
          border: none;
          padding: 0 10px;
        }
      }
    }
    button {
      background-color: #32801a; /* Green */
      border: none;
      color: white;
      padding: 15px 32px;
      text-align: center;
      text-decoration: none;
      display: inline-block;
      cursor: pointer;
      font-size: 1.25rem;
      &:disabled {
        opacity: 0.5;
        cursor: not-allowed;
      }
    }
    button, input {
      color: rgb(3, 172, 184);
      border: none;
    }
    p {
      max-width: 500px;
      margin-bottom: 12px;
      line-height: 24px;
      padding: 10px 20px;
      border-radius: 25px;
      position: relative;
      color: white;
      text-align: center;
    }
    .message {
      display: flex;
      align-items: center;
      &.received {
        p {
          background: #e5e5ea;
          color: #000;
        }
      }
      &.sent {
        flex-direction: row-reverse;
        p {
          color: #fff;
          background: #0b93f6;
          align-self: flex-end;
        }
      }
      img {
        width: 40px;
        height: 40px;
        border-radius: 50%;
        margin: 2px 5px;
      }
      p {
        max-width: 500px;
        margin-bottom: 12px;
        line-height: 24px;
        padding: 10px 20px;
        border-radius: 25px;
        position: relative;
        color: #fff;
        text-align: center;
      }
    }
  }
</style>