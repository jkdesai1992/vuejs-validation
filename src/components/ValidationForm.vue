<template>
  <div>
    <div class="border">
      <div>
        <div>
          <label>First name:</label>
          <input name="firstName" v-model="firstName" type="text" placeholder="First name">
        </div>
        <div>
          <span class="text-danger">{{errorMsg.firstName}}</span>
        </div>
      </div>
      <div>
        <label>Email:</label>
        <input name="lastName" v-model="lastName" type="text" placeholder="Last name">
        <div>
          <span class="text-danger">{{errorMsg.lastName}}</span>
        </div>
      </div>
      <div>
        <label>Address:</label>
        <input name="addressLine" v-model="addressLine" type="text" placeholder="Address line">
        <div>
          <span class="text-danger">{{errorMsg.addressLine}}</span>
        </div>
      </div>
      <div>
        <label>Pin Code:</label>
        <input name="pinCode" v-model="pinCode" type="text" placeholder="Pincode">
        <div>
          <span class="text-danger">{{errorMsg.pinCode}}</span>
        </div>
      </div>
      <div>
        <label>Email:</label>
        <input name="email" v-model="email" type="text" placeholder="Email">
        <div>
          <span class="text-danger">{{errorMsg.email}}</span>
        </div>
      </div>
      <div>
        <label>Phone:</label>
        <input name="phone" v-model="phone" type="tel" placeholder="Phone no">
        <div>
          <span class="text-danger">{{errorMsg.phone}}</span>
        </div>
      </div>
    </div>
    <br>
    <button v-on:click="handelBillingInfo" class="btn btn-style1 margin-right-5px">Submit</button>
  </div>
</template>

<script>
export default {
  name: "ValidationForm",
  data() {
    return {
      cartList: [],
      total: 0,
      firstName: "",
      lastName: "",
      addressLine: "",
      pinCode: "",
      email: "",
      phone: "",
      errorMsg: [],
      showPaymetOption: false
    };
  },
  methods: {
    validate: function(name, value) {
      switch (name) {
        case "firstName":
          if (!value) {
            return "First Name is require";
          } else {
            return null;
          }
        case "lastName":
          if (!value) {
            return "Last Name is require";
          } else {
            return null;
          }
        case "phone":
          if (!value) {
            return "Phone Number  is require";
          } else if (
            !value.match(/^\(?([0-9]{3})\)?[-. ]?([0-9]{3})[-. ]?([0-9]{4})$/)
          ) {
            return "Enter a valid Phone ";
          } else {
            return null;
          }
        case "addressLine":
          if (!value) {
            return "Address line 1 is require";
          } else {
            return null;
          }
        case "email":
          if (!value) {
            return "Email is require";
          } else {
            return null;
          }
        case "pinCode":
          if (!value) {
            return "Pin Code is required";
          } else if (value.length < 4) {
            return "Pin Code is inValid";
          } else {
            return null;
          }
        default:
          return null;
      }
    },

    handelBillingInfo: function(e) {
      const { firstName, lastName, addressLine, pinCode, email, phone } = this;
      e.preventDefault();
      const allError = {};
      const data = {
        firstName: firstName,
        lastName: lastName,
        addressLine: addressLine,
        pinCode: pinCode,
        email: email,
        phone: phone
      };

      Object.keys(data).forEach(key => {
        const error = this.validate(key, data[key]);
        if (error) {
          allError[key] = error;
        }
      });
      if (Object.keys(allError).length > 0) {
        this.errorMsg = allError;
        console.log("error msg", this.errorMsg);
        return;
      } else {
        if (!Object.keys(allError).length) {
          this.errorMsg = [];
          alert("Hello!" + data.firstName);
        }
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.App {
  font-family: sans-serif;
  text-align: center;
}

input {
  background-repeat: no-repeat;
  background-position: 6px;
  border: 1px solid #dadada;
  margin-top: 10px;
  margin-bottom: 10px;
  padding-left: 5px;
  width: 310px;
  height: 30px;
  font-size: 14px;
}

.border {
  border: 2px solid;
}
.text-danger {
  color: red;
}
</style>
