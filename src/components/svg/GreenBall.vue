<template>
<svg
  width="110px"
  height="110px"
  viewBox="0 0 110 110"
  version="1.1">
  <defs>
    <linearGradient
      x1="29.7550883%"
      y1="43.3934309%"
      x2="0%"
      y2="22.2539062%"
      id="green-gradient">
      <stop
        stop-color="#1F8A24"
        offset="0%"/>
      <stop
        stop-color="#1F9225"
        offset="72.5343208%"/>
      <stop
        stop-color="#EEEEEE"
        offset="100%"/>
    </linearGradient>
    <circle
      id="greenball"
      cx="55"
      cy="53"
      r="50"/>
    <filter
      x="-8.5%"
      y="-6.5%"
      width="117.0%"
      height="117.0%"
      filterUnits="objectBoundingBox"
      id="green-filter">
      <feOffset
        dx="0"
        dy="2"
        in="SourceAlpha"
        result="shadowOffsetOuterGreen"/>
      <feGaussianBlur
        stdDeviation="2.5"
        in="shadowOffsetOuterGreen"
        result="shadowBlurOuterGreen"/>
      <feColorMatrix
        values="0 0 0 0 0.142752169   0 0 0 0 0.457615859   0 0 0 0 0.248259313  0 0 0 0.5 0"
        type="matrix"
        in="shadowBlurOuterGreen"/>
    </filter>
  </defs>
  <g
    id="greenball"
    stroke="none"
    stroke-width="1"
    fill="none"
    fill-rule="evenodd">
    <g id="greenball">
      <use
        fill="black"
        fill-opacity="1"
        filter="url(#green-filter)"
        xlink:href="#greenball"></use>
      <use
        fill="url(#green-gradient)"
        fill-rule="evenodd"
        xlink:href="#greenball"></use>
    </g>
  </g>
</svg>
</template>

<script>
export default {
  name: 'GreenBall',
};
</script>
