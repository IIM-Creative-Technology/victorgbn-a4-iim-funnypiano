<template>
  <div>
    <div class="container-piano">
      <div
        class="key-white" v-for="note in white" :key="`key${note.name}`" :id="`key${note.name}`" @click="onClick(note)" :data-keycode="note.keyCode"></div>

      <div class="container-key-black">
        <div class="key-black" v-for="note in black" :key="`key${note.name}`" :id="`key${note.name}`" @click="onClick(note)" :data-keycode="note.keyCode"></div>
      </div>
    </div>

    <div class="container-note">
      <p class="note-do" v-for="note in white" :key="`key${note.name}`">
        {{ note.name }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "VPiano",

  data() {
    return {
      white: [
        {
          name: "do",
          sound: "C",
          keyCode: 81,
        },
        {
          name: "re",
          sound: "D",
          keyCode: 83,
        },
        {
          name: "mi",
          sound: "E",
          keyCode: 68,
        },
        {
          name: "fa",
          sound: "F",
          keyCode: 70,
        },
        {
          name: "sol",
          sound: "G",
          keyCode: 71,
        },
        {
          name: "la",
          sound: "A",
          keyCode: 72,
        },
        {
          name: "si",
          sound: "B",
          keyCode: 74,
        },
      ],
      black: [
        {
          name: "do#",
          sound: "C#",
          keyCode: 90,
        },
        {
          name: "re#",
          sound: "D#",
          keyCode: 69,
        },
        {
          name: "fa#",
          sound: "F#",
          keyCode: 84,
        },
        {
          name: "sol#",
          sound: "G#",
          keyCode: 89,
        },
        {
          name: "la#",
          sound: "A#",
          keyCode: 85,
        },
      ],
    };
  },

  mounted() {
    this.vEmoji = this.$parent.$children[1];
    this.audio = document.createElement("audio");
    document.addEventListener("keydown", (e) => {
      console.log(e.keyCode);
      const el = this.$el.querySelector(`[data-keycode="${e.keyCode}"`);
      if (el) {
        el.click();
        el.style.backgroundColor = "#ffd12d";
      } 
    });
    document.addEventListener("keyup", (e) => {
       const el = this.$el.querySelector(`[data-keycode="${e.keyCode}"`);
        el.style.backgroundColor = "";
    })
  },

  methods: {
    onClick(note) {
      const name = encodeURIComponent(note.sound);
      this.audio.src = `/assets/sounds/${name}.mp3`;
      this.audio.play();
      this.vEmoji.pickEmoji();
    },
  },
};
</script>

<style lang="postcss" scoped>
.container-piano {
  background-color: #000000;
  border-radius: 10px;
  height: 276px;
  width: 531px;
  margin-top: 59px;
  display: flex;
  justify-content: space-between;
  padding: 10px;
  position: relative;
}
.key-white {
  background-color: #ffffff;
  width: 69px;
  cursor: pointer;
}
.key-white:nth-child(1) {
  border-radius: 5px 0px 0px 5px;
}
.key-white:nth-child(7) {
  border-radius: 0px 5px 5px 0px;
}
.key-white:active {
  background: #ffd12d;
}
.key-black {
  height: 184px;
  width: 30px;
  background-color: #000000;
  border-radius: 0px 0px 5px 5px;
  z-index: 1;
  position: absolute;
  cursor: pointer;
}
.key-black:active {
  background-color: #e6016f;
}
.key-black:nth-child(1) {
  left: 66px;
}
.key-black:nth-child(2) {
  left: 144px;
}
.key-black:nth-child(3) {
  left: 295px;
}
.key-black:nth-child(4) {
  left: 370px;
}
.key-black:nth-child(5) {
  left: 447px;
}

@media (max-width: 700px) {
  .container-piano {
    width: 368px;
  }
  .key-white {
    width: 47px;
  }
  .key-black {
    width: 20px;
  }
  .key-black:nth-child(1) {
    left: 50px;
  }
  .key-black:nth-child(2) {
    left: 102px;
  }
  .key-black:nth-child(3) {
    left: 208px;
  }
  .key-black:nth-child(4) {
    left: 260px;
  }
  .key-black:nth-child(5) {
    left: 312px;
  }
}

.container-note {
  display: flex;
  justify-content: space-around;
  width: 531px;
  margin-top: 48px;
  padding-bottom: 30px;
  font-family: "PT Mono", monospace;
  color: rgba(255, 255, 255, 0.4);
}

@media (max-width: 700px) {
  .container-note {
    display: none;
  }
}
</style>