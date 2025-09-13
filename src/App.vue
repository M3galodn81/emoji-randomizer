<script setup lang="ts">
import {
  Card,
  CardContent,
  CardDescription,
  CardFooter,
  CardHeader,
  CardTitle,
} from '@/components/ui/card'
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
                    Test
                </h1>
                
                <div class="m-2">
                    <Card>
                        <CardHeader>
                            <CardTitle> Wawa</CardTitle>
                            <CardDescription>Omg gdo</CardDescription>
                        </CardHeader>

                        <CardContent>
                            Card Content &#129303;
                        </CardContent>

                        <CardFooter>
                            romanji
                        </CardFooter>

                    </Card>
                </div>
            </div>
        </section>

        <Card>
            <CardHeader>
                <CardTitle> Wawa</CardTitle>
                <CardDescription>Omg gdo</CardDescription>
            </CardHeader>

            <CardContent>
                Card Content
            </CardContent>

            <CardFooter>
                romanji
            </CardFooter>

        </Card>
    </div>
</template>

<script>




</script>

<style scoped>

</style>