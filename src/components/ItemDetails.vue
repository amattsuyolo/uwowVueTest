<template>
    <!-- 模態視窗 (只有在 isVisible 為 true 時才顯示) -->
    <div v-if="isVisible" class="modal-overlay">
        <div class="modal">
            <!-- 標題與關閉按鈕 -->
            <div class="modal-header">
                <h2 class="modal-title">Item Details</h2>
                <button class="close-button" @click="$emit('close-details')">✕</button>
            </div>

            <!-- 產品圖片與按鈕 (按鈕在右下角) -->
            <div class="product-image">
                {{ product.name }}
                <button class="seen-in-button" @click="$emit('open-seen-in')">Seen In</button>
            </div>

            <!-- 產品描述文字 -->
            <div class="description">
                <p>Some text description</p>
                <p>Some text description</p>
                <p>Some text description</p>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        product: Object,
        isVisible: Boolean
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
    position: relative;
    width: 400px;
    max-width: 90%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

/* 標題置中 */
.modal-title {
    font-size: 28px;
    font-weight: bold;
    margin: 0;
    text-align: center;
    flex-grow: 1;
}

/* 關閉按鈕樣式 */
.close-button {
    background: none;
    border: none;
    font-size: 24px;
    cursor: pointer;
    position: absolute;
    top: 10px;
    right: 10px;
}

/* 產品圖片樣式 */
.product-image {
    background-color: rgb(0, 110, 255);
    color: white;
    text-align: center;
    padding: 50px;
    font-size: 24px;
    border-radius: 10px;
    margin-bottom: 20px;
    position: relative;
}

/* Seen In 按鈕移動到產品圖片右下角 */
.seen-in-button {
    background-color: green;
    color: white;
    border: none;
    padding: 8px 12px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 16px;
    position: absolute; /* 相對於 product-image */
    bottom: 10px;
    right: 10px;
}

.seen-in-button:hover {
    background-color: darkgreen;
}

/* 產品描述文字置中 */
.description {
    text-align: center;
    margin-top: 20px;
}

.description p {
    font-size: 16px;
    line-height: 1.5;
}
</style>
