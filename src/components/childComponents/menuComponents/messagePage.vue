<template>
  <nav>
    <button>Edit</button>
    <button>
      <img src="../../../assets/messages/newMessage.png" alt="" />
    </button>
  </nav>
  <div class="middle">
    <h2>Messages</h2>
    <div class="ujra" v-for="message in messages" :key="message.id">
      <img src="../../../assets/Call/user.png" alt="" />
      <div>
        <h6>{{ message.name }}</h6>
        <p>{{ message.description }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      messages: [
        {
          id: 1,
          name: "John Doe",
          description:
            "Lorem Ipsum has been the industry's standard dummy text ever since the 1500s",
        },
        {
          id: 2,
          name: "Jane Smith",
          description:
            "Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
        },
        {
          id: 3,
          name: "Bob Johnson",
          description:
            "when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
        },
        {
          id: 4,
          name: "Johny Walker",
          description:
            "It has survived not only five centuries, but also the leap into electronic typesetting",
        },
        {
          id: 5,
          name: "Sam Lee",
          description:
            " It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages",
        },
        {
          id: 6,
          name: "Adam Black",
          description:
            "more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
        },
        {
          id: 7,
          name: "George Wrangler",
          description:
            "It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout.",
        },
        {
          id: 8,
          name: "Gaby Charlie",
          description:
            "The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters",
        },
        {
          id: 9,
          name: "Jack Davies",
          description:
            "Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text",
        },
        {
          id: 10,
          name: "Oliver Thompson",
          description:
            " Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).",
        },
        {
          id: 11,
          name: "Jacob Hall",
          description:
            "Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old.",
        },
        {
          id: 12,
          name: "Charlie Jackson",
          description:
            "Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur",
        },
      ],
    };
  },

  methods: {},
};
</script>

<style scoped>
.ujra {
  height: 60px;
  display: flex;
}
.ujra p {
  font-family: unset;
  color: gray;
  font-size: 14px;
  padding: 0;
  margin: 0;
  height: 40px;
  white-space: nowrap;
}
.ujra h6 {
  padding: 0;
  margin: 0;
}
.ujra div {
  width: 60px;
  height: 100%;
  width: 82%;
  border-top: solid 1px gray;
  border-bottom: solid 1px gray;
}
.ujra img {
  height: 45px;
  width: 45px;
  margin-left: 5px;
  margin-top: 7px;
  margin-right: 10px;
}
nav {
  width: 90%;
  margin-top: 10px;
}
nav button {
  color: #0378e7;
  background: none;
}
nav img {
  height: 20px;
}
.middle {
  height: 509px;
  border-bottom-right-radius: 18px;
  margin-left: 7%;
  overflow: scroll;
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none; /* Firefox */
  overflow: auto;
  border-bottom-right-radius: 1em;
}
.middle::-webkit-scrollbar {
  display: none; /* Chrome, Safari and Opera */
}
</style>
