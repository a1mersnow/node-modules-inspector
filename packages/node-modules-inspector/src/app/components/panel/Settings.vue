<script setup lang="ts">
import { getBackend } from '~/backends'
import { fetchData } from '~/state/data'
import { settings } from '~/state/settings'

const backend = getBackend()
</script>

<template>
  <div>
    <div flex="~ col gap-4" p4>
      <OptionItem title="Simplify module types" description="Show only ESM/CJS">
        <OptionCheckbox v-model="settings.moduleTypeSimple" />
      </OptionItem>
      <OptionItem title="Module type indicator" description="Rendering mode of module type indicator">
        <OptionSelectGroup
          v-model="settings.moduleTypeRender"
          :options="['badge', 'circle', 'none']"
          :titles="['Badge', 'Circle', 'None']"
        />
      </OptionItem>
      <OptionItem title="Show size badge" description="Show install size badge on package list">
        <OptionCheckbox v-model="settings.showInstallSizeBadge" />
      </OptionItem>
      <OptionItem title="Colorize size badge" description="Colorize package size badge">
        <OptionCheckbox v-model="settings.colorizePackageSize" />
      </OptionItem>
    </div>
    <div v-if="backend.isDynamic" border="t base" p4 flex="~ gap-2 items-center">
      <button btn-action @click="fetchData()">
        <div i-ph-arrows-clockwise-duotone />
        Refetch Data
      </button>
    </div>
  </div>
</template>
