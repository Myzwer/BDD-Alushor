<template>
    <div>
        <div class="relative">
            <div class="groomsmen-h1-background">
				<div class="absolute z-2 w-full">
					<TopWave color="text-primary"/>
				</div>
                <div class="content-middle text-white text-center">
                    <h1 class="text-7xl mb-2 px-2">Meet The Guys</h1>
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
            v-for="(bio, index) in groomsmen"
            :key="bio.name"
            :name="bio.name"
            :title="bio.title"
            :image="bio.image"
            :facebook="bio.facebook"
            :instagram="bio.instagram"
            :twitter="bio.twitter"
            :even="index % 2 === 0"
            :description="bio.description"
			:last="index === groomsmen.length - 1"
        />

        <button-footer />
    </div>
</template>

<script>
import SingleBio from '~/components/SingleBio'
import { groomsmen, tagline } from '~/data/data.json'
export default {
    name: 'MeetTheGroomsmen',
    components: { SingleBio },
    data() {
        return {
            groomsmen,
            hashtag: tagline.hashtag,
        }
    },
}
</script>

<style>
/* stylelint-disable color-function-notation */
.groomsmen-h1-background {
    background: linear-gradient(rgba(0, 0, 0, 60%), rgba(0, 0, 0, 60%)),
        url('~static/images/groomsmen/groomsmen-head.jpg');
    height: 60vh;
    background-position: top center;
    background-repeat: no-repeat;
    background-size: cover;
}

/* stylelint-enable color-function-notation */
</style>
