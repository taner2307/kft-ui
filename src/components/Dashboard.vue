<template>
  <div class="tm-main-content" id="top">
    <div class="tm-top-bar-bg"></div>
    <div class="tm-top-bar" id="tm-top-bar">
      <div class="container">
        <div class="row">
          <nav class="navbar navbar-expand-lg narbar-light">
            <a class="navbar-brand mr-auto" href="#">
              <img src="../assets/img/logo.png" alt="servissecin">

            </a>
            <button type="button" id="nav-toggle" class="navbar-toggler collapsed" data-toggle="collapse"
                    data-target="#mainNav" aria-expanded="false" aria-label="Toggle navigation">
              <span class="navbar-toggler-icon"></span>
            </button>
            <div id="mainNav" class="collapse navbar-collapse tm-bg-white">
              <ul class="navbar-nav ml-auto">
                <li class="nav-item">
                  <a class="nav-link active" href="#top">Ana Sayfa <span class="sr-only">(current)</span></a>
                </li>
                <li class="nav-item">
                  <a class="nav-link" href="#tm-section-2">Özellikler</a>
                </li>
                <li class="nav-item">
                  <a class="nav-link" href="#tm-section-3">Ölçü Tablosu</a>
                </li>
              </ul>
            </div>
          </nav>
        </div> <!-- row -->
      </div> <!-- container -->
    </div> <!-- .tm-top-bar -->

    <div class="tm-page-wrap mx-auto">
      <section class="tm-banner">
        <div class="tm-container-outer tm-banner-bg">
          <div class="container">

            <div class="row tm-banner-row tm-banner-row-header">
              <div class="col-xs-12">
                <div class="tm-banner-header">
                  <h1 class="text-uppercase tm-banner-title">Haydi Başlayın</h1>
                  <img src="../assets/img/dots-3.png" alt="Dots">
                </div>
              </div>  <!-- col-xs-12 -->
            </div> <!-- row -->
            <div class="row tm-banner-row" id="tm-section-search">
              <div class="form-control">
                <h3><b>Beden Önerisi</b></h3><br/>
                <hr/>
                <div class="form-row tm-search-form-row">
                  <div class="form-group tm-form-group tm-form-group-pad tm-form-group-1">
                    <label for="inputCity">Boyun</label>
                    <input name="destination" v-model="suggestion.height" type="number" class="form-control" id="inputCity"
                           placeholder="cm">
                  </div>
                  <div class="form-group tm-form-group tm-form-group-pad tm-form-group-w">
                    <label for="inputCity">Kilon</label>
                    <input name="destination" v-model="suggestion.weight" type="number" class="form-control" id="inputCity"
                           placeholder="kg">
                  </div>
                  <div class="form-group tm-form-group tm-form-group-pad tm-form-group-w">
                    <label for="inputCity">Cinsiyetin</label>
                    <div class="form-check">
                      <input class="form-check-input" v-model="suggestion.gender" :value="'FEMALE'" type="radio"
                             name="flexRadioDefault" id="flexRadioDefault1" @change="getSizeList(suggestion.gender)">
                      <label class="form-check-label" for="flexRadioDefault1">
                        Kadın
                      </label>
                    </div>
                    <div class="form-check">
                      <input class="form-check-input" v-model="suggestion.gender" :value="'MALE'" type="radio"
                             name="flexRadioDefault" id="flexRadioDefault2" checked @change="getSizeList(suggestion.gender)">
                      <label class="form-check-label" for="flexRadioDefault2">
                        Erkek
                      </label>
                    </div>
                  </div>
                </div>
                <div class="form-row tm-search-form-row">
                  <div class="form-group tm-form-group tm-form-group-pad tm-form-group-1">
                    <button  class="btn btn-primary tm-btn tm-btn-search text-uppercase"
                             @click="suggest" :disabled="this.suggestion.height === '' || this.suggestion.weight === ''">Öner
                    </button>
                  </div>
                  <div class="form-group tm-form-group tm-form-group-pad tm-form-group-2" v-if="showAlert">
                    <div class="alert alert-primary" role="alert">
                      Önerilen Beden {{suggestionSize}}
                    </div>
                  </div>
                </div>
              </div>

            </div> <!-- row -->
            <div class="tm-banner-overlay"></div>
          </div>  <!-- .container -->
        </div>     <!-- .tm-container-outer -->
      </section>

      <section class="p-5 tm-container-outer tm-bg-gray">
        <div class="container">
          <div class="row">
            <div class="col-xs-12 mx-auto tm-about-text-wrap text-center">
              <p class="mb-4">"Bana göre insanın görevi, gerçeğin yerini keşfetmektir. Eğer bunu yapamıyorsa en azından mümkün olan en iyi, ve aksinin ispatı en zor olan doktrini alıp, tıpkı bir sal gibi yaşam suları üstünde onunla gezinmektir."</p>
            </div>
          </div>
        </div>
      </section>

      <div class="tm-container-outer" id="tm-section-2">
        <section class="tm-slideshow-section">
          <div class="tm-slideshow">
            <img src="../assets/img/tshirt.jpeg" style="height: 700px" alt="Image">
          </div>
          <div class="tm-slideshow-description tm-bg-primary">
            <h2 class="">Kumaş Kalitesi</h2>
            <p>%100 pamuk, 1. sınıf kaliteli penyedir. Kumaş dokusu yumuşak ve esnektir.

              Tişört önceden yıkanmış olarak gelir, böylece önerilen yıkama sonrası çekme yapma olasılığı çok düşüktür.

              Kumaş üretiminde kullanılan boyalar, sertifikalı ve güvenlidir; insan sağlığına zarar vermez.</p>
          </div>
        </section>
        <section class="clearfix tm-slideshow-section tm-slideshow-section-reverse">

          <div class="tm-right tm-slideshow tm-slideshow-highlight">
            <img src="../assets/img/tshirt3.jpeg" style="height: 700px" alt="Image">
          </div>

          <div class="tm-slideshow-description tm-slideshow-description-left tm-bg-highlight">
            <h2 class="">Baskı Kalitesi</h2>
            <p>Emprime / Serigrafi tekniğini kullanıyoruz. Bu, hava alan bir baskı türüdür. Dokunduğunuzda plastik değil, çoğunlukla yumuşak bir his verir, çünkü kumaşla tamamen bütünleşiktir. Yeni nesil dijital baskıların dezavantajlarını içermez.

              Baskılarımız sonsuza kadar solmaz diye bir iddiamız yok, ama çoğu baskılı tişörtten çok daha uzun ömürlü olacağına emin olabilirsin.

              Kullanılan boyalar tamamen sertifikalı ve sağlıklıdır.</p>
          </div>

        </section>
        <div class="tm-container-outer" id="tm-section-3">
          <section class="tm-slideshow-section">
            <div class="tm-slideshow">
              <img src="../assets/img/tshirt2.png" style="height: 700px" alt="Image">
            </div>
            <div class="tm-slideshow-description tm-bg-custom">
              <h2 class="">Ölçü Tablosu ({{genderLabel}})</h2>
              <table class="table table-striped">
                <thead>
                <tr>
                  <th>Beden</th>
                  <th>Boy</th>
                  <th>Kilo</th>
                </tr>
                </thead>
                <tbody>
                <tr v-for="(data,i) in sizeList" :key="i">
                  <td>{{data.size}}</td>
                  <td>{{data.bodyHeightMin}} - {{data.bodyHeightMax}}</td>
                  <td>{{data.bodyWeightMin}} - {{data.bodyWeightMax}}</td>
                </tr>
                </tbody>
              </table>
            </div>
          </section>

        </div>

      </div>
      <footer class="tm-container-outer" style="margin-top: 10px">
        <p class="mb-0">Copyright © <span class="tm-current-year">2021</span> taneracis.com</p>
      </footer>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'Dashboard',
  props: {
    msg: String
  },
  data() {
    return {
      sizeList: [],
      suggestionSize: '',
      showAlert: false,
      disabledSuggestionButton: true,
      suggestion: {
        height: 150,
        weight: 50,
        gender: ''
      },
      genderLabel: ''
    }
  },
  methods: {
   suggest() {
    axios.post('http://localhost:5001/kaft/', this.suggestion).then(res => {
      this.genderLabel = res.data.gender === 'MALE' ? 'Erkek': 'Kadın';
      this.showAlert = true;
      this.suggestionSize = res.data.sizeSuggestion;
    })
   },
    getSizeList(gender) {
     this.sizeList = [];
      this.genderLabel = gender === 'MALE' ? 'Erkek': 'Kadın';
      axios.get('http://localhost:5001/kaft/sizeList/gender/' + gender).then(res => {
       this.sizeList = res.data;
     });
    }
  },
  mounted() {
    if (this.suggestion.gender === "") {this.suggestion.gender = 'MALE';this.genderLabel = 'ERKEK';}
    this.getSizeList('MALE');
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "https://fonts.googleapis.com/css?family=Open+Sans:300,400,600,700";
@import "../assets/font-awesome-4.7.0/css/font-awesome.min.css";
@import "../assets/css/bootstrap.min.css";
@import "../assets/css/datepicker.css";
@import "../assets/slick/slick.css";
@import "../assets/slick/slick-theme.css";
@import "../assets/css/templatemo-style.css";
@import "https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js";
@import "https://oss.maxcdn.com/respond/1.4.2/respond.min.js";

</style>
