<template>
  <div class="blog">
    <h1>This is a blog page</h1>
    <video
      controls
      autoplay
      webkit-playsinline
      playsinline
      loop
      muted
      ref="videoo"
    >
      <source
        src="http://video.itunes.apple.com/apple-assets-us-std-000001/Video118/v4/67/76/0d/67760df3-65e6-a3d3-02a7-81340664bcf2/mzvf_5168019211393929040.720w.h264lc.U.p.m4v"
      />
    </video>
    <button @click="onClick">+1</button>
  </div>
</template>

<script>
export default {
  mounted() {
    const var123 = this.$refs.videoo;
    var123.play();
    var123.currentTime = 12;
    console.log(this.$refs.videoo);
  },
  methods: {
    onClick: function () {
      this.$refs.videoo.currentTime += 1;
    },
  },
};
</script>
