---
layout: post
title: test
---

### test

<script>
	if (/bz_tracking_id/.test(location.search)) { localStorage.BuzzAd = location.search }

	(function (img) { img.onload = function () {
		var length = localStorage.BuzzAd.length;
    		if(localStorage.BuzzAd.indexOf('10023_71ffbffd-ccf1-4edf-9c4c') != -1){
        	alert("[Success] Action Completed!");
    	};

	};
	if (localStorage.BuzzAd == null) { localStorage.BuzzAd = ""; }
	img.src = "//track.buzzvil.com/action/pb/cpa/default/pixel.gif" + localStorage.BuzzAd; }) (new Image())
</script>
