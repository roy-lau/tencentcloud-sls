<template>
  <v-app-bar absolute color="white" flat :style="{'left':styleLeft}">
    <v-app-bar-nav-icon @click="setDrawer" />

    <v-toolbar-title>微信公众号管理后台</v-toolbar-title>

    <v-spacer />

    <v-btn icon>
      <v-icon>mdi-magnify</v-icon>
    </v-btn>

    <v-btn icon>
      <v-icon>mdi-bell</v-icon>
    </v-btn>

    <v-menu left bottom>
      <template v-slot:activator="{ on, attrs }">
        <v-btn icon v-bind="attrs" v-on="on">
          <v-icon>mdi-account</v-icon>
        </v-btn>
      </template>

      <v-list>
        <v-list-item @click="() => {}">个人中心</v-list-item>
        <v-list-item @click="() => {}">设置</v-list-item>
        <v-list-item @click="() => {}">退出</v-list-item>
      </v-list>
    </v-menu>
  </v-app-bar>
</template>

<script>
export default {
  name: "AppBar",

  data: () => ({
    showDrawer: true,
  }),

  mounted() {
    console.log(this.$vuetify.breakpoint);
  },

  computed: {
    styleLeft() {
      if (!this.$vuetify.breakpoint.mobile)
        return this.showDrawer ? "260px" : "0px";
    },
  },

  methods: {
    setDrawer() {
      this.showDrawer = !this.showDrawer;
      this.$emit("on-drawer", this.showDrawer);
    },
  },
};
</script>
