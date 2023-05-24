<script>
export default {
  props: {
    price: {
      type: Number,
      required: true,
    },
  },
};
</script>

<template>
  <div class="container" id="step3" @click.stop="">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      fill="none"
      viewBox="0 0 24 24"
      stroke-width="1.5"
      stroke="#00C568"
      width="48"
      height="48"
    >
      <path
        stroke-linecap="round"
        stroke-linejoin="round"
        d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
      />
    </svg>
    <h3>Payment completed</h3>
    <p>
      You recharged
      <strong>{{
        price.toLocaleString('en', { style: 'currency', currency: 'EUR' })
      }}</strong>
      to Client Account<br />
      You can use coins to send virtual Gifts
    </p>
  </div>
</template>

<style lang="scss" scoped>
.container {
  h3 {
    font-size: 18px;
    margin-top: 1rem;
  }
  p {
    margin-top: 0.25rem;
    font-size: 1rem;
    text-align: center;
  }
}
</style>
