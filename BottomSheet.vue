<template>
  <div>
    <div :id="id" class="overlay">
      <aside
        :class="['social', modalClass]"
        tabindex="-1"
        role="dialog"
        aria-labelledby="modal-label"
        aria-hidden="true"
        :style="[{padding: '3px'},modalStyle]"
      >
        <slot></slot>
      </aside>
      <a href="#close" class="btn-close" aria-hidden="true">
        <span class="mdi mdi-close"></span>
        <span class="sr-only">Close</span>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      default: "bottom-sheet"
    },
    modalClass: {
      type: String,
      default: ""
    },
    modalStyle: {
      type: String,
      default: ""
    }
  }
};
</script>

<style lang="scss" scoped>
.overlay {
  position: absolute;
  right: 0;
  left: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.6);
  opacity: 0;
  transition: all 450ms cubic-bezier(0.32, 1, 0.23, 1) 0ms;

  .social {
    position: fixed;
    bottom: 0;
    width: 100%;
    background-color: #fff;
    box-sizing: border-box;
    box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.22),
      0px 14px 56px rgba(0, 0, 0, 0.25);
    transform: translate(0, 100%);
    transition: all 450ms cubic-bezier(0.32, 1, 0.23, 1) 100ms;
  }

  .btn-close {
    color: #666;
    transform: scale(0, 0);
    transition: all 450ms ease-in-out 0;
  }

  &:target {
    // Active animate in modal
    display: block;
    position: fixed;
    top: 0;
    opacity: 1;

    .social {
      transform: translate(0, 0);
      z-index: 9;
    }
    .btn-close {
      display: block;
      position: absolute;
      top: 0;
      left: 0;
      bottom: 0;
      right: 0;
      outline: 0 none;
      transform: scale(1, 1);
    }
  }
}
@media screen and (min-width: 640px) {
  .overlay {
    .social {
      width: 100%;
      margin: 0 auto;

      ul {
        column-gap: 64px;
      }
    }
  }
}
@media screen and (min-width: 960px) {
  .overlay {
    .social {
      min-width: 384px;
      width: 100%;
      ul {
        column-gap: 124px;
      }
    }
  }
}
@media screen and (min-width: 1280px) {
  .overlay {
    .social {
      min-width: 512px;
      width: 100%;
    }
  }
}
@media screen and (min-width: 1440px) {
  .overlay {
    .social {
      min-width: 576px;
      width: 100%;
    }
  }
}
.mdi::before {
  font-size: 24px;
  line-height: 48px;
}
.social .mdi::before {
  font-size: 48px;
}
.sr-only {
  clip: rect(0 0 0 0);
  overflow: hidden;
  position: absolute;
  height: 1px;
  width: 1px;
}
</style>
