<template>
  <div>
    <PostList :posts="posts" @open-details="showItemDetails" />
    <ItemDetails 
      :product="selectedProduct" 
      :isVisible="isItemDetailsVisible" 
      @close-details="isItemDetailsVisible = false"
      @open-seen-in="openSeenIn"
    />
    <SeenIn 
      :product="selectedProduct" 
      :isVisible="isSeenInVisible" 
      @close-seen-in="isSeenInVisible = false"
      @back-to-details="goBackToDetails"
    />
  </div>
</template>

<script>
import PostList from './components/PostList.vue'
import ItemDetails from './components/ItemDetails.vue'
import SeenIn from './components/SeenIn.vue'

export default {
  components: {
    PostList,
    ItemDetails,
    SeenIn
  },
  data() {
    return {
      posts: [
        { id: 1, title: "Post Image 1", products: [{ id: 1, name: "Product Image1", img: "https://via.placeholder.com/150", description: "Product A details" },{ id: 2, name: "Product Image2", img: "https://via.placeholder.com/150", description: "Product A details" },{ id: 3, name: "Product Image3", img: "https://via.placeholder.com/150", description: "Product A details" }] },
        { id: 2, title: "Post Image 2", products: [{ id: 4, name: "Product Image4", img: "https://via.placeholder.com/150", description: "Product B details" },{ id: 5, name: "Product Image5", img: "https://via.placeholder.com/150", description: "Product B details" },{ id: 6, name: "Product Image6", img: "https://via.placeholder.com/150", description: "Product B details" }] }
      ],
      selectedProduct: null,
      isItemDetailsVisible: false,
      isSeenInVisible: false
    };
  },
  methods: {
    showItemDetails(product) {
      this.selectedProduct = product;
      this.isItemDetailsVisible = true;
    },
    openSeenIn() {
      this.isItemDetailsVisible = false;
      this.isSeenInVisible = true;
    },
    goBackToDetails() {
      this.isItemDetailsVisible = true;
      this.isSeenInVisible = false;
    }
  }
}
</script>
