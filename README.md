
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ASSIGNMENT</title>
</head>
<style>
    
        
    .container{
        img left: 50mm;
        position : relative;
        
    }
    .text-block{
        position: absolute;
        

    }
    body{
        background-color: aqua;
        background-image: url("bg12.webp");
        background-size: cover;
    }
    img{
        float: left;
        
    }
    .rhony{
        margin-left: 25cm;
    }
    #Search-form{
        display : flex;
        justify-content: center;
        align-items: center;

    }
    #Search-button{
        column-rule-color: blanchedalmond;
        text-transform: uppercase;
        text-decoration: solid;
        background-color: white;
        border-radius: 10px;
        margin-left: 10px;
        padding: 11px;
        border: 2px solid;
        display: inline-block;
        transition: all 0.4 ease 0s;
        size: 10cm;
    }
    #Search-button:hover{
        color: bisque;
        background-color: aqua;
        transition: all 0.4 ease 0s;
    }
    #Search-input{
        width: 260px;
        font-size: 20px;
        margin:8px 0;
        padding: 8px 0;
        border-bottom: 3px solid;
        color: rgb(7, 20, 32);
        outline: rgb(57, 49, 36);
    }
    input{
        border: none;
    }


</style>
<body>
    
    <div class="container">
        <div class="icon">---</div>
        <div class="temp">-°C</div>
        <div class="summary">----</div>
        <div class="location"></div>
      </div>
    <img src="op9.jpeg">
    <div class="text-block">
        <form id = "search-form">
            <input type = "search"
            placeholder="Enter City Name"
            id="Search-input"
            required
            autocomplete="off"/>
            <br>
        </br>
        <button id="Search-button">Search</button>
        </form>
    </div>

</div>
<div class="smart">
<img src="op2.webp" alt="background" sizes="500" width="500" height="900">

</div>
<div class="rhony">
<img src="op3.jpeg" width="400px" height="900">
</div>
<script>
 let lon;
let lat;
let temperature = document.querySelector(".temp");
let summary = document.querySelector(".summary");
let loc = document.querySelector(".location");
const kelvin = 273;
  
window.addEventListener("load", () => {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition((position) => {
      console.log(position);
      lon = position.coords.longitude;
      lat = position.coords.latitude;
  
      // API ID
      const api = "6d055e39ee237af35ca066f35474e9df";
  
      // API URL
      const base =
`http://api.openweathermap.org/data/2.5/weather?lat=${lat}&` +
`lon=${lon}&appid=6d055e39ee237af35ca066f35474e9df`;
  
      // Calling the API
      fetch(base)
        .then((response) => {
          return response.json();
        })
        .then((data) => {
          console.log(data);
          temperature.textContent = 
              Math.floor(data.main.temp - kelvin) + "°C";
          summary.textContent = data.weather[0].description;
          loc.textContent = data.name + "," + data.sys.country;
        });
    });
  }
});
</script>
</body>
</html>
