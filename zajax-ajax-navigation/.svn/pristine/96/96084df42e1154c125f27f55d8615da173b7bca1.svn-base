// http://www.deluxeblogtips.com/2010/05/how-to-ajaxify-wordpress-theme.html

//Nprogress
(function(f,h){"function"===typeof define&&define.amd?define(h):"object"===typeof exports?module.exports=h():f.NProgress=h()})(this,function(){function f(a,b,d){return a<b?b:a>d?d:a}function h(a,b,d){a="translate3d"===e.positionUsing?{transform:"translate3d("+100*(-1+a)+"%,0,0)"}:"translate"===e.positionUsing?{transform:"translate("+100*(-1+a)+"%,0)"}:{"margin-left":100*(-1+a)+"%"};a.transition="all "+b+"ms "+d;return a}function p(a,b){return 0<=("string"==typeof a?a:m(a)).indexOf(" "+b+" ")}function q(a,
b){var d=m(a),c=d+b;p(d,b)||(a.className=c.substring(1))}function r(a,b){var d=m(a);p(a,b)&&(d=d.replace(" "+b+" "," "),a.className=d.substring(1,d.length-1))}function m(a){return(" "+(a.className||"")+" ").replace(/\s+/gi," ")}var c={version:"0.1.6"},e=c.settings={minimum:.08,easing:"ease",positionUsing:"",speed:200,trickle:!0,trickleRate:.02,trickleSpeed:800,showSpinner:!0,barSelector:'[role="bar"]',spinnerSelector:'[role="spinner"]',parent:"body",template:'<div class="bar" role="bar"><div class="peg"></div></div><div class="spinner" role="spinner"><div class="spinner-icon"></div></div>'};
c.configure=function(a){var b,d;for(b in a)d=a[b],void 0!==d&&a.hasOwnProperty(b)&&(e[b]=d);return this};c.status=null;c.set=function(a){var b=c.isStarted();a=f(a,e.minimum,1);c.status=1===a?null:a;var d=c.render(!b),n=d.querySelector(e.barSelector),k=e.speed,v=e.easing;d.offsetWidth;w(function(b){""===e.positionUsing&&(e.positionUsing=c.getPositioningCSS());l(n,h(a,k,v));1===a?(l(d,{transition:"none",opacity:1}),d.offsetWidth,setTimeout(function(){l(d,{transition:"all "+k+"ms linear",opacity:0});
setTimeout(function(){c.remove();b()},k)},k)):setTimeout(b,k)});return this};c.isStarted=function(){return"number"===typeof c.status};c.start=function(){c.status||c.set(0);var a=function(){setTimeout(function(){c.status&&(c.trickle(),a())},e.trickleSpeed)};e.trickle&&a();return this};c.done=function(a){return a||c.status?c.inc(.3+.5*Math.random()).set(1):this};c.inc=function(a){var b=c.status;return b?("number"!==typeof a&&(a=(1-b)*f(Math.random()*b,.1,.95)),b=f(b+a,0,.994),c.set(b)):c.start()};c.trickle=
function(){return c.inc(Math.random()*e.trickleRate)};(function(){var a=0,b=0;c.promise=function(d){if(!d||"resolved"==d.state())return this;0==b&&c.start();a++;b++;d.always(function(){b--;0==b?(a=0,c.done()):c.set((a-b)/a)});return this}})();c.render=function(a){if(c.isRendered())return document.getElementById("nprogress");q(document.documentElement,"nprogress-busy");var b=document.createElement("div");b.id="nprogress";b.innerHTML=e.template;var d=b.querySelector(e.barSelector),n=a?"-100":100*(-1+
(c.status||0));a=document.querySelector(e.parent);l(d,{transition:"all 0 linear",transform:"translate3d("+n+"%,0,0)"});e.showSpinner||(d=b.querySelector(e.spinnerSelector))&&d&&d.parentNode&&d.parentNode.removeChild(d);a!=document.body&&q(a,"nprogress-custom-parent");a.appendChild(b);return b};c.remove=function(){r(document.documentElement,"nprogress-busy");r(document.querySelector(e.parent),"nprogress-custom-parent");var a=document.getElementById("nprogress");a&&a&&a.parentNode&&a.parentNode.removeChild(a)};
c.isRendered=function(){return!!document.getElementById("nprogress")};c.getPositioningCSS=function(){var a=document.body.style,b="WebkitTransform"in a?"Webkit":"MozTransform"in a?"Moz":"msTransform"in a?"ms":"OTransform"in a?"O":"";return b+"Perspective"in a?"translate3d":b+"Transform"in a?"translate":"margin"};var w=function(){function a(){var d=b.shift();d&&d(a)}var b=[];return function(d){b.push(d);1==b.length&&a()}}(),l=function(){function a(a){return a.replace(/^-ms-/,"ms-").replace(/-([\da-z])/gi,
function(a,b){return b.toUpperCase()})}function b(b){b=a(b);var e;if(!(e=c[b])){e=b;a:{var t=document.body.style;if(!(b in t))for(var u=d.length,f=b.charAt(0).toUpperCase()+b.slice(1),g;u--;)if(g=d[u]+f,g in t){b=g;break a}}e=c[e]=b}return e}var d=["Webkit","O","Moz","ms"],c={};return function(a,d){var c=arguments,e,f;if(2==c.length)for(e in d){if(f=d[e],void 0!==f&&d.hasOwnProperty(e)){var c=a,g=e,g=b(g);c.style[g]=f}}else e=a,g=c[1],c=c[2],g=b(g),e.style[g]=c}}();return c});


/*zajax*/
(function($) {
//jQuery(document).ready(function($){
	
	var ismobile = (/android|webos|iphone|ipad|ipod|blackberry|bb|playbook|iemobile|windows phone|kindle|silk|opera mini/i.test(navigator.userAgent.toLowerCase()));

	if(ismobile) FastClick.attach(document.body);
	
	if ( typeof $.fn.imagesLoaded === "function") {
		console.log('imagesLoaded exist');
		var FNimagesLoaded = true;
	}
	if ( typeof $.fn.masonry === "function" ) {
		console.log('masonry exist');
		var FNmasonry = true;
	}
	
	if(zajax_data['zajax_back'] == 1)
	$("body").prepend('<span class="zaback"><div></div></span>');

	$(document).on("click", ".zaback", function(){
		window.history.back();
	});

	NProgress.configure({ ease: 'ease', speed: 300, minimum: 0.02, trickleRate: 0.2, trickleSpeed: 175 });
	
	var 
	getmasonry = zajax_data['zajax_masonry'],
	getignore = zajax_data['zajax_ignore'],
	doList = zajax_data['zajax_dolist'],
	getsearch = zajax_data['zajax_search'];
	
	if(getignore) getignore = ','+$.trim(getignore); //','+getignore.trim();
	else getignore = '';
	
	//var ignoreList = "zajax.js,podzic.js,nprogress.js,send_complete.js,jquery.jplayer.min.js,jplayer.playlist.min.js"+getignore;
	var ignoreList = "zajax.js"+getignore;
	ignoreList = ignoreList.replace(/,/g , "|").replace(/ /g,'');

	if(doList && doList !== undefined && doList !== null){
		doList = $.trim(doList);
		doList = doList.replace(/,/g , "|").replace(/ /g,'');
	}else {
		doList = '';
	}
	
	var 
		zajax_started = false,
		loadbody = 0,
		hoverUrl,
		$ishover = false,
		$hoverdata,
		lastHover,
		lastUrl,
		$preloadUrl,
		thisHashID = '',
		$isPreloading = false,
		zajax_preload;
		
		if(zajax_data['zajax_body'] == 1) loadbody = 1;
		
		if(zajax_data['zajax_preload'] == 1) zajax_preload = 1 ;
	
	/* Get all IDs and Class to ajaxify */
	
	var searchformID = getsearch;
	
	/* Get all IDs and Class to ajaxify */
	var getIDClass = $.trim(zajax_data['zajax_ClassID']);
	
	//if(getIDClass === "") getIDClass = '';
	if(getIDClass) getIDClass = ','+getIDClass;
	
	/*
	if(ismobile) $mainContent = zajax_data['zajax_main_mobile'];
	else $mainContent = zajax_data['zajax_main'];
	*/
	$mainContent = zajax_data['zajax_main'];

	
	// GC NEW, check Multiple main ID or Class for Desktop or mobile
	$mainContent = $mainContent+',';
	
	$.each($mainContent.split(",").slice(0,-1), function(index, item) {
		//alert(item); 
		if($(item).length !== 0) {
		  //it do exist
		  $mainContent = item;
		  return false ;
		}
		
	});

	if(ismobile) $mainContent = zajax_data['zajax_main_mobile'];
	else $mainContent = zajax_data['zajax_main'];
	
	if(!$mainContent || $mainContent === undefined) $mainContent = zajax_data['zajax_main'];
	
	$mainContent = $.trim($mainContent);
		
	var IDClass = $mainContent+getIDClass;

	
	$($mainContent).addClass("zajax-transition");

	if($("#zajax").length == 0 && loadbody == 1) {
	  $('body').wrapInner('<div id="zajax" />');
	  //$('body').addClass(newClass);
	  //$('body').attr('id', 'zajax');
	}

	if(loadbody == 1) {
	  var IDClass = '#zajax';	  
	}
	//alert(IDClass);
	
	//var IDClass = 'head,footer,#content,#topside';
	var IDClass_arr = IDClass.split(',');
	/************************************/
	
	//var siteUrl = location.origin.toString(),
	var siteUrl = location.origin,
	url = '',
	href = "a[href^='"+siteUrl+"']:not(a[href*='/wp-']):not([href$='/feed'])";
	
	var timer; 
	var delay=100;

	var time=0; //time in milliseconds 

	$(document).on("mouseover", href, function() {

		if(ismobile || zajax_preload !== 1 ) return ;
		
		url = this.href;
		
		time = new Date(); //time in milliseconds
		
		timer = setTimeout(function(){
			
			if(url != window.location && url != lastHover ){
				zajax_url(url, true);
			}
			lastHover = url;
			checklastHover(lastHover); 
		}, delay);
		//}, 
		//lastHover = url;
		//console.log(lastHover);

		
	}).mouseout(function(){ //.on("mouseout", function(){
    	//clearTimeout(timer);
		if(ismobile || zajax_preload !== 1 ) return ;
		
		if (timer != null) clearTimeout(timer);
		
		//$hoverdata = '';
		
		if (!$isPreloading) return ;
		//$zajax.abort();		
		$isPreloading = false ;
		
		lastHover = url;
		//console.log(lastHover);
	}).on("click", href, function() {
		
		if (timer != null) clearTimeout(timer);
		
		var diff=new Date() - time;
		console.log(diff);
		time=0;
		
		//window.clearTimeout(timer);
		//e.preventDefault();
		
		url = this.href;
		//alert(url);
		
		this.blur();
		
		if(url.indexOf('#') === -1)
		{
			$('html,body').animate({scrollTop: 0}, 500);
		}else{
			
			var urlnohash = url.slice(0, url.indexOf("#"));
			//alert(urlnohash+' '+window.location);
			
			if(window.location == urlnohash || window.location == url){
				
				thisHashID = '#'+url.split('#')[1] ;
				$('html,body').animate({ scrollTop: $(thisHashID).offset().top-100},700);
				//location.replace(url);
				window.history.pushState(null, null, url);
				url = '';	
				//alert(url);			
			}
			
			//return
			//function later if same url
		}

		//location.hash = this.pathname;
				//to change the browser URL to 'pageurl'
		if(url!=window.location && url ){
			window.history.pushState({path:url},'',url);
			zajax_url(url, false);	
			//alert(url.split('#')[0]);
		}
		
		return false;
	}); 

	
	$(document).on('submit','form',function(e){

		var thisSubmit = $(this);
		
		var thisID = thisSubmit.attr('id');
        var thisClass = '.' + thisSubmit.attr('class');

        //alert(thisID+" "+thisClass);
        if (thisID) var eClassID = '#' + thisID;
        else var eClassID = thisClass;
		var ThisSerialize = thisSubmit.serialize();

		if (searchformID.indexOf(eClassID) >= 0){

            var $input = $(this).find('input[type="search"]').val();

            if (typeof $input === "undefined") {
                $input = $(this).find('input[type="text"]').val();
            }
            var thisSearch = siteUrl+'?s=' + $input;

			window.history.pushState({path:thisSearch},'',thisSearch);
			zajax_url(thisSearch, false);
			$('html,body').animate({scrollTop: 0}, 500);
		}else{
			NProgress.start();

			$(eClassID).append('<span class="submitLoading">Please wait...</span>');
			//var documentURL = document.URL ;
			
			$.ajax({
				url: thisSubmit.attr('action'),
				type: thisSubmit.attr('method'),
				data: ThisSerialize,
				success: function (a) {
					$('.submitLoading').remove();
					$(eClassID).append('<div class="m_success alert alert-success" style="margin:10px"><span class="close" data-dismiss="alert"></span><strong>Success!</strong>  You successfully submit the form.</div>');

					zajax_url(window.location, false);
					
					$('.submitLoading').remove();
					$(".m_success").show().delay(3000).fadeOut(1000);
					setTimeout(function () {
						$('.m_success').remove();
					}, 4000)
				},
				error: function () {
					NProgress.done();
					$(eClassID).append('<div class="m_error alert alert-error"><span class="close" style="margin:10px" data-dismiss="alert"></span><strong>Error!</strong>  Failed to submit.</div>');
					$(".m_error").show().delay(3000).fadeOut(1000);
					setTimeout(function () {
						$('.submitLoading').remove();
						$('.m_error').remove()
					}, 4000)
				}
			})
		}

        thisSubmit.find('input[type=text],input[type=search]').blur().val('');

	  //alert(parentFormID);
	  //alert($(this).attr('class'));
	  
	  	e.preventDefault();
	});
	
	
	
    window.onpopstate = function(event) {
        if (zajax_started === true) {
        zajax_url(document.location, false);
        //zajax_url(document.location.toString(),1, false);
        }
    };

function checklastHover(response) {  
	lastHover = response;  
}

window.zajax_url = function(url, $ishover){
//function zajax_url(url, $ishover){

    if (!url) return;

    //enable onpopstate after first page load
    zajax_started = true;

    if($ishover === false){
        zajax_send(); // jQuery codes from admin panel
        NProgress.start();
        $($mainContent).addClass('zajax-opacity'); // if load all body option: $mainContent = 'body' ?
    }

    if(hoverUrl === url && $ishover === false){

        if ($hoverdata && (url == $preloadUrl)) { // if ($hoverdata && (url == $preloadUrl)) {
        //if($hoverdata){
            zajax_parse($hoverdata, $ishover);
        }else{

            var promise = $zajax;
            zajax_displayData(promise);

        }

    /*
        $.when(zajax_call()).then(function (resp) {
            zajax_parse($hoverdata, $ishover);
        });

    */
        //zajax_parse($hoverdata, $ishover);
        //hoverUrl = '';
        $ishover = false;
        return;

    }

    if($ishover === true) hoverUrl = url;

    zajax_call(url, $ishover);
	
};

window.zajax_goto = function($url){

    if($url!=window.location && $url ){
        window.history.pushState({path:$url},'',$url);
        zajax_url($url, false);
        //$url = '';
    }
};
    // HOW TO USE ZAJAX_GOTO
    /*
    $(document).on("click", "#target", function(){
        zajax_goto('http://www.exemple.com/page.php');
    });
    */

function zajax_call(url, $ishover) {
	
	$isPreloading = true;
		
	return $zajax = $.ajax({
	  type: "GET",
	  url: url,
	  dataType: "html"
	  //async:   false
	})
	.done(function(data, Status, jqXHR) {
	
		//if(Status=='error')alert(Status); // should be always or error to get status
	
		console.log('ajax preload');
		
		if(loadbody == 1) {
            var body = data.replace('<body', '<body><div id="zajax"').replace('</body>','</div></body>');
			var $data = $(body);
		  //alert('zajax');
		}else{
			var $data = $(data);
		}
		
		$hoverdata = $data;
		$preloadUrl = url;
	
		$isPreloading = false;

		if($ishover === false){			
			zajax_parse($data, $ishover);
		}
	
	})
	.fail(function() {
		
		//alert( "Error loading page");
		NProgress.done();
	
		$($mainContent).removeClass('zajax-opacity').html('<h2 style="text-align: center;margin:50px 0;">Error loading page<\h2>');
		
		//$isPreloading = false;
	})
	.always(function() {
	
		//zajax_loadjs();
	
	}); // Ajax end

}

function zajax_displayData(x) {
    x.done(function(data) {		
		$waitdata = $(data);
		zajax_parse($waitdata, $ishover);
    });
}

function zajax_parse($data, $ishover){
	
	//console.log($data);
	hoverUrl = '';
	$ishover = false;

	$title = $data.filter('title').text();
	//alert($title);		
	document.title = $title;
	
	//var getClass = $data.filter($mainContent).attr("class");
	//alert(getClass);
	
	//var getClass = '';

	//var zajax_debug = true;
	
	var getData = $data.html();
	
	for (var a in IDClass_arr){
		var el = $.trim(IDClass_arr[a]);
		//alert(el);		
		$datael = $data.find(el);
		if($datael.html()== undefined )
		$datael = $data.filter(el);

	   $(el).html($datael.html());
	}
	
	$hoverdata = '';
		
	zajax_loadjs();
	
	if(doList && doList !== undefined && doList !== null)
	zajax_loadjsHead();
	
	NProgress.done();
	//alert('done');	
	
	$($mainContent).removeClass("zajax-opacity").addClass('zajax-transition');
	//$($mainContent).removeClass('zajax-opacity');	
	
	zajax_complete(); // jQuery codes from admin panel

	// reload masonry and us imagesLoaded if exist
	if ( FNimagesLoaded && FNmasonry) { // pure javascript
	//if ( $.isFunction($.fn.imagesLoaded) && $.isFunction($.fn.masonry) ) {
		console.log('imagesLoaded exist');
		$(getmasonry).imagesLoaded()
			.done(function (instance) {
			console.log('all images loaded');
			$(getmasonry).masonry();
		})
	} else if ( !FNimagesLoaded && FNmasonry) {
		//alert('Masonry exist');
		$(getmasonry).masonry();
		//$(getmasonry).masonry( 'reload' );
		//$(getmasonry).masonry( 'reloadItems' );
		//window.dispatchEvent(new Event('resize')); // fake resize test
	}

}

function zajax_loadjsHead() {
	
	document.head = document.head || document.getElementsByTagName('head')[0];
	
    var scripts = document.head.getElementsByTagName('script'),
        script,
        copy,
        parentNode,
        nextSibling,
		i = 0;

    for (i = 0, j = scripts.length; i < j; i++) {
        script = scripts[i];
		//console.log('FOREACH DO LIST '+doList);
		
        if (script.src.match(doList)) {
            //console.log(script.src.match(ignoreList));
			copy = document.createElement('script');
			if (script.src) {
				copy.src = script.src
				//console.log(script);
			}
			
			parentNode = script.parentNode;
			nextSibling = script.nextSibling;
			parentNode.removeChild(script);
			parentNode.insertBefore(copy, nextSibling);
			
        }
		
        //console.log(script.src);

        /*
		if (script.innerHTML) {
            copy.innerHTML = script.innerHTML
        }
		*/

    }

}

function zajax_loadjs() {

    //var scripts = $data.filter('script[src]'); //script[src]

    var scripts = document.body.getElementsByTagName('script'),
        script,
        copy,
        parentNode,
        nextSibling,
		i = 0;

    for (i = 0, j = scripts.length; i < j; i++) {
        script = scripts[i]      

        if (script.src.match(ignoreList)) {
            //console.log(script.src.match(ignoreList));
            continue
        }
		
        //console.log(script.src);
        copy = document.createElement('script');
        if (script.src) {
            copy.src = script.src
        }		

        /*
		if (script.innerHTML) {
            copy.innerHTML = script.innerHTML
        }
*/
        parentNode = script.parentNode;
        nextSibling = script.nextSibling;
        parentNode.removeChild(script);
        parentNode.insertBefore(copy, nextSibling);

    }


    if (window.location.hash) {
        //if(document.URL.indexOf('#') !== -1) {

        thisHashID = '#' + window.location.hash.split('#')[1];
        $('html,body').animate({
            scrollTop: $(thisHashID).offset().top - 100
        }, 700);
        thisHashID = '';
    }
	/*
	if (hasGoogleAnalytics()) {
		ga('send', 'pageview', {
			'page': location.pathname + location.search + location.hash,
			'title': document.title
		});
		//console.log($(document).find("title").text());
		//console.log(document.title);
		//console.log(location.pathname + location.search + location.hash);
	}
	*/
}
/*
function hasGoogleAnalytics(){
    var scripts = document.getElementsByTagName('script'),
        ga = true, ua = true, dc = true,
        i, len, s;
    
    len = scripts.length;
 
    if (ga || ua || dc) {
        for (i = 0; i < len; i += 1) {
            s = scripts[i].src;
 
            if (
                (ga && s.indexOf('google-analytics.com/ga.js')>-1) ||
                
                (ua && s.indexOf('google-analytics.com/analytics.js')>-1) ||
                
                (dc && s.indexOf('doubleclick.net/dc.js')>-1)
            ) {
                return true;
            }
        }
    }
    return false;
}
*/
	
})(jQuery);