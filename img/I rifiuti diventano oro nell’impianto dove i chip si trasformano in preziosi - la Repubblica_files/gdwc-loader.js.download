(function () {

  //console.log('WC-LOADER-<<<<<<<<<<<<<<<<<<<<<<<< INIT')
  // detect IE11 or Edge
  var ua = window.navigator.userAgent;
  var isIe = ua.indexOf('Trident/');
  var isEdge = ua.indexOf('Edge/');

  var polyfillScript = document.createElement('script');

  if (isIe > 0 || isEdge > 0) {
    polyfillScript.src = 'https://webcomponent.gedidigital.it/ajax/libs/webcomponentsjs/2.4.3/webcomponents-bundle.js';
  } else {
    polyfillScript.src = 'https://webcomponent.gedidigital.it/ajax/libs/webcomponentsjs/2.4.3/webcomponents-loader.js';
  }

  polyfillScript.async = true;
  document.head.appendChild(polyfillScript);
  //document.body.appendChild(polyfillScript);
  polyfillScript.onload = function () {


    //console.warn('onload<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<', window.gdwc.length);

    window.gdwc.forEach(function (element) {

      if (location.href.indexOf('test-new-audioplayer') != -1) {
        env = "https://webcomponent.gedidigital.it/v2/gdwc-audio-player/";
      } else {
        var env = "https://webcomponent.gedidigital.it/" + element.name + "/public/";
      }


      if (element.name === 'gdwc-calendar') {
        var env = env = "https://webcomponent.gedidigital.it/" + element.name + '-v2' + "/public/";
      }


      try {
        var component = document.createElement("script");
        // component.language = "javascript";
        // console.log('tryzzzz<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<', component)
        // component.type = "text/javascript";
        component.async = true;
        component.setAttribute('name', element.name);
        component.src = env + element.name + '.js';
        var scriptComponent = document.querySelector("script[name=" + element.name + "]");
        if (!scriptComponent) {
          document.head.appendChild(component);
          // document.body.appendChild(component);
        } else {
          //console.log('<<<<< gia appeso')
        }
      } catch (err) {
        console.log("error caught", err);
      }
    });
  };
})();