<template>
	<v-app>
		<!-- <v-app-bar
			app
			color="primary"
			dark
		>
			<div class="d-flex align-center">
				<v-img
					alt="Vuetify Logo"
					class="shrink mr-2"
					contain
					src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
					transition="scale-transition"
					width="40"
				/>

				<v-img
					alt="Vuetify Name"
					class="shrink mt-1 hidden-sm-and-down"
					contain
					min-width="100"
					src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
					width="100"
				/>
			</div>

			<v-spacer></v-spacer>

			<v-btn
				href="https://github.com/vuetifyjs/vuetify/releases/latest"
				target="_blank"
				text
			>
				<span class="mr-2">Latest Release</span>
				<v-icon>mdi-open-in-new</v-icon>
			</v-btn>
		</v-app-bar> -->
			<v-card>
				<v-navigation-drawer
					expand-on-hover
					permanent
					app
					dark
					width="240"
					mini-variant-width=70
					color="#7c5454"
				>
					<v-list>
						<v-list-item-group
							v-model="selected"
							color="pink lighten-4"
						>

							<!-- Core 1000 Datasets -->
							<v-list-group
								:value="false"
								color="pink lighten-4"
								prepend-icon="mdi-numeric-1-box-multiple"
							>
								<template v-slot:activator>
									<v-list-item-title class="d-flex justify-center">Core 1000</v-list-item-title>
								</template>

								<v-list-item
										v-for="item in core1000"
										:key="item.title"
										link
										color="pink lighten-4"
										@click="chooseDataset(item.dataset_name)"
									>
										<v-list-item-icon><v-icon color="#faf1ea" v-text="item.icon"></v-icon></v-list-item-icon>
										<v-list-item-title v-text="item.title" class="ml-4"></v-list-item-title>
								</v-list-item>
							</v-list-group>

							<!-- Core 2000 Datasets -->
							<v-list-group
								:value="false"
								color="pink lighten-4"
								prepend-icon="mdi-numeric-2-box-multiple"
							>
								<template v-slot:activator>
									<v-list-item-title class="d-flex justify-center">Core 2000</v-list-item-title>
								</template>


								<v-list-item
										v-for="item in core2000"
										:key="item.title"
										link
										color="pink lighten-4"
										@click="chooseDataset(item.dataset_name)"
									>
										<v-list-item-icon><v-icon color="#faf1ea" v-text="item.icon"></v-icon></v-list-item-icon>
										<v-list-item-title v-text="item.title" class="ml-4"></v-list-item-title>
								</v-list-item>
							</v-list-group>
							
							<!-- Other Datasets -->
							<v-list-group
								:value="false"
								color="pink lighten-4"
								prepend-icon="mdi-alien-outline"
							>
								<template v-slot:activator>
									<v-list-item-title class="d-flex justify-center">Others</v-list-item-title>
								</template>

								<v-list-item
										v-for="item in others"
										:key="item.title"
										link
										color="pink lighten-4"
										@click="chooseDataset(item.dataset_name)"
									>
										<v-list-item-icon><v-icon  color="#faf1ea" v-text="item.icon"></v-icon></v-list-item-icon>
										<v-list-item-title v-text="item.title" class="ml-4"></v-list-item-title>
								</v-list-item>
							</v-list-group>
						
						</v-list-item-group>
					</v-list>
				</v-navigation-drawer>
			</v-card>
		<v-main>
			<!-- <router-view/> -->
			<Home v-if="selected && !([0,1,2].includes(selected))" :dataset=dataset />
			<h3 v-else class="mt-8"> Choose a Set </h3>
		</v-main>
	</v-app>
</template>

<script>
import Home from './views/Home.vue';
import datasets from './datasets/datasets.js';

export default {
	components: { Home },
	name: 'App',

	data: () => ({
		datasets,
		dataset: null,
		selected: null,
		core1000: [
			{ title: 'Set 1', icon: 'mdi-roman-numeral-1', dataset_name: 'Core 1000 - 1' },
			{ title: 'Set 2', icon: 'mdi-roman-numeral-2', dataset_name: 'Core 1000 - 2' },
			{ title: 'Set 3', icon: 'mdi-roman-numeral-3', dataset_name: 'Core 1000 - 3' },
			{ title: 'Set 4', icon: 'mdi-roman-numeral-4', dataset_name: 'Core 1000 - 4' },
			{ title: 'Set 5', icon: 'mdi-roman-numeral-5', dataset_name: 'Core 1000 - 5' },
			{ title: 'Set 6', icon: 'mdi-roman-numeral-6', dataset_name: 'Core 1000 - 6' },
			{ title: 'Set 7', icon: 'mdi-roman-numeral-7', dataset_name: 'Core 1000 - 7' },
			{ title: 'Set 8', icon: 'mdi-roman-numeral-8', dataset_name: 'Core 1000 - 8' },
			{ title: 'Set 9', icon: 'mdi-roman-numeral-9', dataset_name: 'Core 1000 - 9' },
			{ title: 'Set 10', icon: 'mdi-roman-numeral-10', dataset_name: 'Core 1000 - 10' },
		],
		core2000: [
			{ title: 'Set 1', icon: 'mdi-roman-numeral-1', dataset_name: 'Core 2000 - 1' },
			{ title: 'Set 2', icon: 'mdi-roman-numeral-2', dataset_name: 'Core 2000 - 2' },
			{ title: 'Set 3', icon: 'mdi-roman-numeral-3', dataset_name: 'Core 2000 - 3' },
			{ title: 'Set 4', icon: 'mdi-roman-numeral-4', dataset_name: 'Core 2000 - 4' },
			{ title: 'Set 5', icon: 'mdi-roman-numeral-5', dataset_name: 'Core 2000 - 5' },
			{ title: 'Set 6', icon: 'mdi-roman-numeral-6', dataset_name: 'Core 2000 - 6' },
			{ title: 'Set 7', icon: 'mdi-roman-numeral-7', dataset_name: 'Core 2000 - 7' },
			{ title: 'Set 8', icon: 'mdi-roman-numeral-8', dataset_name: 'Core 2000 - 8' },
			{ title: 'Set 9', icon: 'mdi-roman-numeral-9', dataset_name: 'Core 2000 - 9' },
			{ title: 'Set 10', icon: 'mdi-roman-numeral-10', dataset_name: 'Core 2000 - 10' },
		],
		others: [
			{ title: 'Emotions', icon: 'mdi-heart', dataset_name: 'Emotions' },
		],
	}),

	methods: {
		chooseDataset: function(title) {
			this.dataset = this.datasets[this.datasets.findIndex(x => x.title == title)];
		},
		teste: function() {
			alert(this.selected + '\n' + [0,1,2].includes(this.selected))
		},
	}
};
</script>

<style>
	#app {
		background: #d3a39b;
	}
	h3 {
      font-size: 50px !important;
      color:#8d5a5a !important;
      text-align: center !important;
      font-weight: bold;
   }
</style>