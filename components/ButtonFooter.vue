<template>
	<div>
		<div class="bg-primary-alt">
			<div class="text-center mx-auto max-w-2xl md:max-w-4xl pt-10 pb-20">
				<div class="grid grid-cols-12 gap-4">
					<div class="col-span-12 text-center mx-auto">
						<h3 class="pb-5 text-7xl text-left text-white">
							View More
						</h3>
					</div>

						<div class="hidden md:block md:col-span-5 text-center mx-auto">
							<img
								:src="footerPhoto"
								alt="Photo of the Couple"
							/>
						</div>

						<div class="col-span-12 md:col-span-7 text-center mx-auto">

							<div class="grid grid-cols-12 gap-4 md:mt-20">
							<div
								v-if="coupleCheck"
								class="col-span-12 pb-5"
							>
								<div class="text-center">
									<NuxtLink
										to="/the-couple"
										class="text-white underline underline-offset-2 uppercase font-bold text-white px-8 py-3 mt-10"
									>
										Meet The Couple
									</NuxtLink>
								</div>
							</div>

							<div
								v-if="groomCheck"
								class="col-span-12 pb-5"
							>
								<div class="text-center">
									<NuxtLink
										to="/groom"
										class="text-white underline underline-offset-2 uppercase font-bold text-white px-8 py-3 mt-10"
									>
										Meet The Groom
									</NuxtLink>
								</div>
							</div>

							<div v-if="menCheck" class="col-span-12 pb-5">
								<div class="text-center">
									<NuxtLink
										to="/groomsmen"
										class="text-white underline underline-offset-2 uppercase font-bold text-white px-8 py-3 mt-10"
									>
										Meet The Groomsmen
									</NuxtLink>
								</div>
							</div>

							<div
								v-if="brideCheck"
								class="col-span-12 pb-5"
							>
								<div class="text-center">
									<NuxtLink
										to="/bride"
										class="text-white underline underline-offset-2 uppercase font-bold text-white px-8 py-3 mt-10"
									>
										Meet The Bride
									</NuxtLink>
								</div>
							</div>

							<div
								v-if="maidCheck"
								class="col-span-12  pb-5"
							>
								<div class="text-center">
									<NuxtLink
										to="/bridesmaids"
										class="text-white underline underline-offset-2 uppercase font-bold text-white px-8 py-3 mt-10"
									>
										Meet The Bridesmaids
									</NuxtLink>
								</div>
							</div>
						</div>
					</div>
				</div>
			</div>
			<BottomWave color="text-primary"/>
		</div>
	</div>
</template>

<script>
import {couple} from '~/data/data.json'
export default {
	name: 'ButtonFooter',

	data(){
		return {
			footerPhoto: couple.footerPhoto
		}
	},

	computed: {
		currentPath() {
			return this.$nuxt.$route.name
		},

		coupleCheck() {
			return this.currentPath !== 'the-couple'
		},
		brideCheck() {
			return this.currentPath !== 'bride'
		},
		maidCheck() {
			return this.currentPath !== 'bridesmaids'
		},
		groomCheck() {
			return this.currentPath !== 'groom'
		},
		menCheck() {
			return this.currentPath !== 'groomsmen'
		},
	},
}
</script>
