<template>
  <button>Custom button</button>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import type { PlasmoContentScript, PlasmoGetInlineAnchor, PlasmoMountShadowHost } from "plasmo";

export const config: PlasmoContentScript = {
  matches: ["https://www.plasmo.com/*"]
}

export const getInlineAnchor: PlasmoGetInlineAnchor = () =>
  document.querySelector("#supercharge > h2 > span")

const mountShadowHost: PlasmoMountShadowHost = ({
  inlineAnchor,
  shadowHost
}) => {
  inlineAnchor!.insertBefore(shadowHost!, inlineAnchor!.firstChild)
}

export default defineComponent({
  plasmo: {
    getInlineAnchor,
    mountShadowHost
  },
  setup() {
    return {}
  }
})
</script>
