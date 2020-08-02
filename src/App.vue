<template>
  <div>
    <div class="emojiPanel">
      <div class="emojiPanel__header">
        <div class="emojiPanel__types">
          <div class="emojiPanel__types-item active"><span>Emoji</span></div>
          <div class="emojiPanel__types-item"><span>GIF'ler</span></div>
        </div>
        <div class="emojiPanel__filter">
          <label for="searchEmoji" class="emojiPanel__search">
            <input class="emojiPanel__search-input" id="searchEmoji" type="text" placeholder="Mükemmel emojiyi bul" v-model="emojiInput">
            <span class="emojiPanel__search-button" :class="{ 'emojiPanel__search-button--clear' : emojiInput.length > 0 }" @click="clearEmojiInput()">
              <span>
                <svg aria-hidden="false" width="24" height="24" viewBox="0 0 24 24" :class="{ active : emojiInput.length === 0 }">
                  <path fill="currentColor" d="M21.707 20.293L16.314 14.9C17.403 13.504 18 11.799 18 10C18 7.863 17.167 5.854 15.656 4.344C14.146 2.832 12.137 2 10 2C7.863 2 5.854 2.832 4.344 4.344C2.833 5.854 2 7.863 2 10C2 12.137 2.833 14.146 4.344 15.656C5.854 17.168 7.863 18 10 18C11.799 18 13.504 17.404 14.9 16.314L20.293 21.706L21.707 20.293ZM10 16C8.397 16 6.891 15.376 5.758 14.243C4.624 13.11 4 11.603 4 10C4 8.398 4.624 6.891 5.758 5.758C6.891 4.624 8.397 4 10 4C11.603 4 13.109 4.624 14.242 5.758C15.376 6.891 16 8.398 16 10C16 11.603 15.376 13.11 14.242 14.243C13.109 15.376 11.603 16 10 16Z"></path>
                </svg>
                <svg aria-hidden="false" width="24" height="24" viewBox="0 0 24 24" :class="{ 'active clear' : emojiInput.length > 0 }">
                  <path fill="currentColor" d="M18.4 4L12 10.4L5.6 4L4 5.6L10.4 12L4 18.4L5.6 20L12 13.6L18.4 20L20 18.4L13.6 12L20 5.6L18.4 4Z"></path>
                </svg>
              </span>
            </span>
          </label>
          <div class="emojiPanel__color"></div>
        </div>
      </div>
      <div class="emojiPanel__content">
        <div class="emojiPanel__content-sidebar">

        </div>
        <div class="emojiPanel__content-inner">
          <div class="emojiPanel__picker">
            <div class="emojiPanel__picker-list"></div>
            <div class="emojiPanel__picker-info"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "App",
    data() {
      return {
        emojiInput: ""
      }
    },
    methods: {
      clearEmojiInput() {
        if (this.emojiInput.length > 0)
          this.emojiInput = "";
      }
    },
  }
</script>

<style>
  @import url("https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css");
</style>
<style lang="scss">
  @font-face {
    font-family: "Font";
    font-weight: 300;
    src: url("fonts/font-300.woff") format("woff")
  }
  @font-face {
    font-family: "Font";
    font-weight: 400;
    src: url("fonts/font-400.woff") format("woff")
  }
  @font-face {
    font-family: "Font";
    font-weight: 500;
    src: url("fonts/font-500.woff") format("woff")
  }
  @font-face {
    font-family: "Font";
    font-weight: 600;
    src: url("fonts/font-600.woff") format("woff")
  }
  @font-face {
    font-family: "Font";
    font-weight: 700;
    src: url("fonts/font-700.woff") format("woff")
  }

  body {
    font-family: 'Font', sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    background: #36393f;
  }

  .emojiPanel {
    background: #2f3136;
    height: 444px;
    width: 424px;
    overflow: hidden;
    position: relative;
    z-index: 1;
    border-radius: 8px;
    box-shadow: 0 0 0 1px rgba(4,4,5,0.15), 0 8px 16px rgba(0,0,0,0.24);
    display: flex;
    flex-direction: column;

    &__header {
      padding: 12px 16px;
      box-shadow: 0 1px 0 0 rgba(24,25,28,.3), 0 1px 2px 0 rgba(24,25,28,.3);
    }
    &__types {
      display: flex;

      &-item {
        cursor: pointer;
        border-radius: 4px;
        color: #b9bbbe;
        font-size: 16px;
        font-weight: 600;
        padding: 0 8px;
        height: 24px;
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        transition: background-color .1s ease-in-out,color .1s ease-in-out;

        span {
          line-height: 20px;
        }
        &:hover {
          color: #dcddde;
        }
        &.active {
          background: #4f545c;
          color: #fff;
        }
        &:not(:last-child) {
          margin-right: 8px;
        }
      }
    }
    &__filter {
      display: flex;
      padding-top: 12px;
    }
    &__search {
      flex: 1 1 auto;
      display: flex;
      align-items: center;
      border: 1px solid transparent;
      background: #202225;
      border-radius: 4px;
      overflow: hidden;
      height: auto;
      margin-bottom: 0;

      &-input {
        line-height: 31px;
        font-size: 16px;
        height: 30px;
        padding: 0 8px;
        background: transparent;
        border: 0;
        color: #dcddde;
        flex: 1;
        min-width: 48px;
        margin: 1px;

        &:focus {
          outline: none;
        }
        &::placeholder {
          color: rgba(#dcddde, .3);
        }
      }
      &-button {
        padding: 0;
        border: 0;
        background: transparent;
        height: 100%;
        min-width: 32px;
        display: flex;
        align-items: center;
        justify-content: center;

        span {
          width: 20px;
          height: 20px;
          position: relative;
        }
        svg {
          width: 100%;
          height: 100%;
          position: absolute;
          top: 0;
          left: 0;
          opacity: 0;
          z-index: 2;
          transition: transform .1s ease-out,opacity .1s ease-out,-webkit-transform .1s ease-out;
          transform: rotate(90deg);
          color: #72767d;

          &.active {
            transform: rotate(0deg);
            opacity: 1;
          }
          &.clear {
            color: #b9bbbe;
          }
        }
        &--clear {
          cursor: pointer;

          &:hover svg.clear {
            color: #dcddde;
          }
        }
      }
    }
    &__content {
      display: flex;
      flex: 1;

      &-sidebar {
        width: 48px;
        background-color: #202225;
        overflow-x: hidden;
        overflow-y: auto;
      }
      &-inner {
        height: 100%;
        flex: 1;
      }
    }
    &__picker {
      height: 100%;
      display: flex;
      flex-direction: column;

      &-list {
        flex: 1;
        height: 100%;
      }
      &-info {
        flex: 0 0 56px;
        height: 56px;
        width: 100%;
        padding: 0 16px;
        background-color: #292b2f;
      }
    }
  }
</style>
