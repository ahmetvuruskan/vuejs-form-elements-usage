<template>
  <div class="container">
    <h3>Form Verileriyle Çalışmak</h3>
    <hr>
    <div class="row">
      <div class="col-md-6">
        <div class="panel panel-warning">
          <div class="panel-heading">
            <h4>Başvuru Formu</h4>
          </div>
          <div class="panel-body">
            <form>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label for="email">Kullanıcı Adı</label>
                    <input v-model="userData.username"  type="text" id="username" class="form-control">
                  </div>
                  <div class="form-group">
                    <label for="password">Şifre</label>
                    <input v-model.lazy.trim="userData.password" type="password" id="password" class="form-control">
                  </div>
                  <div class="form-group">
                    <label for="age">Yaş</label>
                    <input v-model.number.trim="userData.age" type="number" id="age" class="form-control">
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label for="message">Açıklama</label><br>
                  <textarea id="message" rows="3" class="form-control" v-model="userData.message" ></textarea>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label>
                      <input v-model="userData.interests" type="checkbox" value="yazilim"> Yazılım
                    </label>
                    <label>
                      <input v-model="userData.interests" type="checkbox" value="donanim"> Donanım
                    </label>
                  </div>

                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label>
                    <input v-model="userData.gender" type="radio" value="erkek"> Erkek
                  </label>
                  <label>
                    <input v-model="userData.gender" type="radio" value="kadin"> Kadın
                  </label>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 from-group">
                  <label>Şehir</label>
                  <select v-model="userData.selectedCity" class="form-control">
                    <option
                        :selected="city == 'Adana'"
                        v-for="city in userData.cities" >{{city}}</option>
                  </select>
                </div>
              </div>
              <div class="row" >
                <div class="col-md-12 form-group">
                  <appswitch v-model="switched" ></appswitch>
                </div>
              </div>
              <hr>
              <div class="row">
                <div class="col-md-12">
                  <button
                      @click.prevent="submit()"
                    class="btn btn-primary">Gönder!
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
      <div class="col-md-6" v-if="isSubmitted" >
          <div class="panel panel-info">
            <div class="panel-heading">
              <h4>Form Verileri</h4>
            </div>
            <div class="panel-body">
              <p>Kullanıcı Adı: {{userData.username}} </p>
              <p>Şifre: {{userData.password}}  </p>
              <p>Yaş: {{userData.age}} </p>
              <p style="white-space: pre" >Açıklama: {{userData.message}}</p>
              <p><strong>İlgi Alanları</strong></p>
              <ul>
                <li v-for="item in userData.interests" >{{item}}</li>
              </ul>
              <p>Cinsiyet: {{userData.gender}} </p>
              <p>Şehir: {{userData.selectedCity}}</p>
              <p>Toggle:{{switched}}</p>
            </div>
          </div>
      </div>
    </div>

  </div>
</template>

<script>
import Switch from "./Switch";
  export default {
    components:{
      appswitch : Switch
    },
    data : ()=>{
      return {
       userData : {
         username : "ahmet",
         password : 123456,
         age : 22,
         message: '',
         interests : [],
         gender:null,
         cities : [
             'Antalya',
             'İstanbul',
             'Ankara',
             'İzmir',
             'Adana'
         ],
         selectedCity : null
       },
        switched :null,
        isSubmitted : false
      }
    },
    methods:{
      submit(){
        this.isSubmitted = true;

      }
    }
  }
</script>

<style>

</style>
