<template>
  <div class="toolbar">
    <button class="toolbar__btn" title="назад" @click="formatDoc('undo')"></button>
    <button class="toolbar__btn" title="вперед" @click="formatDoc('redo')"></button>
    <button class="toolbar__btn" title="заголовок" @click="formatDoc('formatBlock', '<h1>')"></button>
    <button class="toolbar__btn" title="параграф" @click="formatDoc('formatBlock', '<p>')"></button>
    <button class="toolbar__btn" title="вставить изображение" @click="insertImage"></button>
    <button class="toolbar__btn" @click="copyHtml">Скопировать HTML</button>
  </div>
</template>

<script>
export default {
  methods: {
    formatDoc(cmd, value) {
      document.execCommand(cmd, false, value);
    },
    insertImage() {
      document.execCommand('insertImage', false, prompt('введите URL картинки'));
    },
    copyHtml() {
      const htmlContainer = document.createElement('textarea');
      htmlContainer.value = document.getElementById("textBox").innerHTML;
      document.body.appendChild(htmlContainer);
      htmlContainer.select();
      document.execCommand('copy');
      document.body.removeChild(htmlContainer);
      alert('HTML скопирован')
    }
  }
}
</script>

<style lang="scss">
.toolbar {
  display: flex;
  margin: 77px 0 30px;
}
.toolbar__btn {
  width: 42px;
  height: 38px;
  background: #282828 no-repeat center;
  border-radius: 4px;
  border: 0;
  outline: 0;
  cursor: pointer;
  margin-right: 12px;
  transition: all .3s;

  &:first-of-type {
    background-image: url('~@/assets/img/arrow.png');
  }
  &:nth-of-type(2) {
    background-image: url('~@/assets/img/arrow-back.png');
  }
  &:nth-of-type(3) {
    background-image: url('~@/assets/img/title.png');
  }
  &:nth-of-type(4) {
    background-image: url('~@/assets/img/del-title.png');
  }
  &:nth-of-type(5) {
    background-image: url('~@/assets/img/paste-image.png');
  }
  &:last-of-type {
    background: none;
    width: auto;
    color: #639EFF;
    font-size: 15px;
  }
  &:hover {
    background-color: #545454;
  }
}
</style>