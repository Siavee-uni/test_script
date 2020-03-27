´´´
<?php
  $timenow = date('H:m:s');
 
  $timefrom = $post->timefrom;
  $timeto = $post->timeto;
  
?>

@forelse($posts as $post)

<a><img style="width:100%" onclick="timer({{ $post->id }}, '{{ $timefrom }}', '{{ $timeto }}', '{{ $timenow }}')" id="{{$post->id}}"class="z-depth-1 img-thumbnail" src="/uploads/{{$post->image}}" alt="video" data-toggle="modal" data-target="#modal-{{$post->id}}"></a>

@endforelse

<script>  

 function msToTime(s) {
         if (s > 0) {
         var ms = s % 1000;
         s = (s - ms) / 1000;
         var secs = s % 60;
         s = (s - secs) / 60;
         var mins = s % 60;
         var hrs = (s - mins) / 60;

         return hrs + ' Stunde und ' + mins + ' minuten';
         }
        else
         {
          return "wait"
         }
     }
     
      

  function timer (postid, timefrom, timeto, timenow) {
      if (timefrom == "00:00:00") or (timeto == "00:00:00"){
        alert("test");
        }

     
      else{
      let from = new Date(Date.parse("2020/3/27 " + timefrom));
      let to = new Date(Date.parse("2020/3/27 " + timeto));
      let now = new Date(Date.parse("2020/3/27 " + timenow));
      
      let timediffinmilisec = to - now - 3600000 ;
      }  
      console.log(now);
        if (timefrom === "00:00:00") or (timeto === "00:00:00") 
              {alert('test');}
              elseif (from <= now && now <= to) {
              var close = function() {
                 $("#modal-" + postid).modal("hide");
              }
              setTimeout(close, timediffinmilisec);
              
              alert("Stream schließ sich in " + msToTime(timediffinmilisec))
              } 
              else 
              {
              document.getElementById(postid).removeAttribute("data-toggle");
              alert("Stream startet um " + timefrom);
           }
      };
</script>
´´´

Funktioniereder code 
´´´
<script>  
function msToTime(s) {
         if (s > 0) {
         var ms = s % 1000;
         s = (s - ms) / 1000;
         var secs = s % 60;
         s = (s - secs) / 60;
         var mins = s % 60;
         var hrs = (s - mins) / 60;

         return hrs + ' Stunde und ' + mins + ' minuten';
         }
        else
         {
          return "wait"
         }
     }
      
      

  function timer (postid, timefrom, timeto, timenow) {
      let from = new Date(Date.parse("2020/3/27 " + timefrom));
      let to = new Date(Date.parse("2020/3/27 " + timeto));
      let now = new Date(Date.parse("2020/3/27 " + timenow));
      
      let timediffinmilisec = to - now - 3600000 ;
      }  
      console.log(now);
      
              if (from <= now && now <= to) {
              var close = function() {
                 $("#modal-" + postid).modal("hide");
              }
              setTimeout(close, timediffinmilisec);
              
              alert("Stream schließ sich in " + msToTime(timediffinmilisec))
              } 
              else 
              {
              document.getElementById(postid).removeAttribute("data-toggle");
              alert("Stream startet um " + timefrom);
           }
      };
</script>
´´´
