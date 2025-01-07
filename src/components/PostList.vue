<template>
    <div class="post-container">
        <!-- Post Image 占上方一半高度 -->
        <div class="post-image">
            {{ posts[0].title }}
        </div>

        <!-- 小空白分隔線 -->
        <div class="divider"></div>

        <!-- Product Images (三等分且無間隔) -->
        <div class="product-container">
            <div 
                class="product-image" 
                v-for="product in posts[0].products" 
                :key="product.id" 
                @click="$emit('open-details', product)"
            >
                {{ product.name }}
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        posts: Array
    }
};
</script>
  
<style scoped>
/* 整個頁面佔滿螢幕高度 */
.post-container {
    height: 100vh;
    display: flex;
    flex-direction: column;
    margin: 0;
    padding: 0;
}

/* Post Image 佔據上方一半高度 */
.post-image {
    background-color: rgb(0, 110, 255);
    color: white;
    font-size: 48px;
    padding: 50px;
    width: 100%;
    text-align: center;
    box-sizing: border-box;
    flex: 1; 
    display: flex;
    justify-content: center;
    align-items: center;
}

/* 小空白分隔線 */
.divider {
    height: 10px; /* 控制空白的高度 */
    background-color: white; /* 與背景顏色一致 */
    width: 100%;
}

/* Product Images 容器 (三等分且無間隔) */
.product-container {
    flex: 1; 
    display: flex;
    width: 100%;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

/* 每張產品圖片佔 1/3 寬度且無間隔 */
.product-image {
    flex: 1; /* 每張佔據 1/3 */
    background-color: rgb(0, 110, 255);
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-size: 24px;
    border: none;
    cursor: pointer;
    transition: background-color 0.2s ease, transform 0.2s ease;
}

/* Hover 效果 */
.product-image:hover {
    background-color: darkblue;
    transform: scale(1.05);
}
</style>
