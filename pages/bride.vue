<template>
	<div>
		<div class="relative">
			<div class="bride-h1-background">
				<div class="absolute z-2 w-full">
					<TopWave color="text-primary"/>
				</div>
				<div class="content-middle text-white text-center">
					<h1 class="text-7xl mb-2 px-2">Meet The Bride</h1>
					<h2 class="text-xl font-bold uppercase body-font">
						{{ hashtag }}
					</h2>
				</div>
			</div>
			<div class="absolute bottom-0 z-2 w-full">
				<BottomWave color="text-secondary"/>
			</div>
		</div>

		<div class="bg-secondary">
			<div class="text-center mx-auto max-w-2xl md:max-w-3xl">
				<div class="grid grid-cols-12 gap-4 pt-10 pb-12">
					<div class="col-span-12 md:col-start-3 md:col-span-8 px-5">
						<div class="mt-10 px-5">
							<img
								:src="headshot"
								alt="Bride Headshot"
							/>
						</div>
					</div>

					<div class="col-span-12 px-5 pb-5">
						<h2 class="pt-7 pb-5 text-7xl text-center">
							Hey! I'm {{ firstName }}.
						</h2>
						<p class="text-left pb-5">
							{{ bio1 }}
						</p>

						<p class="text-left pb-5">
							{{ bio2 }}
						</p>

						<div class="text-left">
							<span v-if="facebook != null" class="pb-5 text-4xl text-black">
								<a :href="facebook" target="_blank">
									<font-awesome-icon
										icon="fa-brands fa-facebook"
									/>
								</a>
							</span>

							<span v-if="instagram != null" class="pb-5 text-4xl text-black">
                            	<a :href="instagram" target="_blank">
                                    <font-awesome-icon
										icon="fa-brands fa-instagram"
									/>
                            	</a>
                        	</span>

							<span v-if="twitter != null" class="pb-5 text-4xl text-black">
                            	<a :href="twitter" target="_blank">
                                    <font-awesome-icon
										icon="fa-brands fa-twitter"
									/>
                            	</a>
                        	</span>
						</div>
					</div>
				</div>
			</div>
			<BottomWave color = "text-primary-alt" />
		</div>

		<button-footer/>
	</div>
</template>

<script>
import {bride, tagline} from '~/data/data.json'

export default {
	name: 'MeetTheBride',

	data() {
		return {
			hashtag: tagline.hashtag,
			name: bride.name,
			firstName: bride.firstName,
			headshot: bride.headshot,
			bio1: bride.bio1,
			bio2: bride.bio2,
			facebook: bride.facebook,
			instagram: bride.instagram,
			twitter: bride.twitter,
		}
	},
}
</script>

<style>
/* stylelint-disable color-function-notation */
.bride-h1-background {
	background: linear-gradient(rgba(0, 0, 0, 60%), rgba(0, 0, 0, 60%)),
	url('~static/images/bride/bride-head.jpg');
	height: 70vh;
	background-position: center center;
	background-repeat: no-repeat;
	background-size: cover;
}

/* stylelint-enable color-function-notation */
</style>
