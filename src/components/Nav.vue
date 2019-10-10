<template>
	<v-navigation-drawer permanent dark mini-variant app right color="grey darken-4">
		<v-list>
			<v-list-item-group v-model="model" color="brown lighten-3">
				<v-list-item v-for="(item, i) in items" :key="i">
					<v-list-item-icon>
						<v-icon v-text="item.icon"></v-icon>
					</v-list-item-icon>
					<v-list-item-content>
						<v-list-item-title v-text="item.text" />
					</v-list-item-content>
				</v-list-item>
			</v-list-item-group>
		</v-list>
	</v-navigation-drawer>
</template>

<script>
export default {
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