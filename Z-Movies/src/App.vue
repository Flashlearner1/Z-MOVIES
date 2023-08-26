<script>


</script>


<template>


  

  <main>
    <router-view />
  </main>

  <section class="body">
    <div class="rectangle">
      <div class="left">
        <h1>It has never been easier to <br> watch free movies online.</h1>
        <p>Once you register for a free account with Plex, we’ll keep your place <br>
          from screen to screen as long as you’re signed in. No matter what <br>
          device you choose, your free movies will pick up where you left off <br> with ease.</p>
        <button><a href="">Watch Free</a></button>
      </div>
      <div class="right">
        <img src="https://www.plex.tv/wp-content/uploads/2021/09/Continue_Watching_v2-2-1024x1088.png" alt="photo" width="550px">
      </div>
    </div>
  </section>

 

  <footer>
        <div class='container'>
          <div class='box'>
            <ul class='flex'>
              <li>Terms of Use |</li>
              <li>Privacy-Policy |</li>
              <li>Blog |</li>
              <li>FAQ |</li>
              <li>Watch List</li>
            </ul>


            
            
          </div>
          <div className='box'>
            <h3>Follow Us</h3>
            <i className='fab fa-facebook-f'></i>
            <i className='fab fa-twitter'></i>
            <i className='fab fa-github'></i>
            <i className='fab fa-instagram'></i>
          </div>
          <div className='box'>
            <h3>F-Movies App</h3>
            <div className='img-flexSB'>
              <div class="imag">
                <img src='https://img.icons8.com/color/48/000000/apple-app-store--v3.png' />
                <span>App Store</span>
              </div>
              
             

             <div class="imag">
              <img src='https://img.icons8.com/fluency/48/000000/google-play.png' />
              <span>Google Play Store</span>
             </div> 
            </div>
          </div>

        </div>
        <div class="copyright">
            <h5>© 2023 F-Movies. All Right Reserved Language: <span>English(US)</span></h5>
          </div>
    </footer>
</template>





<style>




footer {
  background-color: #191919;
  margin-top: 100px;
  padding: 50px 0;
  color: #fff;
}

footer .container {
  display: flex;
  justify-content: space-between;
}

footer ul {
  text-decoration: none;
  list-style-type: none;
  display: flex;
  margin: 80px 0px 0px 20px;

}
footer ul li {
  line-height: 25px;
  margin-left: 20px;
}
footer i {
  width: 40px;
  height: 40px;
  line-height: 40px !important;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.1);
  text-align: center;
  margin-right: 20px;
  margin-top: 50px;
}
footer i:hover{
  transition: .4s;
  background: red;
  transform: translateY(10px);
}
footer .img {
  margin-top: 40px;
}
footer .img:hover{
  transform: scaleY(-10px);
}

.flex li:hover{
  cursor: pointer;
  color: red;
  transition: .4s;
  transform: translateY(10px);
}
.box{
  margin-right: 100px;
}
.box h3:hover{
  cursor: pointer;
  transition: .4s;
  color: red;
}
.copyright{
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 100px;
}
.copyright span:hover{
  transition: .4s;
  color: rgb(212, 38, 38);
  cursor: pointer;
}

.box .img-flexSB {
  margin-top: 40px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.imag{
  margin-left: 10px;
}
.imag span{
  display: block;
}
.rectangle{
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 200px;
}
.left{
  margin-left: 80px;
  margin-bottom: 50px;
}
.left h1{
  font-weight: bolder;
  font-size: 40px;
}
.left p{
  font-size: 18px;
  margin-top: 20px;
}
.left button{
  padding: 10px 30px 10px 30px;
  border-radius: 50px;
  background: black;
  margin-top: 20px;
}
.left button:hover{
  transform: translateY(5px);
  background: red;
  transition: .4s;
}
.left button a{
  color: white;
  text-decoration: none;
  font-weight: 1000;
}
.right{
  margin-right: 80px;
}

</style>