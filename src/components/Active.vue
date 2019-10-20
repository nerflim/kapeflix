<template>
  <div>
    <div class="d-flex flex-row-reverse">
      <v-btn icon color="brown" @click="$emit('close')">
        <v-icon>mdi-close</v-icon>
      </v-btn>
    </div>
    <v-row>
      <v-col cols="12" sm="6" class="brown--text text--lighten-2">
        <p v-text="item.name" class="title"></p>
        <p v-text="item.desc" class="caption"></p>

        <p>Available sizes:</p>

        <v-card class="d-flex flex-row mb-6" tile flat color="transparent">
          <v-btn-toggle v-model="selected" tile color="brown" group>
            <v-btn
              v-for="(size, i) in sizes"
              :key="i"
              color="brown--text text--lighten-1"
              height="auto"
            >
              <div class="pa-2 d-flex flex-column">
                <p v-text="size.name"></p>
                <p class="caption mb-0" v-text="size.ml"></p>
              </div>
            </v-btn>
          </v-btn-toggle>
        </v-card>

        <v-btn outlined depressed color="brown">
          Add to cart
          <v-icon right>mdi-cart-outline</v-icon>
        </v-btn>
      </v-col>
      <v-col cols="12" sm="6">
        <v-img :src="item.img"></v-img>
      </v-col>
    </v-row>
    <v-divider dark class="my-4"></v-divider>
  </div>
</template>

<script>
export default {
  props: ['item'],
  data: () => ({
    sizes: [
      { name: 'Tall', ml: 354, icon: '' },
      { name: 'Grande', ml: 473, icon: '' },
      { name: 'Venti', ml: 591, icon: '' }
    ],
    selected: null
  })
};
</script>