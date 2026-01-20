<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE html>
<html b:css='false' b:defaultwidgetversion='2' b:layoutsVersion='3' b:responsive='true' b:templateUrl='indie' b:templateVersion='1.3.0' expr:dir='data:blog.languageDirection' expr:lang='data:blog.locale' xmlns='http://www.w3.org/1999/xhtml' xmlns:b='http://www.google.com/2005/gml/b' xmlns:data='http://www.google.com/2005/gml/data' xmlns:expr='http://www.google.com/2005/gml/expr'>
<head>
    <meta charset='UTF-8'/>
    <meta content='width=device-width, initial-scale=1' name='viewport'/>
    <title><data:blog.pageTitle/></title>
    <b:include data='blog' name='all-head-content'/>

    <b:skin><![CDATA[
    /* 
    ========================================================
       ARTIST PORTFOLIO THEME CSS
    ======================================================== 
    */
    * { margin: 0; padding: 0; box-sizing: border-box; }
        
    :root {
        --bg-primary: #ffffff;
        --bg-secondary: #fafafa;
        --text-primary: #1a1a1a;
        --text-secondary: #666666;
        --border: #e5e5e5;
        --accent: #1a1a1a;
    }
    
    [data-theme="dark"] {
        --bg-primary: #0a0a0a;
        --bg-secondary: #1a1a1a;
        --text-primary: #f5f5f5;
        --text-secondary: #999999;
        --border: #2a2a2a;
        --accent: #f5f5f5;
    }
    
    body {
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
        background: var(--bg-primary);
        color: var(--text-primary);
        line-height: 1.6;
        transition: background 0.3s, color 0.3s;
    }

    /* Navigation */
    nav {
        position: fixed; top: 0; width: 100%;
        background: rgba(255, 255, 255, 0.9);
        backdrop-filter: blur(10px);
        border-bottom: 1px solid var(--border);
        padding: 1rem 2rem;
        display: flex; justify-content: space-between; align-items: center;
        z-index: 1000; transition: transform 0.3s;
    }
    [data-theme="dark"] nav { background: rgba(10, 10, 10, 0.9); }
    
    .logo { font-size: 1.2rem; font-weight: 600; letter-spacing: -0.5px; color: var(--text-primary); text-decoration: none; }
    
    .nav-links { display: flex; gap: 2rem; align-items: center; }
    .nav-links a { color: var(--text-primary); text-decoration: none; font-size: 0.9rem; transition: opacity 0.2s; }
    .nav-links a:hover { opacity: 0.6; }
    
    .theme-toggle { background: none; border: 1px solid var(--border); color: var(--text-primary); padding: 0.5rem 1rem; border-radius: 20px; cursor: pointer; font-size: 0.9rem; transition: all 0.2s; }
    .theme-toggle:hover { background: var(--bg-secondary); }
    
    .mobile-menu { display: none; background: none; border: none; color: var(--text-primary); font-size: 1.5rem; cursor: pointer; }

    /* Hero Slideshow */
    .hero { margin-top: 60px; height: 70vh; max-width: 100%; margin-left: auto; margin-right: auto; position: relative; overflow: hidden; }
    .hero-slideshow { position: relative; width: 100%; height: 100%; }
    .hero-slide { position: absolute; top: 0; left: 0; width: 100%; height: 100%; opacity: 0; transition: opacity 1s ease-in-out; }
    .hero-slide.active { opacity: 1; }
    .hero-slide img { width: 100%; height: 100%; object-fit: cover; }
    .hero-content { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); z-index: 2; text-align: center; color: white; text-shadow: 0 2px 10px rgba(0,0,0,0.5); width: 100%; }
    .hero h1 { font-size: clamp(2.5rem, 8vw, 5rem); font-weight: 300; letter-spacing: -2px; margin-bottom: 1rem; }
    .hero p { font-size: clamp(1rem, 2vw, 1.5rem); font-weight: 300; }
    .hero-nav { position: absolute; bottom: 2rem; left: 50%; transform: translateX(-50%); display: flex; gap: 0.5rem; z-index: 3; }
    .hero-dot { width: 10px; height: 10px; border-radius: 50%; background: rgba(255, 255, 255, 0.5); cursor: pointer; transition: all 0.3s; }
    .hero-dot.active { background: white; width: 30px; border-radius: 5px; }
    .hero-arrow { position: absolute; top: 50%; transform: translateY(-50%); background: rgba(255, 255, 255, 0.3); border: none; color: white; width: 50px; height: 50px; font-size: 1.5rem; cursor: pointer; z-index: 3; transition: background 0.3s; backdrop-filter: blur(5px); }
    .hero-arrow:hover { background: rgba(255, 255, 255, 0.5); }
    .hero-arrow.prev { left: 1rem; }
    .hero-arrow.next { right: 1rem; }

    /* Section Styles */
    section { padding: 4rem 2rem; max-width: 1400px; margin: 0 auto; }
    h2 { font-size: clamp(2rem, 4vw, 3rem); font-weight: 300; letter-spacing: -1px; margin-bottom: 3rem; text-align: center; }

    /* Gallery Grid */
    .gallery-controls { display: flex; justify-content: center; gap: 1rem; margin-bottom: 2rem; }
    .grid-toggle { padding: 0.5rem 1rem; border: 1px solid var(--border); background: none; color: var(--text-primary); cursor: pointer; transition: all 0.2s; border-radius: 4px; }
    .grid-toggle.active { background: var(--accent); color: var(--bg-primary); border-color: var(--accent); }
    .gallery-grid { display: grid; gap: 2rem; transition: all 0.3s; grid-template-columns: repeat(3, 1fr); }
    .gallery-grid.grid-2 { grid-template-columns: repeat(2, 1fr); }
    .gallery-grid.grid-3 { grid-template-columns: repeat(3, 1fr); }
    .gallery-grid.grid-4 { grid-template-columns: repeat(4, 1fr); }

    .gallery-item { position: relative; overflow: hidden; cursor: pointer; aspect-ratio: 4/5; background: var(--bg-secondary); }
    .gallery-item a { display: block; width: 100%; height: 100%; }
    .gallery-item img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.5s; }
    .gallery-item:hover img { transform: scale(1.05); }
    .gallery-item-info { position: absolute; bottom: 0; left: 0; right: 0; padding: 1.5rem; background: linear-gradient(transparent, rgba(0,0,0,0.8)); color: white; transform: translateY(100%); transition: transform 0.3s; }
    .gallery-item:hover .gallery-item-info { transform: translateY(0); }
    .gallery-item-info h3 { font-size: 1.2rem; font-weight: 400; margin-bottom: 0.5rem; }
    .gallery-item-info p { font-size: 0.9rem; opacity: 0.9; }

    /* Media & Text */
    .text-container { max-width: 700px; margin: 0 auto 3rem auto; padding: 0 1rem; }
    .lead-text { font-size: 1.25rem; font-weight: 300; line-height: 1.6; text-align: center; color: var(--text-primary); margin-bottom: 2rem; }
    .process-text { font-size: 1rem; line-height: 1.8; color: var(--text-secondary); text-align: left; margin-bottom: 1.5rem; }
    .text-divider { width: 50px; height: 1px; background: var(--accent); margin: 2rem auto; opacity: 0.3; }
    .media-embed { max-width: 900px; margin: 0 auto; padding: 2rem 0; }
    .video-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; margin-bottom: 2rem; }
    .video-container iframe { position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: none; }
    .video-caption { text-align: center; color: var(--text-secondary); margin-top: 1rem; font-size: 0.9rem; }

    /* Social Embeds */
    .social-embed { max-width: 600px; margin: 2rem auto; padding: 2rem; border: 1px solid var(--border); border-radius: 8px; background: var(--bg-secondary); }
    .social-embed-header { display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem; padding-bottom: 1rem; border-bottom: 1px solid var(--border); }
    .social-platform-icon { width: 28px; height: 28px; display: flex; align-items: center; justify-content: center; color: var(--text-primary); }
    .social-platform-icon svg { width: 100%; height: 100%; fill: currentColor; }
    .social-embed-content img { width: 100%; border-radius: 4px; margin-bottom: 1rem; }
    .social-embed-text { color: var(--text-secondary); line-height: 1.6; margin-bottom: 1rem; }
    .social-embed-link { display: inline-block; color: var(--accent); text-decoration: none; font-size: 0.9rem; }
    
    /* About */
    .about-content { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: start; }
    .about-image { width: 100%; aspect-ratio: 3/4; object-fit: cover; border-radius: 4px; }
    .about-text h3 { font-size: 1.5rem; font-weight: 400; margin-bottom: 1rem; }
    .about-text p { color: var(--text-secondary); margin-bottom: 1.5rem; line-height: 1.8; }
    .about-details { display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; margin-top: 2rem; }
    .about-details h4 { font-size: 0.9rem; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 1rem; color: var(--text-secondary); }
    .about-details ul { list-style: none; }
    .about-details li { margin-bottom: 0.5rem; color: var(--text-secondary); }

    /* Timeline */
    .timeline { max-width: 800px; margin: 0 auto; }
    .timeline-item { padding: 2rem 0; border-bottom: 1px solid var(--border); }
    .timeline-item:last-child { border-bottom: none; }
    .timeline-date { font-size: 0.9rem; color: var(--text-secondary); margin-bottom: 0.5rem; }
    .timeline-item h3 { font-size: 1.5rem; font-weight: 400; margin-bottom: 0.5rem; }
    .timeline-item p { color: var(--text-secondary); line-height: 1.8; }
    .timeline-location { font-style: italic; margin-top: 0.5rem; color: var(--text-secondary); }

    /* Contact */
    .contact-content { max-width: 600px; margin: 0 auto; text-align: center; }
    .social-links { display: flex; gap: 2rem; justify-content: center; align-items: center; margin-top: 2rem; }
    .social-links a { display: flex; align-items: center; justify-content: center; width: 24px; height: 24px; color: var(--text-primary); transition: all 0.3s ease; }
    .social-links a svg { width: 100%; height: 100%; fill: currentColor; }
    .social-links a:hover { transform: translateY(-3px) scale(1.1); opacity: 0.7; }
    .contact-email { display: inline-block; margin-top: 2rem; font-size: 1.2rem; color: var(--text-primary); text-decoration: none; border-bottom: 1px solid var(--text-primary); transition: opacity 0.2s; }
    .contact-email:hover { opacity: 0.6; }

    /* Footer */
    footer { background: var(--bg-secondary); padding: 2rem; text-align: center; color: var(--text-secondary); font-size: 0.9rem; }
    .share-btn { position: fixed; bottom: 2rem; right: 2rem; width: 50px; height: 50px; border-radius: 50%; background: var(--accent); color: var(--bg-primary); border: none; cursor: pointer; font-size: 1.2rem; box-shadow: 0 4px 12px rgba(0,0,0,0.2); transition: transform 0.2s; z-index: 999; }
    .share-btn:hover { transform: scale(1.1); }

    /* Single Post Styling */
    .post-page { max-width: 900px; margin: 100px auto 0; padding: 2rem; }
    .post-page h1 { font-size: 3rem; text-align: center; margin-bottom: 1rem; font-weight: 300; }
    .post-page .date { text-align: center; color: var(--text-secondary); margin-bottom: 3rem; display: block; }
    .post-page img { max-width: 100%; height: auto; display: block; margin: 2rem auto; }
    .post-body { font-size: 1.1rem; line-height: 1.8; color: var(--text-secondary); }

    /* Responsive */
    @media (max-width: 1100px) { .gallery-grid.grid-4 { grid-template-columns: repeat(2, 1fr); } }
    @media (max-width: 768px) {
        nav { padding: 1rem; }
        .nav-links { display: none; position: absolute; top: 100%; left: 0; right: 0; background: var(--bg-primary); border-bottom: 1px solid var(--border); flex-direction: column; padding: 1rem; gap: 1rem; }
        .nav-links.active { display: flex; }
        .mobile-menu { display: block; }
        .hero-arrow { width: 40px; height: 40px; font-size: 1.2rem; }
        .gallery-grid.grid-3 { grid-template-columns: repeat(2, 1fr); }
        .gallery-grid { gap: 1rem; }
        .about-content { grid-template-columns: 1fr; gap: 2rem; }
        .about-details { grid-template-columns: 1fr; }
        section { padding: 3rem 1rem; }
        .share-btn { bottom: 1rem; right: 1rem; }
        .social-embed { padding: 1rem; }
    }
    @media (max-width: 480px) {
        .gallery-grid.grid-2, .gallery-grid.grid-3 { grid-template-columns: repeat(2, 1fr); }
        .hero h1 { font-size: 2rem; }
    }
    ]]></b:skin>
</head>

<body>
    <!-- Navigation -->
    <nav>
        <a class='logo' expr:href='data:blog.homepageUrl'><data:blog.title/></a>
        <div class='nav-links' id='navLinks'>
            <a href='#work'>Work</a>
            <a href='#media'>Media</a>
            <a href='#about'>About</a>
            <a href='#exhibitions'>Exhibitions</a>
            <a href='#news'>News</a>
            <a href='#contact'>Contact</a>
            <button class='theme-toggle' onclick='toggleTheme()'>&#9680;</button>
        </div>
        <button class='mobile-menu' onclick='toggleMenu()'>&#9776;</button>
    </nav>

    <!-- Main Content Container -->
    <div class='main-container'>
        
        <!-- Only show One-Page Layout on Homepage -->
        <b:if cond='data:view.isHomepage'>
            
            <!-- Hero Section -->
            <b:section id='Hero-Section' maxwidgets='1' showaddelement='yes'>
              <b:widget id='HTML1' locked='false' title='Hero Slideshow' type='HTML' version='2' visible='true'>
                <b:widget-settings>
                  <b:widget-setting name='content'><![CDATA[<!-- PASTE YOUR SLIDESHOW HTML HERE IN THE WIDGET EDITOR -->
                        <div class="hero" id="home">
                            <div class="hero-slideshow">
                                <div class="hero-slide active"><img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjrcz8-8Beu6NUBCmvKFCrxW5899Yp-o4sAhQ3dJJ-HybTBPawjG-_Woik1fkvSdNbZAkQ5u_ikSbLsWcqqY8bJOyK1pevXIVKl1L49XUbhcVDoQM5o0B8prRceojGsToHj-NxziBsL7_NS1vM_uqOsqD4IaoQPbcxcj-LIexMS7QkZdpHymEJ65ft4j44/s1920/Detail%20III.jpg" alt="Art 1" /></div>
                                <div class="hero-slide"><img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjfsVyrpMc0NQw7b1lQIJP3OHJgvyW20trxBzDBKQOd7-zFB2OYpb0_Gro0LYpRrJF0OJM0cPIra5K0s1GU70xBVaU-p-2ml6CCN8N86-lB2ws0IwOJNVuiQ8k8Qmccco5LmHNpB0z65jF2egtRSqKg_DrQ-XmJyMmdJVNpzm8al7vxiMwoTRVsAEdUmgA/s1920/Detail%20II.jpg" alt="Art 2" /></div>
                                <div class="hero-slide"><img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiT_xB9aNoDdCWs3cPSStkKxt35jMJPxqxNHljSXa9CPMkBfzqeBM5LYIM3s9J3fFiohZvSoyVucr1k3NRe38Hba9Vzb4HSPtDKn78hwiFydogVZpvkL8RWHihRN2lH9vjpq_sRzBL0dSmcS6PEn70f9Sq5B8vlzlib2Gy5mbLZiGNaF95jU8SqcdN3WLU/s1920/Rozp%C3%ADnavost%20temnoty%20III,%202021,%20olej%20na%20pl%C3%A1tn%C4%9B,%20170%20x%20120%20cm.jpg" alt="Art 3" /></div>
                            </div>
                            <button class="hero-arrow prev" onclick="changeSlide(-1)">‹</button>
                            <button class="hero-arrow next" onclick="changeSlide(1)">›</button>
                            <div class="hero-content">
                                <h1>Markéta Pragerová</h1>
                                <p>Contemporary Artist &amp; Designer</p>
                            </div>
                            <div class="hero-nav" id="heroNav"></div>
                        </div>]]></b:widget-setting>
                </b:widget-settings>
                <b:includable id='main'>
                        <data:content/>
                    </b:includable>
              </b:widget>
            </b:section>

            <!-- Gallery/Work Section (Powered by Blogger Posts) -->
            <section id='work'>
                <h2>Selected Works</h2>
                <div class='gallery-controls'>
                    <button class='grid-toggle' onclick='setGridLayout(2)'>2 Columns</button>
                    <button class='grid-toggle active' onclick='setGridLayout(3)'>3 Columns</button>
                    <button class='grid-toggle' onclick='setGridLayout(4)'>4 Columns</button>
                </div>

                <b:section id='Work-Section' showaddelement='no'>
                  <b:widget id='Blog1' locked='true' title='Blog Posts' type='Blog' version='2' visible='true'>
                    <b:widget-settings>
                      <b:widget-setting name='showDateHeader'>false</b:widget-setting>
                      <b:widget-setting name='style.textcolor'>#ffffff</b:widget-setting>
                      <b:widget-setting name='showShareButtons'>false</b:widget-setting>
                      <b:widget-setting name='showCommentLink'>true</b:widget-setting>
                      <b:widget-setting name='style.urlcolor'>#ffffff</b:widget-setting>
                      <b:widget-setting name='showAuthor'>false</b:widget-setting>
                      <b:widget-setting name='style.linkcolor'>#ffffff</b:widget-setting>
                      <b:widget-setting name='style.unittype'>TextAndImage</b:widget-setting>
                      <b:widget-setting name='style.bgcolor'>#ffffff</b:widget-setting>
                      <b:widget-setting name='timestampLabel'/>
                      <b:widget-setting name='reactionsLabel'/>
                      <b:widget-setting name='showAuthorProfile'>false</b:widget-setting>
                      <b:widget-setting name='style.layout'>1x1</b:widget-setting>
                      <b:widget-setting name='showLabels'>false</b:widget-setting>
                      <b:widget-setting name='showLocation'>true</b:widget-setting>
                      <b:widget-setting name='postLabelsLabel'/>
                      <b:widget-setting name='showTimestamp'>true</b:widget-setting>
                      <b:widget-setting name='postsPerAd'>1</b:widget-setting>
                      <b:widget-setting name='showBacklinks'>false</b:widget-setting>
                      <b:widget-setting name='style.bordercolor'>#ffffff</b:widget-setting>
                      <b:widget-setting name='showInlineAds'>false</b:widget-setting>
                      <b:widget-setting name='showReactions'>false</b:widget-setting>
                    </b:widget-settings>
                    <b:includable id='main'>
                            <div class='gallery-grid grid-3' id='galleryGrid'>
                                <b:loop values='data:posts' var='post'>
                                    <div class='gallery-item'>
                                        <a expr:href='data:post.url'>
                                            <b:if cond='data:post.featuredImage'>
                                                <img expr:alt='data:post.title' expr:src='data:post.featuredImage'/>
                                            <b:else/>
                                                <img alt='No image' src='https://via.placeholder.com/600x750?text=No+Image'/>
                                            </b:if>
                                            <div class='gallery-item-info'>
                                                <h3><data:post.title/></h3>
                                                <p><b:eval expr='snippet(data:post.body, {length: 50, links: false})'/></p>
                                            </div>
                                        </a>
                                    </div>
                                </b:loop>
                            </div>
                        </b:includable>
                    <b:includable id='aboutPostAuthor'>
  <div class='author-name'>
    <a class='g-profile' expr:href='data:post.author.profileUrl' rel='author' title='author profile'>
      <span>
        <data:post.author.name/>
      </span>
    </a>
  </div>
  <div>
    <span class='author-desc'>
      <data:post.author.aboutMe/>
    </span>
  </div>
</b:includable>
                    <b:includable id='addComments'>
  <a expr:href='data:post.commentsUrl' expr:onclick='data:post.commentsUrlOnclick'>
    <b:message name='messages.postAComment'/>
  </a>
</b:includable>
                    <b:includable id='commentAuthorAvatar'>
  <div class='avatar-image-container'>
    <img class='author-avatar' expr:src='data:comment.authorAvatarSrc' height='35' width='35'/>
  </div>
</b:includable>
                    <b:includable id='commentDeleteIcon' var='comment'>
  <span expr:class='&quot;item-control &quot; + data:comment.adminClass'>
    <b:if cond='data:showCmtPopup'>
      <div class='goog-toggle-button'>
        <div class='goog-inline-block comment-action-icon'/>
      </div>
    <b:else/>
      <a class='comment-delete' expr:href='data:comment.deleteUrl' expr:title='data:messages.deleteComment'>
        <img src='https://resources.blogblog.com/img/icon_delete13.gif'/>
      </a>
    </b:if>
  </span>
</b:includable>
                    <b:includable id='commentForm' var='post'>
  <div class='comment-form'>
    <a name='comment-form'/>
    <h4 id='comment-post-message'><data:messages.postAComment/></h4>
    <b:if cond='data:this.messages.blogComment != &quot;&quot;'>
      <p><data:this.messages.blogComment/></p>
    </b:if>
    <b:include data='post' name='commentFormIframeSrc'/>
    <iframe allowtransparency='allowtransparency' class='blogger-iframe-colorize blogger-comment-from-post' expr:height='data:cmtIframeInitialHeight ?: &quot;90px&quot;' frameborder='0' id='comment-editor' name='comment-editor' src='' width='100%'/>
    <data:post.cmtfpIframe/>
    <script type='text/javascript'>
      BLOG_CMT_createIframe(&#39;<data:post.appRpcRelayPath/>&#39;);
    </script>
  </div>
</b:includable>
                    <b:includable id='commentFormIframeSrc' var='post'>
  <a expr:href='data:post.commentFormIframeSrc' id='comment-editor-src'/>
</b:includable>
                    <b:includable id='commentItem' var='comment'>
  <div class='comment' expr:id='&quot;c&quot; + data:comment.id'>
    <b:include cond='data:blog.enabledCommentProfileImages' name='commentAuthorAvatar'/>

    <div class='comment-block'>
      <div class='comment-author'>
        <b:if cond='data:comment.authorUrl'>
          <b:message name='messages.authorSaidWithLink'>
            <b:param expr:value='data:comment.author' name='authorName'/>
            <b:param expr:value='data:comment.authorUrl' name='authorUrl'/>
          </b:message>
        <b:else/>
          <b:message name='messages.authorSaid'>
            <b:param expr:value='data:comment.author' name='authorName'/>
          </b:message>
        </b:if>
      </div>
      <div expr:class='&quot;comment-body&quot; + (data:comment.isDeleted ? &quot; deleted&quot; : &quot;&quot;)'>
        <data:comment.body/>
      </div>
      <div class='comment-footer'>
        <span class='comment-timestamp'>
          <a expr:href='data:comment.url' title='comment permalink'>
            <data:comment.timestamp/>
          </a>
          <b:include data='comment' name='commentDeleteIcon'/>
        </span>
      </div>
    </div>
  </div>
</b:includable>
                    <b:includable id='commentList' var='comments'>
  <div id='comments-block'>
    <b:loop values='data:comments' var='comment'>
      <b:include data='comment' name='commentItem'/>
    </b:loop>
  </div>
</b:includable>
                    <b:includable id='commentPicker' var='post'>
  <b:if cond='data:post.showThreadedComments'>
    <b:include data='post' name='threadedComments'/>
  <b:else/>
    <b:include data='post' name='comments'/>
  </b:if>
</b:includable>
                    <b:includable id='comments' var='post'>
  <section expr:class='&quot;comments&quot; + (data:post.embedCommentForm ? &quot; embed&quot; : &quot;&quot;)' expr:data-num-comments='data:post.numberOfComments' id='comments'>
    <a name='comments'/>
    <b:if cond='data:post.allowComments'>

      <b:include name='commentsTitle'/>

      <div expr:id='data:widget.instanceId + &quot;_comments-block-wrapper&quot;'>
        <b:include cond='data:post.comments' data='post.comments' name='commentList'/>
      </div>

      <b:if cond='data:post.commentPagingRequired'>
        <div class='paging-control-container'>
          <b:if cond='data:post.hasOlderLinks'>
            <a expr:class='data:post.oldLinkClass' expr:href='data:post.oldestLinkUrl'>
              <data:messages.oldest/>
            </a>
            <a expr:class='data:post.oldLinkClass' expr:href='data:post.olderLinkUrl'>
              <data:messages.older/>
            </a>
          </b:if>

          <span class='comment-range-text'>
            <data:post.commentRangeText/>
          </span>

          <b:if cond='data:post.hasNewerLinks'>
            <a expr:class='data:post.newLinkClass' expr:href='data:post.newerLinkUrl'>
              <data:messages.newer/>
            </a>
            <a expr:class='data:post.newLinkClass' expr:href='data:post.newestLinkUrl'>
              <data:messages.newest/>
            </a>
          </b:if>
        </div>
      </b:if>

      <div class='footer'>
        <b:if cond='data:post.embedCommentForm'>
          <b:if cond='data:post.allowNewComments'>
            <b:include data='post' name='commentForm'/>
          <b:else/>
            <data:post.noNewCommentsText/>
          </b:if>
        <b:else/>
          <b:if cond='data:post.allowComments'>
            <b:include data='post' name='addComments'/>
          </b:if>
        </b:if>
      </div>
    </b:if>
    <b:if cond='data:showCmtPopup'>
      <div id='comment-popup'>
        <iframe allowtransparency='allowtransparency' frameborder='0' id='comment-actions' name='comment-actions' scrolling='no'>
        </iframe>
      </div>
    </b:if>
  </section>
</b:includable>
                    <b:includable id='commentsTitle'>
  <h3 class='title'><data:messages.comments/></h3>
</b:includable>
                    <b:includable id='feedLinks'>
  <b:if cond='!data:view.isPost'> <!-- Blog feed links -->
    <b:if cond='data:feedLinks'>
      <div class='blog-feeds'>
        <b:include data='feedLinks' name='feedLinksBody'/>
      </div>
    </b:if>
  <b:else/> <!--Post feed links -->
    <div class='post-feeds'>
      <b:loop values='data:posts' var='post'>
        <b:if cond='data:post.allowComments and data:post.feedLinks'>
          <b:include data='post.feedLinks' name='feedLinksBody'/>
        </b:if>
      </b:loop>
    </div>
  </b:if>
</b:includable>
                    <b:includable id='feedLinksBody' var='links'>
  <div class='feed-links'>
  <data:messages.subscribeTo/>
  <b:loop values='data:links' var='f'>
     <a class='feed-link' expr:href='data:f.url' expr:type='data:f.mimeType' target='_blank'><data:f.name/> (<data:f.feedType/>)</a>
  </b:loop>
  </div>
</b:includable>
                    <b:includable id='homePageLink'>
  <a class='home-link' expr:href='data:blog.homepageUrl'>
    <data:messages.home/>
  </a>
</b:includable>
                    <b:includable id='iframeComments' var='post'>
  <!-- G+ comments, no longer available. The includable is retained for backwards-compatibility. -->
</b:includable>
                    <b:includable id='inlineAd' var='post'>
  <b:if cond='!data:view.isPreview'>
    <b:if cond='data:this.adCode or data:this.adClientId or data:blog.adsenseClientId'>
      <!-- Ad -->
      <div class='inline-ad'>
        <b:if cond='data:this.adCode != &quot;&quot;'>
          <data:this.adCode/>
        <b:else/>
          <b:include cond='data:this.adClientId or data:blog.adsenseClientId' name='defaultAdUnit'/>
        </b:if>
      </div>
    </b:if>
  <b:else/>
    <div class='inline-ad'>
      <div class='inline-ad-placeholder'>
        <span><b:message name='messages.adsGoHere'/></span>
      </div>
    </div>
  </b:if>
</b:includable>
                    <b:includable id='nextPageLink'>
  <a class='blog-pager-older-link' expr:href='data:olderPageUrl' expr:id='data:widget.instanceId + &quot;_blog-pager-older-link&quot;' expr:title='data:messages.olderPosts'>
    <data:messages.olderPosts/>
  </a>
</b:includable>
                    <b:includable id='post' var='post'>
  <div class='post'>
    <b:include data='post' name='postMeta'/>
    <b:include data='post' name='postTitle'/>
    <b:include name='headerByline'/>
    <b:if cond='data:view.isSingleItem'>
      <b:include data='post' name='postBody'/>
    <b:else/>
      <b:include data='post' name='postBodySnippet'/>
      <b:include data='post' name='postJumpLink'/>
    </b:if>
    <b:include data='post' name='postFooter'/>
  </div>
</b:includable>
                    <b:includable id='postBody' var='post'>
  <!-- If metaDescription is empty, use the post body as the schema.org description too, for G+/FB snippeting. -->
  <div class='post-body entry-content float-container' expr:id='&quot;post-body-&quot; + data:post.id'>
    <data:post.body/>
  </div>
</b:includable>
                    <b:includable id='postBodySnippet' var='post'>
  <b:include data='post' name='postBody'/>
</b:includable>
                    <b:includable id='postCommentsAndAd' var='post'>
  <article class='post-outer-container'>
    <!-- Post title and body -->
    <div class='post-outer'>
      <b:include data='post' name='post'/>
    </div>

    <!-- Comments -->
    <b:include cond='data:view.isSingleItem' data='post' name='commentPicker'/>

    <!-- Show ad inside post container, after comments, if single item. -->
    <b:include cond='data:view.isSingleItem and data:post.includeAd' data='post' name='inlineAd'/>
  </article>

  <!-- Show ad outside post container (between posts) for feed pages. -->
  <b:include cond='data:view.isMultipleItems and data:post.includeAd' data='post' name='inlineAd'/>
</b:includable>
                    <b:includable id='postCommentsLink'>
  <b:if cond='data:view.isMultipleItems'>
    <span class='byline post-comment-link container'>
      <b:include cond='data:post.commentSource != 1' name='commentsLink'/>
    </span>
  </b:if>
</b:includable>
                    <b:includable id='postFooter' var='post'>
  <div class='post-footer'>
    <b:include name='footerBylines'/>
    <b:include data='post' name='postFooterAuthorProfile'/>
  </div>
</b:includable>
                    <b:includable id='postFooterAuthorProfile' var='post'>
  <b:if cond='data:post.author.aboutMe and data:view.isPost'>
    <div class='author-profile'>
      <b:if cond='data:post.author.authorPhoto.url'>
        <img class='author-image' expr:src='data:post.author.authorPhoto.url' width='50px'/>
        <div class='author-about'>
          <b:include data='post' name='aboutPostAuthor'/>
        </div>
      <b:else/>
        <b:include data='post' name='aboutPostAuthor'/>
      </b:if>
    </div>
  </b:if>
</b:includable>
                    <b:includable id='postHeader' var='post'>
  <b:include name='headerByline'/>
</b:includable>
                    <b:includable id='postMeta' var='post'>
  <b:include data='post' name='postMetadataJSON'/>
</b:includable>
                    <b:includable id='postPagination'>
  <div class='blog-pager container' id='blog-pager'>
    <b:include cond='data:newerPageUrl' name='previousPageLink'/>
    <b:include cond='data:olderPageUrl' name='nextPageLink'/>
    <b:include cond='data:view.url != data:blog.homepageUrl' name='homePageLink'/>
  </div>
</b:includable>
                    <b:includable id='postTitle' var='post'>
  <a expr:name='data:post.id'/>
  <b:if cond='data:post.title != &quot;&quot;'>
    <h3 class='post-title entry-title'>
      <b:if cond='data:post.link or (data:post.url and data:view.url != data:post.url)'>
        <a expr:href='data:post.link ?: data:post.url'><data:post.title/></a>
      <b:else/>
        <data:post.title/>
      </b:if>
    </h3>
  </b:if>
</b:includable>
                    <b:includable id='previousPageLink'>
  <a class='blog-pager-newer-link' expr:href='data:newerPageUrl' expr:id='data:widget.instanceId + &quot;_blog-pager-newer-link&quot;' expr:title='data:messages.newerPosts'>
    <data:messages.newerPosts/>
  </a>
</b:includable>
                    <b:includable id='threadedCommentForm' var='post'>
  <div class='comment-form'>
    <a name='comment-form'/>
    <h4 id='comment-post-message'><data:messages.postAComment/></h4>
    <b:if cond='data:this.messages.blogComment != &quot;&quot;'>
      <p><data:this.messages.blogComment/></p>
    </b:if>
    <b:include data='post' name='commentFormIframeSrc'/>
    <iframe allowtransparency='allowtransparency' class='blogger-iframe-colorize blogger-comment-from-post' expr:height='data:cmtIframeInitialHeight ?: &quot;90px&quot;' frameborder='0' id='comment-editor' name='comment-editor' src='' width='100%'/>
    <data:post.cmtfpIframe/>
    <script type='text/javascript'>
      BLOG_CMT_createIframe(&#39;<data:post.appRpcRelayPath/>&#39;);
    </script>
  </div>
</b:includable>
                    <b:includable id='threadedCommentJs' var='post'>
  <script async='async' expr:src='data:post.commentSrc' type='text/javascript'/>
  <b:template-script inline='true' name='threaded_comments'/>
  <script type='text/javascript'>
    blogger.widgets.blog.initThreadedComments(
        <data:post.commentJso/>,
        <data:post.commentMsgs/>,
        <data:post.commentConfig/>);
  </script>
</b:includable>
                    <b:includable id='threadedComments' var='post'>
  <section class='comments threaded' expr:data-embed='data:post.embedCommentForm' expr:data-num-comments='data:post.numberOfComments' id='comments'>
    <a name='comments'/>

    <b:include name='commentsTitle'/>

    <div class='comments-content'>
      <b:if cond='data:post.embedCommentForm'>
        <b:include data='post' name='threadedCommentJs'/>
      </b:if>
      <div id='comment-holder'>
         <data:post.commentHtml/>
      </div>
    </div>

    <p class='comment-footer'>
      <b:if cond='data:post.allowNewComments'>
        <b:include data='post' name='threadedCommentForm'/>
      <b:else/>
        <data:post.noNewCommentsText/>
      </b:if>
      <b:if cond='data:post.showManageComments'>
        <b:include data='post' name='manageComments'/>
      </b:if>
    </p>

    <b:if cond='data:showCmtPopup'>
      <div id='comment-popup'>
        <iframe allowtransparency='allowtransparency' frameborder='0' id='comment-actions' name='comment-actions' scrolling='no'>
        </iframe>
      </div>
    </b:if>
  </section>
</b:includable>
                    <b:includable id='tooltipCss'>
  <!-- LINT.IfChange -->
  <style>
    .post-body a.b-tooltip-container {
      position: relative;
      display: inline-block;
    }

    .post-body a.b-tooltip-container .b-tooltip {
      display: block !important;
      position: absolute;
      top: 100%;
      left: 50%;
      transform: translate(-20%, 1px);
      visibility: hidden;
      opacity: 0;
      z-index: 1;
      transition: opacity 0.2s ease-in-out;
    }

    .post-body a.b-tooltip-container .b-tooltip iframe {
      width: 200px;
      height: 198px;
      max-width: none;
      border: none;
      border-radius: 20px;
      box-shadow: 1px 1px 3px 1px rgba(0, 0, 0, 0.2);
    }

    @media (hover: hover) {
      .post-body a.b-tooltip-container:hover .b-tooltip {
        visibility: visible;
        opacity: 1;
      }
    }
  </style>
  <!-- LINT.ThenChange(//depot/google3/java/com/google/blogger/b2/layouts/widgets/v2-style.css) -->
</b:includable>
                  </b:widget>
                </b:section>
            </section>

            <!-- Static Sections (Media, About, Exhibitions) -->
            <!-- These are HTML Widgets so you can edit the text easily in Layout -->
            
            <b:section id='Static-Content-Sections' showaddelement='yes'>
              <b:widget id='HTML2' locked='false' title='Media Section' type='HTML' version='2' visible='true'>
                <b:widget-settings>
                  <b:widget-setting name='content'><![CDATA[<section id="media">
    <h2>Media & Process</h2>
    
    <div class="text-container">
        <!-- Lead Text -->
        <p class="lead-text">
            Hledání hranice mezi přesností a organickým chaosem.<br />
            <span style="font-size: 0.85em; color: var(--text-secondary); font-style: italic;">Exploring the boundary between precision and organic chaos.</span>
        </p>
        
        <div class="text-divider"></div>

        <!-- Main Process Text (Czech) -->
        <p class="process-text">
            Moje tvorba často začíná studiem materiálu a formy. Ráda pracuji s tuší a akvarelem, experimentuji s automatickou kresbou, výraznými tahy štětcem a technikami otisku barvy. Má inspirace často vzniká v přírodě, a to i v případě abstraktních prací. Techniky, které rozvíjím v abstrakci, pak zpětně ovlivňují atmosféru a texturu mých akvarelových a pastelových krajin, i skicových portrétů.
        </p>

        <!-- Main Process Text (English Translation) -->
        <p class="process-text" style="color: var(--text-secondary); font-style: italic; margin-top: -1rem;">
            My creative process often begins with raw material studies. I enjoy working with ink and watercolor, experimenting with automatic drawing, expressive brushstrokes, and paint printing techniques. My inspiration is deeply rooted in nature—even in my abstract works. The techniques I develop in abstraction inevitably influence the atmosphere and texture of my watercolor and pastel landscapes.
        </p>

        <!-- Quote Block -->
        <div style="margin: 3rem 0; padding: 2rem; background: var(--bg-secondary); border-left: 3px solid var(--accent); text-align: center;">
            <p style="font-size: 1.2rem; font-weight: 400; margin-bottom: 0.5rem;">
                „Příroda a lidské pocity jsou propojené a vzájemně se ovlivňují. Co se může zdát jako náhoda, často skrývá hlubší významy.“
            </p>
            <p style="color: var(--text-secondary); font-style: italic; margin: 0; font-size: 0.95rem;">
                "Both nature and human feelings are interconnected and affect each other. What may seem like randomness can reveal deep meanings."
            </p>
            <div style="margin-top: 1rem; font-size: 0.8rem; letter-spacing: 2px; text-transform: uppercase; opacity: 0.7;">
                — Markéta Pragerová
            </div>
        </div>
    </div>

    <!-- Image Embed (Replaces Video) -->
    <div class="media-embed">
        <!-- IMPORTANT: Replace the src below with a link from your "Assets" page -->
        <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh92DDeML63PVy-S1Y24MUrZW0qyXBwEwj1YNmnjvWlE2sHbv6yqkEC2LEFIKBmWCpsf6TG0RjBlEHUz78yDKcGBwky3LKCeUIPUdaLGR5qiM0XCmH4dWCho8O07Oy5sh-tGp4Yue8wTliW2u5U9niNrar6t1MoAqMmaXZ4Hb-dQIvei94fmEf2v6ZljVU/w400-h266/CVG019172.jpg" 
             alt="Exhibition View" 
             style="width: 100%; height: auto; border-radius: 4px; box-shadow: 0 4px 20px rgba(0,0,0,0.05);" />
        
        <p class="video-caption">
            Vystavená díla / Exhibition view
        </p>
    </div>
</section>]]></b:widget-setting>
                </b:widget-settings>
                <b:includable id='main'><data:content/></b:includable>
              </b:widget>
              <b:widget id='HTML3' locked='false' title='About Section' type='HTML' version='2' visible='true'>
                <b:widget-settings>
                  <b:widget-setting name='content'><![CDATA[<section id="about">
    <h2>About</h2>
    <div class="about-content">
        <!-- IMPORTANT: Upload a photo of Markéta to a post, copy the link, and replace this src below -->
        <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjfsVyrpMc0NQw7b1lQIJP3OHJgvyW20trxBzDBKQOd7-zFB2OYpb0_Gro0LYpRrJF0OJM0cPIra5K0s1GU70xBVaU-p-2ml6CCN8N86-lB2ws0IwOJNVuiQ8k8Qmccco5LmHNpB0z65jF2egtRSqKg_DrQ-XmJyMmdJVNpzm8al7vxiMwoTRVsAEdUmgA/s1920/Detail%20II.jpg" alt="Markéta Pragerová" class="about-image" style="object-position: top;" />
        
        <div class="about-text">
            <h3>Markéta Pragerová</h3>
            <p style="margin-bottom: 2rem;">
                *1975 v Roudnici nad Labem, žije v Teplicích.<br />
                <span style="color: var(--text-secondary); font-style: italic; font-size: 0.9em;">Born in Roudnice nad Labem, currently living in Teplice.</span>
            </p>
            
            <!-- Timeline of Career/Education -->
            <div class="bio-timeline" style="margin-bottom: 2.5rem;">
                
                <div style="margin-bottom: 1rem;">
                    <strong>Nyní / Currently</strong><br />
                    Volná tvorba<br />
                    <span style="color: var(--text-secondary); font-style: italic;">Free creative projects</span>
                </div>

                <div style="margin-bottom: 1rem;">
                    <strong>2011 – 2012</strong><br />
                    Designérka pro Lasvit (výroba svítidel a světelných plastik)<br />
                    <span style="color: var(--text-secondary); font-style: italic;">Designer for Lasvit (Glassmaking & premium light sculptures)</span>
                </div>

                <div style="margin-bottom: 1rem;">
                    <strong>2008</strong><br />
                    Akademie výtvarných umění v Praze – Letní akademie<br />
                    <span style="color: var(--text-secondary); font-style: italic;">Academy of Fine Arts, Prague – Summer Academy (Intensive painting & drawing)</span>
                </div>

                <div style="margin-bottom: 1rem;">
                    <strong>1993 – 2000</strong><br />
                    Univerzita J. E. Purkyně v Ústí nad Labem<br />
                    <span style="color: var(--text-secondary); font-style: italic;">Jan Evangelista Purkyně University in Ústí nad Labem</span>
                </div>

                <div style="margin-bottom: 1rem;">
                    <strong>1991 – 1996</strong><br />
                    Soukromé studium u ak. mal. Jana Sedláčka<br />
                    <span style="color: var(--text-secondary); font-style: italic;">Private studies in the atelier of academic painter Jan Sedláček</span>
                </div>
            </div>

            <!-- Details Grid -->
            <div class="about-details">
                <div>
                    <h4>Technika / Technique</h4>
                    <ul>
                        <li>
                            Akvarel, pastel, olej<br />
                            <span style="color: var(--text-secondary); font-style: italic; font-size: 0.9em;">Watercolor, pastel, oil</span>
                        </li>
                    </ul>
                </div>
                <div>
                    <h4>Styl / Style</h4>
                    <ul>
                        <li>
                            Imprese a exprese, automatická kresba<br />
                            <span style="color: var(--text-secondary); font-style: italic; font-size: 0.9em;">Impressionism, expressionism, automatic drawing</span>
                        </li>
                    </ul>
                </div>
                <div style="grid-column: 1 / -1;">
                    <h4>Inspirace / Inspiration</h4>
                    <p style="margin: 0; color: var(--text-secondary);">
                        Krajina, příroda, figura, filozofická a emocionální témata.<br />
                        <span style="font-style: italic;">Landscape, nature, figure, philosophical and emotional themes.</span>
                    </p>
                </div>
            </div>
        </div>
    </div>
</section>]]></b:widget-setting>
                </b:widget-settings>
                <b:includable id='main'><data:content/></b:includable>
              </b:widget>
              <b:widget id='HTML4' locked='false' title='Exhibitions &amp;amp; News' type='HTML' version='2' visible='true'>
                <b:widget-settings>
                  <b:widget-setting name='content'><![CDATA[<section id="exhibitions">
    <h2>Exhibitions</h2>
    <div class="timeline">
        
        <!-- 2025 -->
        <div class="timeline-item">
            <div class="timeline-date">2025</div>
            <h3>Galerie Klášter</h3>
            <p>Solo exhibition featuring recent works.</p>
            <div class="timeline-location">Osek u Duchcova</div>
        </div>

        <!-- 2024 -->
        <div class="timeline-item">
            <div class="timeline-date">2024</div>
            <h3>Oblastní muzeum v Ústí nad Labem</h3>
            <p>Solo exhibition, watercolors.</p>
            <div class="timeline-location">Ústí nad Labem</div>
        </div>

        <!-- 2022 (Museum) -->
        <div class="timeline-item">
            <div class="timeline-date">2022</div>
            <h3>Regionální muzeum v Teplicích</h3>
            <p>Solo exhibition, selection of works.</p>
            <div class="timeline-location">Teplice</div>
        </div>

        <!-- 2022 (Library) -->
        <div class="timeline-item">
            <div class="timeline-date">2022</div>
            <h3>Regionální knihovna Teplice</h3>
            <p>Solo exhibition featuring abstract and portrait works.</p>
            <div class="timeline-location">Teplice</div>
        </div>

        <!-- 2021 -->
        <div class="timeline-item">
            <div class="timeline-date">2021</div>
            <h3>Vinotéka Hruška</h3>
            <p>Solo exhibition featuring automatic drawings and abstract works.</p>
            <div class="timeline-location">Liberec</div>
        </div>

    </div>
</section>

<!-- I kept the News section here so you don't lose it, 
     but you can delete it if you don't have news yet -->
<section id="news">
    <h2>Latest News</h2>
    <div class="timeline">
        <div class="timeline-item">
            <div class="timeline-date">2026</div>
            <h3>New Studio Works</h3>
            <p>Currently working on a new series of large format paintings.</p>
        </div>
    </div>
</section>]]></b:widget-setting>
                </b:widget-settings>
                <b:includable id='main'><data:content/></b:includable>
              </b:widget>
              <b:widget id='HTML5' locked='false' title='Contact Section' type='HTML' version='2' visible='true'>
                <b:widget-settings>
                  <b:widget-setting name='content'><![CDATA[<section id="contact">
                            <h2>Get in Touch</h2>
                            <div class="contact-content">
                                <p>For inquiries about available works.</p>
                                <a href="mailto:artist@email.com" class="contact-email">artist@email.com</a>
                                <div class="social-links">
                                    <a href="#" aria-label="Instagram"><svg viewbox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></path></svg></a>
                                </div>
                            </div>
                        </section>]]></b:widget-setting>
                </b:widget-settings>
                <b:includable id='main'><data:content/></b:includable>
              </b:widget>
            </b:section>

        <!-- Single Post View -->
        <b:else/>
            <b:section id='Single-Post-Section' showaddelement='no'>
              <b:widget id='Blog2' locked='true' title='Blog Posts' type='Blog' version='2' visible='true'>
                <b:widget-settings>
                  <b:widget-setting name='showDateHeader'>false</b:widget-setting>
                  <b:widget-setting name='style.textcolor'>#ffffff</b:widget-setting>
                  <b:widget-setting name='showShareButtons'>false</b:widget-setting>
                  <b:widget-setting name='showCommentLink'>true</b:widget-setting>
                  <b:widget-setting name='style.urlcolor'>#ffffff</b:widget-setting>
                  <b:widget-setting name='showAuthor'>true</b:widget-setting>
                  <b:widget-setting name='style.linkcolor'>#ffffff</b:widget-setting>
                  <b:widget-setting name='style.unittype'>TextAndImage</b:widget-setting>
                  <b:widget-setting name='style.bgcolor'>#ffffff</b:widget-setting>
                  <b:widget-setting name='reactionsLabel'/>
                  <b:widget-setting name='showAuthorProfile'>false</b:widget-setting>
                  <b:widget-setting name='style.layout'>1x1</b:widget-setting>
                  <b:widget-setting name='showLabels'>true</b:widget-setting>
                  <b:widget-setting name='showLocation'>true</b:widget-setting>
                  <b:widget-setting name='showTimestamp'>true</b:widget-setting>
                  <b:widget-setting name='postsPerAd'>1</b:widget-setting>
                  <b:widget-setting name='showBacklinks'>false</b:widget-setting>
                  <b:widget-setting name='style.bordercolor'>#ffffff</b:widget-setting>
                  <b:widget-setting name='showInlineAds'>false</b:widget-setting>
                  <b:widget-setting name='showReactions'>false</b:widget-setting>
                </b:widget-settings>
                <b:includable id='main'>
                        <b:loop values='data:posts' var='post'>
                            <article class='post-page'>
                                <h1><data:post.title/></h1>
                                <span class='date'><data:post.date/></span>
                                <div class='post-body'>
                                    <data:post.body/>
                                </div>
                            </article>
                        </b:loop>
                    </b:includable>
                <b:includable id='aboutPostAuthor'>
  <div class='author-name'>
    <a class='g-profile' expr:href='data:post.author.profileUrl' rel='author' title='author profile'>
      <span>
        <data:post.author.name/>
      </span>
    </a>
  </div>
  <div>
    <span class='author-desc'>
      <data:post.author.aboutMe/>
    </span>
  </div>
</b:includable>
                <b:includable id='addComments'>
  <a expr:href='data:post.commentsUrl' expr:onclick='data:post.commentsUrlOnclick'>
    <b:message name='messages.postAComment'/>
  </a>
</b:includable>
                <b:includable id='commentAuthorAvatar'>
  <div class='avatar-image-container'>
    <img class='author-avatar' expr:src='data:comment.authorAvatarSrc' height='35' width='35'/>
  </div>
</b:includable>
                <b:includable id='commentDeleteIcon' var='comment'>
  <span expr:class='&quot;item-control &quot; + data:comment.adminClass'>
    <b:if cond='data:showCmtPopup'>
      <div class='goog-toggle-button'>
        <div class='goog-inline-block comment-action-icon'/>
      </div>
    <b:else/>
      <a class='comment-delete' expr:href='data:comment.deleteUrl' expr:title='data:messages.deleteComment'>
        <img src='https://resources.blogblog.com/img/icon_delete13.gif'/>
      </a>
    </b:if>
  </span>
</b:includable>
                <b:includable id='commentForm' var='post'>
  <div class='comment-form'>
    <a name='comment-form'/>
    <h4 id='comment-post-message'><data:messages.postAComment/></h4>
    <b:if cond='data:this.messages.blogComment != &quot;&quot;'>
      <p><data:this.messages.blogComment/></p>
    </b:if>
    <b:include data='post' name='commentFormIframeSrc'/>
    <iframe allowtransparency='allowtransparency' class='blogger-iframe-colorize blogger-comment-from-post' expr:height='data:cmtIframeInitialHeight ?: &quot;90px&quot;' frameborder='0' id='comment-editor' name='comment-editor' src='' width='100%'/>
    <data:post.cmtfpIframe/>
    <script type='text/javascript'>
      BLOG_CMT_createIframe(&#39;<data:post.appRpcRelayPath/>&#39;);
    </script>
  </div>
</b:includable>
                <b:includable id='commentFormIframeSrc' var='post'>
  <a expr:href='data:post.commentFormIframeSrc' id='comment-editor-src'/>
</b:includable>
                <b:includable id='commentItem' var='comment'>
  <div class='comment' expr:id='&quot;c&quot; + data:comment.id'>
    <b:include cond='data:blog.enabledCommentProfileImages' name='commentAuthorAvatar'/>

    <div class='comment-block'>
      <div class='comment-author'>
        <b:if cond='data:comment.authorUrl'>
          <b:message name='messages.authorSaidWithLink'>
            <b:param expr:value='data:comment.author' name='authorName'/>
            <b:param expr:value='data:comment.authorUrl' name='authorUrl'/>
          </b:message>
        <b:else/>
          <b:message name='messages.authorSaid'>
            <b:param expr:value='data:comment.author' name='authorName'/>
          </b:message>
        </b:if>
      </div>
      <div expr:class='&quot;comment-body&quot; + (data:comment.isDeleted ? &quot; deleted&quot; : &quot;&quot;)'>
        <data:comment.body/>
      </div>
      <div class='comment-footer'>
        <span class='comment-timestamp'>
          <a expr:href='data:comment.url' title='comment permalink'>
            <data:comment.timestamp/>
          </a>
          <b:include data='comment' name='commentDeleteIcon'/>
        </span>
      </div>
    </div>
  </div>
</b:includable>
                <b:includable id='commentList' var='comments'>
  <div id='comments-block'>
    <b:loop values='data:comments' var='comment'>
      <b:include data='comment' name='commentItem'/>
    </b:loop>
  </div>
</b:includable>
                <b:includable id='commentPicker' var='post'>
  <b:if cond='data:post.showThreadedComments'>
    <b:include data='post' name='threadedComments'/>
  <b:else/>
    <b:include data='post' name='comments'/>
  </b:if>
</b:includable>
                <b:includable id='comments' var='post'>
  <section expr:class='&quot;comments&quot; + (data:post.embedCommentForm ? &quot; embed&quot; : &quot;&quot;)' expr:data-num-comments='data:post.numberOfComments' id='comments'>
    <a name='comments'/>
    <b:if cond='data:post.allowComments'>

      <b:include name='commentsTitle'/>

      <div expr:id='data:widget.instanceId + &quot;_comments-block-wrapper&quot;'>
        <b:include cond='data:post.comments' data='post.comments' name='commentList'/>
      </div>

      <b:if cond='data:post.commentPagingRequired'>
        <div class='paging-control-container'>
          <b:if cond='data:post.hasOlderLinks'>
            <a expr:class='data:post.oldLinkClass' expr:href='data:post.oldestLinkUrl'>
              <data:messages.oldest/>
            </a>
            <a expr:class='data:post.oldLinkClass' expr:href='data:post.olderLinkUrl'>
              <data:messages.older/>
            </a>
          </b:if>

          <span class='comment-range-text'>
            <data:post.commentRangeText/>
          </span>

          <b:if cond='data:post.hasNewerLinks'>
            <a expr:class='data:post.newLinkClass' expr:href='data:post.newerLinkUrl'>
              <data:messages.newer/>
            </a>
            <a expr:class='data:post.newLinkClass' expr:href='data:post.newestLinkUrl'>
              <data:messages.newest/>
            </a>
          </b:if>
        </div>
      </b:if>

      <div class='footer'>
        <b:if cond='data:post.embedCommentForm'>
          <b:if cond='data:post.allowNewComments'>
            <b:include data='post' name='commentForm'/>
          <b:else/>
            <data:post.noNewCommentsText/>
          </b:if>
        <b:else/>
          <b:if cond='data:post.allowComments'>
            <b:include data='post' name='addComments'/>
          </b:if>
        </b:if>
      </div>
    </b:if>
    <b:if cond='data:showCmtPopup'>
      <div id='comment-popup'>
        <iframe allowtransparency='allowtransparency' frameborder='0' id='comment-actions' name='comment-actions' scrolling='no'>
        </iframe>
      </div>
    </b:if>
  </section>
</b:includable>
                <b:includable id='commentsTitle'>
  <h3 class='title'><data:messages.comments/></h3>
</b:includable>
                <b:includable id='feedLinks'>
  <b:if cond='!data:view.isPost'> <!-- Blog feed links -->
    <b:if cond='data:feedLinks'>
      <div class='blog-feeds'>
        <b:include data='feedLinks' name='feedLinksBody'/>
      </div>
    </b:if>
  <b:else/> <!--Post feed links -->
    <div class='post-feeds'>
      <b:loop values='data:posts' var='post'>
        <b:if cond='data:post.allowComments and data:post.feedLinks'>
          <b:include data='post.feedLinks' name='feedLinksBody'/>
        </b:if>
      </b:loop>
    </div>
  </b:if>
</b:includable>
                <b:includable id='feedLinksBody' var='links'>
  <div class='feed-links'>
  <data:messages.subscribeTo/>
  <b:loop values='data:links' var='f'>
     <a class='feed-link' expr:href='data:f.url' expr:type='data:f.mimeType' target='_blank'><data:f.name/> (<data:f.feedType/>)</a>
  </b:loop>
  </div>
</b:includable>
                <b:includable id='homePageLink'>
  <a class='home-link' expr:href='data:blog.homepageUrl'>
    <data:messages.home/>
  </a>
</b:includable>
                <b:includable id='iframeComments' var='post'>
  <!-- G+ comments, no longer available. The includable is retained for backwards-compatibility. -->
</b:includable>
                <b:includable id='inlineAd' var='post'>
  <b:if cond='!data:view.isPreview'>
    <b:if cond='data:this.adCode or data:this.adClientId or data:blog.adsenseClientId'>
      <!-- Ad -->
      <div class='inline-ad'>
        <b:if cond='data:this.adCode != &quot;&quot;'>
          <data:this.adCode/>
        <b:else/>
          <b:include cond='data:this.adClientId or data:blog.adsenseClientId' name='defaultAdUnit'/>
        </b:if>
      </div>
    </b:if>
  <b:else/>
    <div class='inline-ad'>
      <div class='inline-ad-placeholder'>
        <span><b:message name='messages.adsGoHere'/></span>
      </div>
    </div>
  </b:if>
</b:includable>
                <b:includable id='nextPageLink'>
  <a class='blog-pager-older-link' expr:href='data:olderPageUrl' expr:id='data:widget.instanceId + &quot;_blog-pager-older-link&quot;' expr:title='data:messages.olderPosts'>
    <data:messages.olderPosts/>
  </a>
</b:includable>
                <b:includable id='post' var='post'>
  <div class='post'>
    <b:include data='post' name='postMeta'/>
    <b:include data='post' name='postTitle'/>
    <b:include name='headerByline'/>
    <b:if cond='data:view.isSingleItem'>
      <b:include data='post' name='postBody'/>
    <b:else/>
      <b:include data='post' name='postBodySnippet'/>
      <b:include data='post' name='postJumpLink'/>
    </b:if>
    <b:include data='post' name='postFooter'/>
  </div>
</b:includable>
                <b:includable id='postBody' var='post'>
  <!-- If metaDescription is empty, use the post body as the schema.org description too, for G+/FB snippeting. -->
  <div class='post-body entry-content float-container' expr:id='&quot;post-body-&quot; + data:post.id'>
    <data:post.body/>
  </div>
</b:includable>
                <b:includable id='postBodySnippet' var='post'>
  <b:include data='post' name='postBody'/>
</b:includable>
                <b:includable id='postCommentsAndAd' var='post'>
  <article class='post-outer-container'>
    <!-- Post title and body -->
    <div class='post-outer'>
      <b:include data='post' name='post'/>
    </div>

    <!-- Comments -->
    <b:include cond='data:view.isSingleItem' data='post' name='commentPicker'/>

    <!-- Show ad inside post container, after comments, if single item. -->
    <b:include cond='data:view.isSingleItem and data:post.includeAd' data='post' name='inlineAd'/>
  </article>

  <!-- Show ad outside post container (between posts) for feed pages. -->
  <b:include cond='data:view.isMultipleItems and data:post.includeAd' data='post' name='inlineAd'/>
</b:includable>
                <b:includable id='postCommentsLink'>
  <b:if cond='data:view.isMultipleItems'>
    <span class='byline post-comment-link container'>
      <b:include cond='data:post.commentSource != 1' name='commentsLink'/>
    </span>
  </b:if>
</b:includable>
                <b:includable id='postFooter' var='post'>
  <div class='post-footer'>
    <b:include name='footerBylines'/>
    <b:include data='post' name='postFooterAuthorProfile'/>
  </div>
</b:includable>
                <b:includable id='postFooterAuthorProfile' var='post'>
  <b:if cond='data:post.author.aboutMe and data:view.isPost'>
    <div class='author-profile'>
      <b:if cond='data:post.author.authorPhoto.url'>
        <img class='author-image' expr:src='data:post.author.authorPhoto.url' width='50px'/>
        <div class='author-about'>
          <b:include data='post' name='aboutPostAuthor'/>
        </div>
      <b:else/>
        <b:include data='post' name='aboutPostAuthor'/>
      </b:if>
    </div>
  </b:if>
</b:includable>
                <b:includable id='postHeader' var='post'>
  <b:include name='headerByline'/>
</b:includable>
                <b:includable id='postMeta' var='post'>
  <b:include data='post' name='postMetadataJSON'/>
</b:includable>
                <b:includable id='postPagination'>
  <div class='blog-pager container' id='blog-pager'>
    <b:include cond='data:newerPageUrl' name='previousPageLink'/>
    <b:include cond='data:olderPageUrl' name='nextPageLink'/>
    <b:include cond='data:view.url != data:blog.homepageUrl' name='homePageLink'/>
  </div>
</b:includable>
                <b:includable id='postTitle' var='post'>
  <a expr:name='data:post.id'/>
  <b:if cond='data:post.title != &quot;&quot;'>
    <h3 class='post-title entry-title'>
      <b:if cond='data:post.link or (data:post.url and data:view.url != data:post.url)'>
        <a expr:href='data:post.link ?: data:post.url'><data:post.title/></a>
      <b:else/>
        <data:post.title/>
      </b:if>
    </h3>
  </b:if>
</b:includable>
                <b:includable id='previousPageLink'>
  <a class='blog-pager-newer-link' expr:href='data:newerPageUrl' expr:id='data:widget.instanceId + &quot;_blog-pager-newer-link&quot;' expr:title='data:messages.newerPosts'>
    <data:messages.newerPosts/>
  </a>
</b:includable>
                <b:includable id='threadedCommentForm' var='post'>
  <div class='comment-form'>
    <a name='comment-form'/>
    <h4 id='comment-post-message'><data:messages.postAComment/></h4>
    <b:if cond='data:this.messages.blogComment != &quot;&quot;'>
      <p><data:this.messages.blogComment/></p>
    </b:if>
    <b:include data='post' name='commentFormIframeSrc'/>
    <iframe allowtransparency='allowtransparency' class='blogger-iframe-colorize blogger-comment-from-post' expr:height='data:cmtIframeInitialHeight ?: &quot;90px&quot;' frameborder='0' id='comment-editor' name='comment-editor' src='' width='100%'/>
    <data:post.cmtfpIframe/>
    <script type='text/javascript'>
      BLOG_CMT_createIframe(&#39;<data:post.appRpcRelayPath/>&#39;);
    </script>
  </div>
</b:includable>
                <b:includable id='threadedCommentJs' var='post'>
  <script async='async' expr:src='data:post.commentSrc' type='text/javascript'/>
  <b:template-script inline='true' name='threaded_comments'/>
  <script type='text/javascript'>
    blogger.widgets.blog.initThreadedComments(
        <data:post.commentJso/>,
        <data:post.commentMsgs/>,
        <data:post.commentConfig/>);
  </script>
</b:includable>
                <b:includable id='threadedComments' var='post'>
  <section class='comments threaded' expr:data-embed='data:post.embedCommentForm' expr:data-num-comments='data:post.numberOfComments' id='comments'>
    <a name='comments'/>

    <b:include name='commentsTitle'/>

    <div class='comments-content'>
      <b:if cond='data:post.embedCommentForm'>
        <b:include data='post' name='threadedCommentJs'/>
      </b:if>
      <div id='comment-holder'>
         <data:post.commentHtml/>
      </div>
    </div>

    <p class='comment-footer'>
      <b:if cond='data:post.allowNewComments'>
        <b:include data='post' name='threadedCommentForm'/>
      <b:else/>
        <data:post.noNewCommentsText/>
      </b:if>
      <b:if cond='data:post.showManageComments'>
        <b:include data='post' name='manageComments'/>
      </b:if>
    </p>

    <b:if cond='data:showCmtPopup'>
      <div id='comment-popup'>
        <iframe allowtransparency='allowtransparency' frameborder='0' id='comment-actions' name='comment-actions' scrolling='no'>
        </iframe>
      </div>
    </b:if>
  </section>
</b:includable>
                <b:includable id='tooltipCss'>
  <!-- LINT.IfChange -->
  <style>
    .post-body a.b-tooltip-container {
      position: relative;
      display: inline-block;
    }

    .post-body a.b-tooltip-container .b-tooltip {
      display: block !important;
      position: absolute;
      top: 100%;
      left: 50%;
      transform: translate(-20%, 1px);
      visibility: hidden;
      opacity: 0;
      z-index: 1;
      transition: opacity 0.2s ease-in-out;
    }

    .post-body a.b-tooltip-container .b-tooltip iframe {
      width: 200px;
      height: 198px;
      max-width: none;
      border: none;
      border-radius: 20px;
      box-shadow: 1px 1px 3px 1px rgba(0, 0, 0, 0.2);
    }

    @media (hover: hover) {
      .post-body a.b-tooltip-container:hover .b-tooltip {
        visibility: visible;
        opacity: 1;
      }
    }
  </style>
  <!-- LINT.ThenChange(//depot/google3/java/com/google/blogger/b2/layouts/widgets/v2-style.css) -->
</b:includable>
              </b:widget>
            </b:section>
        </b:if>
    </div>

    <!-- Footer -->
    <footer>
        <p>&#169; <span id='currentYear'/> <data:blog.title/>. All rights reserved.</p>
    </footer>
    <button class='share-btn' onclick='sharePortfolio()' title='Share'>&#8599;</button>

    <script>
    //<![CDATA[
        document.getElementById('currentYear').textContent = new Date().getFullYear();

        // Hero Slideshow
        let currentSlide = 0;
        const slides = document.querySelectorAll('.hero-slide');
        const heroNav = document.getElementById('heroNav');
        let slideInterval;

        if (slides.length > 0) {
            slides.forEach((slide, index) => {
                const dot = document.createElement('div');
                dot.className = 'hero-dot';
                if (index === 0) dot.classList.add('active');
                dot.onclick = () => goToSlide(index);
                if(heroNav) heroNav.appendChild(dot);
            });

            const dots = document.querySelectorAll('.hero-dot');

            function showSlide(n) {
                slides.forEach(slide => slide.classList.remove('active'));
                dots.forEach(dot => dot.classList.remove('active'));
                currentSlide = (n + slides.length) % slides.length;
                slides[currentSlide].classList.add('active');
                if(dots[currentSlide]) dots[currentSlide].classList.add('active');
            }

            window.changeSlide = function(direction) {
                showSlide(currentSlide + direction);
                resetInterval();
            }

            function goToSlide(n) {
                showSlide(n);
                resetInterval();
            }

            function nextSlide() { showSlide(currentSlide + 1); }
            function startSlideshow() { slideInterval = setInterval(nextSlide, 5000); }
            function resetInterval() { clearInterval(slideInterval); startSlideshow(); }

            startSlideshow();
            const heroSection = document.querySelector('.hero');
            if(heroSection) {
                heroSection.addEventListener('mouseenter', () => clearInterval(slideInterval));
                heroSection.addEventListener('mouseleave', startSlideshow);
            }
        }

        // Gallery Grid
        window.setGridLayout = function(columns) {
            const gallery = document.getElementById('galleryGrid');
            if(gallery) {
                const buttons = document.querySelectorAll('.grid-toggle');
                buttons.forEach(btn => btn.classList.remove('active'));
                event.target.classList.add('active');
                gallery.className = 'gallery-grid grid-' + columns;
            }
        }

        // Theme Toggle
        window.toggleTheme = function() {
            const html = document.documentElement;
            const newTheme = html.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
            html.setAttribute('data-theme', newTheme);
            localStorage.setItem('theme', newTheme);
        }
        document.documentElement.setAttribute('data-theme', localStorage.getItem('theme') || 'light');
        
        // Mobile Menu
        window.toggleMenu = function() {
            const navLinks = document.getElementById('navLinks');
            navLinks.classList.toggle('active');
        }
        
        // Share
        window.sharePortfolio = async function() {
            try {
                if (navigator.share) {
                    await navigator.share({
                        title: document.title,
                        url: window.location.href
                    });
                } else {
                    await navigator.clipboard.writeText(window.location.href);
                    alert('Link copied!');
                }
            } catch (err) { console.log('Error sharing:', err); }
        }
        
        // Smooth Scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                if(targetId === '#') return;
                const target = document.querySelector(targetId);
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                    document.getElementById('navLinks').classList.remove('active');
                }
            });
        });
        
        // Nav Scroll Effect
        let lastScroll = 0;
        const nav = document.querySelector('nav');
        window.addEventListener('scroll', () => {
            const currentScroll = window.pageYOffset;
            if (currentScroll > lastScroll && currentScroll > 80) {
                nav.style.transform = 'translateY(-100%)';
            } else {
                nav.style.transform = 'translateY(0)';
            }
            lastScroll = currentScroll;
        });
    //]]>
    </script>
</body>
</html>