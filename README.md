<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Barcode Generator</title>
    <script src="https://cdn.jsdelivr.net/npm/bwip-js/dist/bwip-js-min.js"></script>
    <style>
        body { display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; background: white; }
        canvas { max-width: 90%; height: auto; }
    </style>
</head>
<body>
    <canvas id="canvas"></canvas>
    <script>
        // 從網址列取得參數，例如 ?code=/ABC1234
        const urlParams = new URLSearchParams(window.location.search);
        const myCode = urlParams.get('code') || "NO CODE";

        try {
            bwipjs.toCanvas('canvas', {
                bcid: 'code128',       // 橫向條碼格式
                text: myCode,          // 要生成的文字
                scale: 5,              // 解析度放大，確保好掃
                height: 15,            // 條碼高度比例
                includetext: true,     // 顯示下方文字
                textxalign: 'center',  // 文字居中
            });
        } catch (e) {
            console.error(e);
        }
    </script>
</body>
</html>
