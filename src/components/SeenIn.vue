<template>
    <!-- 模態視窗 (只有在 isVisible 為 true 時才顯示) -->
    <div v-if="isVisible" class="modal-overlay">
        <div class="modal">
            <!-- 標題區域 -->
            <div class="modal-header">
                <!-- 返回箭頭 -->
                <button class="back-button" @click="$emit('back-to-details')">←</button>
                <h2 class="modal-title">Seen In</h2>
                <!-- 關閉按鈕 -->
                <button class="close-button" @click="$emit('close-seen-in')">✕</button>
            </div>

            <!-- 上方的產品圖片 -->
            <div class="product-image">
                {{ product.name }}
            </div>

            <!-- 中間 Post Image -->
            <div class="post-image">
                Post Image {{ product.id }}
            </div>

            <!-- 下方三個產品圖片 (可點擊回到 Item Details) -->
            <div class="related-products">
                <div 
                    v-for="relatedProduct in relatedProducts" 
                    :key="relatedProduct.id" 
                    class="product-item"
                    @click="$emit('open-details', relatedProduct)"
                >
                    {{ relatedProduct.name }}
                </div>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        product: Object,
        isVisible: Boolean
    },
    computed: {
        relatedProducts() {
            // 模擬回傳三個產品 (可根據實際資料調整)
            return [
                { id: 1, name: "Product Image1" },
                { id: 4, name: "Product Image4" },
                { id: 5, name: "Product Image5" }
            ];
        }
    }
};
</script>
  
<style scoped>
/* 覆蓋整個螢幕的背景 */
.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.5); /* 半透明灰色背景 */
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
}

/* 彈窗主體 */
.modal {
    background: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
    width: 400px;
    max-width: 90%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

/* 標題與按鈕 */
.modal-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}

/* 返回按鈕 */
.back-button {
    background: none;
    border: none;
    font-size: 24px;
    cursor: pointer;
    color: black;
}

/* 標題文字置中 */
.modal-title {
    flex-grow: 1;
    text-align: center;
    font-size: 24px;
    font-weight: bold;
}

/* 關閉按鈕 */
.close-button {
    background: none;
    border: none;
    font-size: 24px;
    cursor: pointer;
    color: black;
}

/* 上方產品圖片樣式 */
.product-image {
    background-color: rgb(0, 110, 255);
    color: white;
    padding: 20px;
    font-size: 24px;
    border-radius: 10px;
    text-align: center;
    margin-bottom: 20px;
}

/* 中間 Post Image 樣式 */
.post-image {
    background-color: rgb(0, 110, 255);
    color: white;
    padding: 40px;
    font-size: 24px;
    border-radius: 10px;
    text-align: center;
    margin-bottom: 20px;
}

/* 下方相關產品區域 */
.related-products {
    display: flex;
    justify-content: space-around;
    gap: 10px;
    padding: 10px 0;
}

/* 每個產品圖片樣式 */
.product-item {
    background-color: rgb(0, 110, 255);
    color: white;
    padding: 15px;
    border-radius: 10px;
    cursor: pointer;
    text-align: center;
    flex: 1;
    transition: background-color 0.2s ease, transform 0.2s ease;
}

.product-item:hover {
    background-color: darkblue;
    transform: scale(1.1);
}
</style>
