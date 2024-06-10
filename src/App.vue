<script setup>
import { defineModel, ref } from 'vue';
import { DATAMatrix } from "./components/datamatrix-svg.vue";
    

    var mdata = defineModel('data');
    var hod = defineModel('height');
    var rctCh = defineModel('rectangle');
    var padCh = defineModel('padding');
    var faceCh = defineModel('facecolor');
    var bgCh = defineModel('bgcolor');
    var opCh = defineModel('opaque');


</script>

<template>
  <header>

  </header>

  <main>
   
  </main>
  <div id="box" v-html="DATAMatrix({msg:mdata,dim:hod,rct:rctCh,pad:padCh,pal:[faceCh,opCh]}).outerHTML"></div>

<div id="set">

<a id="op1" class="opt" href="#">Show settings</a>
<a id="op2" class="opt" href="#">Hide settings</a>

<div class="legend">

	<h3>DATAMATRIX SETTINGS</h3>

</div>

<table><tr><th>

<label for="in1">Height or Dim</label></th><td><input
	id="in1" type="number" value="256" min="256" max="61440" step="64"
  v-model="hod" placeholder=256 /></td></tr><tr><th>

<label for="in2">Rectangle</label></th><td><input
	id="in2" type="checkbox"
  v-model="rctCh" v-bind:true-value="1" v-bind:false-value="0" placeholder=0 /></td></tr><tr><th>

<label for="in3">Padding</label></th><td><input
	id="in3" type="number" value="2" min="0" max="10"
  v-model="padCh" placeholder=2 /></td></tr><tr><th>

<label for="in4">Faces</label></th><td><input
	id="in4" type="color"
  v-model="faceCh"  placeholder="#000000" /></td></tr><tr><th>

<label for="in5">Background color</label></th><td><input
	id="in5" type="color"
  v-model="bgCh" placeholder="#f2f4f8" @input="opCh=bgCh" /></td></tr><tr><th>

<label for="in6">Background opaque</label></th><td><input
	id="in6" type="checkbox"
  v-model="opCh" v-bind:true-value="bgCh" v-bind:false-value="0"/></td></tr><tr><th>

</th></tr></table>

</div>

<div id="txt"><textarea id="msg" v-model="mdata" placeholder="LOOOH"></textarea></div>
<div id="hnt"><pre id="res">{{ mdata }}<br>{{rctCh}}<br>{{bgCh}}</pre></div>
</template>

<style scoped>


*			{margin:0; padding:0; box-sizing:border-box;}
		#box			{background:url('data:image/gif;base64,R0lGODlhBgAGAIAAAO7u7t7e3iH5BAAAAAAALAAAAAAGAAYAAAIKhIOXgKGuDIOzAAA7') #eeeff1;}


		body			{font-size:12px; background:#ffe;}
		body,
		textarea		{text-align:center; font-family:arial;}


		input			{}
		input[type='number'],
		input[type='color']	{width:5em;}
		input[type='number']	{padding:0.25em; text-align:right;}
		select			{width:9em; font-size:11px; padding:0.25em 0.2em;}
		option			{padding:0.25em 0.2em;}
		textarea		{resize:none; padding:2.5em; color:#358; background:#eef2f4; font-size:2em; border:0; width:100%;}


		#set			{user-select:none; background:#fff; overflow:hidden;}
		#set table		{border-collapse:collapse; padding:2em; font-size:11px; text-transform:uppercase; margin:2em auto;}
		#set th,
		#set td			{padding:0.4em 0.5em;}
		#set th			{text-align:right; color:#567;}
		#set td			{text-align:left;}


		/* res beautifier */
		#res			{color:#789; padding:2em; text-align:left; font-family:'Lucida Console', Monaco, monospace;}
		#res b			{font-weight:normal;}
		#res i			{font-style:normal;}
		#res .obj		{color:#789;}
		#res .obj b		{color:#345; font-weight:bold;}
		#res .key		{color:#45a;}
		#res .num		{color:#12a;}
		#res .txt		{color:#9ab;}
		#res .txt i		{color:#384;}
		#res .clr		{color:#9ab;}
		#res .clr i		{color:#731;}
		#res a			{color:#67a;}
		#res a:hover		{color:#67e;}


		#box			{overflow:hidden; position:relative; height:300px; padding:3em;}
		#box svg		{display:block; position:absolute; right:50%; bottom:50%; transform:translate( 50%, 50%); cursor:pointer;}
		#box svg		{max-width:100%; max-height:100%;}


		/* minimized options for small screen */
		.opt			{display:block; padding:1em; background:#0ae; color:#fff; text-decoration:none;}
		.opt:hover		{background:#0af;}

		#op2.opt		{background:#ea0;}
		#op2.opt:hover		{background:#fa0;}

		#set table,
		#set .legend,
		#set #op2.opt,
		#set.show #op1.opt	{display:none;}

		#set.show table		{display:table;}
		#set.show #op2.opt	{display:block;}

	@media (min-width: 620px) {

		html,
		body,			
		#box,
		#set,
		#txt,
		#msg,
		#hnt			{display:block; position:absolute; top:0; right:0; left:0; bottom:0;}

		html,
		body			{overflow:hidden;}
		#box			{height:auto;}

		#txt,
		#hnt			{height:250px; top:auto; border-top:3px #eee solid;}

		#set,
		#hnt			{width:270px; left:auto;}
		#set table		{font-size:10px;}

		#box,
		#txt			{right:270px}

		#box,
		#set			{bottom:250px;}

		#hnt			{overflow:auto;}
		#msg			{width:100%; height:100%;}

		#set			{overflow-y:auto;}
		#set .legend		{display:block;}
		#set table		{display:table;}
		#set .opt		{display:none !important;}
	}

	@media (min-width:900px) {

		#set,
		#hnt			{width:30%}
		#box,
		#txt			{right:30%}
	}

	@media (min-width:1024px) {

		#set table		{font-size:11px;}
	}

	@media (min-width:1600px) {

		#set,
		#hnt			{width:480px}
		#box,
		#txt			{right:480px}
	}

		.legend			{padding:1.5em 0.5em; border-bottom:1px #eee solid;}

</style>
