<template>
  <div class="navbar">
    <div class="navbar__nav">
      <button
        v-for="(item, index) in menuItems"
        :key="index"
        :title="item.title"
        class="navbar__nav__item"
      >
        <Icons :name="item.icon" />
      </button>
    </div>
  </div>
</template>

<script>
import Icons from "@/components/Icons.vue";

export default {
  name: "Navbar",
  components: {
    Icons,
  },
  data: () => {
    return {
      menuItems: [
        {
          title: "Read List",
          icon: "list",
        },
        {
          title: "Discover",
          icon: "search",
        },
        {
          title: "My Library",
          icon: "book-reader",
        },
        {
          title: "My Profile",
          icon: "user",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.navbar {
  min-height: 56px;
  max-height: 56px;
  position: fixed;
  border-top: 1px solid $c-dark-400;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: $z-lvl-1;
  background-color: $c-dark-600;
  overflow: hidden;

  @media #{$mq-lg} {
    min-height: 64px;
    max-height: 64px;
    top: 0;
    bottom: auto;
    border-top: 0px;
    border-bottom: 1px solid $c-dark-400;
  }

  //navbar itens list
  @include element(nav) {
    display: flex;
    max-width: 720px;
    margin: 0 auto;

    // navbar item (button)
    @include element(item) {
      display: flex;
      flex-basis: 100%;
      justify-content: center;
      align-items: center;
      height: 56px;
      padding: 0;
      border: 0;
      position: relative;
      background-color: transparent;
      cursor: pointer;

      @media #{$mq-lg} {
        height: 64px;
      }

      // controll the hover effect only in desktop
      &:hover {
        @media #{$mq-lg} {
          &::before {
            content: "";
            display: block;
            width: 90%;
            height: 80%;
            border-radius: 5px;
            position: absolute;
            z-index: $z-lvl-0;
            background-color: $c-dark-400;
          }
        }
      }

      // SVG icon
      svg {
        height: 20px;
        position: relative;
        z-index: $z-lvl-1;
        fill: $c-light-100;
      }

      // selected modifier when item is related to route
      @include modifier(selected) {
        @extend .navbar__nav__item;

        &:hover {
            &::before {
                content: none;
            }
        }

        &::after {
            content: '';
            display: block;
            width: 100%;
            height: 2px;
            position: absolute;
            top: 0;
            background-color: $c-deepPurple-200;

            @media #{$mq-lg} {
                height: 4px;
                top: auto;
                bottom: 0;
            }
        }

        svg {
          fill: $c-deepPurple-200;
        }
      }
    }
  }
}
</style>