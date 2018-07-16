<template>
<svg
  width="110px"
  height="110px"
  viewBox="0 0 110 110"
  version="1.1">
  <defs>
    <linearGradient
      x1="28.5779994%"
      y1="42.5571671%"
      x2="0%"
      y2="22.2539062%"
      id="pink-gradient">
        <stop stop-color="#EB6DDC" offset="0%"></stop>
        <stop stop-color="#EF71CF" offset="72.9768786%"></stop>
        <stop stop-color="#EEEEEE" offset="100%"></stop>
    </linearGradient>
    <circle
      id="pinkball"
      cx="55"
      cy="53"
      r="50"/>
    <filter
      x="-8.5%"
      y="-6.5%"
      width="117.0%"
      height="117.0%"
      filterUnits="objectBoundingBox"
      id="pink-filter">
      <feOffset
        dx="0"
        dy="2"
        in="SourceAlpha"
        result="shadowOffsetOuterPink"/>
      <feGaussianBlur
        stdDeviation="2.5"
        in="shadowOffsetOuterPink"
        result="shadowBlurOuterPink"/>
      <feColorMatrix
        values="0 0 0 0 0.532073767   0 0 0 0 0.194762008   0 0 0 0 0.460521052  0 0 0 0.5 0"
        type="matrix"
        in="shadowBlurOuter1"/>
    </filter>
  </defs>
  <g
    id="pinkball"
    stroke="none"
    stroke-width="1"
    fill="none"
    fill-rule="evenodd">
    <g id="pinkball">
      <use
        fill="black"
        fill-opacity="1"
        filter="url(#pink-filter)"
        xlink:href="#pinkball"/>
      <use
        fill="url(#pink-gradient)"
        fill-rule="evenodd"
        xlink:href="#pinkball"/>
    </g>
  </g>
</svg>
</template>

<script>
export default {
  name: 'PinkBall',
};
</script>
