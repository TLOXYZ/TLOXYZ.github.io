---
layout: default
title: Get My IP
---

<p style="margin-bottom: 0;">IPv4 Address</p>

<textarea rows="1" id="ipv4" readonly="readonly" style="font-size: 20px" placeholder="Loading…"></textarea>

<p style="margin-bottom: 0;">IPv4 Country Code</p>

<textarea rows="1" id="ipv4country" readonly="readonly" style="font-size: 20px" placeholder="Loading…"></textarea>

<hr />

<p id="checkingipv6">Detecting IPv6 Network…</p>

<div id="ipv6area" style="display: none;">

<p style="margin-bottom: 0;">IPv6 Address</p>

<textarea rows="1" id="ipv6" readonly="readonly" style="font-size: 20px"></textarea>

<p style="margin-bottom: 0;">IPv6 Country Code</p>

<textarea rows="1" id="ipv6country" readonly="readonly" style="font-size: 20px"></textarea>

</div>

<div id="noipv6" style="display: none;">

<p>Not support IPv6, no IPv6 address can be found.</p>

</div>

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
	ipv4 = response.ip;
	$("#ipv4").text(response.ip);
	$("#ipv4country").text(response.country);
}).fail(function(error){
	console.log(error.statusText);
});

$.ajax({
	type: 'GET',
	url: 'https://ipv6-api.tlo.xyz/myip/jsonp.php',
	dataType: 'jsonp',
	crossDomain: true,
	timeout: 10000
}).done(function(response){
	$("#checkingipv6").hide();
	$("#noipv6").hide();
	$("#ipv6area").show();
	$("#ipv6").text(response.ip);
	$("#ipv6country").text(response.country);
}).fail(function(error){
	$("#checkingipv6").text(error.statusText);
	$("#noipv6").show();
});
</script>
