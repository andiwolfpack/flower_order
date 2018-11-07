<template>
  <div>
    <v-data-table :headers="headers" :items="orders" :loading="loading" hide-actions class="elevation-1">
      <v-progress-linear slot="progress" color="blue" indeterminate></v-progress-linear>
      <template slot="items" slot-scope="props">
        <td class="text-xs-left">{{ props.item.id }}</td>
        <td class="text-xs-left">{{ props.item.description }}</td>
        <td class="text-xs-left">{{ props.item.price }}</td>
        <td class="text-xs-left">{{ props.item.deliver_to }}</td>
        <td><img :src="props.item.image" style="width: 300px; height: 150px"></td>
      </template>
    </v-data-table>
    <p>{{answer}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: () => ({
    headers: [
      {
        text: "Order ID",
        align: "left",
        sortable: true,
        value: "id"
      },
      {
        text: "Description",
        value: "description"
      },
      {
        text: "Price",
        value: "price"
      },
      {
        text: "Deliver to",
        value: "deliver_to"
      },
      {
        text: "Image",
        value: "image"
      }
    ],
    orders: [],
    answer: "",
    loading: true
  }),
  created: function() {
    let _this = this;
    axios
      .get("http://demo5252393.mockable.io/flowers")
      .then(function(response) {
        _this.orders = response.data;
        _this.loading = false;
      })
      .catch(function(error) {
        _this.answer = "Error! Could not reach the API. " + error;
      });
  }
};
</script>

<style>
</style>