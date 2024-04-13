<!DOCTYPE html>
<html ng-app="qrGeneratorApp">
<head>
    <title>QR Code Generator</title>
    <script src="angular.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrious/4.0.2/qrious.min.js"></script>
</head>
<body>

<div ng-controller="QRGeneratorController as qrCtrl">
    <input type="text" ng-model="qrCtrl.text" placeholder="Enter text">
    <button ng-click="qrCtrl.generateQR()">Generate QR Code</button>
    <br>
    <canvas id="qrCanvas"></canvas>
</div>

<script>
    angular.module('qrGeneratorApp', [])
        .controller('QRGeneratorController', function () {
            var qrCtrl = this;
            qrCtrl.text = '';

            qrCtrl.generateQR = function () {
                var qr = new QRious({
                    element: document.getElementById('qrCanvas'),
                    value: qrCtrl.text,
                    size: 200
                });
            };
        });
</script>

</body>
</html>
