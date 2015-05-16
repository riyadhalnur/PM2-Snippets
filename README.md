# PM2-Snippets for Sublime Text 2/3  

PM2 (the process manager) snippets for Sublime Text    

In order to use the snippets, just enter the shortcode and press the <kbd>Tab</kbd> (or whatever you have set as completion key) to use the snippets.  

Included are all snippets listed below. $1, $2, etc. show the position where the caret will appear whenever you press the tab key inside the snippet.  

You're free to alter the snippets in any way imaginable.  

---  

### pm2-json (works on .json files only)  
```json  
[{
  "script"    : "${1:server.js}",
  "name"      : "${2:node-app}",
  "exec_mode" : "${3:cluster}",
  "instances" : ${4:-1}  // number of CPUs -1
}, {
  "script"    : "${5:worker.js}",
  "name"      : "${6:worker}",
  "exec_mode" : "${7:fork}",
  "watch"     : ${0:true},  // auto restart app on change,
  "env"            : {  // common env variables
    "INTERVAL" : 1000
  },
  "env_production" : {  // Used if --env prod
    "INTERVAL" : 60000
  }
}]  
```  

Default shortcode is `[{`  

### pm2-js (works on .js files only)  
```js  
var pm2 = require('pm2');

pm2.connect(function(err) {
  pm2.start('${1:server.js}', { name: '${2:my-app}' }, function(err, proc) {
    if (err) { throw new Error('There was a problem starting your application ' + err); }

    pm2.list(function(err, process_list) {
      if (err) { throw new Error('There was a problem listing your applications ' + err); }
      console.log(process_list);
    });
  });
});  
```  

Default shortcode is `pm2`  

Made with love in Dhaka, Bangladesh by [Riyadh Al Nur](https://twitter.com/riyadhalnur)
