<script>
import debounce from '../utils/debounce';
export default {
  data() {
    return {
      query: '',
      searchData: '',
    };
  },
  methods: {
    getSearch: debounce(async function () {
      this.searchData = this.query ? this.query : '';
    }, 750),
  },
  watch: {
    query(v) {
      this.getSearch();
      if (!v) this.searchData = '';
    },
  },
};
</script>

<template>
  <div class="tiktok-1x100u9-DivHeaderCenterContainer e10c4g870">
    <div class="tiktok-thiumz-DivSearchFormContainer eagc08l0">
      <div class="search-input tiktok-dhqzc6-FormElement ev30f210">
        <input
          placeholder="Search"
          class="tiktok-fkcqlv-InputElement ev30f212"
          v-model="query"
          @focus="this.searchData = this.query"
          @focusout="this.searchData = ''"
        />
        <button
          v-if="query.length"
          class="tiktok-coj13k-DivIconWrapper e14ntknm4"
          data-e2e="reset-search-form"
          @click="this.query = ''"
        >
          <svg
            width="16"
            data-e2e=""
            height="16"
            viewBox="0 0 48 48"
            fill="rgba(22, 24, 35, .34)"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M24 46C36.1503 46 46 36.1503 46 24C46 11.8497 36.1503 2 24 2C11.8497 2 2 11.8497 2 24C2 36.1503 11.8497 46 24 46ZM15.1466 30.7323L21.8788 24.0001L15.1466 17.2679C14.756 16.8774 14.756 16.2442 15.1466 15.8537L15.8537 15.1466C16.2442 14.756 16.8774 14.756 17.2679 15.1466L24.0001 21.8788L30.7323 15.1466C31.1229 14.756 31.756 14.756 32.1466 15.1466L32.8537 15.8537C33.2442 16.2442 33.2442 16.8774 32.8537 17.2679L26.1214 24.0001L32.8537 30.7323C33.2442 31.1229 33.2442 31.756 32.8537 32.1466L32.1466 32.8537C31.756 33.2442 31.1229 33.2442 30.7323 32.8537L24.0001 26.1214L17.2679 32.8537C16.8774 33.2442 16.2442 33.2442 15.8537 32.8537L15.1466 32.1466C14.756 31.756 14.756 31.1229 15.1466 30.7323Z"
            ></path>
          </svg>
        </button>
        <button class="tiktok-laero7-ButtonSearch ev30f216">
          <div class="tiktok-17iic05-DivSearchIconContainer ev30f217">
            <svg
              width="24"
              data-e2e=""
              height="24"
              viewBox="0 0 48 48"
              fill="rgba(22, 24, 35, .34)"
              xmlns="http://www.w3.org/2000/svg"
              data-darkreader-inline-fill=""
              style="--darkreader-inline-fill: rgba(214, 210, 205, 0.34)"
            >
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M22 10C15.3726 10 10 15.3726 10 22C10 28.6274 15.3726 34 22 34C28.6274 34 34 28.6274 34 22C34 15.3726 28.6274 10 22 10ZM6 22C6 13.1634 13.1634 6 22 6C30.8366 6 38 13.1634 38 22C38 25.6974 36.7458 29.1019 34.6397 31.8113L43.3809 40.5565C43.7712 40.947 43.7712 41.5801 43.3807 41.9705L41.9665 43.3847C41.5759 43.7753 40.9426 43.7752 40.5521 43.3846L31.8113 34.6397C29.1019 36.7458 25.6974 38 22 38C13.1634 38 6 30.8366 6 22Z"
              ></path>
            </svg>
          </div>
        </button>
        <div class="tiktok-18w6lxc-DivInputBorder ev30f211"></div>
      </div>
    </div>
    <div v-if="searchData" class="search">
      <ul>
        <li>
          <svg
            width="20"
            height="20"
            viewBox="0 0 48 48"
            fill="#777"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M22 10C15.3726 10 10 15.3726 10 22C10 28.6274 15.3726 34 22 34C28.6274 34 34 28.6274 34 22C34 15.3726 28.6274 10 22 10ZM6 22C6 13.1634 13.1634 6 22 6C30.8366 6 38 13.1634 38 22C38 25.6974 36.7458 29.1019 34.6397 31.8113L43.3809 40.5565C43.7712 40.947 43.7712 41.5801 43.3807 41.9705L41.9665 43.3847C41.5759 43.7753 40.9426 43.7752 40.5521 43.3846L31.8113 34.6397C29.1019 36.7458 25.6974 38 22 38C13.1634 38 6 30.8366 6 22Z"
            />
          </svg>
          <span>{{ this.searchData }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.search {
  * {
    font-family: ProximaNova;
  }
  position: absolute;
  top: calc(100% + 8px);
  border-radius: 8px;
  padding: 1rem;
  background: #ffffff;
  box-shadow: 0 0 10px rgba(#000, 0.1);
  width: 100%;
  ul {
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
    li {
      display: flex;
      align-items: center;
      gap: 0.75rem;
      span {
        font-size: 1rem;
        font-weight: 700;
      }
    }
  }
}
</style>
