var cookieWall = (function() {
  let _wall = {
    pageHtml: document.getElementsByTagName('HTML')[0],
    wrapper: document.querySelector('.cookiewall'),
    /* consent: '#cookieWallConsentButton',
    noConsent: '#cookieWallNoConsentButton',
    moreInfo : '#cookieWallMoreInfoButton',
    back : '#cookieWallBackButton',
    close: '#cookieWallCloseButton', */
    activeClass: 'is-cookiewall-open',
    frame2ActiveClass: 'is-cookiewall-frame2-active'
  }

  function _init(frame) {
    _wall.wrapper = document.querySelector('.cookiewall');
    if (frame && frame === 'frame-2') {
      var backBtn = _wall.wrapper.querySelector('.cookiewall__button-back');
      _wall.wrapper.classList.add(_wall.frame2ActiveClass);
    }
    _disablePageScroll();
    _onClick();
    _checkUser();
    /* if (!_isMobile()) {
      _openDetailsSummary();
    } */
  }

  function _close() {
    _wall.pageHtml.classList.remove(_wall.activeClass);
    _wall.wrapper.remove();
  }

  function _onClick() {
    _wall.wrapper.addEventListener('click', function (e) {
      let action = e.target.dataset.action;
      if (action) {
        switch (action) {
          case "back":
            _wall.wrapper.classList.remove(_wall.frame2ActiveClass);
            break;
          case "forward":
            e.preventDefault();
            if (window.kw_tlh_activeBrand && window.kw_tlh_activeBrand.length > 0 && window.kw_tlh_activeBrand.indexOf("repubblica") > -1 && e.target.nodeName.toLowerCase() === "a") {
                window.location = e.target.getAttribute("href");
            } else {
                _wall.wrapper.classList.add(_wall.frame2ActiveClass);
            }
            break;
          case "close":
            _close();
            break;
          case "login":
            GediSocial.interface.ssoLogin();
            break;
          case "logout":
            GediSocial.interface.logout();
          break;
          case "adv-settings":
            _iub.cs.ui.showCP(!1, true);
          break;
          case "vendor-iab":
            _iub.cs.api.showTcfVendors();
          break;
        }
      }
    })
  }


  function _checkUser(){
    let cookieWallLogin = document.querySelector('.cookiewall__login');
    if (cookieWallLogin && window.kwloggeduser === true) {
       cookieWallLogin.innerHTML='Sei già abbonato? <button data-action="logout">ESCI</button>';
    }
  }

  function _disablePageScroll() {
    console.log("disablePageScroll");
    _wall.pageHtml.classList.add(_wall.activeClass);
  }

  /* function _isMobile() {
    let test = window.matchMedia('(max-width: 767px)').matches ? true : false;
    return test;
  } */

  return {
    init: _init,
    close: _close
  }
}
)()