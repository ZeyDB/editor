<template>
  <div id="textBox" class="textbox" contenteditable="true">
    Введите текст...
  </div>
</template>

<style lang="scss">
.textbox {
  font-size: 15px;
  line-height: 23px;
  color: #eaeaea;

  &:focus {
    outline: 0;
  }
}
</style>