<template>
  <div class="open-sheet-music-display-component">
    <div ref="container"></div>
  </div>
</template>

<script setup lang="ts">
import { OpenSheetMusicDisplay as OSMD } from 'opensheetmusicdisplay';
import { ref, toRefs, onMounted } from 'vue';

const props = defineProps<{
  file: string,
  autoResize?: boolean | null,
}>()

const container = ref(null)
const { autoResize, file } = toRefs(props)
const normalizedAutoResize = autoResize.value || true;


onMounted(() => {
  setupOsmd();
});

const setupOsmd = async () => {
  if (container.value !== null) {
    const osmd = new OSMD(container.value, { autoResize: normalizedAutoResize });
    await osmd.load(file.value);
    await osmd.render();
  }
}
</script>
