<template>
    <Head>
        <title>Geograph - Epuero</title>
        <meta name="description" content="Geograph - Eepis Plane Unit Operational Rescue Forest">
    </Head>
    <view-layout active="geograph">
        <template v-slot:content>
            <div class="relative pt-36 pb-12" id="geograph">
                <div class="md:container mx-auto relative z-20 px-2 md:px-12">
                    <div>
                        <div class="my-8 grid grid-cols-2">
                            <div class="col-span-2 md:col-span-1">
                                <a href="/" class="text-gray-900 relative -top-3 bg-white border border-gray-300 focus:outline-none hover:bg-gray-100 focus:ring-4 focus:ring-gray-200 font-medium rounded-lg text-sm px-5 py-2.5 mr-2 mb-2 dark:bg-gray-800 dark:text-white dark:border-gray-600 dark:hover:bg-gray-700 dark:hover:border-gray-600 dark:focus:ring-gray-700">
                                    <Icon icon="akar-icons:arrow-left" class="text-xl inline-block"/>
                                    <span>Back</span>
                                </a>
                                <div class="inline-block bg-white shadow pt-4 px-4 rounded-lg">
                                    <Icon icon="jam:mountain" class="text-5xl relative -top-3 text-indigo-700 inline-block"/>
                                    <div class="relative ml-4 inline-block">
                                        <h4 class="text-lg font-semibold">Gunung Arjuna</h4>
                                        <span class="text-sm -top-4 text-gray-600">Jawatimur</span>
                                    </div>
                                    <div class="relative -top-4 ml-12 inline-block">
                                        <div class="bg-indigo-100 py-2 px-4 rounded">
                                            <span class="text-indigo-600 font-semibold">12 Item</span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div class="col-span-2 md:col-span-1 text-right py-4">
                                <select id="countries" class="bg-gray-50 border inline-block border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full md:w-1/2 p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                                    <option selected>Newest</option>
                                    <option value="US">Oldest</option>
                                </select>
                            </div>
                        </div>
                        <div class="grid grid-cols-4 gap-6">
                            <div v-for="(item, index) in 4" class="w-full card-mapping h-72 relative rounded-lg overflow-hidden col-span-2 md:col-span-1" @mouseover="onShowMapping(item)">
                                <img :src="`/images/mapping/map${item}.png`" class="block absolute top-1/2 left-1/2 w-full h-full object-cover object-center -translate-x-1/2 -translate-y-1/2" :alt="`Map${item}`"/>
                                <div class="hoverable relative w-full h-full flex text-center bg-gradient-to-b from-indigo-600 to-cyan-400">
                                    <button @click="onShowMapping(item)" data-modal-toggle="mappingModal" type="button" class="inline-block w-full align-middle text-white bg-gradient-to-b from-indigo-600 to-cyan-400 hover:bg-gradient-to-bl focus:ring-4 focus:outline-none focus:ring-cyan-300 dark:focus:ring-cyan-800 font-medium rounded-lg text-lg px-5 py-2.5 text-center mr-2 mb-2">See Detail</button>
                                </div>
                            </div>
                        </div>
                        <div class="my-8">
                            <pagination/>
                        </div>
                    </div>
                </div>
            </div>
            <div id="mappingModal" tabindex="-1" aria-hidden="true" class="hidden overflow-y-auto overflow-x-hidden z-70 fixed top-0 right-0 left-0 w-full md:inset-0 h-modal md:h-full">
                <div class="relative p-4 w-full max-w-2xl h-full md:h-auto">
                    <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
                        <div class="flex justify-between items-start p-4 rounded-t border-b dark:border-gray-600">
                            <div>
                                <h3 class="text-xl font-semibold text-gray-900 dark:text-white">
                                    Image Mapping {{ mapping }}
                                </h3>
                                <span class="text-sm text-gray-500">Senin, 20 Maret 2022 13:35</span>
                            </div>
                            <button type="button" class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center dark:hover:bg-gray-600 dark:hover:text-white" data-modal-toggle="mappingModal">
                                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
                            </button>
                        </div>
                        <div class="p-6 space-y-6 h-96 overflow-auto">
                            <img :src="`/images/mapping/map${mapping}.png`" class="w-full rounded-lg" :alt="`Map${mapping}-detail`">
                        </div>
                        <div class="flex items-center p-6 space-x-2 rounded-b border-t border-gray-200 dark:border-gray-600">
                            <button data-modal-toggle="mappingModal" type="button" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">I accept</button>
                            <button data-modal-toggle="mappingModal" type="button" class="text-gray-500 bg-white hover:bg-gray-100 focus:ring-4 focus:outline-none focus:ring-blue-300 rounded-lg border border-gray-200 text-sm font-medium px-5 py-2.5 hover:text-gray-900 focus:z-10 dark:bg-gray-700 dark:text-gray-300 dark:border-gray-500 dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-gray-600">Decline</button>
                        </div>
                    </div>
                </div>
            </div>
        </template>
    </view-layout>
</template>

<script>
import { Head, Link } from '@inertiajs/inertia-vue3'
import ViewLayout from '@/Layouts/ViewLayout.vue'
import { Icon } from '@iconify/vue'
import Pagination from '@/Components/Pagination.vue'

export default {
    data() {
        return {
            mapping: 1,
        }
    },
    components: {
        Head,
        Link,
        ViewLayout,
        Icon,
        Pagination,
    },
    methods: {
        onShowMapping(item) {
            this.mapping = item
        },
    }
}

</script>

<style>
@import "../../../../css/customize.css";
</style>
