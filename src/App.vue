<template>
	<div class="container">
		<div class="row">
			<div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
				<h1 class="text-center">The Super Quiz</h1>
			</div>
		</div>
		<hr>
		<div class="row">
			<div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
				<transition name="flip" mode="out-in">
					<component :is="mode" @answered="answered($event)" @confirmed="mode= 'Question'">

					</component>
				</transition>

			</div>
		</div>
	</div>
</template>

<script>
	import Question from './components/Question.vue';
	import Answer from './components/Answer.vue';

	export default {
		data() {
			return {
				mode: 'Question'
			}
		},
		methods: {
			answered(isCorrect) {
				if (isCorrect) {
					this.mode = 'Answer';

				} else {
					alert('Wrong, try again!');
				}
			}
		},
		components: {
			Question,
			Answer
		}
	}
</script>

<style>
	.flip-enter {
		/*transform: rotateY(0deg);*/
	}

	.flip-enter-active {
		-webkit-animation: flip-in 0.5s ease-out forwards;
		-o-animation: flip-in 0.5s ease-out forwards;
		animation: flip-in 0.5s ease-out forwards;
	}

	.flip-leave {
		-webkit-transform: rotateY(0deg);
		-moz-transform: rotateY(0deg);
		-ms-transform: rotateY(0deg);
		-o-transform: rotateY(0deg);
		transform: rotateY(0deg);
	}

	.flip-leave-active {
		animation: flip-out 0.5s ease-out forwards;
	}

	@keyframes flip-out {
		from {
			-webkit-transform: rotateY(0deg);
			-moz-transform: rotateY(0deg);
			-ms-transform: rotateY(0deg);
			-o-transform: rotateY(0deg);
			transform: rotateY(0deg);
		}
		to {
			transform: rotateY(90deg);
		}
	}

	@keyframes flip-in {
		from {
			transform: rotateY(90deg);
		}
		to {
			transform: rotateY(0deg);
		}
	}
</style>
