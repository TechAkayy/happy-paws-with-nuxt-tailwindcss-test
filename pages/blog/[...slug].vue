<script setup lang="ts">
  const post = await getPost()

  useHead({
    title: post.value.title,
  })

  // const currentIndex = computed(() =>
  //   posts.value.findIndex((p) => p.href === page.value.href),
  // )
  // const post = computed(() => posts.value[currentIndex.value])
  // const nextPost = computed(() => posts.value[currentIndex.value - 1])
  // const prevPost = computed(() => posts.value[currentIndex.value + 1])

  const author = computed(() => {
    const { twitter, avatar, gravatar, author } = post.value
    return { twitter, avatar, gravatar, author }
  })
</script>
<template>
  <section>
    <div class="mt-12 mx-auto px-4 w-full">
      <div class="flex flex-col p-4 rounded-lg">
        <article class="dark:xl:divide-gray-700 xl:divide-gray-200 xl:divide-y">
          <header class="pt-6 relative space-y-1 text-center xl:pb-10">
            <div class="flex justify-center mb-4 lg:absolute lg:justify-start">
              <BaseButton to="/blog"><span>&lt;- Go Back</span> </BaseButton>
            </div>
            <div>
              <PostDate :date="post.date" />
              <h1>
                {{ post.title }}
              </h1>
            </div>
          </header>
          <div
            class="dark:divide-gray-700 divide-gray-200 divide-y pb-16 xl:divide-y-0 xl:gap-x-10 xl:grid xl:grid-cols-4 xl:pb-20 xl:sticky"
            style="grid-template-rows: auto 1fr"
          >
            <div class="p-4 rounded-xl xl:hidden xl:sticky xl:top-28">
              <TheAuthor v-bind="author" />
            </div>
            <div
              class="hidden pl-8 pr-4 py-4 rounded-xl xl:block xl:sticky xl:top-28 pg-surface-container pg-on-surface-container-text"
            >
              <TheAuthor v-bind="author" />
              <TableOfContents
                :post="post"
                class="hidden xl:block"
              ></TableOfContents>
            </div>
            <div
              class="dark:divide-gray-700 divide-gray-200 divide-y xl:col-span-3 xl:pb-0 xl:row-span-2"
            >
              <div
                id="post"
                class="dark:prose-invert dark:prose-neutral-100 prose prose-neutral-800 pt-10 md:max-w-none lg:prose-lg"
              >
                <ContentRenderer :value="post">
                  <template #empty>
                    <p>No content found.</p>
                  </template>
                </ContentRenderer>
              </div>
            </div>
            <div class="hidden">
              <footer
                class="dark:divide-gray-700 divide-gray-200 divide-y font-medium leading-5 text-sm xl:col-start-1 xl:row-start-2"
              >
                <!-- <div v-if="nextPost" class="py-8">
                  <span class="pg-primary-text text-xs tracking-wide uppercase"
                    >Next Article</span
                  >
                  <div class="link">
                    <a :href="nextPost.href">{{ nextPost.title }}</a>
                  </div>
                </div>
                <div v-if="prevPost" class="py-8">
                  <span class="pg-primary-text text-xs tracking-wide uppercase"
                    >Previous Article</span
                  >
                  <div class="link">
                    <a :href="prevPost.href">{{ prevPost.title }}</a>
                  </div>
                </div> -->
                <NuxtLink class="block pt-8" to="/blog"
                  >Back to the blog
                </NuxtLink>
              </footer>
            </div>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>
<style scoped></style>
