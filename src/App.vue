<template>
  <div class=" d-flex w-100 h-100 p-3 flex-column">

    <div class="container-fluid">
      <div class="row ana-baslik">
        <div class="tool-tip">
          <Tooltip class="tooltip-style " :fitContent="true">

             Smart Trash Bin
          </Tooltip>
        </div>
      </div>
      <div class="row row-gaz">

        <div class="col-md-12 goruntu-gaz ">
          <div class="row camera-div">
            <div class="col-md-4">
              <div class="tool-tip">
                <Tooltip class="tooltip-style " :fitContent="true">

                  <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="currentColor" class="bi bi-trash2"
                    viewBox="0 0 16 16">
                    <path
                      d="M14 3a.702.702 0 0 1-.037.225l-1.684 10.104A2 2 0 0 1 10.305 15H5.694a2 2 0 0 1-1.973-1.671L2.037 3.225A.703.703 0 0 1 2 3c0-1.105 2.686-2 6-2s6 .895 6 2zM3.215 4.207l1.493 8.957a1 1 0 0 0 .986.836h4.612a1 1 0 0 0 .986-.836l1.493-8.957C11.69 4.689 9.954 5 8 5c-1.954 0-3.69-.311-4.785-.793z" />
                  </svg>  HCSR04 % {{ doluluk }}
                </Tooltip>
              </div>
              <img id="kamera" ref="kamera" :width="160" :height="160">
              <Button class="camera-button" @click="takephoto()">
                <i class="pi pi-camera"></i>
                <span class="text-class">Görüntü AL</span>
              </Button>
            </div>



          </div>
          <!-- <div class="col-md-4 gaz-tittle"> -->
          <div class="row mt-3">
            <div class="col-md-6 tool-tip-div">
              <div class="tool-tip">
                <Tooltip class="tooltip-style " :fitContent="true">

                  <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="red"
                    class="bi bi-exclamation-triangle" viewBox="0 0 16 16">
                    <path
                      d="M7.938 2.016A.13.13 0 0 1 8.002 2a.13.13 0 0 1 .063.016.146.146 0 0 1 .054.057l6.857 11.667c.036.06.035.124.002.183a.163.163 0 0 1-.054.06.116.116 0 0 1-.066.017H1.146a.115.115 0 0 1-.066-.017.163.163 0 0 1-.054-.06.176.176 0 0 1 .002-.183L7.884 2.073a.147.147 0 0 1 .054-.057zm1.044-.45a1.13 1.13 0 0 0-1.96 0L.165 13.233c-.457.778.091 1.767.98 1.767h13.713c.889 0 1.438-.99.98-1.767L8.982 1.566z" />
                    <path
                      d="M7.002 12a1 1 0 1 1 2 0 1 1 0 0 1-2 0zM7.1 5.995a.905.905 0 1 1 1.8 0l-.35 3.507a.552.552 0 0 1-1.1 0L7.1 5.995z" />
                  </svg> MQ4 GAZ SENSÖRÜ {{ gazvalue }} PPM
                </Tooltip>
              </div>

              <Message :severity="gazseverity" :content="gazuyari" @visibleChange="gazhideMessage"> {{
                this.gazuyari }} değer</Message>


              <Slider class="sliderTitle" v-model="gazvalue" :min="0" :max="100" :step="1"></Slider>



            </div>
            <div class="col-md-6 tool-tip-div">
              <div class="tool-tip">
                <Tooltip class="tooltip-style " :fitContent="true">

                  <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="#D3D30C" class="bi bi-lightning"
                    viewBox="0 0 16 16">
                    <path
                      d="M5.52.359A.5.5 0 0 1 6 0h4a.5.5 0 0 1 .474.658L8.694 6H12.5a.5.5 0 0 1 .395.807l-7 9a.5.5 0 0 1-.873-.454L6.823 9.5H3.5a.5.5 0 0 1-.48-.641l2.5-8.5zM6.374 1 4.168 8.5H7.5a.5.5 0 0 1 .478.647L6.78 13.04 11.478 7H8a.5.5 0 0 1-.474-.658L9.306 1H6.374z" />
                  </svg> IŞIK DEĞERİ LDR % {{ isik_value }}
                </Tooltip>
              </div>

              <Message :severity="o2severity" :content="o2uyari" @visibleChange="o2hideMessage"> {{
                this.o2uyari }} değer</Message>

              <Slider class="sliderTitle" v-model="isik_value" :min="0" :max="100" :step="1"></Slider>



            </div>


          </div>

        </div>





      </div>
      <div class="row">
        <div class="col-md-4 tool-tip-div">
          <div class="tool-tip">
            <Tooltip class="tooltip-style " :fitContent="true">

              <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="black" class="bi bi-fan"
                viewBox="0 0 16 16">
                <path
                  d="M10 3c0 1.313-.304 2.508-.8 3.4a1.991 1.991 0 0 0-1.484-.38c-.28-.982-.91-2.04-1.838-2.969a8.368 8.368 0 0 0-.491-.454A5.976 5.976 0 0 1 8 2c.691 0 1.355.117 1.973.332.018.219.027.442.027.668Zm0 5c0 .073-.004.146-.012.217 1.018-.019 2.2-.353 3.331-1.006a8.39 8.39 0 0 0 .57-.361 6.004 6.004 0 0 0-2.53-3.823 9.02 9.02 0 0 1-.145.64c-.34 1.269-.944 2.346-1.656 3.079.277.343.442.78.442 1.254Zm-.137.728a2.007 2.007 0 0 1-1.07 1.109c.525.87 1.405 1.725 2.535 2.377.2.116.402.222.605.317a5.986 5.986 0 0 0 2.053-4.111c-.208.073-.421.14-.641.199-1.264.339-2.493.356-3.482.11ZM8 10c-.45 0-.866-.149-1.2-.4-.494.89-.796 2.082-.796 3.391 0 .23.01.457.027.678A5.99 5.99 0 0 0 8 14c.94 0 1.83-.216 2.623-.602a8.359 8.359 0 0 1-.497-.458c-.925-.926-1.555-1.981-1.836-2.96-.094.013-.191.02-.29.02ZM6 8c0-.08.005-.16.014-.239-1.02.017-2.205.351-3.34 1.007a8.366 8.366 0 0 0-.568.359 6.003 6.003 0 0 0 2.525 3.839 8.37 8.37 0 0 1 .148-.653c.34-1.267.94-2.342 1.65-3.075A1.988 1.988 0 0 1 6 8Zm-3.347-.632c1.267-.34 2.498-.355 3.488-.107.196-.494.583-.89 1.07-1.1-.524-.874-1.406-1.733-2.541-2.388a8.363 8.363 0 0 0-.594-.312 5.987 5.987 0 0 0-2.06 4.106c.206-.074.418-.14.637-.199ZM8 9a1 1 0 1 0 0-2 1 1 0 0 0 0 2Z" />
                <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14Zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16Z" />
              </svg> Fan Level {{ fan_speed }}
            </Tooltip>
          </div>
          <div class="button-level-style">
            <Button v-bind:class="{'p-button-danger':fan_speed==0}" @click="insertvalue('fan_level', 0)">kapalı</Button>
            <Button v-bind:class="{'p-button-danger':fan_speed==1}"  @click="insertvalue('fan_level', 1)">düşük</Button>
            <Button v-bind:class="{'p-button-danger':fan_speed==2}"  @click="insertvalue('fan_level', 2)">orta</Button>
            <Button v-bind:class="{'p-button-danger':fan_speed==3}"  @click="insertvalue('fan_level', 3)">yüksek</Button>

          </div>



        </div>
        <div class="col-md-4 tool-tip-div">
          <div class="tool-tip">
            <Tooltip class="tooltip-style " :fitContent="true">

              <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="currentColor"
                class="bi bi-life-preserver" viewBox="0 0 16 16">
                <path
                  d="M8 16A8 8 0 1 0 8 0a8 8 0 0 0 0 16zm6.43-5.228a7.025 7.025 0 0 1-3.658 3.658l-1.115-2.788a4.015 4.015 0 0 0 1.985-1.985l2.788 1.115zM5.228 14.43a7.025 7.025 0 0 1-3.658-3.658l2.788-1.115a4.015 4.015 0 0 0 1.985 1.985L5.228 14.43zm9.202-9.202-2.788 1.115a4.015 4.015 0 0 0-1.985-1.985l1.115-2.788a7.025 7.025 0 0 1 3.658 3.658zm-8.087-.87a4.015 4.015 0 0 0-1.985 1.985L1.57 5.228A7.025 7.025 0 0 1 5.228 1.57l1.115 2.788zM8 11a3 3 0 1 1 0-6 3 3 0 0 1 0 6z" />
              </svg> Servo Level {{ Servo_speed }}
            </Tooltip>

          </div>
          <div class="button-level-style">
            <Button v-bind:class="{'p-button-danger':Servo_speed==0}"  @click="insertvalue('servo_level', 0)">kapalı</Button>
            <Button v-bind:class="{'p-button-danger':Servo_speed==1}" @click="insertvalue('servo_level', 1)">Açık</Button>


          </div>




        </div>
        <div class="col-md-4 tool-tip-div">
          <div class="tool-tip">
            <Tooltip class="tooltip-style " :fitContent="true">

              <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="#D3D30C" class="bi bi-lightbulb"
                viewBox="0 0 16 16">
                <path
                  d="M2 6a6 6 0 1 1 10.174 4.31c-.203.196-.359.4-.453.619l-.762 1.769A.5.5 0 0 1 10.5 13a.5.5 0 0 1 0 1 .5.5 0 0 1 0 1l-.224.447a1 1 0 0 1-.894.553H6.618a1 1 0 0 1-.894-.553L5.5 15a.5.5 0 0 1 0-1 .5.5 0 0 1 0-1 .5.5 0 0 1-.46-.302l-.761-1.77a1.964 1.964 0 0 0-.453-.618A5.984 5.984 0 0 1 2 6zm6-5a5 5 0 0 0-3.479 8.592c.263.254.514.564.676.941L5.83 12h4.342l.632-1.467c.162-.377.413-.687.676-.941A5 5 0 0 0 8 1z" />
              </svg> Light Level {{ light_level }}
            </Tooltip>
          </div>
          <div class="button-level-style">
            <Button v-bind:class="{'p-button-danger':light_level==0}" @click="insertvalue('light_level', 0)">Kapalı</Button>
            <Button v-bind:class="{'p-button-danger':light_level==1}" @click="insertvalue('light_level', 1)">Düşük</Button>
            <Button v-bind:class="{'p-button-danger':light_level==2}" @click="insertvalue('light_level', 2)">Orta</Button>
            <Button v-bind:class="{'p-button-danger':light_level==3}" @click="insertvalue('light_level', 3)">Yüksek</Button>
          </div>




        </div>

      </div>
      <div class="row">






        <DataTable :value="logList" :scrollable="true" scrollHeight="380px" tableStyle="{'width':'auto'}"
          class="table table-dark table-dark-hover mt-3">
          <Column field="datetime" header="Tarih" [style]="{'width':'10px'}"></Column>
          <Column field="level" header="Seviye"></Column>
          <Column field="message" header="Mesaj"></Column>
        </DataTable>









      </div>

    </div>
  </div>
</template>

<script>

import arayuzAssetVerileri from '@/assets/arayuz_assetleri.json'
import Slider from 'primevue/slider';
import DataTable from 'primevue/datatable';
import Column from 'primevue/column';
import Message from 'primevue/message';
import Button from 'primevue/button';
import { initializeApp } from 'firebase/app';
import { getDatabase, ref, onValue, set } from 'firebase/database';

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
    gazvalue(newVal) {
      console.log(newVal)
      if (newVal < 33) {
        this.gazshowMessage = true;
        this.gazseverity = 'warn'
        this.gazuyari = "düşük"
      }
      else if (newVal >= 33 && newVal < 75) {
        this.gazshowMessage = true;
        this.gazseverity = 'info'
        this.gazuyari = "orta"
      }
      else {// if (newVal >= 75) {
        this.gazshowMessage = true;
        this.gazseverity = 'error'
        this.gazuyari = "yüksek"
      }

    },
    isik_value(newVal) {
      if (newVal < 256) {
        this.o2showMessage = true;
        this.o2severity = 'warn'
        this.o2uyari = "düşük"
      }
      else if (newVal >= 256 && newVal < 768) {
        this.o2showMessage = true;
        this.o2severity = 'info'
        this.o2uyari = "orta"
      }
      else {
        this.o2showMessage = true;
        this.o2severity = 'error'
        this.o2uyari = "yüksek"
      }

    }

  },
  data() {
    return {
      kamera: {
        en: 320,
        boy: 320,
      },
      firebaseConfig: {

        databaseURL: "https://trash-9498e-default-rtdb.firebaseio.com/",

      },
      app: null,
      database: null,
      gazvalue: 0,
      o2value: 0,
      isik_value: 0,
      doluluk: 0,
      light_level: null,
      fan_speed: null,
      Servo_speed: null,


      o2showMessage: false,
      gazshowMessage: false,
      o2severity: "warn",
      o2uyari: "düşük",
      gazseverity: "warn",
      gazuyari: "düşük",

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

      ]


    }
  },
  created() {


  },
  mounted() {

    this.parsedata();

  },
  methods: {
    addlog(level, message) {
      var date = new Date()
      this.logList.push({
        datetime: date,
        level: level,
        message: message
      });
    },
    parsedata() {
      const app = initializeApp(this.firebaseConfig);
      const database = getDatabase(app);
      const arduino = ref(database, '/arduino');

      // Değişiklikleri dinle
      onValue(arduino, (snapshot) => {
        const data = snapshot.val();
        const parts = data.split("&");
        const values = {};

        parts.forEach(part => {
          part=part.replace("G=G=","G=")
          const sipletted = part.split("=");
          const key=sipletted[0];
          const value=sipletted[sipletted.length-1]
          console.log(key);
          console.log("value : " + value)
          if (key == "G") {
            this.gazvalue = parseFloat(value)
          }
          else if (key == "L") {
            this.isik_value = parseInt(value / 10)
          }
          else if (key == "D") {
            this.doluluk = parseFloat(value)
          }
          else if (key == "LS") {
            this.light_level = parseInt(value);

          }
          else if (key == "FS") {
            this.fan_speed = parseInt(value);
          }
          else if (key == "SS") {
            this.Servo_speed = parseInt(value);
          }
        });

        // document.getElementById("kamera").src=data
        // this.gazvalue=data
        // Verileri kullanın veya işleyin
      });
    },


    insertvalue(dbrefname, deger) {
      // Firebase referansını oluşturun
      const app = initializeApp(this.firebaseConfig);
      const database = getDatabase(app);
      const databaseRef = ref(database, '/' + dbrefname);
      // const databaseRef = ref(database, $`/{dbrefname}`);

      // Veriyi ekleyin
      set(databaseRef,
        deger
      )
        .then(() => {
          console.log('Veri eklendi');
        })
        .catch((error) => {
          console.error('Veri eklenirken bir hata oluştu:', error);
        });
    },
    takegazvalue() {

      const app = initializeApp(this.firebaseConfig);
      const database = getDatabase(app);
      const espCamRef = ref(database, '/gaz_value');

      // Değişiklikleri dinle
      onValue(espCamRef, (snapshot) => {
        const data = snapshot.val();
        console.log(data);
        // document.getElementById("kamera").src=data
        this.gazvalue = data
        // Verileri kullanın veya işleyin
      });

    },
    takeo2value() {
      const app = initializeApp(this.firebaseConfig);
      const database = getDatabase(app);
      const espCamRef = ref(database, '/oksijen_value');

      // Değişiklikleri dinle
      onValue(espCamRef, (snapshot) => {
        const data = snapshot.val();

        // document.getElementById("kamera").src=data
        this.o2value = data
        // Verileri kullanın veya işleyin
      });

    },
    takephoto() {
      this.insertvalue("take_photo", true);
      const app = initializeApp(this.firebaseConfig);
      const database = getDatabase(app);
      // Veritabanı referansını alın
      const espCamRef = ref(database, '/esp32-cam');

      // Değişiklikleri dinle
      onValue(espCamRef, (snapshot) => {
        const data = snapshot.val();
        // document.getElementById("kamera").src=data
        this.$refs["kamera"].src = data
        this.addlog("INFO", "görüntü alındı..")
        // Verileri kullanın veya işleyin
      });
    },
    gazhideMessage() {
      this.gazshowMessage = false;
    },
    o2hideMessage() {
      this.o2showMessage = false;
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
  width: 100%;
  height: 100px;
  margin-bottom: 0.5rem;
  margin-top: 1%;
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
  font-size: x-large;

}

.tooltip-icon {
  margin-right: 10px;


}

.sliderTitle {
  margin: 10%;
  margin-left: 1%;
  margin-right: 1%;

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

.ana-baslik {
  color: white;
  display: flex;
  justify-content: center;
  margin-bottom: 1%;

}

.no-padding {
  padding: 0px !important;
  padding-top: 1% !important;
}

img+button {
  margin-bottom: 10%;
}

.row-gaz {
  display: flex;
}

#kamera {
  width: 100%;
  height: 320px;

}

.camera-div {
  display: flex;
  justify-content: center;
}

.tool-tip-div p {

  color: white;
}

.baglanti-bilgisi-div .card-body {
  display: flex;

  flex-direction: column;
  justify-content: space-between;
  align-content: space-between;

}


.card-body>div {
  display: flex;
  align-content: stretch;
}

.button-level-style {
  display: flex;
  justify-content: space-between;
  align-items: stretch;
  align-content: stretch;
}

.button-level-style>button {
  display: flex;
  /* align-items: stretch; */
  align-content: stretch;
  width: 100%;
  border-radius: 10px;
  margin-top: 2%;
}</style>
