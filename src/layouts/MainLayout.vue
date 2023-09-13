<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="flex justify-around items-center q-pa-md">
        <q-toolbar-title class="text-center">
          Gerador de Versículo
        </q-toolbar-title>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Início',
    caption: 'Início da aplicação',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Cursos',
    caption: 'Ir para site de recursos',
    icon: 'code',
    link: 'https://github.com/augustoglago'
  }
]

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>

<style>

.q-header {
  background-color: #f95179;
}

.q-page-container {
  padding-top: 65px !important;
}

</style>