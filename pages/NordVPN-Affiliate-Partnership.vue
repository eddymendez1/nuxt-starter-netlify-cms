<template>
  <div
    class="px-8 mx-auto mt-12 prose sm:px-6 md:px-4 lg:px-2 xl:px-0 xl:prose-xl lg:prose-lg md:prose-md"
  >
    <h1>NordVPN Affiliate Partnership</h1>
    <!-- fill this in with spaces -->

    <h2>What is NordVPN?</h2>
    <p>
      NordVPN is a virtual private network (VPN) service provider. It is based
      in Panama and has been in business since 2012. NordVPN is one of the most
      popular VPN services in the world, with over 14 million users. It is
      available for Windows, macOS, Android, iOS, and Linux. It also has browser
      extensions for Chrome and Firefox. NordVPN is also available for routers,
      smart TVs, and streaming devices such as the Amazon Fire TV Stick.
    </p>
    <p>
      NordVPN is a great VPN service. It has a large network of servers, fast
      speeds, and strong security. It is also easy to use and has a lot of
      features. NordVPN is a great choice for anyone who wants a VPN service.
    </p>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const page = await $content('products').fetch()

    return {
      page,
    }
  },
}
</script>
