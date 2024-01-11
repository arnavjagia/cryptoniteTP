It is evident on inspecting the `index.php` file that the red and blue bg colors are attributed to `GET` and `POST` requests respectively (as can be seen below).  
Now,  
  the title of the challenge is interesting as it is a wordplay of `GET` and `HEAD` which are http request types.  
So,  
  using burpsuite to send a `HEAD` request, we obtain the flag.  

File-> index.php

```html
<div class="container">
  <div class="row">
    <div class="col-md-6">
      <div class="panel panel-primary" style="margin-top:50px">
        <div class="panel-heading">
          <h3 class="panel-title" style="color:red">Red</h3>
        </div>
        <div class="panel-body">
          <form action="index.php" method="GET">
            <input type="submit" value="Choose Red"/>
          </form>
        </div>
      </div>
    </div>
    <div class="col-md-6">
      <div class="panel panel-primary" style="margin-top:50px">
        <div class="panel-heading">
          <h3 class="panel-title" style="color:blue">Blue</h3>
        </div>
        <div class="panel-body">
          <form action="index.php" method="POST">
            <input type="submit" value="Choose Blue"/>
          </form>
        </div>
      </div>
    </div>
  </div>
</div>
```

![Burpsuite](https://github.com/arnavjagia/cryptoniteTP/assets/89345926/3f70dbaf-6c26-4ec2-b061-1ea3c625adb2)
