<script setup lang="ts">
import { computed, ref } from 'vue';

interface Props {
  message: string;
  type: string;
}
// const prop = defineProps<Props>({
//   message: string;
//   type: string;
// });
// prop.var?.forEach(e => {
//   return e.message;
// });
const { message, type } = defineProps<Props>();

const isActive = ref(true);

const progressType = computed(() => {
  return `active progress-${type?.toLowerCase()}`;
});

const timer1 = setTimeout(() => {
  isActive.value = false;
}, 5000); // 1s = 1000 milliseconds

const timer2 = setTimeout(() => {
  isActive.value = false;
}, 5300);

const closeIcon = () => {
  isActive.value = true;
  setTimeout(() => {
    isActive.value = false;
  }, 300);
  clearTimeout(timer1);
  clearTimeout(timer2);
};
</script>

<template>
  <div
    :class="[
      `toaster-${type?.toLowerCase()}`,
      { active: isActive, toast: true },
    ]"
    data-testid="toasterTestId"
  >
    <div class="toast-content" data-testid="toasterContentId">
      <i
        v-if="type?.toLowerCase() === 'success'"
        data-testid="toasterIcon"
        class="i-sf-checkmark-circle-fill check"
      />
      <i
        v-if="type?.toLowerCase() === 'error'"
        data-testid="toasterIcon"
        class="i-sf-exclamationmark-triangle-fill exclamationmark"
      />
      <div class="message">
        <span v-if="type?.toLowerCase() === 'success'" class="text success"
          >Success</span
        >
        <span v-if="type?.toLowerCase() === 'error'" class="text error"
          >Error</span
        >
        <span class="text text-2">{{ message }} developed by Tonmoy</span>
      </div>
    </div>
    <i class="i-sf-xmark close" data-testid="closeIconId" @click="closeIcon" />
    <div :class="progressType" data-testid="progressType" />
  </div>
</template>

<style lang="scss" scoped>
.main-toaster-container {
  background: #abadadf7;
  color: white;
}
.toast {
  // position: fixed;

  margin-top: 50px;
  top: 4px;
  // right: 30px;
  border-radius: 12px;
  // background: var(--primary-white-color);
  padding: 20px 35px 20px 25px;
  box-shadow: 0 6px 20px -5px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  transform: translateX(calc(100% + 30px));
  transition: all 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.35);
  width: 300px;
  z-index: 9999999;
  .theme-dark & {
    // background-color: var(--primary-text-color);
    border: 1px solid #424245;
  }
  .toast-content {
    display: flex;
    align-items: center;
    .check {
      display: flex;
      align-items: center;
      justify-content: center;
      height: 35px;
      min-width: 35px;
      background-color: #4070f4;
      color: var(--primary-white-color);
      font-size: 20px;
      border-radius: 50%;
    }
    .exclamationmark {
      display: flex;
      align-items: center;
      justify-content: center;
      height: 35px;
      min-width: 35px;
      background-color: #f27474;
      color: var(--primary-white-color);
      font-size: 20px;
      border-radius: 50%;
    }
    .message {
      display: flex;
      flex-direction: column;
      margin: 0 20px;
      .text {
        font-size: 13px;
        font-weight: 400;
        color: #000000;
        .theme-dark & {
          color: #dddddd;
        }
      }
      .success {
        font-weight: 600;
        color: #08840e;
        .theme-dark & {
          color: #ffffff;
        }
      }
    }
  }
  .close {
    position: absolute;
    top: 10px;
    right: 15px;
    padding: 5px;
    background-color: red;
    // color: white;
    cursor: pointer;
    opacity: 1;
    width: 10px;
    &:hover {
      opacity: 1;
    }
  }
  .progress-error,
  .progress-success {
    position: absolute;
    bottom: 0;
    left: 0;
    height: 3px;
    width: 100%;
  }
  .progress-success {
    &:before {
      content: '';
      position: absolute;
      bottom: 0;
      right: 0;
      height: 100%;
      width: 100%;
      background-color: #f629f6;
    }
  }
  .progress-error {
    &:before {
      content: '';
      position: absolute;
      bottom: 0;
      right: 0;
      height: 100%;
      width: 100%;
      background-color: #f27474;
    }
  }
}

.toast.active {
  transform: translateX(0%);
}

.progress-success.active:before {
  animation: progress 5s linear forwards;
}
.progress-error.active:before {
  animation: progress 5s linear forwards;
}
.active-progress-success {
  color: white;
}

@keyframes progress {
  100% {
    right: 100%;
  }
}
</style>
