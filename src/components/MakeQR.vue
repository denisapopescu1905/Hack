<template>
  <div>
    <h1>QR Code Generator</h1>
    <div v-if="qrCodeImage">
      <img :src="qrCodeImage" alt="QR Code" />
    </div>
    <div v-else>
      <p>No data available.</p>
    </div>
  </div>
</template>

<script>
import QRCode from 'qrcode-generator';

export default {
  data() {
    return {
      data: 'https://ocw.cs.pub.ro/courses/',
      qrCodeImage: '',
    };
  },
  mounted() {
    const qr = QRCode(0, 'H');
    qr.addData(this.data);
    qr.make();
    this.qrCodeImage = qr.createDataURL(4); // Size of QR code image
  },
};
</script>
