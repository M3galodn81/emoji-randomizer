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

const emojiName = ref<string>('')
const emojiCategory = ref<string>('')
const emojiGroup = ref<string>('')
const emoji = ref<string>('')
const emojiUnicode = ref<string>('')


// function to fetch random emoji
async function fetchEmoji() {
  try {
    const response = await axios.get('https://emojihub.yurace.pro/api/random')
    // console.log(response.data) // debug
    // show actual emoji (HTML code → decoded)
    emoji.value = response.data.htmlCode.join('')
    emojiName.value = response.data.name.normalize();
    emojiCategory.value = response.data.category
    emojiGroup.value = response.data.group
    emojiUnicode.value = response.data.unicode[0]
  } catch (error) {
    console.error(error)
  }
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

                        <CardContent>
                           <span class="text-9xl" v-html="emoji"> </span>
                        </CardContent>

                        <CardFooter class="flex flex-col">
                            <div> HTML Code: <span v-text="emoji"> </span> </div>
                            <div> Unicode: <span v-text="emojiUnicode"> </span> </div>
                        </CardFooter>
                        <Button  size="lg" class="m-auto" @click="fetchEmoji"> 
                            Randomize
                    </Button>
                    </Card>

                    
                </div>
            </div>
        </section>

       
    </div>
</template>


   



<style scoped>

</style>