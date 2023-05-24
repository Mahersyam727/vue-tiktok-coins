<template>
  <div class="container" id="step1">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      width="50px"
      height="50px"
      viewBox="0 0 100 100"
      preserveAspectRatio="xMidYMid"
    >
      <circle
        cx="50"
        cy="50"
        fill="none"
        stroke="currentColor"
        stroke-width="5"
        r="35"
        stroke-dasharray="164.93361431346415 56.97787143782138"
      >
        <animateTransform
          attributeName="transform"
          type="rotate"
          repeatCount="indefinite"
          dur="1s"
          values="0 50 50;360 50 50"
          keyTimes="0;1"
        ></animateTransform>
      </circle>
    </svg>
    <h3>Processing your payment</h3>
    <p>This could take a few seconds</p>
  </div>
</template>

<style lang="scss" scoped>
.container {
  svg {
    margin-bottom: 0.5rem;
  }
  h3 {
    font-size: 1.125rem;
    padding: 0;
    margin: 0;
  }
  p {
    font-size: 1rem;
    padding: 0;
    margin: 0;
  }
}
</style>
