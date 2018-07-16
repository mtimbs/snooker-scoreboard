<template>
<svg
  width="100px"
  height="100px"
  viewBox="0 0 100 100"
  version="1.1">
  <defs>
    <linearGradient
      x1="28.5779994%"
      y1="42.5571671%"
      x2="0%"
      y2="22.2539062%"
      id="black-gradient">
      <stop
        stop-color="#060606"
        offset="0%"/>
      <stop
        stop-color="#161616"
        offset="74.7651734%"/>
      <stop
        stop-color="#EEEEEE"
        offset="100%"/>
    </linearGradient>
  </defs>
  <g
    id="blackball"
    stroke="none"
    stroke-width="1"
    fill="none"
    fill-rule="evenodd">
    <circle
      id="blackball"
      fill="url(#black-gradient)"
      cx="50"
      cy="50"
      r="50"/>
  </g>
</svg>
</template>

<script>
export default {
  name: 'BlackBall',
};
</script>
