<template>
    <div class="item">
       <div class="temp">{{unixToHumanDate(current.dt)}}</div> 
       <div class="date">{{simplifyTemp(current.temp)}}°C</div>
       <div class="icon">
           <img                    
                v-if="current.weather?.[0].icon"
                :src="'http://openweathermap.org/img/wn/'+current.weather?.[0].icon+'@2x.png'" alt="Ikona pogody">

       </div>
    </div>
    <table border="1">   
        <tr>
            <th>DATE</th>
            <td>{{unixToHumanDate(current.dt)}}</td>
        </tr>
        <tr>
            <th>TEMP</th>
            <td>{{simplifyTemp(current.temp)}}C</td>
        </tr>
        <tr>
            <th>ICON</th>
            <td>
                <img                    
                v-if="current.weather?.[0].icon"
                :src="'http://openweathermap.org/img/wn/'+current.weather?.[0].icon+'@2x.png'" alt="Ikona pogody">
            </td>           
        </tr>                          
    </table>
 
</template>    

<script>
export default {
    props: {
      current: Object  
    },
    methods: {
      unixToHumanDate( unixDate ){
        const dt = new Date(unixDate * 1000)
        return dt.toLocaleDateString()
        },
      simplifyTemp( temp ){
        if(typeof temp == "object") {
        return temp.min + '-' + temp.max;
         }
        else{
            return temp
        }
      }
    }
    

}
</script>

<style lang="scss">
 .iten {
     border:2px dashed red;
     width:fit-content;
     box-shadow:0 0 7px #008;
     color:#fff;
     background: linear-gradient(#767, #444);
     border-radius: 5px;
     padding: .5em;
     font-weight: bold;
    .icon{
        border-radius: 5px;
        background: rgba(255, 255, 255, 0.283);
        img{
            width: 100px;
            height: 100px;
     }
 }
.temp{
    margin:.5em;

  }
 }

 


</style>