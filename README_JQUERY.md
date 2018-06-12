# Jquery Plugins in common use

## nice scroll

```html
<div id="demo" style="height: 600px; overflow: scroll;">

    <!-- content -->
    <div id="iframe-container" class="content">
        <!-- iframe -->
        <iframe src="./demo.html" scrolling="no" width="1040" height="1000" frameborder="0">
        </iframe>
    </div>

</div>
<script src="./node_modules/jquery/dist/jquery.js"></script>
<script src="./jquery.nicescroll.js"></script>
<script>
    $(function () {
        $("#demo").niceScroll("#iframe-container", {
            cursorcolor: "#00F"
        });
    });
</script>

<!-- 若此处不成立， 有两处测试点 -->
<!-- 1. 在 子页面中去引入 jquery.nice.framehelper.js -->
<!-- 1. 调用 $("#mydiv").getNiceScroll().resize(); 重置高度 -->

```