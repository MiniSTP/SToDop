<template>
    <div id="app-sidebar" :style="{ width: width + 'px', 'margin-left': margin }" @mouseover="$emit('sidebar-mouseover')" @mouseleave="$emit('sidebar-mouseleave')">
        <SidebarItem id="sidebar-item-inbox" name="Inbox" :action="false" :paths="[
            {
                path: 'M10 14.5a2 2 0 104 0h5.5V18a1.5 1.5 0 01-1.5 1.5H6A1.5 1.5 0 014.5 18v-3.5H10z',
                opacity: 0.1,
            }, {
                path: 'M8.062 4h7.876a2 2 0 011.94 1.515l2.062 8.246a2 2 0 01.06.485V18a2 2 0 01-2 2H6a2 2 0 01-2-2v-3.754a2 2 0 01.06-.485l2.06-8.246A2 2 0 018.061 4zm0 1a1 1 0 00-.97.757L5.03 14.004a1 1 0 00-.03.242V18a1 1 0 001 1h12a1 1 0 001-1v-3.754a1 1 0 00-.03-.242l-2.06-8.247A1 1 0 0015.94 5H8.061zM12 17.25A2.75 2.75 0 019.295 15H7a.5.5 0 110-1h2.75a.5.5 0 01.5.5 1.75 1.75 0 003.5 0 .5.5 0 01.5-.5H17a.5.5 0 110 1h-2.295A2.75 2.75 0 0112 17.25z',
            }]"
        />

        <SidebarItem id="sidebar-item-today" name="Today" :action="false" :paths="[
            {
                path: 'M6 4.5h12A1.5 1.5 0 0 1 19.5 6v2.5h-15V6A1.5 1.5 0 0 1 6 4.5z',
                opacity: 0.1,
            }, {
                path: 'M6 4h12a2 2 0 0 1 2 2v12a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2zm0 1a1 1 0 0 0-1 1v12a1 1 0 0 0 1 1h12a1 1 0 0 0 1-1V6a1 1 0 0 0-1-1H6zm1 3h10a.5.5 0 1 1 0 1H7a.5.5 0 0 1 0-1z',
            }]"
        />

        <SidebarItem id="sidebar-item-upcoming" name="Upcoming" :action="false" :paths="[
            {
                path: 'M6 4.5h12A1.5 1.5 0 0119.5 6v2.5h-15V6A1.5 1.5 0 016 4.5z',
                opacity: 0.1
            }, {
                path: 'M6 4h12a2 2 0 012 2v12a2 2 0 01-2 2H6a2 2 0 01-2-2V6a2 2 0 012-2zm0 1a1 1 0 00-1 1v12a1 1 0 001 1h12a1 1 0 001-1V6a1 1 0 00-1-1H6zm10 12a1 1 0 110-2 1 1 0 010 2zm-4 0a1 1 0 110-2 1 1 0 010 2zm-4 0a1 1 0 110-2 1 1 0 010 2zm8-4a1 1 0 110-2 1 1 0 010 2zm-4 0a1 1 0 110-2 1 1 0 010 2zm-4 0a1 1 0 110-2 1 1 0 010 2zM7 8h10a.5.5 0 110 1H7a.5.5 0 010-1z',
            }]"
        />

        <SidebarList :action="false" name="Favorites" />
        <SidebarList name="Projects" empty="You have no projects."/>
        <SidebarList name="Labels" empty="Your list of labels will show up here."/>
        <SidebarList name="Filters" empty="Your list of filters will show up here."/>
  </div>
</template>

<script>
import SidebarItem from '@/components/SidebarItem.vue';
import SidebarList from '@/components/SidebarList.vue';

export default {
  name: 'AppSidebar',
  components: {
    SidebarItem,
    SidebarList
  },
  props: {
    width: {
      type: Number,
      default: 277,
    },
  },
  data() {
    return {
      expanded: true,
    }
  },
  computed: {
    margin() {
      return this.expanded ? '0' : '-' + this.width + 'px'
    },
  },
  mounted() {
    this.$root.$on('sidebar-toggle', () => {
      this.expanded = !this.expanded
    })
  },
}
</script>


<style scoped>
#app-sidebar {
  display: flex;
  flex-direction: column;
  transition: margin-left 0.4s;
  padding: 30px 0 30px 35px;
}
</style>