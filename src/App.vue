<template>
  <div>
    <div class="wrapper">
      <div class="wrapper-content">
        <section>
          <div class="container">
            <!-- first modal -->
            <button class="btn btnPrimary" @click="modalFirst = !modalFirst">
              Show first modal
            </button>

            <modals
              title="First modal"
              v-show="modalFirst"
              @close="modalFirst = false"
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

            <!-- second-modal -->
            <button
              class="btn btnPrimary"
              @click="modalSecond.show = !modalFirst.show"
            >
              Show modal with form
            </button>

            <modals
              title="Modal with form"
              v-show="modalSecond.show"
              @close="modalSecond.show = false"
            >
              <div slot="body">
                <form @submit.prevent="submitSecondForm">
                  <label>Name:</label>
                  <input type="text" v-model="modalSecond.name" />
                  <label>Email:</label>
                  <input type="email" v-model="modalSecond.email" />
                  <button class="btn btnPrimary">Submit!</button>
                </form>
              </div>
            </modals>

            <!-- modal with validate -->
            <button class="btn btnPrimary" @click="modalValidate = !modalFirst">
              Show modal with form + validate
            </button>

            <modalValidate v-show="modalValidate" @close="modalValidate = false"/>

          </div>
        </section>
      </div>
    </div>
  </div>
</template>

<script>
import modals from "@/components/UI/Modal.vue";
import modalValidate from "@/components/ModalValidate.vue";

export default {
  components: { modals, modalValidate },
  data() {
    return {
      modalFirst: false,
      modalSecond: {
        show: false,
        name: "",
        email: "",
      },
      modalValidate: false
    };
  },
  methods: {
    submitSecondForm() {
      console.log({
        name: this.modalSecond.name,
        email: this.modalSecond.email,
      });
      this.modalSecond.name = "";
      this.modalSecond.email = "";
      this.modalSecond.show = false;
    },
  },
};
</script>

<style>
</style>
