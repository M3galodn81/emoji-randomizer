<script setup lang="ts">
import {
  Card,
  CardContent,
  CardDescription,
  CardFooter,
  CardHeader,
  CardTitle,
} from '@/components/ui/card'

import { Button } from '@/components/ui/button'

import axios from 'axios';
import { ref , onMounted } from 'vue'

// {
//     "name": "hugging face",
//     "category": "smileys and people",
//     "group": "face positive",
//     "htmlCode": ["&#129303;"],
//     "unicode": ["U+1F917"]
// }
// api format

type EmojiItem = {
  name: string
  emoji: string
  unicode: string
}

const history = ref<EmojiItem[]>([])
const copied = ref(false)


const emojiName = ref<string>('')
const emojiCategory = ref<string>('')
const emojiGroup = ref<string>('')
const emoji = ref<string>('')
const emojiUnicode = ref<string>('')


// function to fetch random emoji
async function fetchEmoji() {
  try {
    const response = await axios.get('https://emojihub.yurace.pro/api/random')

    const newEmoji = response.data.htmlCode.join('')
    const name = response.data.name.normalize()
    const unicode = response.data.unicode[0]

    emoji.value = newEmoji
    emojiName.value = name
    emojiCategory.value = response.data.category
    emojiGroup.value = response.data.group
    emojiUnicode.value = unicode

    // push to history (avoid duplicates at top)
    history.value.unshift({ name, emoji: newEmoji, unicode })

    // limit to 10
    history.value = history.value.slice(0, 10)
  } catch (error) {
    console.error(error)
  }
}

async function copyEmoji(value: string) {
  await navigator.clipboard.writeText(value)
  copied.value = true
  setTimeout(() => (copied.value = false), 1200)
}


// fetch one when component mounts
onMounted(fetchEmoji)
</script>

<template>
    <div class="min-h-screen min-w-screen bg-amber-200 ">
        <section class="pt-32 pb-16 px-16 ">
            <!-- Hero -->
            <div class="relative ">
                <div class="absolute inset-0 flex items-center justify-center ">
                    <div class=" text-[10rem] bg-gradient-to-t from-blue-50 via-blue-500 to-red-500 bg-clip-text">
                     Emoji 
                     </div>
                    
                </div>
            </div>

            <!-- Content -->
            <div class="relative z-10 text-center py-20 ">
                <h1 class="text-black mb-10">
                    Randomizer
                </h1>
                
                <div class="m-2">
                    <Card>
                        <CardHeader>
                            <CardTitle >
                                <span class="text-2xl" v-text="emojiName"> </span>
                            </CardTitle>
                            <CardDescription>Group: <span  v-text="emojiGroup"> </span></CardDescription>
                        </CardHeader>

                        <CardContent class="flex flex-col items-center gap-4">
                            <span class="text-9xl" v-html="emoji"></span>

                            <Button @click="copyEmoji(emoji)">
                                {{ copied ? 'Copied!' : 'Copy Emoji' }}
                            </Button>
                        </CardContent>


                        <CardFooter class="flex flex-col">
                            <div> HTML Code: <span v-text="emoji"> </span> </div>
                            <div> Unicode: <span v-text="emojiUnicode"> </span> </div>
                        </CardFooter>
                        <Button  size="lg" class="m-auto" @click="fetchEmoji"> 
                            Randomize
                    </Button>
                    </Card>

                    <div class="mt-10 max-w-xl mx-auto">
                        <h2 class="text-xl mb-4 font-semibold">History (last 10)</h2>

                        <div class="grid grid-cols-5 gap-3">
                            <button
                            v-for="(item, index) in history"
                            :key="index"
                            class="text-3xl p-2 rounded hover:bg-amber-300 transition"
                            @click="copyEmoji(item.emoji)"
                            :title="item.name"
                            v-html="item.emoji"
                            />
                        </div>
                    </div> 
                </div>

                <div class="mt-8 text-sm text-gray-700">
                    Made by M3galodn81 | 
                    <a href="https://github.com/M3galodn81/emoji-randomizer" target="_blank" class="underline">
                        Source Code
                    </a>

                </div>
            </div>
        </section>

       
    </div>
</template>

<style scoped>

</style>