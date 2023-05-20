<template>
  <div class=" d-flex w-100 h-100 p-3 flex-column">

    <div class="container-fluid">
      <div class="row ana-baslik">
        <div class="tool-tip">
          <Tooltip class="tooltip-style " :fitContent="true">

            <span class="tooltip-icon">⚠️</span> HQRC04
          </Tooltip>
        </div>
      </div>
      <div class="row row-gaz">
        <div class="col-md-2">
          <div class="card text-bg-dark mb-3">
            <div class="card-header text-green">
              BAĞLANTI BİLGİLERİ
            </div>
            <div class="card-body">
              <div class="d-flex justify-content-between flex-row">
                <p class="card-text">Yer istasyonu</p>
                <p class="card-text text-green">Bağlandı</p>
              </div>

              <div class="d-flex justify-content-between flex-row">
                <p class="card-text">Hakem Sunucu</p>
                <p class="card-text text-danger">Bağlı değil</p>
              </div>

              <div class="d-flex justify-content-between flex-row">
                <p class="card-text">IHA Bağlantı</p>
                <p class="card-text text-secondary">Bilgi yok</p>
              </div>

              <div class="d-flex justify-content-between flex-row">
                <p class="card-text">Yarışma Süresi</p>
                <p class="card-text text-secondary">Bilgi yok</p>
              </div>

            </div>
          </div>

          <div class="card text-bg-dark mb-3">
            <div class="card-header text-green">
              SUNUCU BİLGİLERİ
            </div>
            <div class="card-body">

              <div class="mb-2 row align-items-center">
                <label for="takim_no" class="col-sm-4 col-form-label">Takım No.</label>
                <div class="col-sm-8">
                  <input type="text" class="form-control form-control-sm" id="takim_no">
                </div>
              </div>

              <div class="mb-2 row align-items-center">
                <label for="hakem_sunucu" class="col-sm-4 col-form-label">Hakem Sunucu</label>
                <div class="col-sm-5">
                  <input type="text" class="form-control form-control-sm" id="hakem_sunucu">
                </div>

                <div class="col-sm-3">
                  <input type="text" class="form-control form-control-sm" id="hakem_sunucu_port">
                </div>
              </div>

              <div class="mb-2 row align-items-center">
                <label for="iha_adres" class="col-sm-4 col-form-label">IHA Adres</label>
                <div class="col-sm-5">
                  <input type="text" class="form-control form-control-sm" id="iha_adres">
                </div>

                <div class="col-sm-3">
                  <input type="text" class="form-control form-control-sm" id="iha_adres_port">
                </div>
              </div>

              <div class="mb-2 row align-items-center">
                <label for="username" class="col-sm-4 col-form-label">Kullanıcı Adı</label>
                <div class="col-sm-8">
                  <input type="text" class="form-control form-control-sm" id="username">
                </div>
              </div>

              <div class="mb-2 row align-items-center">
                <label for="password" class="col-sm-4 col-form-label">Şifre</label>
                <div class="col-sm-8">
                  <input type="text" class="form-control form-control-sm" id="password">
                </div>
              </div>

              <div class="d-grid gap-2 mt-3">
                <a href="#" class="btn btn-success">Kaydet</a>
              </div>

            </div>
          </div>

          <div class="card text-bg-dark mb-3">
            <div class="card-header text-green">
              GÖREV BİLGİLERİ
            </div>
            <div class="card-body">
              <div class="d-flex justify-content-between flex-row">
                <p class="card-text">Yarışma Süresi</p>
                <p class="card-text">00:00</p>
              </div>

              <div class="d-flex justify-content-between flex-row">
                <p class="card-text">Son Kilitlenme</p>
                <p class="card-text">156879</p>
              </div>

              <div class="d-flex justify-content-between flex-row">
                <p class="card-text">Kilitlenilen İHA Sayısı</p>
                <p class="card-text">5</p>
              </div>

              <div class="d-flex justify-content-between flex-row">
                <p class="card-text">Kamikaze Görevi</p>
                <p class="card-text text-green">Yapıldı</p>
              </div>

            </div>
          </div>

        </div>
        <div class="col-md-8 goruntu-gaz">
          <div class="row">
            <div>
              <Tooltip class="tooltip-style no-pading" :fitContent="true">

                <span class="tooltip-icon">⚠️</span> Gaz değeri
              </Tooltip>
            </div>

            <img id="kamera" :width="kamera.en" :height="kamera.boy">
            <Button class="camera-button" @click="takePhoto">
              <i class="pi pi-camera"></i>
              <span class="text-class">Görüntü AL</span>
            </Button>

          </div>
          <!-- <div class="col-md-4 gaz-tittle"> -->
          <div class="row">
            <div class="col-md-6">
              <div class="tool-tip">
              <Tooltip class="tooltip-style " :fitContent="true">

                <span class="tooltip-icon">⚠️</span> Gaz değeri
              </Tooltip>
            </div>

            <Slider class="sliderTitle" v-model="value" :min="0" :max="100" :step="25"></Slider>
            <p>Seçili değer: {{ value }}</p>

            <Message v-if="showMessage" :severity="severity" :content="uyari" @visibleChange="hideMessage"> {{
              this.uyari }} değer</Message>

          </div>
            </div>
           
        </div>





      </div>
      <div class="row">


        <div class="col-md-9">


          <div class="col-md-12 mt-4">
            <img class="img-fluid" src="https://via.placeholder.com/1500x300" alt="kadran">
          </div>

          <div class="col-md-12">
            <DataTable :value="logList" :scrollable="true" scrollHeight="380px" tableStyle="{'width':'auto'}"
              class="table table-dark table-dark-hover mt-3">
              <Column field="datetime" header="Tarih" [style]="{'width':'10px'}"></Column>
              <Column field="level" header="Seviye"></Column>
              <Column field="message" header="Mesaj"></Column>
            </DataTable>

          </div>
        </div>






      </div>

    </div>
  </div>
</template>

<script>

import sunucuBilgileriJSON from '../../sunucu_bilgileri.json'
import arayuzAssetVerileri from '@/assets/arayuz_assetleri.json'
import Slider from 'primevue/slider';
import DataTable from 'primevue/datatable';
import Column from 'primevue/column';
import Message from 'primevue/message';
import Button from 'primevue/button';

export default {
  name: 'App',
  components: {
    [DataTable.name]: DataTable,
    [Column.name]: Column,
    [Button.name]: Button,
    Slider,
    Message
  },
  watch: {
    value(newVal) {
      if (newVal < 33) {
        this.showMessage = true;
        this.severity = 'warn'
        this.uyari = "düşük"
      }
      else if (newVal => 33 && newVal <= 50) {
        this.showMessage = true;
        this.severity = 'error'
        this.uyari = "orta"
      }
      if (this.value == 100) {
        this.showMessage = true;
        this.severity = 'error'
        this.uyari = "yüksek"
      }

    }

  },
  data() {
    return {
      kamera: {
        en: 320,
        boy: 320,
      },

      value: 0,
      showMessage: false,
      severity: "info",
      uyari: "",
      sunucuBilgileri: JSON.parse(JSON.stringify(sunucuBilgileriJSON)),

      yerIstasyonuWebsocket: null,
      websocketBaglantiTimeout: 5000, // 5 sn

      yerIstasyonuBagli: false,
      hakemSunucuBagli: false,
      ihaDurum: 'Bilgi yok',
      yarismaSuresi: 'Bilgi yok', // Nasi yapilir ? Sunucudan da gelebilir.

      msg: '',
      response: '',
      logs: '',
      logSeviyeITOS: {
        0: 'NOTSET',
        10: 'DEBUG',
        20: 'INFO',
        30: 'WARNING',
        40: 'ERROR',
        50: 'CRITICAL',
      },
      logSeviyeSTOI: {
        NOTSET: 0,
        DEBUG: 10,
        INFO: 20,
        WARNING: 30,
        ERROR: 40,
        CRITICAL: 50,
      },
      logList: [
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
        { 'datetime': '01/01/2032 16:23:05:159873', 'level': 'INFO', 'message': 'Test Mesajı' },
      ]


    }
  },
  created() {

  },
  mounted() {

  },
  methods: {

    hideMessage() {
      this.showMessage = false;
    },
    logAnlikZaman() {
      var dt = new Date();
      return `${dt.getHours()}:${dt.getMinutes()}:${dt.getSeconds()}.${dt.getMilliseconds()}`;
    },
    loglaraEkle(log) {
      this.logs += `${log}\n`;
      this.logList.push(log);
      // Burdan sonrası asagi autoscroll
      var textarea = this.$refs.logtextarea;
      if (textarea === undefined || textarea === null)
        return;
      textarea.scrollTop = textarea.scrollHeight;
      this.$forceUpdate();
      this.logTableAsagiScroll();
    },
    logTableAsagiScroll() {
      var dt = document.getElementsByClassName('ui-datatable-scrollable-body')[0];
      if (dt === undefined || dt === null) return
      dt.scrollTop = dt.scrollHeight - dt.clientHeight;
    },


  }
}
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
} */

.container {
  display: flex;
  flex-direction: column;
}

.bilgiler-kamera-kalman {
  display: flex;
  margin-left: 10px;
  margin-right: 10px;
}

.bilgiler {
  display: flex;
  flex-direction: column;
  margin-right: 10px;
}

.bilgiler>* {
  border: solid 1px;
}

.satir-1 {
  display: flex;
}

.sunucu-bilgileri {
  display: flex;
  flex-direction: column;
}

.bilgi-satir {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  max-height: 40px;
}

.kamera-ibreler-kalman {
  display: flex;
  flex-direction: column;
}

.kamera-kalman {
  display: flex;
}

.kamera-kalman>* {
  border: solid 1px black;
}

.ibreler {
  display: flex;
  justify-content: center;
  background-color: black;
  border: 5px solid gray;
  border-bottom-right-radius: 50px;
  border-bottom-left-radius: 50px;
}

.ibreler>* {
  margin-right: 10px;
}

.kalman-harita {
  /* background-color: green; */
  border: solid 1px black;
  width: 40%;
}

/* #kamera-ibreler-canvas {
  width: 33%;
} */

.hizli-komutlar-satir {
  display: flex;
  flex-direction: column;
}

.hizli-komutlar {
  display: flex;
  justify-content: center;
}

.yki-komut {
  display: flex;
  justify-content: center;
}

.log-satir {
  display: flex;
  flex-direction: row;
}

.log-kayitlari {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  padding: 0.5%;
  margin: 0.5%;
  width: 100%;
}

#logtextarea {
  width: 100%;
  min-height: 250%;
}

#logtable tr {
  font-size: 13px;
  height: 30px;
}

body {
  font-family: Roboto Mono;
  background-color: #121212;
}

.text-green {
  color: #94bc2f !important;
}


.btn-outline-success {
  --bs-btn-color: #94bc2f;
  --bs-btn-border-color: #94bc2f;
  --bs-btn-hover-color: #fff;
  --bs-btn-hover-bg: #94bc2f;
  --bs-btn-hover-border-color: #94bc2f;
  --bs-btn-focus-shadow-rgb: 25, 135, 84;
  --bs-btn-active-color: #fff;
  --bs-btn-active-bg: #94bc2f;
  --bs-btn-active-border-color: #94bc2f;
  --bs-btn-active-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  --bs-btn-disabled-color: #94bc2f;
  --bs-btn-disabled-bg: transparent;
  --bs-btn-disabled-border-color: #94bc2f;
  --bs-gradient: none;
}

.btn-success {
  --bs-btn-color: #fff;
  --bs-btn-bg: #94bc2f;
  --bs-btn-border-color: #94bc2f;
  --bs-btn-hover-color: #fff;
  --bs-btn-hover-bg: #648121;
  --bs-btn-hover-border-color: #648121;
  --bs-btn-focus-shadow-rgb: 60, 153, 110;
  --bs-btn-active-color: #fff;
  --bs-btn-active-bg: #648121;
  --bs-btn-active-border-color: #13653f;
  --bs-btn-active-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  --bs-btn-disabled-color: #fff;
  --bs-btn-disabled-bg: #94bc2f;
  --bs-btn-disabled-border-color: #94bc2f;
}

.camera-button {
  font-size: 600px;
  width: 50%;
  height: 100px;
  margin-bottom: 0.5rem;
}

.pi pi-camera {
  font-size: large;
  margin-left: 10px;
}

.text-class {

  margin-left: 50px;
  text-align: center;

}

.Gaz-Tittle {
  color: white;
  position: relative;
}

.slider-container {
  width: 300px;
  height: 30px;
}

.tooltip-style {
  background-color: #f1f1f1;
  color: #333;

  padding: 16px;

  /* padding-right: 50%;
  padding-left: 50%; */
  font-size: large;

}

.tooltip-icon {
  margin-right: 10px;


}

.sliderTitle {
  margin: 15%;
  margin-left: 0%;

}

.tool-tip {
  display: flex;
  justify-content: center;
  background-color: #f1f1f1;
  border: 1px solid #ccc;
  border-radius: 16px;
}

.goruntu-gaz {
  display: flex;
  flex-direction: column;
}

.goruntu-gaz>h2 {
  color: black;
  background-color: #f1f1f1;
  border-radius: 5%;
}
.goruntu-gaz *{
  margin-top: 1%;
}
.ana-baslik {
  color: white;
  display: flex;
  justify-content: center;
  margin-bottom: 1%;

}

.no-pading {
  padding: 0px !important;
  padding-top: 1% !important;
}

.row-gaz {
  display: flex;
}
</style>
