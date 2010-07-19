!SLIDE

abstraction thru extraction 

!SLIDE

request extractors

!SLIDE
<div class="hc"><span class="comment">// the ghost in the compiler</span>
def unapply(x: <strong>X</strong>): (<strong>Y</strong>, HttpServletRequest)    
</div>
!SLIDE
<div class="hc"><span class="ex">GET</span>(_), <span class="ex">POST</span>(_), <span class="ex">PUT</span>(_), <span class="ex">DELETE</span>(_), <span class="ex">HEAD</span>(_)
</div>
!SLIDE
<div class="hc"><span class="ex">Path</span>(<strong>"/hello"</strong>, _)
</div>
!SLIDE
<div class="hc">Path(<span class="ex">Seg</span>(<strong>"have" :: "a" :: what :: when :: Nil</strong>), _)
</div>
!SLIDE
<div class="hc"><span class="ex">Params</span>(<strong>params</strong>, _) <span class="comment">// Map[String, Seq[String]] </span>
</div>
!SLIDE
<div class="hc"><span class="ex">InStream</span>(<strong>in</strong>, _)
</div>
!SLIDE
<div class="hc"><span class="ex">Reader</span>(<strong>r</strong>, _)
</div>
!SLIDE
<div class="hc"><span class="ex">BasicAuth</span>(<strong>creds</strong>, _)
</div>