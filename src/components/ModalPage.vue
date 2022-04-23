<template>
  <div class="modal-bg">
    <div class="modal-container">
      <h2 class="modal-title">모달창 제목</h2>
      <p class="modal-text">모달입니다.</p>
      <button class="btn modal-close">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalPage',
  data() {},
  methods: {},
};
</script>

<style>
.modal-bg {
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  width: 100%;
  height: 100%;
  z-index: 5;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-container {
  width: 600px;
  background: #fff;
  border-radius: 5px;
  margin: 0 auto;
  padding: 20px;
}

.modal-title {
}

.modal-close {
  cursor: pointer;
}

.modal-close:hover {
  background: #324b67;
}
</style>
