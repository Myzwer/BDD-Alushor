<template>
    <div>
        <div class="relative">
            <div class="registry-h1-background">
				<div class="absolute z-2 w-full">
					<TopWave color="text-primary"/>
				</div>
                <div class="content-middle text-white text-center">
                    <h1 class="text-7xl mb-2 px-2">Registry</h1>
                    <h2 class="text-xl font-bold uppercase body-font">
                        {{ hashtag }}
                    </h2>
                </div>
				<div class="absolute bottom-0 z-2 w-full">
					<BottomWave color="text-secondary"/>
				</div>
            </div>
        </div>

        <div class="bg-secondary">
            <div class="text-center mx-auto max-w-2xl md:max-w-5xl">
                <div
                    class="grid grid-cols-12 gap-4 pt-10 pb-12 text-white px-5"
                >
                    <div class="col-span-12 text-center">
                        <h2 class="text-6xl text-black">Our Registries</h2>
                    </div>

                    <RegistryLinks
                        v-for="reg in registries"
                        :key="reg.store"
                        :store="reg.store"
                        :item1="reg.item1"
                        :item2="reg.item2"
                        :item3="reg.item3"
                        :link="reg.link"
                    />
                </div>
            </div>
			<BottomWave color = "text-primary" />
        </div>
    </div>
</template>

<script>
import RegistryLinks from '~/components/RegistryLinks'
import { registries, tagline } from '~/data/data.json'

export default {
    name: 'WeddingRegistry',
    components: { RegistryLinks },
    data() {
        return {
            registries,
            hashtag: tagline.hashtag,
        }
    },
}
</script>

<style>
/* stylelint-disable color-function-notation */
.registry-h1-background {
    background: linear-gradient(rgba(0, 0, 0, 60%), rgba(0, 0, 0, 60%)),
        url('~static/images/registry/registry-head.jpg');
    height: 60vh;
    background-position: top center;
    background-repeat: no-repeat;
    background-size: cover;
}

/* stylelint-enable color-function-notation */
</style>
