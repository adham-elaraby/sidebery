<template lang="pug">
#root.root.Sync(
  :data-native-scrollbar="Settings.state.nativeScrollbars"
  :data-native-scrollbars-thin="Settings.state.nativeScrollbarsThin"
  :data-native-scrollbars-left="Settings.state.nativeScrollbarsLeft"
  :data-theme="Settings.state.theme"
  :data-density="Settings.state.density"
  :data-frame-color-scheme="Styles.reactive.frameColorScheme"
  :data-toolbar-color-scheme="Styles.reactive.toolbarColorScheme"
  :data-act-el-color-scheme="Styles.reactive.actElColorScheme"
  :data-popup-color-scheme="Styles.reactive.popupColorScheme"
  :data-animations="animations"
  :data-syncing="Sync.reactive.syncing"
  :data-tabs-tree-lvl-marks="Settings.state.tabsLvlDots")
  .header
    .header-btn(@click="Sync.reload")
      svg.icon.-sync(): use(xlink:href="#icon_sync")
    .title Sync
    .space-filler
  SyncPanel
  NotificationsPopup
</template>

<script lang="ts" setup>
import { computed } from 'vue'
import { Settings } from 'src/services/settings'
import { Styles } from 'src/services/styles'
import { Sync } from 'src/services/_services'
import SyncPanel from 'src/sidebar/components/panel.sync.vue'
import NotificationsPopup from 'src/sidebar/components/popup.notifications.vue'

const animations = computed(() => (Settings.state.animations ? 'fast' : 'none'))
</script>
