<template>
  <div class="app">
    <form class="form" @submit.prevent>
      <input
        v-bind:value="title"
        @input="title = $event.target.value"
        class="input"
        type="text"
        placeholder="Название"
      />
      <input
        v-bind:value="body"
        @input="body = $event.target.value"
        class="input"
        type="text"
        placeholder="Описание"
      />
      <button class="button" @click="createPost">Создать</button>
    </form>
    <div class="post" v-bind:key="post.id" v-for="post in posts">
      <div><strong>Название </strong>{{ post.title }}</div>
      <div><strong>Описание </strong>{{ post.body }}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [
        { id: 1, title: "JavaScript", body: "Описание поста" },
        { id: 2, title: "JavaScript", body: "Описание поста" },
        { id: 3, title: "JavaScript", body: "Описание поста" },
      ],
      title: "",
      body: "",
    };
  },
  methods: {
    createPost() {
      const newPost = {
        id: Date.now(),
        title: this.title,
        body: this.body,
      };
      console.log(newPost);
      this.posts.push(newPost);
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.post {
  padding: 15px;
  border: 1px solid teal;
  margin-top: 15px;
}

.form {
  display: flex;
  flex-direction: column;
}

.button {
  align-self: flex-end;
  margin-top: 15px;
}

.input {
  width: 100%;
  padding: 10px 15px;
  border: 1px solid teal;
  margin-top: 15px;
}

.app {
  padding: 20px;
}
</style>
