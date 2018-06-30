# currency-converter
A front-end development of a free version of currency converter which works both in online and offline mode
<!DOCTYPE html>
<head>
<title>Currency converter</title>
<!-- saved from url=(0038)https://free.currencyconverterapi.com/ -->
<html class=" js flexbox flexboxlegacy canvas canvastext webgl no-touch geolocation postmessage websqldatabase indexeddb hashchange history draganddrop websockets rgba hsla multiplebgs backgroundsize borderimage borderradius boxshadow textshadow opacity cssanimations csscolumns cssgradients cssreflections csstransforms csstransforms3d csstransitions fontface generatedcontent video audio localstorage sessionstorage webworkers applicationcache svg inlinesvg smil svgclippaths" lang="en" style=""><!--<![endif]--><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8"><script type="text/javascript" src="./Currency Conversion Tool For Devs _ Free Currency Converter API_files/shares.json"></script><script type="text/javascript" src="./Currency Conversion Tool For Devs _ Free Currency Converter API_files/1.txt"></script>

  <meta http-equiv="content-language" content="en">
  <meta name="author" lang="en" content="Manny Vergel">
  <meta name="copyright" lang="en" content="2013">
  <meta name="description" content="Free Currency Converter API offers free web services for developers to convert one currency to another. Conversion is updated every 60 minutes which can be upgraded to premium options available in different packages.">
  <meta name="keywords" content="currency exchange rates, foreign exchange, currency converter, free, api, web service">


  <meta name="robots" content="all,follow">
  <!-- Set the viewport width to device width for mobile -->
  <meta name="viewport" content="width=device-width">

</head>
<body>

<?php
function convertCurrency($amount,$from_currency,$to_currency){
  
  $from_Currency = urlencode($from_currency);
  $to_Currency = urlencode($to_currency);
  $query =  "{$from_Currency}_{$to_Currency}";

  $json = file_get_contents("https://www.currencyconverterapi.com/api/v5/convert?q={$query}&compact=ultra&apiKey={$apikey}");
  $obj = json_decode($json, true);

  $val = floatval($obj["$query"]);


  $total = $val * $amount;
  return number_format($total, 2, '.', '');
}

//uncomment to test
echo convertCurrency(10, 'USD', 'PHP');
?>

<h1 style="text-align:center;">Currency Converter alc 3.0<h1>
<style>
body {
    background:#ff0f00 url("")no-repeat right top;
    background-size:cover;
    }
</style>
<style>
h1 {
    color:white;
    text-shadow:1px 1px 2px black,0 0 25px blue,0 0 5px darkblue;
    }
</style>
<script src="./Currency Conversion Tool For Devs _ Free Currency Converter API_files/numeral.min.js.download"></script>
<style>
.feature-box {
  text-align: center;
  width: 400px;
}

.feature-box .title {
  font-size: 1.2em;
  font-weight: normal;
  margin-bottom: 6px;
}

.feature-box .desc {

}
</style>
<script>
var addthis_share = {
    url: "https://free.currencyconverterapi.com"
}

function getCurrencyUsingJQuery() {
  var currVal = $("#CURR_VAL");
  currVal.val("");

  var currFrSelect = $("#CURR_FR");
  var fr = currFrSelect.val();

  var currToSelect = $("#CURR_TO");
  var to = currToSelect.val();

  var currId = fr + "_" + to;
  var protocol = window.location.protocol.replace(/:/g,'');

  currVal.attr("placeholder", "Converting...");
  $.getJSON(protocol + "://free.currencyconverterapi.com/api/v5/convert?q=" + currId + "&compact=y&callback=?",
    function(data){
      try {
       var currFrVal = parseFloat(document.getElementById("CURR_FR_VAL").value);
       currVal.val(numeral(currFrVal * data[currId].val).format("0,0.00[0]"));

     } catch (e) {
      alert("Please enter a number in the Amount field.");
    }

    currVal.attr("placeholder", "Press Convert button");

  });
  };
</script>



<script>
var https = require('https');

function convertCurrency(amount, fromCurrency, toCurrency, cb) {
  var apiKey = 'your-api-key-here';

  fromCurrency = encodeURIComponent(fromCurrency);
  toCurrency = encodeURIComponent(toCurrency);
  var query = fromCurrency + '_' + toCurrency;

  var url = 'https://www.currencyconverterapi.com/api/v5/convert?q='
            + query + '&compact=ultra&apiKey=' + apiKey;

  https.get(url, function(res){
      var body = '';

      res.on('data', function(chunk){
          body += chunk;
      });

      res.on('end', function(){
          try {
            var jsonObj = JSON.parse(body);

            var val = jsonObj[query];
            if (val) {
              var total = val * amount;
              cb(null, Math.round(total * 100) / 100);
            } else {
              var err = new Error("Value not found for " + query);
              console.log(err);
              cb(err);
            }
          } catch(e) {
            console.log("Parse error: ", e);
            cb(e);
          }
      });
  }).on('error', function(e){
        console.log("Got an error: ", e);
        cb(e);
  });
}

//uncomment to test

convertCurrency(10, 'USD', 'PHP', function(err, amount) {
  console.log(amount);
});
</script>
<h2 style="text-align:center;">
<style>
div {
    width: 400px;
    margin: auto;
    border: 0px
}
</style>
<style>
.floating-box {
    float: left;
    width: 150px
    height: 750px
    margin: 10px;
    border: 3px solid #73AD21;
 }
  </style>

<div class="row">

<div class="medium-6 columns">
  <div class="row collapse">
    <div class="medium-3 columns">
      <input type="text" value="1" name="CURR_FR_VAL" id="CURR_FR_VAL" placeholder="Enter amount">
    </div>
    <div class="medium-3 columns">
      <select id="CURR_FR" class="postfix">

        <option value="AED">AED</option>

        <option value="AFN">AFN</option>

        <option value="ALL">ALL</option>

        <option value="AMD">AMD</option>

        <option value="ANG">ANG</option>

        <option value="AOA">AOA</option>

        <option value="ARS">ARS</option>

        <option value="AUD">AUD</option>

        <option value="AWG">AWG</option>

        <option value="AZN">AZN</option>

        <option value="BAM">BAM</option>

        <option value="BBD">BBD</option>

        <option value="BDT">BDT</option>

        <option value="BGN">BGN</option>

        <option value="BHD">BHD</option>

        <option value="BIF">BIF</option>

        <option value="BND">BND</option>

        <option value="BOB">BOB</option>

        <option value="BRL">BRL</option>

        <option value="BSD">BSD</option>

        <option value="BTC">BTC</option>

        <option value="BTN">BTN</option>

        <option value="BWP">BWP</option>

        <option value="BYN">BYN</option>

        <option value="BYR">BYR</option>

        <option value="BZD">BZD</option>

        <option value="CAD">CAD</option>

        <option value="CDF">CDF</option>

        <option value="CHF">CHF</option>

        <option value="CLP">CLP</option>

        <option value="CNY">CNY</option>

        <option value="COP">COP</option>

        <option value="CRC">CRC</option>

        <option value="CUP">CUP</option>

        <option value="CVE">CVE</option>

        <option value="CZK">CZK</option>

        <option value="DJF">DJF</option>

        <option value="DKK">DKK</option>

        <option value="DOP">DOP</option>

        <option value="DZD">DZD</option>

        <option value="EGP">EGP</option>

        <option value="ERN">ERN</option>

        <option value="ETB">ETB</option>

        <option value="EUR">EUR</option>

        <option value="FJD">FJD</option>

        <option value="FKP">FKP</option>

        <option value="GBP">GBP</option>

        <option value="GEL">GEL</option>

        <option value="GHS">GHS</option>

        <option value="GIP">GIP</option>

        <option value="GMD">GMD</option>

        <option value="GNF">GNF</option>

        <option value="GTQ">GTQ</option>

        <option value="GYD">GYD</option>

        <option value="HKD">HKD</option>

        <option value="HNL">HNL</option>

        <option value="HRK">HRK</option>

        <option value="HTG">HTG</option>

        <option value="HUF">HUF</option>

        <option value="IDR">IDR</option>

        <option value="ILS">ILS</option>

        <option value="INR">INR</option>

        <option value="IQD">IQD</option>

        <option value="IRR">IRR</option>

        <option value="ISK">ISK</option>

        <option value="JMD">JMD</option>

        <option value="JOD">JOD</option>

        <option value="JPY">JPY</option>

        <option value="KES">KES</option>

        <option value="KGS">KGS</option>

        <option value="KHR">KHR</option>

        <option value="KMF">KMF</option>

        <option value="KPW">KPW</option>

        <option value="KRW">KRW</option>

        <option value="KWD">KWD</option>

        <option value="KYD">KYD</option>

        <option value="KZT">KZT</option>

        <option value="LAK">LAK</option>

        <option value="LBP">LBP</option>

        <option value="LKR">LKR</option>

        <option value="LRD">LRD</option>

        <option value="LSL">LSL</option>

        <option value="LVL">LVL</option>

        <option value="LYD">LYD</option>

        <option value="MAD">MAD</option>

        <option value="MDL">MDL</option>

        <option value="MGA">MGA</option>

        <option value="MKD">MKD</option>

        <option value="MMK">MMK</option>

        <option value="MNT">MNT</option>

        <option value="MOP">MOP</option>

        <option value="MRO">MRO</option>

        <option value="MUR">MUR</option>

        <option value="MVR">MVR</option>

        <option value="MWK">MWK</option>

        <option value="MXN">MXN</option>

        <option value="MYR">MYR</option>

        <option value="MZN">MZN</option>

        <option value="NAD">NAD</option>

        <option value="NGN">NGN</option>

        <option value="NIO">NIO</option>

        <option value="NOK">NOK</option>

        <option value="NPR">NPR</option>

        <option value="NZD">NZD</option>

        <option value="OMR">OMR</option>

        <option value="PAB">PAB</option>

        <option value="PEN">PEN</option>

        <option value="PGK">PGK</option>

        <option value="PHP">PHP</option>

        <option value="PKR">PKR</option>

        <option value="PLN">PLN</option>

        <option value="PYG">PYG</option>

        <option value="QAR">QAR</option>

        <option value="RON">RON</option>

        <option value="RSD">RSD</option>

        <option value="RUB">RUB</option>

        <option value="RWF">RWF</option>

        <option value="SAR">SAR</option>

        <option value="SBD">SBD</option>

        <option value="SCR">SCR</option>

        <option value="SDG">SDG</option>

        <option value="SEK">SEK</option>

        <option value="SGD">SGD</option>

        <option value="SHP">SHP</option>

        <option value="SLL">SLL</option>

        <option value="SOS">SOS</option>

        <option value="SRD">SRD</option>

        <option value="STD">STD</option>

        <option value="SYP">SYP</option>

        <option value="SZL">SZL</option>

        <option value="THB">THB</option>

        <option value="TJS">TJS</option>

        <option value="TMT">TMT</option>

        <option value="TND">TND</option>

        <option value="TOP">TOP</option>

        <option value="TRY">TRY</option>

        <option value="TTD">TTD</option>

        <option value="TWD">TWD</option>

        <option value="TZS">TZS</option>

        <option value="UAH">UAH</option>

        <option value="UGX">UGX</option>

        <option value="USD" selected="">USD</option>

        <option value="UYU">UYU</option>

        <option value="UZS">UZS</option>

        <option value="VEF">VEF</option>

        <option value="VND">VND</option>

        <option value="VUV">VUV</option>

        <option value="WST">WST</option>

        <option value="XAF">XAF</option>

        <option value="XCD">XCD</option>

        <option value="XDR">XDR</option>

        <option value="XOF">XOF</option>

        <option value="XPF">XPF</option>

        <option value="YER">YER</option>

        <option value="ZAR">ZAR</option>

        <option value="ZMW">ZMW</option>

      </select>
    </div>
    <div class="medium-3 columns" style="text-align: center;">
      <span class="postfix">to</span>
    </div>
    <div class="medium-3 columns">
      <select id="CURR_TO" class="postfix">

        <option value="AED">AED</option>

        <option value="AFN">AFN</option>

        <option value="ALL">ALL</option>

        <option value="AMD">AMD</option>

        <option value="ANG">ANG</option>

        <option value="AOA">AOA</option>

        <option value="ARS">ARS</option>

        <option value="AUD">AUD</option>

        <option value="AWG">AWG</option>

        <option value="AZN">AZN</option>

        <option value="BAM">BAM</option>

        <option value="BBD">BBD</option>

        <option value="BDT">BDT</option>

        <option value="BGN">BGN</option>

        <option value="BHD">BHD</option>

        <option value="BIF">BIF</option>

        <option value="BND">BND</option>

        <option value="BOB">BOB</option>

        <option value="BRL">BRL</option>

        <option value="BSD">BSD</option>

        <option value="BTC">BTC</option>

        <option value="BTN">BTN</option>

        <option value="BWP">BWP</option>

        <option value="BYN">BYN</option>

        <option value="BYR">BYR</option>

        <option value="BZD">BZD</option>

        <option value="CAD">CAD</option>

        <option value="CDF">CDF</option>

        <option value="CHF">CHF</option>

        <option value="CLP">CLP</option>

        <option value="CNY">CNY</option>

        <option value="COP">COP</option>

        <option value="CRC">CRC</option>

        <option value="CUP">CUP</option>

        <option value="CVE">CVE</option>

        <option value="CZK">CZK</option>

        <option value="DJF">DJF</option>

        <option value="DKK">DKK</option>

        <option value="DOP">DOP</option>

        <option value="DZD">DZD</option>

        <option value="EGP">EGP</option>

        <option value="ERN">ERN</option>

        <option value="ETB">ETB</option>

        <option value="EUR">EUR</option>

        <option value="FJD">FJD</option>

        <option value="FKP">FKP</option>

        <option value="GBP">GBP</option>

        <option value="GEL">GEL</option>

        <option value="GHS">GHS</option>

        <option value="GIP">GIP</option>

        <option value="GMD">GMD</option>

        <option value="GNF">GNF</option>

        <option value="GTQ">GTQ</option>

        <option value="GYD">GYD</option>

        <option value="HKD">HKD</option>

        <option value="HNL">HNL</option>

        <option value="HRK">HRK</option>

        <option value="HTG">HTG</option>

        <option value="HUF">HUF</option>

        <option value="IDR">IDR</option>

        <option value="ILS">ILS</option>

        <option value="INR">INR</option>

        <option value="IQD">IQD</option>

        <option value="IRR">IRR</option>

        <option value="ISK">ISK</option>

        <option value="JMD">JMD</option>

        <option value="JOD">JOD</option>

        <option value="JPY">JPY</option>

        <option value="KES">KES</option>

        <option value="KGS">KGS</option>

        <option value="KHR">KHR</option>

        <option value="KMF">KMF</option>

        <option value="KPW">KPW</option>

        <option value="KRW">KRW</option>

        <option value="KWD">KWD</option>

        <option value="KYD">KYD</option>

        <option value="KZT">KZT</option>

        <option value="LAK">LAK</option>

        <option value="LBP">LBP</option>

        <option value="LKR">LKR</option>

        <option value="LRD">LRD</option>

        <option value="LSL">LSL</option>

        <option value="LVL">LVL</option>

        <option value="LYD">LYD</option>

        <option value="MAD">MAD</option>

        <option value="MDL">MDL</option>

        <option value="MGA">MGA</option>

        <option value="MKD">MKD</option>

        <option value="MMK">MMK</option>

        <option value="MNT">MNT</option>

        <option value="MOP">MOP</option>

        <option value="MRO">MRO</option>

        <option value="MUR">MUR</option>

        <option value="MVR">MVR</option>

        <option value="MWK">MWK</option>

        <option value="MXN">MXN</option>

        <option value="MYR">MYR</option>

        <option value="MZN">MZN</option>

        <option value="NAD">NAD</option>

        <option value="NGN">NGN</option>

        <option value="NIO">NIO</option>

        <option value="NOK">NOK</option>

        <option value="NPR">NPR</option>

        <option value="NZD">NZD</option>

        <option value="OMR">OMR</option>

        <option value="PAB">PAB</option>

        <option value="PEN">PEN</option>

        <option value="PGK">PGK</option>

        <option value="PHP" selected="">PHP</option>

        <option value="PKR">PKR</option>

        <option value="PLN">PLN</option>

        <option value="PYG">PYG</option>

        <option value="QAR">QAR</option>

        <option value="RON">RON</option>

        <option value="RSD">RSD</option>

        <option value="RUB">RUB</option>

        <option value="RWF">RWF</option>

        <option value="SAR">SAR</option>

        <option value="SBD">SBD</option>

        <option value="SCR">SCR</option>

        <option value="SDG">SDG</option>

        <option value="SEK">SEK</option>

        <option value="SGD">SGD</option>

        <option value="SHP">SHP</option>

        <option value="SLL">SLL</option>

        <option value="SOS">SOS</option>

        <option value="SRD">SRD</option>

        <option value="STD">STD</option>

        <option value="SYP">SYP</option>

        <option value="SZL">SZL</option>

        <option value="THB">THB</option>

        <option value="TJS">TJS</option>

        <option value="TMT">TMT</option>

        <option value="TND">TND</option>

        <option value="TOP">TOP</option>

        <option value="TRY">TRY</option>

        <option value="TTD">TTD</option>

        <option value="TWD">TWD</option>

        <option value="TZS">TZS</option>

        <option value="UAH">UAH</option>

        <option value="UGX">UGX</option>

        <option value="USD">USD</option>

        <option value="UYU">UYU</option>

        <option value="UZS">UZS</option>

        <option value="VEF">VEF</option>

        <option value="VND">VND</option>

        <option value="VUV">VUV</option>

        <option value="WST">WST</option>

        <option value="XAF">XAF</option>

        <option value="XCD">XCD</option>

        <option value="XDR">XDR</option>

        <option value="XOF">XOF</option>

        <option value="XPF">XPF</option>

        <option value="YER">YER</option>

        <option value="ZAR">ZAR</option>

        <option value="ZMW">ZMW</option>

      </select>
    </div>
  </div>
</div>

<script>
var addthis_share = {
    url: "https://free.currencyconverterapi.com"
}

function getCurrencyUsingJQuery() {
  var currVal = $("#CURR_VAL");
  currVal.val("");

  var currFrSelect = $("#CURR_FR");
  var fr = currFrSelect.val();

  var currToSelect = $("#CURR_TO");
  var to = currToSelect.val();


  var currId = fr + "_" + to;
  var protocol = window.location.protocol.replace(/:/g,'');

  currVal.attr("placeholder", "Converting...");
  $.getJSON(protocol + "://free.currencyconverterapi.com/api/v5/convert?q=" + currId + "&compact=y&callback=?",
    function(data){
      try {
       var currFrVal = parseFloat(document.getElementById("CURR_FR_VAL").value);
       currVal.val(numeral(currFrVal * data[currId].val).format("0,0.00[0]"));

     } catch (e) {
      alert("Please enter a number in the Amount field.");
    }

    currVal.attr("placeholder", "Press Convert button");

  });
  }
</script>


<div class="medium-3 columns">
<button onclick="getCurrencyUsingJQuery()" class="button postfix">Convert</button>
</div>

<div class="medium-3 columns">
<input type="text" id="CURR_VAL" readonly="" placeholder="Press Convert button" style="background-color: #eee; font-weight: bold;">
</div>
</div>

</body>
</html>
