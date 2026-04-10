(function(){
	
	var data = window.kwait || [];
	if(data.call) return;
	
	var init = {};
	var events = {};
	
	var trigger = function(args){
		if(!(args instanceof Array) || args.length == 0) return;
		var f1 = args[0]; var args = args.slice(1);
		try {
			if(!(f1 instanceof Function)) f1 = eval(f1);
			f1.apply(window, args);
		} catch(e){console.error(e)};
	}
	// wait and call
	var kwait = {};
	kwait.push = function(arr){
		if(!arr || !arr[0] || !arr[1]) return;
		var event = arr[0];
		if(event.constructor===Array){
			if(event.length<2) event = event[0];
			else {
				kwait.push([arr[0][0], function(){
					kwait.push([arr[0].slice(1)].concat(arr.slice(1)));
				}]); return;
			}
		} 
		else if(event == "call"){ event = "kwait"; arr.splice(1,0,"kwait.call"); }
		else if(event == "timeout"){ event = "kwait"; arr.splice(1,0,"kwait.timeout"); }
		
		var args = arr.slice(1);
		if(event && !init[event]){
			if(!events[event]) events[event] = [];
			events[event].push(args);
		} else {
			trigger(args);
		}
	}
	
	kwait.call = function(name){
		init[name] = true;
		var evs = events[name]
		if(evs && (evs instanceof Array) ){
			for(var i=0;i<evs.length; i++){
				var args = evs[i];
				trigger(args);
			}
			delete events[name];
		}
	}
	
	kwait.timeout = function(name, timeout){
		if(name) setTimeout(function(){
			if(!init[name]) kwait.call(name);
		}, timeout);
	}
	
	window.kwait = kwait;
	for(var i=0;i<data.length;i++){
		kwait.push(data[i]);
	}
	kwait.cache = data.cache || {};
	kwait.deps = data.deps || {};
	kwait.init = init;
	
	// compatibility
	if(!window.RenderAsync){
		window.RenderAsync = kwait;
	}
	kwait.call("kwait");
	
})();