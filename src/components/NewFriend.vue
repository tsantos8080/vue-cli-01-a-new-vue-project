<template>
  <form @submit.prevent="submitData">
    <div>
      <label>Name</label>
      <input type="text" placeholder="Name" v-model="enteredName" />
    </div>
    <div>
      <label>Phone</label>
      <input type="tel" placeholder="Phone" v-model="enteredPhone" />
    </div>
    <div>
      <label>Email</label>
      <input type="email" placeholder="Email" v-model="enteredEmail" />
    </div>
    <!-- <div>
      <input type="checkbox" name="isFavorite" v-model="enteredIsFavorite" />
      <label for="isFavorite">Favorite friend</label>
    </div> -->
    <div>
      <button>Add contact</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      id: "",
      enteredName: "",
      enteredPhone: "",
      enteredEmail: "",
      //   enteredIsFavorite: false,
    };
  },
  emits: ["add-contact"],
  methods: {
    submitData() {
      this.$emit(
        "add-contact",
        this.enteredName,
        this.enteredPhone,
        this.enteredEmail
      );

      this.id = "";
      this.enteredName = "";
      this.enteredPhone = "";
      this.enteredEmail = "";
      //   this.isFavorite = false;
    },
  },
};
</script>
