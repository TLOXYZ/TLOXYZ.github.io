---
layout: default
title: Get My IP
---

<p style="margin-bottom: 0;">IP Address</p>

<textarea rows="1" id="ip" readonly="readonly" style="font-size: 20px" placeholder="Loading…"></textarea>

<p style="margin-bottom: 0;">IP Country Code</p>

<textarea rows="1" id="ipcountry" readonly="readonly" style="font-size: 20px" placeholder="Loading…"></textarea>

<hr />

This is a static page, using free [apiTLO](https://git.tlo.xyz/TLOxyz/API/wikis/my-ip#jsonp-api)

<script>
$.ajax({
	type: 'GET',
	url: 'https://api.tlo.xyz/myip/jsonp.php',
	dataType: 'jsonp',
	crossDomain: true,
	timeout: 10000
}).done(function(response){
	$("#ip").text(response.ip);
	$("#ipcountry").text(response.country);
}).fail(function(error){
	console.log(error.statusText);
	$("#ip").text(error.statusText);
});
</script>
