abstraction thru extraction 

!SLIDE

request extractors

!SLIDE


    def unapply(something: Something): (
      Somethingelse, HttpServletRequest
    )    

!SLIDE
<div class="hc">
<span class="ex">GET</span>, <span class="ex">POST</span>, <span class="ex">PUT</span>, <span class="ex">DELETE</span>, <span class="ex">HEAD</span>
</div>
!SLIDE
<div class="hc">
  <span class="ex">Path</span>(<strong>"/hello"</strong>, req)
</div>
!SLIDE
<div class="hc">
  <span class="ex">Seg</span>(<strong>"have" :: "a" :: what :: when :: Nil</strong>, req)
</div>
!SLIDE
<div class="hc">
  <span class="ex">Params</span>(<strong>params</strong>, req) <span class="comment">// Map[String, Seq[String]] </span>
</div>
!SLIDE
<div class="hc">
  <span class="ex">InStream</span>(<strong>in</strong>, req)
</div>
!SLIDE
<div class="hc">
  <span class="ex">Reader</span>(<strong>r</strong>, req)
</div>
!SLIDE
<div class="hc">
  <span class="ex">BasicAuth</span>(<strong>creds</strong>, req)
</div>