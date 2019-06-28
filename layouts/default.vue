<template>
  <div>
    <Header/>
    <nuxt/>
    <Footer/>
  </div>
</template>
<script>
import Header from "@/components/header";
import Footer from "@/components/footer";
export default {
  components: {
    Header,
    Footer
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
a {
  text-decoration: none;
  color: inherit;
  display: inline-block;
}
img {
  display: block;
}
i,
em {
  font-style: normal;
}
</style>
