<template>
    <div>
        <div class="relative">
            <div class="bridesmaids-h1-background">
				<div class="absolute z-2 w-full">
					<TopWave color="text-primary"/>
				</div>
                <div class="content-middle text-white text-center">
                    <h1 class="text-7xl mb-2 px-2">Meet The Ladies</h1>
                    <h2 class="text-xl font-bold uppercase body-font">
                        {{ hashtag }}
                    </h2>
                </div>
            </div>
			<div class="absolute bottom-0 z-2 w-full">
				<BottomWave color="text-secondary"/>
			</div>
        </div>

        <SingleBio
            v-for="(bio, index) in bridesmaids"
            :key="bio.name"
            :name="bio.name"
            :title="bio.title"
            :image="bio.image"
            :facebook="bio.facebook"
            :instagram="bio.instagram"
            :twitter="bio.twitter"
            :even="index % 2 === 0"
            :description="bio.description"
			:last="index === bridesmaids.length - 1"
        />

		<button-footer />
    </div>
</template>

<script>
import SingleBio from '~/components/SingleBio'
import { bridesmaids, tagline } from '~/data/data.json'
export default {
    name: 'MeetTheBridesmaids',
    components: { SingleBio },
    data() {
        return {
            bridesmaids,
            hashtag: tagline.hashtag,
        }
    },
}
</script>

<style>
/* stylelint-disable color-function-notation */
.bridesmaids-h1-background {
    background: linear-gradient(rgba(0, 0, 0, 60%), rgba(0, 0, 0, 60%)),
        url('~static/images/bridesmaids/bridesmaid-head.jpg');
    height: 60vh;
    background-position: top center;
    background-repeat: no-repeat;
    background-size: cover;
}

/* stylelint-enable color-function-notation */
</style>
