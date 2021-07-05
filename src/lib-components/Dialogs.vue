<template>
  <VeilFadeTransition>
    <div
        v-if="containerVisible"
        class="tw-fixed tw-h-screen tw-top-0 tw-left-0 tw-bottom-0 tw-right-0 tw-w-screen tw-bg-gray-500 tw-bg-opacity-30 tw-flex tw-items-center tw-justify-center"
        @click="onClick()"
    >
      <VeilScaleTransition>
        <div
            class="dialog-wrapper overflow-auto tw-bg-white tw-rounded-lg tw-p-3 tw-select-none"
            :class="[shake?'animate-tickle':'']"
            v-if="dialogVisible"
        >
          <div class="tw-px-6 tw-pt-3 tw-pb-1 tw-flex tw-justify-start">
            <div v-if="dialogStore.type === 'confirm'" class="tw-mr-2">
              <svg fill="#555" class="icon" viewBox="0 0 1024 1024" xmlns="http://www.w3.org/2000/svg" width="24" height="24">
                <path
                    d="M512 180c88.6 0 172 34.6 234.8 97.2C809.4 340 844 423.4 844 512s-34.6 172-97.2 234.8C684 809.4 600.6 844 512 844s-172-34.6-234.8-97.2C214.6 684 180 600.6 180 512s34.6-172 97.2-234.8C340 214.6 423.4 180 512 180m0-84C282.2 96 96 282.2 96 512s186.2 416 416 416 416-186.2 416-416S741.8 96 512 96z"></path>
                <path
                    d="M554 720h-84V470h84v250z m0-332h-84v-84h84v84z"></path>
              </svg>
            </div>
            <div class="tw-w-max-screen tw-break-all tw-text-ellipse">{{ dialogStore.message }}</div>
          </div>
          <div class="tw-flex">
            <div class="tw-flex-grow"></div>
            <button
                class="tw-text-base tw-m-1 tw-font-medium tw-rounded-lg tw-px-3 tw-py-1 tw-bg-gray-100 tw-text-black"
                v-if="dialogStore.type === 'confirm'"
                @click.stop="dialogStore.cancel()"
            >
              取消
            </button>
            <button
                class="tw-text-base tw-m-1 tw-font-medium tw-rounded-lg tw-px-3 tw-py-1 tw-bg-purple-500 tw-text-white"
                @click.stop="dialogStore.confirm()">
              确认
            </button>
          </div>
        </div>
      </VeilScaleTransition>
    </div>
  </VeilFadeTransition>
</template>

<script>
import { dialogStore } from './dialog'
import { VeilFadeTransition,VeilScaleTransition } from 'veil-transitions'
import { ref, watch } from 'vue'
export default {
  name: 'Dialogs',
  components: { VeilFadeTransition, VeilScaleTransition},
  setup(props){

    const shake = ref(false);
    const dialogVisible = ref(dialogStore.show);
    const containerVisible = ref(dialogStore.show);
    const onClick = ()=> {
      if (dialogStore.type === 'alert') {
        dialogStore.cancel()
      } else {
        shake.value = true;
        setTimeout(()=>{
          shake.value = false;
        },300)
      }
    }

    watch(dialogStore,(store)=>{
      if(store.show) {
        containerVisible.value = true
        setTimeout(() => {
          dialogVisible.value = true
        }, 100)
      } else {
        dialogVisible.value = false
        setTimeout(() => {
          containerVisible.value = false
        }, 150)
      }
    })

    return {
      onClick,
      shake,
      dialogStore,
      dialogVisible,
      containerVisible
    }
  }
}
</script>

<style scoped>
.dialog-wrapper {
  min-width: 12rem;
  max-height: 80vh;
  max-width: 80vw;

}
.animate-tickle{
  animation: tickle 0.3s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

@keyframes tickle {
  0%, 20%, 40%, 60%, 80%, 100% {
    transform: translateY(0) translateX(0);
  }
  10%,50%,90% {
    transform: translateY(5%) translateX(5%);
  }
  30%,70% {
    transform: translateY(-5%) translateX(-5%);
  }
}
</style>
