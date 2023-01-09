# CurrencyConverter

<br>This Plugin is to convert all the Currencies on your Store according to  Customer location </br>


<h3>Step 1: Get API from Geo Location</h3>
 Go to https://app.ipgeolocation.io/ and SingUp with your account.
 After Sign In you can the API as Shown below.
 
![tempsnip](https://user-images.githubusercontent.com/121421319/210345543-fc5a4ff8-2cfa-424c-9638-36e3b59c8e7a.png)

 <h3>Step 2 : Wrap you Currency Amouunt Tag Class</h3>
 
 Before
 <code>$78,000</code>
 
 After 
 <code>
/* <span class="money"> $78,000 </span>*/
</code>
 
 <h3>Step 3 : Paste This Javascript Code Before Closing Body Tag</h3>
 
 <code>
 <script src="https://cdn.jsdelivr.net/npm/ip-geolocation-api-jquery-sdk@1.1.0/ipgeolocation.min.js"></script>
<script src="https://cdn.shopify.com/s/javascripts/currencies.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>

<script>
  function setCookie(key, value, expiry) {
    var expires = new Date();
    expires.setTime(expires.getTime() + (expiry * 24 * 60 * 60 * 1000));
    document.cookie = key + '=' + value + ';expires=' + expires.toUTCString() + ';path=/';
  }

  function setLocalCurrency(response) {

    if (response) {
      setCookie('cart_currency', response.currency.code, '1');
      console.log(response.ip);
        
        $('.money').each(function(index, el) {
        var Val = (parseInt(Currency.convert( parseInt(this.innerHTML.replace('$','')) ,'USD',response.currency.code))).toLocaleString();
        $(el).html(response.currency.symbol+''+Val);
        });

    }
  }

  _ipgeolocation.makeAsyncCallsToAPI(false);
  _ipgeolocation.enableSessionStorage(true);
  _ipgeolocation.setFields("currency");
  _ipgeolocation.getGeolocation(setLocalCurrency, "YOUR_API_HERE");
</script>
 </code>
 
 <h4> Thats All Happy Javascripting</h4>
 
 
 <h3>Note</h3>
 <p>
 In My Case default Currency in USD you can Change the USD and $ Sign with your default currency.
 </p>
 
