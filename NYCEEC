<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>

    <link rel="stylesheet" href="https://code.jquery.com/ui/1.11.4/themes/smoothness/jquery-ui.css">  
    
    <script src="https://code.jquery.com/jquery-1.12.3.min.js"></script>
    
    <script src="https://code.jquery.com/ui/1.11.4/jquery-ui.js"></script>
    
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.0/jquery.min.js"></script>
    
    <link rel="stylesheet" href="https://cartodb-libs.global.ssl.fastly.net/cartodb.js/v3/3.15/themes/css/cartodb.css" />
    
    <script src="https://cartodb-libs.global.ssl.fastly.net/cartodb.js/v3/3.15/cartodb.js"></script>
    
    <style>
        
        html, body {
            height: 100%;
            margin: 0;
            padding: 0;
            width: 100%;
/*            font-family: sans-serif;*/
        }
        
        #map {
            height: 100%;
            width: 100%;
        }
        
        .sidepanel {
            background-color: #58595B;
            color: white;
            position: absolute;
            top: 0;
/*            right: 0;*/
            bottom: 0;
            width: 25%;
            height: 100%;
            overflow: auto;
            border-right: solid black 1px;
        }
        .wrapper {
            display: block;
            padding: 4px 30px 0 30px; 
        }

        div.cartodb-zoom {
            margin: 20px 0 0 26%;
        }
        
    </style>
    
          <script>
        var dataLayer;
    $(document).ready(function () {
        cartodb.createVis('map', 'https://thenewschool.carto.com/u/whalt973/api/v2/viz/e4697502-1a14-11e7-92eb-0e05a8b3e3d7/viz.json',
                         {
            center_lat: 40.7459192,
            center_lon: -73.991922,
            zoom: 13,
        
        })
        .done(function (vis, layers) {
            dataLayer = layers[1].getSubLayer(0);
        });
        
        function updateSql() {
              var sqltype = "SELECT * FROM nyceec_map";
              var whereConditions = [];
              if ($('#co-gen').is(':checked')) {
                  whereConditions.push("type LIKE '%cogeneration%'");
              }
              if ($('#en-eff').is(':checked')) {
                  whereConditions.push("type LIKE '%energy efficiency%'");
              }
            
            if ($('#en-eff and co-gen').is(':checked')) {
                  whereConditions.push("type LIKE '%energy efficiency & cogeneration%'");
            }
            
            if ($('#demand response').is(':checked')) {
                  whereConditions.push("type LIKE '%demand response%'");
            }
             
            if ($('#fuel conversion').is(':checked')) {
                  whereConditions.push("type LIKE '%fuel conversion%'");
            }
            
            if ($('#en-eff and fc').is(':checked')) {
                  whereConditions.push("type LIKE '%energy efficiency & fuel conversion%'");
            }
            
              if (whereConditions.length > 0) {
                  sqltype+= ' WHERE ' + whereConditions.join(' OR ');
              }
            
              console.log(sqltype);
              dataLayer.setSQL(sqltype);
           }
        
            $('#co-gen').change(function (){
              updateSql();
          });
        
            $('#en-eff').change(function (){
              updateSql();
          });
        
          $('#en-eff and co-gen').change(function (){
              updateSql();
              
          });
        
          $('#demand response').change(function (){
              updateSql();
              
          });
        
          $('#fuel conversion').change(function (){
              updateSql();
              
          });
        
          $('#en-eff and fc').change(function (){
              updateSql();
          })
    });
   </script>
    </head>
    
    <body>
        
    <div id="map"></div>
        
    <!--  sidebox-->
        <div id="side-box" class="sidepanel" style="display:block;">
        <div class="wrapper">
        <div id="title-text">
            <h1 style="color: #7DBE31;">NYCEEC Projects</h1>
            </div>
            
            <div id="project-type">
            <p>Click different project types</p>
            <div>
              
                <input type="checkbox" id="cogen">
                     <label class="checkbox-label" for="co-gen">Cogeneration</label>
                <br>
                <input type="checkbox" id="en-eff">
                     <label class="checkbox-label" for="en-eff">Energy Efficiency</label>
                <br>                
                <input type="checkbox" id="en-eff and co-gen">
                     <label class="checkbox-label" for="energy efficiency and Cogeneration">Energy Efficiency and Cogeneration</label>
                <br>    
                 <input type="checkbox" id="demand response">
                     <label class="checkbox-label" for="demand response">Demand Response</label>
                 <br>  
                 <input type="checkbox" id="fuel conversion">
                     <label class="checkbox-label" for="fuel conversion">Fuel Conversion</label>
                <br>  
                
                 <input type="checkbox" id="en-eff and fc">
                     <label class="checkbox-label" for="energy efficiency & fuel conversion">Energy Efficiency and Fuel Conversion</label>
               
            </div>
            
            </div>
            
            
            </div>
        </div>
        
        
      
    
    </body>
</html>
