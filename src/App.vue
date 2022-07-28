<template>
  <div>
    <div class="wrapper">
      <div class="wrapper-content">
        <section>
          <div class="container">
            <button class="btn btnPrimary" @click="modalFirst = !modalFirst">
              Show first modal
            </button>
            <!-- first modal -->
            <modals
              title="First modal"
              v-show="modalFirst"
              @close="modalFirst = !modalFirst"
            >
              <div slot="body">
                <p>Lorem ipsum dolor sit amet</p>
                <button
                  class="btn btnPrimary"
                  @click="modalFirst = !modalFirst"
                >
                  Well done!
                </button>
              </div>
            </modals>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>

<script>
import modals from "@/components/Modal.vue";

export default {
  components: { modals },
  data() {
    return {
      modalFirst: false,
    };
  },
};
</script>

<style>
</style>
