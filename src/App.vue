<script>
import AppHeader from './components/AppHeader.vue';
import AppCard from './components/AppCard.vue';
import AppInputCard from './components/AppInputCard.vue';
import AppPayment from './components/AppPayment.vue';
import { getRandomInteger } from './utils/random';

export default {
  components: { AppHeader, AppCard, AppInputCard, AppPayment },
  data() {
    return {
      user: { name: 'noname', coins: 0 },
      cards: [
        {
          coins: 70,
          price: 0.85,
        },
        {
          coins: 350,
          price: 4.05,
        },
        {
          coins: 700,
          price: 8.15,
        },
        {
          coins: 1400,
          price: 16.29,
        },
        {
          coins: 3500,
          price: 40.69,
        },
        {
          coins: 7000,
          price: 81.35,
        },
        {
          coins: 17500,
          price: 203.39,
        },
      ],
      selected: null,
      value: 0,
      step: 0,
    };
  },
  computed: {
    price() {
      if (this.selected === null) return 0;
      if (this.selected < this.cards.length)
        return this.cards[this.selected].price;
      return this.value * 0.012142857142857143;
    },
  },
  watch: {
    selected(v) {
      if (v < this.cards.length) this.value = this.cards[v].coins;
      else this.value = 0;
    },
  },
  methods: {
    async fetchUserData() {
      try {
        // API PATH
        const { name, coins } = await fetch('/api/get_user.php').then((res) =>
          res.json()
        );
        this.user = {
          name,
          coins,
        };
      } catch (error) {
        console.log(error);
        alert('Server not available!');
      }
    },
    handlePayment() {
      if (this.selected === null) return;
      this.step = 1;
      const step2Time = getRandomInteger(4000, 7000);
      setTimeout(() => {
        this.step = 2;
      }, step2Time);
    },
    handleNext() {
      this.step = 1;
      const step3Time = getRandomInteger(4000, 7000);
      setTimeout(() => {
        this.step = 3;
      }, step3Time);
    },
  },
  mounted() {
    this.fetchUserData();
  },
};
</script>

<template>
  <app-header />
  <div class="tiktok-1qjl7qr-DivMainContainer e17zolsy1">
    <div class="tiktok-lp888x-DivContentContainer e17zolsy2">
      <section class="tiktok-18xp9s9-SectionContentWrapper e14cybcq0">
        <div class="tiktok-k58u1v-DivTitleInfoContainer e14cybcq1">
          <h1
            data-e2e="wallet-title-get-coins"
            class="tiktok-peg3xr-H1TitleInfoCoin e14cybcq2"
          >
            Buy Coins
          </h1>
          <a
            data-e2e="wallet-transaction-history-entrance"
            class="tiktok-4rsttk-StyledTransactionHistoryLink e14cybcq3"
            href="#"
            >Check history</a
          >
        </div>
        <div class="tiktok-krn24s-DivProfileAndBannerRow e14cybcq8">
          <div class="tiktok-d2sjra-DivProfileInfo e14cybcq9">
            <div
              role="button"
              aria-controls=""
              data-e2e="profile-icon"
              class="tiktok-1igqi6u-DivProfileContainer efubjyv0 imageInCssJs"
            >
              <!-- API PATH -->
              <img src="/api/data/image.png" alt="" />
            </div>
            <div class="tiktok-9l16e2-DivNameCoinInfo e14cybcq10">
              <span
                data-e2e="wallet-user-name"
                class="tiktok-tkaxf7-SpanNameInfo e14cybcq12"
                >{{ user.name }}</span
              >
              <div class="tiktok-6vx15k-DivCoinInfo e14cybcq11">
                <svg
                  class="tiktok-908odc-StyledCoinIcon e14cybcq5"
                  width="1em"
                  data-e2e=""
                  height="1em"
                  viewBox="0 0 48 48"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <circle
                    cx="24"
                    cy="24"
                    r="22"
                    fill="#FFEC9B"
                    data-darkreader-inline-fill=""
                    style="--darkreader-inline-fill: #ffe886"
                  ></circle>
                  <circle
                    cx="24"
                    cy="24"
                    r="17"
                    fill="#FACE15"
                    data-darkreader-inline-fill=""
                    style="--darkreader-inline-fill: #fad229"
                  ></circle>
                  <path
                    fill-rule="evenodd"
                    clip-rule="evenodd"
                    d="M40.9347 25.5C40.9779 25.0058 41 24.5055 41 24C41 14.6112 33.3888 7 24 7C14.6112 7 7 14.6112 7 24C7 24.5055 7.02206 25.0058 7.06527 25.5C7.82466 16.8137 15.1166 10 24 10C32.8834 10 40.1753 16.8137 40.9347 25.5Z"
                    fill="#FABC15"
                    data-darkreader-inline-fill=""
                    style="--darkreader-inline-fill: #fac229"
                  ></path>
                  <path
                    d="M33 19C30.2041 19 27.9375 16.7614 27.9375 14H24.5625V27.6111C24.5625 29.2986 23.1774 30.6667 21.4688 30.6667C19.7601 30.6667 18.375 29.2986 18.375 27.6111C18.375 25.9236 19.7601 24.5556 21.4688 24.5556C21.722 24.5556 21.9659 24.5853 22.1981 24.6406C22.2365 24.6497 22.2747 24.6596 22.3125 24.6701V21.2763C22.0358 21.2406 21.7541 21.2222 21.4688 21.2222C17.8962 21.2222 15 24.0826 15 27.6111C15 31.1396 17.8962 34 21.4688 34C25.0413 34 27.9375 31.1396 27.9375 27.6111V20.6673C29.3477 21.7134 31.1005 22.3333 33 22.3333V19Z"
                    fill="#FEF5CD"
                    data-darkreader-inline-fill=""
                    style="--darkreader-inline-fill: #fdeeaa"
                  ></path></svg
                ><span
                  data-e2e="wallet-coins-balance"
                  class="tiktok-puwl6j-SpanCoinNum e14cybcq4"
                  >{{ user.coins }}</span
                >
              </div>
            </div>
          </div>
        </div>
      </section>
      <div
        data-e2e="wallet-buy-coins-title"
        class="tiktok-xx4hck-DivRechargeCoins eyr93xl0"
      >
        Payment
      </div>
      <div class="tiktok-1un7bi9-DivCoinsBkgContainer eyr93xl1">
        <ol
          data-e2e="wallet-coins-packages"
          class="tiktok-1a7iizi-OlCoinsListContainer eyr93xl2"
        >
          <app-card
            v-for="(card, idx) in cards"
            :key="idx"
            :coins="card.coins"
            :price="card.price"
            :selected="this.selected === idx"
            @click="this.selected = idx"
          />
          <app-input-card
            @click="selected = cards.length"
            :selected="selected === cards.length"
            @input="value = $event"
          />
        </ol>
      </div>
      <div class="tiktok-11ddo6h-DivTotalContainer e1ndw46o0">
        <ul class="tiktok-fbshyx-UlPaymentMethodsContainer e1ndw46o1">
          <li>
            <span
              data-e2e="wallet-title-payment-method"
              class="tiktok-p0hyyy-SpanTotalText e1ndw46o2"
              >Payment method</span
            >
          </li>
          <li>
            <img
              src="https://lf16-co.g-p-static.com/obj/pipo-sgcompliance/sky/visa_light_c558fb.svg"
              data-e2e="wallet-payment-icon-VISA"
              alt="Visa"
              class="tiktok-1quc8c-ImgPaymentIcon e1ndw46o5"
            />
          </li>
          <li>
            <img
              src="https://lf16-co.g-p-static.com/obj/pipo-sgcompliance/sky/mastercard-gray-update_7b3ceb.svg"
              data-e2e="wallet-payment-icon-MASTER"
              alt="Mastercard"
              class="tiktok-1quc8c-ImgPaymentIcon e1ndw46o5"
            />
          </li>
          <li>
            <img
              src="https://lf16-co.g-p-static.com/obj/pipo-sgcompliance/sky/paypal-light-border_4305a4.svg"
              data-e2e="wallet-payment-icon-PAYPAL"
              alt="PAYPAL"
              class="tiktok-1quc8c-ImgPaymentIcon e1ndw46o5"
            />
          </li>
        </ul>
      </div>
      <div class="tiktok-1fguu8v-DivTotalContainer e9ndt4q0">
        <span
          data-e2e="wallet-title-total-price"
          class="tiktok-j4urqu-SpanTotalText e9ndt4q5"
          >Final</span
        ><span
          aria-live="polite"
          data-e2e="wallet-total-price"
          class="tiktok-uzytel-SpanTotalMount e9ndt4q6"
          id="finalP"
          >{{
            price.toLocaleString('en', { style: 'currency', currency: 'EUR' })
          }}</span
        >
      </div>
      <div class="tiktok-vr1v8s-DivButtonContainer e9ndt4q8">
        <button
          @click="handlePayment"
          type="button"
          class="e9ndt4q10 tiktok-19v97s1-Button-StyledBuyButton ehk74z00"
        >
          Continue
        </button>
      </div>
    </div>
    <button
      aria-label="FAQ"
      class="tiktok-1l1fdho-ButtonQuestionContainer e17zolsy4"
    >
      <svg
        class="tiktok-ze008l-StyledQnMarkIcon e17zolsy3"
        width="1em"
        data-e2e=""
        height="1em"
        viewBox="0 0 48 48"
        fill="currentColor"
        xmlns="http://www.w3.org/2000/svg"
        data-darkreader-inline-fill=""
        style="--darkreader-inline-fill: currentColor"
      >
        <path
          fill-rule="evenodd"
          clip-rule="evenodd"
          d="M24 6C14.0589 6 6 14.0589 6 24C6 33.9411 14.0589 42 24 42C33.9411 42 42 33.9411 42 24C42 14.0589 33.9411 6 24 6ZM2 24C2 11.8497 11.8497 2 24 2C36.1503 2 46 11.8497 46 24C46 36.1503 36.1503 46 24 46C11.8497 46 2 36.1503 2 24ZM24.0909 15C22.172 15 20.3433 16.2292 19.2617 18.61C19.0332 19.1128 18.4726 19.4 17.9487 19.2253L16.0513 18.5929C15.5274 18.4182 15.2406 17.8497 15.4542 17.3405C16.9801 13.7031 20.0581 11 24.0909 11C28.459 11 32 14.541 32 18.9091C32 21.2138 30.7884 23.4606 29.2167 25.074C27.8157 26.5121 25.5807 27.702 22.9988 27.9518C22.4491 28.0049 22.0001 27.5523 22.0001 27V25C22.0001 24.4477 22.4504 24.0057 22.9955 23.9167C24.2296 23.7153 25.5034 23.1533 26.3515 22.2828C27.4389 21.1666 28 19.8679 28 18.9091C28 16.7502 26.2498 15 24.0909 15ZM24 36C22.3431 36 21 34.6569 21 33C21 31.3431 22.3431 30 24 30C25.6569 30 27 31.3431 27 33C27 34.6569 25.6569 36 24 36Z"
        ></path>
      </svg>
    </button>
  </div>
  <transition name="fade">
    <app-payment
      v-if="step"
      :step="step"
      :price="this.price"
      @next="handleNext"
      @close="step = 0"
    />
  </transition>
</template>

<style>
.fade-enter-active {
  animation: fade 0.5s;
}
.fade-leave-active {
  animation: fade 0.5s reverse;
}

@keyframes fade {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
