<template>
  <v-navigation-drawer permanent dark mini-variant app right color="grey darken-4">
    <v-list dense flat>
      <v-list-item-group v-model="model">
        <v-list-item color="brown">
          <v-list-item-icon>
            <v-badge color="brown">
              <template v-slot:badge>{{cart.length}}</template>
              <v-icon>mdi-cart-outline</v-icon>
            </v-badge>
          </v-list-item-icon>
          <v-list-item-title>My Files</v-list-item-title>
        </v-list-item>
      </v-list-item-group>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
  props: ['cart'],
  data: () => ({
    items: [
      {
        icon: 'mdi-inbox',
        text: 'Inbox'
      },
      {
        icon: 'mdi-star',
        text: 'Star'
      },
      {
        icon: 'mdi-send',
        text: 'Send'
      },
      {
        icon: 'mdi-email-open',
        text: 'Drafts'
      }
    ],
    model: 1
  })
};
</script>