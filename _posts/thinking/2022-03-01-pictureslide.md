---
layout: post
title: picture slide
description: >
  그림 슬라이드하기
sitemap: false
categories: 
 - thinking
---

<div class="main_center">
    <div><img src= "/assets/img/blog/louis-hansel.jpg" style="width: auto; height: 500px;"></div>
    <div><img src="/assets/img/blog/sidebar-bg.jpg" style="width: auto; height: 500px;"></div>
    <div><img src= "/assets/img/blog/caleb-george-old.jpg" style="width: auto; height: 500px;"></div>
</div>
<script>
    $(document).ready(function() {
        $('.main_center').slick({
            autoplay : true, /*자동으로 슬라이딩됨*/
            dots : true, /* 하단 점 버튼 */
            speed : 300 /* 이미지가 슬라이딩시 걸리는 시간 */,
            infinite : true,
            autoplaySpeed : 30000 /* 이미지가 다른 이미지로 넘어 갈때의 텀 */,
            arrows : true,
            slidesToShow : 1,
            slidesToScroll : 1,
            touchMove : true, /* 마우스 클릭으로 끌어서 슬라이딩 가능여부 */
            nextArrows : true, /* 넥스트버튼 */
            prevArrows : true,
            arrow : true, /*false면 좌우 버튼 없음, true면 좌우 버튼 보임*/
            fade : false
        });
    });
</script>
