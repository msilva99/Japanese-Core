<template >
	<v-container fill-height fluid>
		<v-row
			align="center"
			justify="center"
		>
			<v-col class="d-flex justify-end">
				<v-btn v-if="this.n > 0" icon @click="left">
					<v-icon color="#845151" size=100>mdi-chevron-left</v-icon>
				</v-btn>
			</v-col>
			<v-col>
				<Flashcard :word=dataset.words[n] :kana=dataset.kana[n] :meaning=dataset.meanings[n] :type=dataset.types[n] :checked=checks[n] :clicked1=clicked1 :clicked2=clicked2 v-on:newChecked="onChecked" />
			</v-col>
			
			<v-col>
				<v-btn v-if="this.n < this.dataset.words.length-1" icon @click="right">
					<v-icon color="#845151" size=100>mdi-chevron-right</v-icon>
				</v-btn>
			</v-col>
		</v-row>
	</v-container>
</template>

<script>
	import Flashcard from '../components/Flashcard'

	export default {
		name: 'Home',

		components: {
			Flashcard,
		},

		props: ["dataset"],

		data: () => ({
			checks: [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
			clicked1: false,
			clicked2: false,
			n: 0,
		}),

		methods: {
			left: function() {
				if(this.n > 0) this.n--;
				this.clicked1 = false;
				this.clicked2 = false;
			},
			right: function() {
				if (this.n < this.dataset.words.length-1) this.n++;
				this.clicked1 = false;
				this.clicked2 = false;
			},
			onChecked: function(c) {
				this.checks[this.n] = c;
			}
		}
	}
</script>
