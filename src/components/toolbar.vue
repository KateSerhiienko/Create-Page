<template>
  <div class="toolbar">

    <div
      class="toolbar__item"
      v-for="(toolbarItem, index) in toolbarItems"
      :key="index"
    >

      <label :for="toolbarItem.id">
        {{ toolbarItem.header }}:
      </label>

      <input
        v-show="toolbarItem.teg === 'input'"
        :type="toolbarItem.type"
        :accept="toolbarItem.accept"
        :id="toolbarItem.id"
        v-model="webpageProperties[toolbarItem.id]"
        @input="setProperty(index, $event)"
      />

      <textarea
        rows="4"
        v-show="toolbarItem.teg === 'textarea'"
        :id="toolbarItem.id"
        v-model="webpageProperties[toolbarItem.id]"
        @input="setProperty(index)"
      >
      </textarea>

    </div>

  </div>
</template>

<script>
export default {
  name: 'toolbar',
  data() {
    return {
      toolbarItems: [
        {
          id: "backgroundColor",
          header: "Background color",
          teg: "input",
          type: "color",
          inputEvent: "setBackgroundColor"
        },
        {
          id: "textColor",
          header: "Text color",
          teg: "input",
          type: "color",
          inputEvent: "setTextColor"
        },
        {
          id: "header",
          header: "Header",
          teg: "input",
          type: "text",
          inputEvent: "setHeader"
        },
        {
          id: "name",
          header: "Name",
          teg: "input",
          type: "text",
          inputEvent: "setName"
        },
        {
          id: "age",
          header: "Age",
          teg: "input",
          type: "number",
          inputEvent: "setAge"
        },
        {
          id: "profession",
          header: "Profession",
          teg: "input",
          type: "text",
          inputEvent: "setProfession"
        },
        {
          id: "information",
          header: "Information",
          teg: "textarea",
          inputEvent: "setInformation"
        },
        {
          id: "img",
          header: "Photo",
          teg: "input",
          type: "file",
          accept: "image/*",
          inputEvent: "setPhoto",
        },
      ]
    }
  },
  methods: {
    setProperty(index, event) {
      if(this.toolbarItems[index].type === "file"){
        this.webpageProperties[this.toolbarItems[index].id] = this.getImageUrl(event)
      }
      const inputEvent = this.toolbarItems[index].inputEvent;
      const property = this.webpageProperties[this.toolbarItems[index].id];
      this.$emit(inputEvent, property);
    },
    getImageUrl(event) {
      const file = event.target.files[0];
      if(file) {
        return URL.createObjectURL(file);
      }
    }
  },
  computed: {
    webpageProperties() {
      return {}
    }
  }
}
</script>

<style scoped lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Inconsolata&display=swap');
  .toolbar {
    background-color: grey;
    padding: 2vw;
    font-family: 'Inconsolata', monospace;
    color: white;
    font-size: 1.5vw;
  }
  .toolbar__item {
    display: flex;
    flex-direction: column;
    margin-bottom: 1.2vw;

    label {
      margin-bottom: .3vw;
    }

    input, textarea {
      border: none;
      padding: .5vw;
      background-color: Gainsboro;
      font-size: 1.4vw;

      &:focus {
        background-color: white;
      }
    }

    textarea {
      resize: none;
    }
  }
</style>
