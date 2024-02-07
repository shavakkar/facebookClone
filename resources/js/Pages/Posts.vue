<script setup>
import MainNavLayout from "@/Layouts/MainNavLayout.vue";
import { Head, usePage, Link } from "@inertiajs/vue3";
import CreatePostBox from "@/Components/CreatePostBox.vue";
import Post from "@/Components/Post.vue";

import AccountMultiple from "vue-material-design-icons/AccountMultiple.vue";
import Flag from "vue-material-design-icons/Flag.vue";
import ClockTimeTwoOutline from "vue-material-design-icons/ClockTimeTwoOutline.vue";
import StorefrontOutline from "vue-material-design-icons/StorefrontOutline.vue";
import TelevisionPlay from "vue-material-design-icons/TelevisionPlay.vue";
import Restore from "vue-material-design-icons/Restore.vue";
import AccountGroup from "vue-material-design-icons/AccountGroup.vue";
import VideoImage from "vue-material-design-icons/VideoImage.vue";
import Magnify from "vue-material-design-icons/Magnify.vue";
import DotsHorizontal from "vue-material-design-icons/DotsHorizontal.vue";

defineProps({ posts: Object });
const user = usePage().props.auth.user;
</script>

<template>
    <Head title="Posts" />

    <MainNavLayout>
        <div class="fixed w-full h-[100%] bg-[#e1f2f5]">
            <div
                class="grid grid-rows-3 grid-flow-col w-full max-w-[1600px] mt-[56px] h-[calc(100%-56px)] mx-auto px-4"
            >
                <div id="LeftSection" class="xl:w-[345px] lg:block hidden">
                    <div class="pt-4 max-w-[320px] pr-4">
                        <Link
                            :href="route('user.show', { id: user.id })"
                            class="flex items-center justify-start w-full cursor-pointer hover:bg-[#e5e6e9] p-2 rounded-md"
                        >
                            <img
                                class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                :src="user.image"
                            />
                            <div
                                class="text-[15px] text-gray-800 font-extrabold pl-3"
                            >
                                {{ user.name }}
                            </div>
                        </Link>
                        <button
                            class="flex items-center justify-start w-full cursor-pointer hover:bg-[#e5e6e9] px-2 py-1.5 rounded-md"
                        >
                            <AccountMultiple :size="40" fillColor="#bd7c6" />
                            <div
                                class="text-[15px] text-gray-800 font-extrabold pl-3"
                            >
                                Friends
                            </div>
                        </button>
                        <button
                            class="flex items-center justify-start w-full cursor-pointer hover:bg-[#e5e6e9] px-2 py-1.5 rounded-md"
                        >
                            <Flag :size="40" fillColor="#f2682c" />
                            <div
                                class="text-[15px] text-gray-800 font-extrabold pl-3"
                            >
                                Pages
                            </div>
                        </button>
                        <button
                            class="flex items-center justify-start w-full cursor-pointer hover:bg-[#e5e6e9] px-2 py-1.5 rounded-md"
                        >
                            <ClockTimeTwoOutline
                                :size="40"
                                fillColor="#21aafa"
                            />
                            <div
                                class="text-[15px] text-gray-800 font-extrabold pl-3"
                            >
                                Most Recent
                            </div>
                        </button>
                        <button
                            class="flex items-center justify-start w-full cursor-pointer hover:bg-[#e5e6e9] px-2 py-1.5 rounded-md"
                        >
                            <AccountGroup :size="40" fillColor="#20a9fd" />
                            <div
                                class="text-[15px] text-gray-800 font-extrabold pl-3"
                            >
                                Groups
                            </div>
                        </button>
                        <button
                            class="flex items-center justify-start w-full cursor-pointer hover:bg-[#e5e6e9] px-2 py-1.5 rounded-md"
                        >
                            <StorefrontOutline :size="40" fillColor="#48c0d8" />
                            <div
                                class="text-[15px] text-gray-800 font-extrabold pl-3"
                            >
                                Market Place
                            </div>
                        </button>
                        <button
                            class="flex items-center justify-start w-full cursor-pointer hover:bg-[#e5e6e9] px-2 py-1.5 rounded-md"
                        >
                            <TelevisionPlay :size="40" fillColor="#9739cf" />
                            <div
                                class="text-[15px] text-gray-800 font-extrabold pl-3"
                            >
                                Watch
                            </div>
                        </button>
                        <button
                            class="flex items-center justify-start w-full cursor-pointer hover:bg-[#e5e6e9] px-2 py-1.5 rounded-md"
                        >
                            <Restore :size="40" fillColor="#32b4d0" />
                            <div
                                class="text-[15px] text-gray-800 font-extrabold pl-3"
                            >
                                Memories
                            </div>
                        </button>
                    </div>
                </div>
                <div
                    id="PostsSection"
                    class="row-span-6 max-w-[600px] lg:mx-0 mx-auto overflow-auto"
                >
                    <CreatePostBox
                        :image="user.image"
                        :placeholder="'What\'s on Your Mind ' + user.name"
                    />

                    <div v-for="post in posts.data" :key="post">
                        <Post
                            :user="post.user"
                            :post="post"
                            :comments="post.comments"
                        />
                    </div>
                </div>

                <div id="RightSection" class="pl-4 md:block hidden">
                    <div class="max-w-[340px] min-w-[250px] mx-auto pt-4">
                        <div
                            class="flex items-center justify-between border-b border-b-gray-300"
                        >
                            <div class="font-semibold">Contacts</div>
                            <div class="flex items-center">
                                <div
                                    class="p-2 hover:bg-gray-300 rounded-full cursor-pointer"
                                >
                                    <VideoImage
                                        :size="23"
                                        fillColor="#050505"
                                    />
                                </div>
                                <div
                                    class="p-2 hover:bg-gray-300 rounded-full cursor-pointer"
                                >
                                    <Magnify :size="23" fillColor="#050505" />
                                </div>
                                <div
                                    class="p-2 hover:bg-gray-300 rounded-full cursor-pointer"
                                >
                                    <DotsHorizontal
                                        :size="23"
                                        fillColor="#050505"
                                    />
                                </div>
                            </div>
                        </div>
                        <div class="h-[(100vh-115px)] overflow-auto pt-2">
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/140/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 1
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/141/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 2
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/142/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 3
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/143/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 4
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/144/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 5
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/145/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 6
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/146/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 7
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/140/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 8
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/141/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 9
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/142/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 10
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/143/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 11
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/144/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 12
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/145/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 13
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/146/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 14
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/140/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 15
                                </div>
                            </div>
                            <div
                                class="flex items-center justify-start cursor-pointer hover:bg-[#e5e6e9] py-2 rounded-md"
                            >
                                <img
                                    class="rounded-full ml-1 min-w-[38px] max-h-[38px]"
                                    src="https://picsum.photos/id/141/300/320"
                                    alt=""
                                />
                                <div
                                    class="text-[15px] text-gray-800 font-extrabold pl-3"
                                >
                                    Test 16
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </MainNavLayout>
</template>
