<template>
  <div id="box">
    <div id="up" style=" text-align: center; margin-top: 150px;">
      <div id="temp" style="font-size: 50pt;"></div>
      <div id="cloud" style="font-size: 15pt;"></div>
    </div>


    <div id="down" style="margin-top: 450px; ; height: 130px; font-size: 12pt;;">

      <div id="wind" style="display: inline-block; margin-left: 275px;"></div>

      <div id="strip"><img src="./public/123.png" alt=""></div>

      <div class="day" style="margin-left: auto;margin-right: auto; width: 380px;">

        <div id="day1" style="max-width: 70px; text-align: center; display: inline-block;; padding-right: 20px;">
          <div id="number1"></div>
          <img id="img1" src="./public/clear.png" />
          <div id="degrees1"></div>
        </div>

        <div id="day2"
          style="max-width: 70px; text-align: center;display: inline-block;padding-left: 20px; padding-right: 20px;">
          <div id="number2"></div>
          <img id="img2" src="./public/cloud30.png" />
          <div id="degrees2"></div>
        </div>


        <div id="day3"
          style="max-width: 70px; text-align: center;display: inline-block;padding-left: 20px; padding-right: 20px;">
          <div id="number3"></div>
          <img id="img3" src="./public/rain.png" />
          <div id="degrees3"></div>
        </div>


        <div id="day4"
          style="max-width: 70px; text-align: center;display: inline-block;padding-left: 20px; padding-right: 20px;">
          <div id="number4"></div>
          <img id="img4" src="./public/haze.png" />
          <div id="degrees4"></div>
        </div>


        <div id="day5"
          style="max-width: 70px; text-align: center;display: inline-block;padding-left: 20px; padding-right: 20px;">
          <div id="number5"></div>
          <img id="img5" src="./public/dust.png" />
          <div id="degrees5"></div>
        </div>


        <div id="day6" style="max-width: 70px; text-align: center;display: inline-block;padding-left: 20px;">
          <div id="number6"></div>
          <img id="img6" src="" />
          <div id="degrees6"></div>
        </div>
      </div>

    </div>
  </div>
</template>



<script setup>
import axios from 'axios'
let date = new Date()
let day = date.getDate()
let [clear, clouds, rain, haze, dust] = ["https://psv4.userapi.com/c909228/u291002761/docs/d11/c1a633ba25d2/clear.png?extra=1-xF3mZ88W7e0JXK53QSeLub0zd7tjx5W-SImVgE2YATW3ZkLNRjUuhItDU3d5IvkzemGVYfqhwIvWebhdgQ8SStlE4ON-L7CEUz1Cw159kAcouzHNmkSVxRkb7wQNHivyNtk6DmukgtyqAyNYfSNLiL6A", "https://psv4.userapi.com/c909228/u291002761/docs/d4/e8b929b0bb36/cloud30.png?extra=HGdg0OlQCK4TK-oiVqlsz_rr1CfUzjFD4XQ9SL8LB1PdeOI5jXHHLdDuZ8T41WRk3_OXmK8wfx5FHvTi1DR9ibmrkhFKmrL-n1r1LiMy1UKlUrCmCEDusKdXl0mLmmX_sO3hdfGGAiqyqzmMo0GN60S-0w", "./public/rain.png", "./public/haze.png", "./public/dust.png"]
window.onload = function ge() {

  axios.get(`https://api.openweathermap.org/data/2.5/forecast?q=Kirov&units=metric&appid=dd942f90e8c353bb0a469a7db5bbb3d4`, {
  }).then((res) => {
    console.log(res)
    document.getElementById("temp").innerHTML = Math.round(res.data.list[0].main.temp) + "°";
    switch (res.data.list[0].weather[0].main) {
      case 'Clear':
        document.getElementById("cloud").innerHTML = "Ясно"
        break;
      case 'Clouds':
        document.getElementById("cloud").innerHTML = "Облачно"
        break;
      case "Rain":
        document.getElementById("cloud").innerHTML = "Дождь"
        break;
      case "Haze":
        document.getElementById("cloud").innerHTML = "Туман"
        break;
      case "Dust":
        document.getElementById("cloud").innerHTML = "Пыль"
        break;
    }
    document.getElementById("wind").innerHTML = "Ветер: " + res.data.list[0].wind.speed + "м/с"

    document.getElementById("number1").innerHTML = (res.data.list[0].dt_txt).slice(8, -8)
    switch (res.data.list[0].weather[0].main) {
      case 'Clear':
        document.querySelector("#img1").src = clear
        break;
      case 'Clouds':
        document.querySelector('#img1').src = clouds
        break;
      case "Rain":
        document.querySelector('#img1').src = rain
        break;
      case "Haze":
        document.querySelector('#img1').src = haze
        break;
      case "Dust":
        document.querySelector('#img1').src = dust
        break;
    }
    document.getElementById("degrees1").innerHTML = Math.round(res.data.list[0].main.temp) + "°"

    document.getElementById("number2").innerHTML = (res.data.list[8].dt_txt).slice(8, -8)
    switch (res.data.list[8].weather[0].main) {
      case 'Clear':
        document.querySelector("#img2").src = clear
        break;
      case 'Clouds':
        document.querySelector('#img2').src = clouds
        break;
      case "Rain":
        document.querySelector('#img2').src = rain
        break;
      case "Haze":
        document.querySelector('#img2').src = haze
        break;
      case "Dust":
        document.querySelector('#img2').src = dust
        break;
    }
    document.getElementById("degrees2").innerHTML = Math.round(res.data.list[8].main.temp) + "°"

    document.getElementById("number3").innerHTML = (res.data.list[16].dt_txt).slice(8, -8)
    switch (res.data.list[16].weather[0].main) {
      case 'Clear':
        document.querySelector("#img3").src = clear
        break;
      case 'Clouds':
        document.querySelector('#img3').src = clouds
        break;
      case "Rain":
        document.querySelector('#img3').src = rain
        break;
      case "Haze":
        document.querySelector('#img3').src = haze
        break;
      case "Dust":
        document.querySelector('#img3').src = dust
        break;
    }
    document.getElementById("degrees3").innerHTML = Math.round(res.data.list[16].main.temp) + "°"

    document.getElementById("number4").innerHTML = (res.data.list[24].dt_txt).slice(8, -8)
    switch (res.data.list[24].weather[0].main) {
      case 'Clear':
        document.querySelector("#img4").src = clear
        break;
      case 'Clouds':
        document.querySelector('#img4').src = clouds
        break;
      case "Rain":
        document.querySelector('#img4').src = rain
        break;
      case "Haze":
        document.querySelector('#img4').src = haze
        break;
      case "Dust":
        document.querySelector('#img4').src = dust
        break;
    }
    document.getElementById("degrees4").innerHTML = Math.round(res.data.list[24].main.temp) + "°"

    document.getElementById("number5").innerHTML = (res.data.list[32].dt_txt).slice(8, -8)
    switch (res.data.list[32].weather[0].main) {
      case 'Clear':
        document.querySelector("#img5").src = clear
        break;
      case 'Clouds':
        document.querySelector('#img5').src = clouds
        break;
      case "Rain":
        document.querySelector('#img5').src = rain
        break;
      case "Haze":
        document.querySelector('#img5').src = haze
        break;
      case "Dust":
        document.querySelector('#img5').src = dust
        break;
    }
    document.getElementById("degrees5").innerHTML = Math.round(res.data.list[32].main.temp) + "°"

    document.getElementById("number6").innerHTML = (res.data.list[39].dt_txt).slice(8, -8)
    switch (res.data.list[39].weather[0].main) {
      case 'Clear':
        document.querySelector("#img6").src = clear
        break;
      case 'Clouds':
        document.querySelector('#img6').src = clouds
        break;
      case "Rain":
        document.querySelector('#img6').src = rain
        break;
      case "Haze":
        document.querySelector('#img6').src = haze
        break;
      case "Dust":
        document.querySelector('#img6').src = dust
        break;
    }
    document.getElementById("degrees6").innerHTML = Math.round(res.data.list[39].main.temp) + "°"
  })
}
</script>


