# Weather-App
This is Weather App developed using HTML , CSS , JAVASCRIPT

<html>
<head>
<style>
*{
   font-family:"Poppins" , sans-serif;
   box-sizing:border-box;
}
body{
    

}
#card{
  width:90%;
  max-width:470px;
  background:linear-gradient(135deg,#329da8,#3279a8);
  color:#fff;
  margin:100px auto 0;
  border-radius :20px;
  padding:40px 35px;
  text-align:center;
}
#srch{
width:100%;
display:flex;
align-items:center;
justify-content:space-between;
}
#srch input{
    background:#ebfffc;
    color:#555;
    padding:10px 25px;
    height:60px;
    border-radius:10px;
    flex:1;
    margin-right:16px;
    font-size:18px;
}
#srch button{
     background:#ebfffc;
     border:0;
     border-radius:20px;
     width:60px;
     height:60px; 
}
#weather h1{
 font-size:80px;
 font-weight:500;
}

#weather h2{
 font-size:45px;
 font-weight:500;
 margin-top:-10px;
}
.img1{
  height:15px;
  width:10px;
}
.img2{
  height:200px;
  width:200px;
}
.img3{
 height:50px;
 width:50px;
}
.img4{
 height:50px;
 width:50px;
}
#d{
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:0 20px;
  margin-top:50px;
}
.col1{
  display:flex;
  align-items:center;
  text-align:left;
}
.humid,.wind{
   font-size:28px;
   margin-top:-6px;
}

</style>
</head>
<body>
<div id="card">
 <div id="srch">
 <input type="text" placeholder="Enter the city" >
 <button><img src="C:\Users\NARAYANA\Downloads\search-interface-symbol.png" class="img1"></button>
</div>
<div id="weather">
  <img src="file:///C:/Users/NARAYANA/Desktop/HTML/cloudy-day.png" class="img2">
  <h1 class="temp">22°C</h1>
  <h2 class="city">NewYork</h2>
  <div id="d">
     <div class="col1">
       <img src="C:\Users\NARAYANA\Downloads\humidity.png"class="img3">
       <div>
       <p class="humid">50%</p>
       <p>Humidity</p>
       </div>
      </div>
       <div class="col1">
       <img src="C:\Users\NARAYANA\Downloads\wind.png" class="img4">
       <div>
       <p class="wind">50km/h</p>
       <p>WindSpeed</p>
       </div>
      </div>
</div>
</div>
<script>
const k = "e1ee843f6d73650c01736df92f80ac60";
const u = "https://api.openweathermap.org/data/2.5/weather?units=metric&q=";
const searchBox=document.querySelector("#srch input");
const searchBtn=document.querySelector("#srch button");
const icon = document.querySelector(".img2");
async function check(city){
  const r = await fetch(u +city+`&appid=${k}`);
  var d = await r.json();
   console.log(d);
   document.querySelector(".city").innerHTML = d.name;
   document.querySelector(".temp").innerHTML = Math.round(d.main.temp)+"°C";
   document.querySelector(".humid").innerHTML = d.main.humidity+"%";
   document.querySelector(".wind").innerHTML = d.wind.speed+"kmph"; 
   if(d.weather[0].main == "Clouds"){
    icon.src="file:///C:/Users/NARAYANA/Desktop/HTML/cloudy-day.png"; 
}
else if(d.weather[0].main == "Clear"){
     icon.src="file:///C:/Users/NARAYANA/Desktop/HTML/sunny.png";
}
else if(d.weather[0].main == "Rain"){
     icon.src ="file:///C:/Users/NARAYANA/Desktop/HTML/heavy-rain.png";
}

else if(d.weather[0].main == "Drizzle"){
     icon.src ="file:///C:/Users/NARAYANA/Desktop/HTML/cloudy.png";
}
else if(d.weather[0].main == "Mist"){
     icon.src ="file:///C:/Users/NARAYANA/Desktop/HTML/mist.png";
}
}

searchBtn.addEventListener("click",()=>{
check(searchBox.value);});

</script>
</body>
</html>
