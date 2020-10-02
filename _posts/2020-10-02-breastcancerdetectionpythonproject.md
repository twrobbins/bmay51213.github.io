---
title: "Machine Learning Project:  Breast Cancer Detection Using Machine Learning"
date: 2020-09-04
tags: [machine learning, data science]
header:
  image: "/images/breastcancer/1_yjsLGG-U9km84AvWLLmK8A.png"
excerpt: "Using Machine Learning to Detect Cancer on Biopsy Specimens"
---

<!DOCTYPE html>
<html>
<head><meta charset="utf-8" />

<title>Machine Learning and Breast Cancer Detection</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>



<style type="text/css">
    /*!
*
* Twitter Bootstrap
*
*/
/*!
 * Bootstrap v3.3.7 (http://getbootstrap.com)
 * Copyright 2011-2016 Twitter, Inc.
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/master/LICENSE)
 */
/*! normalize.css v3.0.3 | MIT License | github.com/necolas/normalize.css */
html {
  font-family: sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
body {
  margin: 0;
}
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
main,
menu,
nav,
section,
summary {
  display: block;
}
audio,
canvas,
progress,
video {
  display: inline-block;
  vertical-align: baseline;
}
audio:not([controls]) {
  display: none;
  height: 0;
}
[hidden],
template {
  display: none;
}
a {
  background-color: transparent;
}
a:active,
a:hover {
  outline: 0;
}
abbr[title] {
  border-bottom: 1px dotted;
}
b,
strong {
  font-weight: bold;
}
dfn {
  font-style: italic;
}
h1 {
  font-size: 2em;
  margin: 0.67em 0;
}
mark {
  background: #ff0;
  color: #000;
}
small {
  font-size: 80%;
}
sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}
sup {
  top: -0.5em;
}
sub {
  bottom: -0.25em;
}
img {
  border: 0;
}
svg:not(:root) {
  overflow: hidden;
}
figure {
  margin: 1em 40px;
}
hr {
  box-sizing: content-box;
  height: 0;
}
pre {
  overflow: auto;
}
code,
kbd,
pre,
samp {
  font-family: monospace, monospace;
  font-size: 1em;
}
button,
input,
optgroup,
select,
textarea {
  color: inherit;
  font: inherit;
  margin: 0;
}
button {
  overflow: visible;
}
button,
select {
  text-transform: none;
}
button,
html input[type="button"],
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button;
  cursor: pointer;
}
button[disabled],
html input[disabled] {
  cursor: default;
}
button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0;
}
input {
  line-height: normal;
}
input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box;
  padding: 0;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: textfield;
  box-sizing: content-box;
}
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}
fieldset {
  border: 1px solid #c0c0c0;
  margin: 0 2px;
  padding: 0.35em 0.625em 0.75em;
}
legend {
  border: 0;
  padding: 0;
}
textarea {
  overflow: auto;
}
optgroup {
  font-weight: bold;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
td,
th {
  padding: 0;
}
/*! Source: https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css */
@media print {
  *,
  *:before,
  *:after {
    background: transparent !important;
    box-shadow: none !important;
    text-shadow: none !important;
  }
  a,
  a:visited {
    text-decoration: underline;
  }
  a[href]:after {
    content: " (" attr(href) ")";
  }
  abbr[title]:after {
    content: " (" attr(title) ")";
  }
  a[href^="#"]:after,
  a[href^="javascript:"]:after {
    content: "";
  }
  pre,
  blockquote {
    border: 1px solid #999;
    page-break-inside: avoid;
  }
  thead {
    display: table-header-group;
  }
  tr,
  img {
    page-break-inside: avoid;
  }
  img {
    max-width: 100% !important;
  }
  p,
  h2,
  h3 {
    orphans: 3;
    widows: 3;
  }
  h2,
  h3 {
    page-break-after: avoid;
  }
  .navbar {
    display: none;
  }
  .btn > .caret,
  .dropup > .btn > .caret {
    border-top-color: #000 !important;
  }
  .label {
    border: 1px solid #000;
  }
  .table {
    border-collapse: collapse !important;
  }
  .table td,
  .table th {
    background-color: #fff !important;
  }
  .table-bordered th,
  .table-bordered td {
    border: 1px solid #ddd !important;
  }
}
@font-face {
  font-family: 'Glyphicons Halflings';
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot');
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot?#iefix') format('embedded-opentype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff2') format('woff2'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff') format('woff'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.ttf') format('truetype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.svg#glyphicons_halflingsregular') format('svg');
}
.glyphicon {
  position: relative;
  top: 1px;
  display: inline-block;
  font-family: 'Glyphicons Halflings';
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.glyphicon-asterisk:before {
  content: "\002a";
}
.glyphicon-plus:before {
  content: "\002b";
}
.glyphicon-euro:before,
.glyphicon-eur:before {
  content: "\20ac";
}
.glyphicon-minus:before {
  content: "\2212";
}
.glyphicon-cloud:before {
  content: "\2601";
}
.glyphicon-envelope:before {
  content: "\2709";
}
.glyphicon-pencil:before {
  content: "\270f";
}
.glyphicon-glass:before {
  content: "\e001";
}
.glyphicon-music:before {
  content: "\e002";
}
.glyphicon-search:before {
  content: "\e003";
}
.glyphicon-heart:before {
  content: "\e005";
}
.glyphicon-star:before {
  content: "\e006";
}
.glyphicon-star-empty:before {
  content: "\e007";
}
.glyphicon-user:before {
  content: "\e008";
}
.glyphicon-film:before {
  content: "\e009";
}
.glyphicon-th-large:before {
  content: "\e010";
}
.glyphicon-th:before {
  content: "\e011";
}
.glyphicon-th-list:before {
  content: "\e012";
}
.glyphicon-ok:before {
  content: "\e013";
}
.glyphicon-remove:before {
  content: "\e014";
}
.glyphicon-zoom-in:before {
  content: "\e015";
}
.glyphicon-zoom-out:before {
  content: "\e016";
}
.glyphicon-off:before {
  content: "\e017";
}
.glyphicon-signal:before {
  content: "\e018";
}
.glyphicon-cog:before {
  content: "\e019";
}
.glyphicon-trash:before {
  content: "\e020";
}
.glyphicon-home:before {
  content: "\e021";
}
.glyphicon-file:before {
  content: "\e022";
}
.glyphicon-time:before {
  content: "\e023";
}
.glyphicon-road:before {
  content: "\e024";
}
.glyphicon-download-alt:before {
  content: "\e025";
}
.glyphicon-download:before {
  content: "\e026";
}
.glyphicon-upload:before {
  content: "\e027";
}
.glyphicon-inbox:before {
  content: "\e028";
}
.glyphicon-play-circle:before {
  content: "\e029";
}
.glyphicon-repeat:before {
  content: "\e030";
}
.glyphicon-refresh:before {
  content: "\e031";
}
.glyphicon-list-alt:before {
  content: "\e032";
}
.glyphicon-lock:before {
  content: "\e033";
}
.glyphicon-flag:before {
  content: "\e034";
}
.glyphicon-headphones:before {
  content: "\e035";
}
.glyphicon-volume-off:before {
  content: "\e036";
}
.glyphicon-volume-down:before {
  content: "\e037";
}
.glyphicon-volume-up:before {
  content: "\e038";
}
.glyphicon-qrcode:before {
  content: "\e039";
}
.glyphicon-barcode:before {
  content: "\e040";
}
.glyphicon-tag:before {
  content: "\e041";
}
.glyphicon-tags:before {
  content: "\e042";
}
.glyphicon-book:before {
  content: "\e043";
}
.glyphicon-bookmark:before {
  content: "\e044";
}
.glyphicon-print:before {
  content: "\e045";
}
.glyphicon-camera:before {
  content: "\e046";
}
.glyphicon-font:before {
  content: "\e047";
}
.glyphicon-bold:before {
  content: "\e048";
}
.glyphicon-italic:before {
  content: "\e049";
}
.glyphicon-text-height:before {
  content: "\e050";
}
.glyphicon-text-width:before {
  content: "\e051";
}
.glyphicon-align-left:before {
  content: "\e052";
}
.glyphicon-align-center:before {
  content: "\e053";
}
.glyphicon-align-right:before {
  content: "\e054";
}
.glyphicon-align-justify:before {
  content: "\e055";
}
.glyphicon-list:before {
  content: "\e056";
}
.glyphicon-indent-left:before {
  content: "\e057";
}
.glyphicon-indent-right:before {
  content: "\e058";
}
.glyphicon-facetime-video:before {
  content: "\e059";
}
.glyphicon-picture:before {
  content: "\e060";
}
.glyphicon-map-marker:before {
  content: "\e062";
}
.glyphicon-adjust:before {
  content: "\e063";
}
.glyphicon-tint:before {
  content: "\e064";
}
.glyphicon-edit:before {
  content: "\e065";
}
.glyphicon-share:before {
  content: "\e066";
}
.glyphicon-check:before {
  content: "\e067";
}
.glyphicon-move:before {
  content: "\e068";
}
.glyphicon-step-backward:before {
  content: "\e069";
}
.glyphicon-fast-backward:before {
  content: "\e070";
}
.glyphicon-backward:before {
  content: "\e071";
}
.glyphicon-play:before {
  content: "\e072";
}
.glyphicon-pause:before {
  content: "\e073";
}
.glyphicon-stop:before {
  content: "\e074";
}
.glyphicon-forward:before {
  content: "\e075";
}
.glyphicon-fast-forward:before {
  content: "\e076";
}
.glyphicon-step-forward:before {
  content: "\e077";
}
.glyphicon-eject:before {
  content: "\e078";
}
.glyphicon-chevron-left:before {
  content: "\e079";
}
.glyphicon-chevron-right:before {
  content: "\e080";
}
.glyphicon-plus-sign:before {
  content: "\e081";
}
.glyphicon-minus-sign:before {
  content: "\e082";
}
.glyphicon-remove-sign:before {
  content: "\e083";
}
.glyphicon-ok-sign:before {
  content: "\e084";
}
.glyphicon-question-sign:before {
  content: "\e085";
}
.glyphicon-info-sign:before {
  content: "\e086";
}
.glyphicon-screenshot:before {
  content: "\e087";
}
.glyphicon-remove-circle:before {
  content: "\e088";
}
.glyphicon-ok-circle:before {
  content: "\e089";
}
.glyphicon-ban-circle:before {
  content: "\e090";
}
.glyphicon-arrow-left:before {
  content: "\e091";
}
.glyphicon-arrow-right:before {
  content: "\e092";
}
.glyphicon-arrow-up:before {
  content: "\e093";
}
.glyphicon-arrow-down:before {
  content: "\e094";
}
.glyphicon-share-alt:before {
  content: "\e095";
}
.glyphicon-resize-full:before {
  content: "\e096";
}
.glyphicon-resize-small:before {
  content: "\e097";
}
.glyphicon-exclamation-sign:before {
  content: "\e101";
}
.glyphicon-gift:before {
  content: "\e102";
}
.glyphicon-leaf:before {
  content: "\e103";
}
.glyphicon-fire:before {
  content: "\e104";
}
.glyphicon-eye-open:before {
  content: "\e105";
}
.glyphicon-eye-close:before {
  content: "\e106";
}
.glyphicon-warning-sign:before {
  content: "\e107";
}
.glyphicon-plane:before {
  content: "\e108";
}
.glyphicon-calendar:before {
  content: "\e109";
}
.glyphicon-random:before {
  content: "\e110";
}
.glyphicon-comment:before {
  content: "\e111";
}
.glyphicon-magnet:before {
  content: "\e112";
}
.glyphicon-chevron-up:before {
  content: "\e113";
}
.glyphicon-chevron-down:before {
  content: "\e114";
}
.glyphicon-retweet:before {
  content: "\e115";
}
.glyphicon-shopping-cart:before {
  content: "\e116";
}
.glyphicon-folder-close:before {
  content: "\e117";
}
.glyphicon-folder-open:before {
  content: "\e118";
}
.glyphicon-resize-vertical:before {
  content: "\e119";
}
.glyphicon-resize-horizontal:before {
  content: "\e120";
}
.glyphicon-hdd:before {
  content: "\e121";
}
.glyphicon-bullhorn:before {
  content: "\e122";
}
.glyphicon-bell:before {
  content: "\e123";
}
.glyphicon-certificate:before {
  content: "\e124";
}
.glyphicon-thumbs-up:before {
  content: "\e125";
}
.glyphicon-thumbs-down:before {
  content: "\e126";
}
.glyphicon-hand-right:before {
  content: "\e127";
}
.glyphicon-hand-left:before {
  content: "\e128";
}
.glyphicon-hand-up:before {
  content: "\e129";
}
.glyphicon-hand-down:before {
  content: "\e130";
}
.glyphicon-circle-arrow-right:before {
  content: "\e131";
}
.glyphicon-circle-arrow-left:before {
  content: "\e132";
}
.glyphicon-circle-arrow-up:before {
  content: "\e133";
}
.glyphicon-circle-arrow-down:before {
  content: "\e134";
}
.glyphicon-globe:before {
  content: "\e135";
}
.glyphicon-wrench:before {
  content: "\e136";
}
.glyphicon-tasks:before {
  content: "\e137";
}
.glyphicon-filter:before {
  content: "\e138";
}
.glyphicon-briefcase:before {
  content: "\e139";
}
.glyphicon-fullscreen:before {
  content: "\e140";
}
.glyphicon-dashboard:before {
  content: "\e141";
}
.glyphicon-paperclip:before {
  content: "\e142";
}
.glyphicon-heart-empty:before {
  content: "\e143";
}
.glyphicon-link:before {
  content: "\e144";
}
.glyphicon-phone:before {
  content: "\e145";
}
.glyphicon-pushpin:before {
  content: "\e146";
}
.glyphicon-usd:before {
  content: "\e148";
}
.glyphicon-gbp:before {
  content: "\e149";
}
.glyphicon-sort:before {
  content: "\e150";
}
.glyphicon-sort-by-alphabet:before {
  content: "\e151";
}
.glyphicon-sort-by-alphabet-alt:before {
  content: "\e152";
}
.glyphicon-sort-by-order:before {
  content: "\e153";
}
.glyphicon-sort-by-order-alt:before {
  content: "\e154";
}
.glyphicon-sort-by-attributes:before {
  content: "\e155";
}
.glyphicon-sort-by-attributes-alt:before {
  content: "\e156";
}
.glyphicon-unchecked:before {
  content: "\e157";
}
.glyphicon-expand:before {
  content: "\e158";
}
.glyphicon-collapse-down:before {
  content: "\e159";
}
.glyphicon-collapse-up:before {
  content: "\e160";
}
.glyphicon-log-in:before {
  content: "\e161";
}
.glyphicon-flash:before {
  content: "\e162";
}
.glyphicon-log-out:before {
  content: "\e163";
}
.glyphicon-new-window:before {
  content: "\e164";
}
.glyphicon-record:before {
  content: "\e165";
}
.glyphicon-save:before {
  content: "\e166";
}
.glyphicon-open:before {
  content: "\e167";
}
.glyphicon-saved:before {
  content: "\e168";
}
.glyphicon-import:before {
  content: "\e169";
}
.glyphicon-export:before {
  content: "\e170";
}
.glyphicon-send:before {
  content: "\e171";
}
.glyphicon-floppy-disk:before {
  content: "\e172";
}
.glyphicon-floppy-saved:before {
  content: "\e173";
}
.glyphicon-floppy-remove:before {
  content: "\e174";
}
.glyphicon-floppy-save:before {
  content: "\e175";
}
.glyphicon-floppy-open:before {
  content: "\e176";
}
.glyphicon-credit-card:before {
  content: "\e177";
}
.glyphicon-transfer:before {
  content: "\e178";
}
.glyphicon-cutlery:before {
  content: "\e179";
}
.glyphicon-header:before {
  content: "\e180";
}
.glyphicon-compressed:before {
  content: "\e181";
}
.glyphicon-earphone:before {
  content: "\e182";
}
.glyphicon-phone-alt:before {
  content: "\e183";
}
.glyphicon-tower:before {
  content: "\e184";
}
.glyphicon-stats:before {
  content: "\e185";
}
.glyphicon-sd-video:before {
  content: "\e186";
}
.glyphicon-hd-video:before {
  content: "\e187";
}
.glyphicon-subtitles:before {
  content: "\e188";
}
.glyphicon-sound-stereo:before {
  content: "\e189";
}
.glyphicon-sound-dolby:before {
  content: "\e190";
}
.glyphicon-sound-5-1:before {
  content: "\e191";
}
.glyphicon-sound-6-1:before {
  content: "\e192";
}
.glyphicon-sound-7-1:before {
  content: "\e193";
}
.glyphicon-copyright-mark:before {
  content: "\e194";
}
.glyphicon-registration-mark:before {
  content: "\e195";
}
.glyphicon-cloud-download:before {
  content: "\e197";
}
.glyphicon-cloud-upload:before {
  content: "\e198";
}
.glyphicon-tree-conifer:before {
  content: "\e199";
}
.glyphicon-tree-deciduous:before {
  content: "\e200";
}
.glyphicon-cd:before {
  content: "\e201";
}
.glyphicon-save-file:before {
  content: "\e202";
}
.glyphicon-open-file:before {
  content: "\e203";
}
.glyphicon-level-up:before {
  content: "\e204";
}
.glyphicon-copy:before {
  content: "\e205";
}
.glyphicon-paste:before {
  content: "\e206";
}
.glyphicon-alert:before {
  content: "\e209";
}
.glyphicon-equalizer:before {
  content: "\e210";
}
.glyphicon-king:before {
  content: "\e211";
}
.glyphicon-queen:before {
  content: "\e212";
}
.glyphicon-pawn:before {
  content: "\e213";
}
.glyphicon-bishop:before {
  content: "\e214";
}
.glyphicon-knight:before {
  content: "\e215";
}
.glyphicon-baby-formula:before {
  content: "\e216";
}
.glyphicon-tent:before {
  content: "\26fa";
}
.glyphicon-blackboard:before {
  content: "\e218";
}
.glyphicon-bed:before {
  content: "\e219";
}
.glyphicon-apple:before {
  content: "\f8ff";
}
.glyphicon-erase:before {
  content: "\e221";
}
.glyphicon-hourglass:before {
  content: "\231b";
}
.glyphicon-lamp:before {
  content: "\e223";
}
.glyphicon-duplicate:before {
  content: "\e224";
}
.glyphicon-piggy-bank:before {
  content: "\e225";
}
.glyphicon-scissors:before {
  content: "\e226";
}
.glyphicon-bitcoin:before {
  content: "\e227";
}
.glyphicon-btc:before {
  content: "\e227";
}
.glyphicon-xbt:before {
  content: "\e227";
}
.glyphicon-yen:before {
  content: "\00a5";
}
.glyphicon-jpy:before {
  content: "\00a5";
}
.glyphicon-ruble:before {
  content: "\20bd";
}
.glyphicon-rub:before {
  content: "\20bd";
}
.glyphicon-scale:before {
  content: "\e230";
}
.glyphicon-ice-lolly:before {
  content: "\e231";
}
.glyphicon-ice-lolly-tasted:before {
  content: "\e232";
}
.glyphicon-education:before {
  content: "\e233";
}
.glyphicon-option-horizontal:before {
  content: "\e234";
}
.glyphicon-option-vertical:before {
  content: "\e235";
}
.glyphicon-menu-hamburger:before {
  content: "\e236";
}
.glyphicon-modal-window:before {
  content: "\e237";
}
.glyphicon-oil:before {
  content: "\e238";
}
.glyphicon-grain:before {
  content: "\e239";
}
.glyphicon-sunglasses:before {
  content: "\e240";
}
.glyphicon-text-size:before {
  content: "\e241";
}
.glyphicon-text-color:before {
  content: "\e242";
}
.glyphicon-text-background:before {
  content: "\e243";
}
.glyphicon-object-align-top:before {
  content: "\e244";
}
.glyphicon-object-align-bottom:before {
  content: "\e245";
}
.glyphicon-object-align-horizontal:before {
  content: "\e246";
}
.glyphicon-object-align-left:before {
  content: "\e247";
}
.glyphicon-object-align-vertical:before {
  content: "\e248";
}
.glyphicon-object-align-right:before {
  content: "\e249";
}
.glyphicon-triangle-right:before {
  content: "\e250";
}
.glyphicon-triangle-left:before {
  content: "\e251";
}
.glyphicon-triangle-bottom:before {
  content: "\e252";
}
.glyphicon-triangle-top:before {
  content: "\e253";
}
.glyphicon-console:before {
  content: "\e254";
}
.glyphicon-superscript:before {
  content: "\e255";
}
.glyphicon-subscript:before {
  content: "\e256";
}
.glyphicon-menu-left:before {
  content: "\e257";
}
.glyphicon-menu-right:before {
  content: "\e258";
}
.glyphicon-menu-down:before {
  content: "\e259";
}
.glyphicon-menu-up:before {
  content: "\e260";
}
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
*:before,
*:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
html {
  font-size: 10px;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 13px;
  line-height: 1.42857143;
  color: #000;
  background-color: #fff;
}
input,
button,
select,
textarea {
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
}
a {
  color: #337ab7;
  text-decoration: none;
}
a:hover,
a:focus {
  color: #23527c;
  text-decoration: underline;
}
a:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
figure {
  margin: 0;
}
img {
  vertical-align: middle;
}
.img-responsive,
.thumbnail > img,
.thumbnail a > img,
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  display: block;
  max-width: 100%;
  height: auto;
}
.img-rounded {
  border-radius: 3px;
}
.img-thumbnail {
  padding: 4px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: all 0.2s ease-in-out;
  -o-transition: all 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
  display: inline-block;
  max-width: 100%;
  height: auto;
}
.img-circle {
  border-radius: 50%;
}
hr {
  margin-top: 18px;
  margin-bottom: 18px;
  border: 0;
  border-top: 1px solid #eeeeee;
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
[role="button"] {
  cursor: pointer;
}
h1,
h2,
h3,
h4,
h5,
h6,
.h1,
.h2,
.h3,
.h4,
.h5,
.h6 {
  font-family: inherit;
  font-weight: 500;
  line-height: 1.1;
  color: inherit;
}
h1 small,
h2 small,
h3 small,
h4 small,
h5 small,
h6 small,
.h1 small,
.h2 small,
.h3 small,
.h4 small,
.h5 small,
.h6 small,
h1 .small,
h2 .small,
h3 .small,
h4 .small,
h5 .small,
h6 .small,
.h1 .small,
.h2 .small,
.h3 .small,
.h4 .small,
.h5 .small,
.h6 .small {
  font-weight: normal;
  line-height: 1;
  color: #777777;
}
h1,
.h1,
h2,
.h2,
h3,
.h3 {
  margin-top: 18px;
  margin-bottom: 9px;
}
h1 small,
.h1 small,
h2 small,
.h2 small,
h3 small,
.h3 small,
h1 .small,
.h1 .small,
h2 .small,
.h2 .small,
h3 .small,
.h3 .small {
  font-size: 65%;
}
h4,
.h4,
h5,
.h5,
h6,
.h6 {
  margin-top: 9px;
  margin-bottom: 9px;
}
h4 small,
.h4 small,
h5 small,
.h5 small,
h6 small,
.h6 small,
h4 .small,
.h4 .small,
h5 .small,
.h5 .small,
h6 .small,
.h6 .small {
  font-size: 75%;
}
h1,
.h1 {
  font-size: 33px;
}
h2,
.h2 {
  font-size: 27px;
}
h3,
.h3 {
  font-size: 23px;
}
h4,
.h4 {
  font-size: 17px;
}
h5,
.h5 {
  font-size: 13px;
}
h6,
.h6 {
  font-size: 12px;
}
p {
  margin: 0 0 9px;
}
.lead {
  margin-bottom: 18px;
  font-size: 14px;
  font-weight: 300;
  line-height: 1.4;
}
@media (min-width: 768px) {
  .lead {
    font-size: 19.5px;
  }
}
small,
.small {
  font-size: 92%;
}
mark,
.mark {
  background-color: #fcf8e3;
  padding: .2em;
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}
.text-center {
  text-align: center;
}
.text-justify {
  text-align: justify;
}
.text-nowrap {
  white-space: nowrap;
}
.text-lowercase {
  text-transform: lowercase;
}
.text-uppercase {
  text-transform: uppercase;
}
.text-capitalize {
  text-transform: capitalize;
}
.text-muted {
  color: #777777;
}
.text-primary {
  color: #337ab7;
}
a.text-primary:hover,
a.text-primary:focus {
  color: #286090;
}
.text-success {
  color: #3c763d;
}
a.text-success:hover,
a.text-success:focus {
  color: #2b542c;
}
.text-info {
  color: #31708f;
}
a.text-info:hover,
a.text-info:focus {
  color: #245269;
}
.text-warning {
  color: #8a6d3b;
}
a.text-warning:hover,
a.text-warning:focus {
  color: #66512c;
}
.text-danger {
  color: #a94442;
}
a.text-danger:hover,
a.text-danger:focus {
  color: #843534;
}
.bg-primary {
  color: #fff;
  background-color: #337ab7;
}
a.bg-primary:hover,
a.bg-primary:focus {
  background-color: #286090;
}
.bg-success {
  background-color: #dff0d8;
}
a.bg-success:hover,
a.bg-success:focus {
  background-color: #c1e2b3;
}
.bg-info {
  background-color: #d9edf7;
}
a.bg-info:hover,
a.bg-info:focus {
  background-color: #afd9ee;
}
.bg-warning {
  background-color: #fcf8e3;
}
a.bg-warning:hover,
a.bg-warning:focus {
  background-color: #f7ecb5;
}
.bg-danger {
  background-color: #f2dede;
}
a.bg-danger:hover,
a.bg-danger:focus {
  background-color: #e4b9b9;
}
.page-header {
  padding-bottom: 8px;
  margin: 36px 0 18px;
  border-bottom: 1px solid #eeeeee;
}
ul,
ol {
  margin-top: 0;
  margin-bottom: 9px;
}
ul ul,
ol ul,
ul ol,
ol ol {
  margin-bottom: 0;
}
.list-unstyled {
  padding-left: 0;
  list-style: none;
}
.list-inline {
  padding-left: 0;
  list-style: none;
  margin-left: -5px;
}
.list-inline > li {
  display: inline-block;
  padding-left: 5px;
  padding-right: 5px;
}
dl {
  margin-top: 0;
  margin-bottom: 18px;
}
dt,
dd {
  line-height: 1.42857143;
}
dt {
  font-weight: bold;
}
dd {
  margin-left: 0;
}
@media (min-width: 541px) {
  .dl-horizontal dt {
    float: left;
    width: 160px;
    clear: left;
    text-align: right;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .dl-horizontal dd {
    margin-left: 180px;
  }
}
abbr[title],
abbr[data-original-title] {
  cursor: help;
  border-bottom: 1px dotted #777777;
}
.initialism {
  font-size: 90%;
  text-transform: uppercase;
}
blockquote {
  padding: 9px 18px;
  margin: 0 0 18px;
  font-size: inherit;
  border-left: 5px solid #eeeeee;
}
blockquote p:last-child,
blockquote ul:last-child,
blockquote ol:last-child {
  margin-bottom: 0;
}
blockquote footer,
blockquote small,
blockquote .small {
  display: block;
  font-size: 80%;
  line-height: 1.42857143;
  color: #777777;
}
blockquote footer:before,
blockquote small:before,
blockquote .small:before {
  content: '\2014 \00A0';
}
.blockquote-reverse,
blockquote.pull-right {
  padding-right: 15px;
  padding-left: 0;
  border-right: 5px solid #eeeeee;
  border-left: 0;
  text-align: right;
}
.blockquote-reverse footer:before,
blockquote.pull-right footer:before,
.blockquote-reverse small:before,
blockquote.pull-right small:before,
.blockquote-reverse .small:before,
blockquote.pull-right .small:before {
  content: '';
}
.blockquote-reverse footer:after,
blockquote.pull-right footer:after,
.blockquote-reverse small:after,
blockquote.pull-right small:after,
.blockquote-reverse .small:after,
blockquote.pull-right .small:after {
  content: '\00A0 \2014';
}
address {
  margin-bottom: 18px;
  font-style: normal;
  line-height: 1.42857143;
}
code,
kbd,
pre,
samp {
  font-family: monospace;
}
code {
  padding: 2px 4px;
  font-size: 90%;
  color: #c7254e;
  background-color: #f9f2f4;
  border-radius: 2px;
}
kbd {
  padding: 2px 4px;
  font-size: 90%;
  color: #888;
  background-color: transparent;
  border-radius: 1px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
}
kbd kbd {
  padding: 0;
  font-size: 100%;
  font-weight: bold;
  box-shadow: none;
}
pre {
  display: block;
  padding: 8.5px;
  margin: 0 0 9px;
  font-size: 12px;
  line-height: 1.42857143;
  word-break: break-all;
  word-wrap: break-word;
  color: #333333;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 2px;
}
pre code {
  padding: 0;
  font-size: inherit;
  color: inherit;
  white-space: pre-wrap;
  background-color: transparent;
  border-radius: 0;
}
.pre-scrollable {
  max-height: 340px;
  overflow-y: scroll;
}
.container {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
@media (min-width: 768px) {
  .container {
    width: 768px;
  }
}
@media (min-width: 992px) {
  .container {
    width: 940px;
  }
}
@media (min-width: 1200px) {
  .container {
    width: 1140px;
  }
}
.container-fluid {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
.row {
  margin-left: 0px;
  margin-right: 0px;
}
.col-xs-1, .col-sm-1, .col-md-1, .col-lg-1, .col-xs-2, .col-sm-2, .col-md-2, .col-lg-2, .col-xs-3, .col-sm-3, .col-md-3, .col-lg-3, .col-xs-4, .col-sm-4, .col-md-4, .col-lg-4, .col-xs-5, .col-sm-5, .col-md-5, .col-lg-5, .col-xs-6, .col-sm-6, .col-md-6, .col-lg-6, .col-xs-7, .col-sm-7, .col-md-7, .col-lg-7, .col-xs-8, .col-sm-8, .col-md-8, .col-lg-8, .col-xs-9, .col-sm-9, .col-md-9, .col-lg-9, .col-xs-10, .col-sm-10, .col-md-10, .col-lg-10, .col-xs-11, .col-sm-11, .col-md-11, .col-lg-11, .col-xs-12, .col-sm-12, .col-md-12, .col-lg-12 {
  position: relative;
  min-height: 1px;
  padding-left: 0px;
  padding-right: 0px;
}
.col-xs-1, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9, .col-xs-10, .col-xs-11, .col-xs-12 {
  float: left;
}
.col-xs-12 {
  width: 100%;
}
.col-xs-11 {
  width: 91.66666667%;
}
.col-xs-10 {
  width: 83.33333333%;
}
.col-xs-9 {
  width: 75%;
}
.col-xs-8 {
  width: 66.66666667%;
}
.col-xs-7 {
  width: 58.33333333%;
}
.col-xs-6 {
  width: 50%;
}
.col-xs-5 {
  width: 41.66666667%;
}
.col-xs-4 {
  width: 33.33333333%;
}
.col-xs-3 {
  width: 25%;
}
.col-xs-2 {
  width: 16.66666667%;
}
.col-xs-1 {
  width: 8.33333333%;
}
.col-xs-pull-12 {
  right: 100%;
}
.col-xs-pull-11 {
  right: 91.66666667%;
}
.col-xs-pull-10 {
  right: 83.33333333%;
}
.col-xs-pull-9 {
  right: 75%;
}
.col-xs-pull-8 {
  right: 66.66666667%;
}
.col-xs-pull-7 {
  right: 58.33333333%;
}
.col-xs-pull-6 {
  right: 50%;
}
.col-xs-pull-5 {
  right: 41.66666667%;
}
.col-xs-pull-4 {
  right: 33.33333333%;
}
.col-xs-pull-3 {
  right: 25%;
}
.col-xs-pull-2 {
  right: 16.66666667%;
}
.col-xs-pull-1 {
  right: 8.33333333%;
}
.col-xs-pull-0 {
  right: auto;
}
.col-xs-push-12 {
  left: 100%;
}
.col-xs-push-11 {
  left: 91.66666667%;
}
.col-xs-push-10 {
  left: 83.33333333%;
}
.col-xs-push-9 {
  left: 75%;
}
.col-xs-push-8 {
  left: 66.66666667%;
}
.col-xs-push-7 {
  left: 58.33333333%;
}
.col-xs-push-6 {
  left: 50%;
}
.col-xs-push-5 {
  left: 41.66666667%;
}
.col-xs-push-4 {
  left: 33.33333333%;
}
.col-xs-push-3 {
  left: 25%;
}
.col-xs-push-2 {
  left: 16.66666667%;
}
.col-xs-push-1 {
  left: 8.33333333%;
}
.col-xs-push-0 {
  left: auto;
}
.col-xs-offset-12 {
  margin-left: 100%;
}
.col-xs-offset-11 {
  margin-left: 91.66666667%;
}
.col-xs-offset-10 {
  margin-left: 83.33333333%;
}
.col-xs-offset-9 {
  margin-left: 75%;
}
.col-xs-offset-8 {
  margin-left: 66.66666667%;
}
.col-xs-offset-7 {
  margin-left: 58.33333333%;
}
.col-xs-offset-6 {
  margin-left: 50%;
}
.col-xs-offset-5 {
  margin-left: 41.66666667%;
}
.col-xs-offset-4 {
  margin-left: 33.33333333%;
}
.col-xs-offset-3 {
  margin-left: 25%;
}
.col-xs-offset-2 {
  margin-left: 16.66666667%;
}
.col-xs-offset-1 {
  margin-left: 8.33333333%;
}
.col-xs-offset-0 {
  margin-left: 0%;
}
@media (min-width: 768px) {
  .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
    float: left;
  }
  .col-sm-12 {
    width: 100%;
  }
  .col-sm-11 {
    width: 91.66666667%;
  }
  .col-sm-10 {
    width: 83.33333333%;
  }
  .col-sm-9 {
    width: 75%;
  }
  .col-sm-8 {
    width: 66.66666667%;
  }
  .col-sm-7 {
    width: 58.33333333%;
  }
  .col-sm-6 {
    width: 50%;
  }
  .col-sm-5 {
    width: 41.66666667%;
  }
  .col-sm-4 {
    width: 33.33333333%;
  }
  .col-sm-3 {
    width: 25%;
  }
  .col-sm-2 {
    width: 16.66666667%;
  }
  .col-sm-1 {
    width: 8.33333333%;
  }
  .col-sm-pull-12 {
    right: 100%;
  }
  .col-sm-pull-11 {
    right: 91.66666667%;
  }
  .col-sm-pull-10 {
    right: 83.33333333%;
  }
  .col-sm-pull-9 {
    right: 75%;
  }
  .col-sm-pull-8 {
    right: 66.66666667%;
  }
  .col-sm-pull-7 {
    right: 58.33333333%;
  }
  .col-sm-pull-6 {
    right: 50%;
  }
  .col-sm-pull-5 {
    right: 41.66666667%;
  }
  .col-sm-pull-4 {
    right: 33.33333333%;
  }
  .col-sm-pull-3 {
    right: 25%;
  }
  .col-sm-pull-2 {
    right: 16.66666667%;
  }
  .col-sm-pull-1 {
    right: 8.33333333%;
  }
  .col-sm-pull-0 {
    right: auto;
  }
  .col-sm-push-12 {
    left: 100%;
  }
  .col-sm-push-11 {
    left: 91.66666667%;
  }
  .col-sm-push-10 {
    left: 83.33333333%;
  }
  .col-sm-push-9 {
    left: 75%;
  }
  .col-sm-push-8 {
    left: 66.66666667%;
  }
  .col-sm-push-7 {
    left: 58.33333333%;
  }
  .col-sm-push-6 {
    left: 50%;
  }
  .col-sm-push-5 {
    left: 41.66666667%;
  }
  .col-sm-push-4 {
    left: 33.33333333%;
  }
  .col-sm-push-3 {
    left: 25%;
  }
  .col-sm-push-2 {
    left: 16.66666667%;
  }
  .col-sm-push-1 {
    left: 8.33333333%;
  }
  .col-sm-push-0 {
    left: auto;
  }
  .col-sm-offset-12 {
    margin-left: 100%;
  }
  .col-sm-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-sm-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-sm-offset-9 {
    margin-left: 75%;
  }
  .col-sm-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-sm-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-sm-offset-6 {
    margin-left: 50%;
  }
  .col-sm-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-sm-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-sm-offset-3 {
    margin-left: 25%;
  }
  .col-sm-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-sm-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-sm-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 992px) {
  .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12 {
    float: left;
  }
  .col-md-12 {
    width: 100%;
  }
  .col-md-11 {
    width: 91.66666667%;
  }
  .col-md-10 {
    width: 83.33333333%;
  }
  .col-md-9 {
    width: 75%;
  }
  .col-md-8 {
    width: 66.66666667%;
  }
  .col-md-7 {
    width: 58.33333333%;
  }
  .col-md-6 {
    width: 50%;
  }
  .col-md-5 {
    width: 41.66666667%;
  }
  .col-md-4 {
    width: 33.33333333%;
  }
  .col-md-3 {
    width: 25%;
  }
  .col-md-2 {
    width: 16.66666667%;
  }
  .col-md-1 {
    width: 8.33333333%;
  }
  .col-md-pull-12 {
    right: 100%;
  }
  .col-md-pull-11 {
    right: 91.66666667%;
  }
  .col-md-pull-10 {
    right: 83.33333333%;
  }
  .col-md-pull-9 {
    right: 75%;
  }
  .col-md-pull-8 {
    right: 66.66666667%;
  }
  .col-md-pull-7 {
    right: 58.33333333%;
  }
  .col-md-pull-6 {
    right: 50%;
  }
  .col-md-pull-5 {
    right: 41.66666667%;
  }
  .col-md-pull-4 {
    right: 33.33333333%;
  }
  .col-md-pull-3 {
    right: 25%;
  }
  .col-md-pull-2 {
    right: 16.66666667%;
  }
  .col-md-pull-1 {
    right: 8.33333333%;
  }
  .col-md-pull-0 {
    right: auto;
  }
  .col-md-push-12 {
    left: 100%;
  }
  .col-md-push-11 {
    left: 91.66666667%;
  }
  .col-md-push-10 {
    left: 83.33333333%;
  }
  .col-md-push-9 {
    left: 75%;
  }
  .col-md-push-8 {
    left: 66.66666667%;
  }
  .col-md-push-7 {
    left: 58.33333333%;
  }
  .col-md-push-6 {
    left: 50%;
  }
  .col-md-push-5 {
    left: 41.66666667%;
  }
  .col-md-push-4 {
    left: 33.33333333%;
  }
  .col-md-push-3 {
    left: 25%;
  }
  .col-md-push-2 {
    left: 16.66666667%;
  }
  .col-md-push-1 {
    left: 8.33333333%;
  }
  .col-md-push-0 {
    left: auto;
  }
  .col-md-offset-12 {
    margin-left: 100%;
  }
  .col-md-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-md-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-md-offset-9 {
    margin-left: 75%;
  }
  .col-md-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-md-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-md-offset-6 {
    margin-left: 50%;
  }
  .col-md-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-md-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-md-offset-3 {
    margin-left: 25%;
  }
  .col-md-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-md-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-md-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 1200px) {
  .col-lg-1, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-lg-10, .col-lg-11, .col-lg-12 {
    float: left;
  }
  .col-lg-12 {
    width: 100%;
  }
  .col-lg-11 {
    width: 91.66666667%;
  }
  .col-lg-10 {
    width: 83.33333333%;
  }
  .col-lg-9 {
    width: 75%;
  }
  .col-lg-8 {
    width: 66.66666667%;
  }
  .col-lg-7 {
    width: 58.33333333%;
  }
  .col-lg-6 {
    width: 50%;
  }
  .col-lg-5 {
    width: 41.66666667%;
  }
  .col-lg-4 {
    width: 33.33333333%;
  }
  .col-lg-3 {
    width: 25%;
  }
  .col-lg-2 {
    width: 16.66666667%;
  }
  .col-lg-1 {
    width: 8.33333333%;
  }
  .col-lg-pull-12 {
    right: 100%;
  }
  .col-lg-pull-11 {
    right: 91.66666667%;
  }
  .col-lg-pull-10 {
    right: 83.33333333%;
  }
  .col-lg-pull-9 {
    right: 75%;
  }
  .col-lg-pull-8 {
    right: 66.66666667%;
  }
  .col-lg-pull-7 {
    right: 58.33333333%;
  }
  .col-lg-pull-6 {
    right: 50%;
  }
  .col-lg-pull-5 {
    right: 41.66666667%;
  }
  .col-lg-pull-4 {
    right: 33.33333333%;
  }
  .col-lg-pull-3 {
    right: 25%;
  }
  .col-lg-pull-2 {
    right: 16.66666667%;
  }
  .col-lg-pull-1 {
    right: 8.33333333%;
  }
  .col-lg-pull-0 {
    right: auto;
  }
  .col-lg-push-12 {
    left: 100%;
  }
  .col-lg-push-11 {
    left: 91.66666667%;
  }
  .col-lg-push-10 {
    left: 83.33333333%;
  }
  .col-lg-push-9 {
    left: 75%;
  }
  .col-lg-push-8 {
    left: 66.66666667%;
  }
  .col-lg-push-7 {
    left: 58.33333333%;
  }
  .col-lg-push-6 {
    left: 50%;
  }
  .col-lg-push-5 {
    left: 41.66666667%;
  }
  .col-lg-push-4 {
    left: 33.33333333%;
  }
  .col-lg-push-3 {
    left: 25%;
  }
  .col-lg-push-2 {
    left: 16.66666667%;
  }
  .col-lg-push-1 {
    left: 8.33333333%;
  }
  .col-lg-push-0 {
    left: auto;
  }
  .col-lg-offset-12 {
    margin-left: 100%;
  }
  .col-lg-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-lg-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-lg-offset-9 {
    margin-left: 75%;
  }
  .col-lg-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-lg-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-lg-offset-6 {
    margin-left: 50%;
  }
  .col-lg-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-lg-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-lg-offset-3 {
    margin-left: 25%;
  }
  .col-lg-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-lg-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-lg-offset-0 {
    margin-left: 0%;
  }
}
table {
  background-color: transparent;
}
caption {
  padding-top: 8px;
  padding-bottom: 8px;
  color: #777777;
  text-align: left;
}
th {
  text-align: left;
}
.table {
  width: 100%;
  max-width: 100%;
  margin-bottom: 18px;
}
.table > thead > tr > th,
.table > tbody > tr > th,
.table > tfoot > tr > th,
.table > thead > tr > td,
.table > tbody > tr > td,
.table > tfoot > tr > td {
  padding: 8px;
  line-height: 1.42857143;
  vertical-align: top;
  border-top: 1px solid #ddd;
}
.table > thead > tr > th {
  vertical-align: bottom;
  border-bottom: 2px solid #ddd;
}
.table > caption + thead > tr:first-child > th,
.table > colgroup + thead > tr:first-child > th,
.table > thead:first-child > tr:first-child > th,
.table > caption + thead > tr:first-child > td,
.table > colgroup + thead > tr:first-child > td,
.table > thead:first-child > tr:first-child > td {
  border-top: 0;
}
.table > tbody + tbody {
  border-top: 2px solid #ddd;
}
.table .table {
  background-color: #fff;
}
.table-condensed > thead > tr > th,
.table-condensed > tbody > tr > th,
.table-condensed > tfoot > tr > th,
.table-condensed > thead > tr > td,
.table-condensed > tbody > tr > td,
.table-condensed > tfoot > tr > td {
  padding: 5px;
}
.table-bordered {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > tbody > tr > th,
.table-bordered > tfoot > tr > th,
.table-bordered > thead > tr > td,
.table-bordered > tbody > tr > td,
.table-bordered > tfoot > tr > td {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > thead > tr > td {
  border-bottom-width: 2px;
}
.table-striped > tbody > tr:nth-of-type(odd) {
  background-color: #f9f9f9;
}
.table-hover > tbody > tr:hover {
  background-color: #f5f5f5;
}
table col[class*="col-"] {
  position: static;
  float: none;
  display: table-column;
}
table td[class*="col-"],
table th[class*="col-"] {
  position: static;
  float: none;
  display: table-cell;
}
.table > thead > tr > td.active,
.table > tbody > tr > td.active,
.table > tfoot > tr > td.active,
.table > thead > tr > th.active,
.table > tbody > tr > th.active,
.table > tfoot > tr > th.active,
.table > thead > tr.active > td,
.table > tbody > tr.active > td,
.table > tfoot > tr.active > td,
.table > thead > tr.active > th,
.table > tbody > tr.active > th,
.table > tfoot > tr.active > th {
  background-color: #f5f5f5;
}
.table-hover > tbody > tr > td.active:hover,
.table-hover > tbody > tr > th.active:hover,
.table-hover > tbody > tr.active:hover > td,
.table-hover > tbody > tr:hover > .active,
.table-hover > tbody > tr.active:hover > th {
  background-color: #e8e8e8;
}
.table > thead > tr > td.success,
.table > tbody > tr > td.success,
.table > tfoot > tr > td.success,
.table > thead > tr > th.success,
.table > tbody > tr > th.success,
.table > tfoot > tr > th.success,
.table > thead > tr.success > td,
.table > tbody > tr.success > td,
.table > tfoot > tr.success > td,
.table > thead > tr.success > th,
.table > tbody > tr.success > th,
.table > tfoot > tr.success > th {
  background-color: #dff0d8;
}
.table-hover > tbody > tr > td.success:hover,
.table-hover > tbody > tr > th.success:hover,
.table-hover > tbody > tr.success:hover > td,
.table-hover > tbody > tr:hover > .success,
.table-hover > tbody > tr.success:hover > th {
  background-color: #d0e9c6;
}
.table > thead > tr > td.info,
.table > tbody > tr > td.info,
.table > tfoot > tr > td.info,
.table > thead > tr > th.info,
.table > tbody > tr > th.info,
.table > tfoot > tr > th.info,
.table > thead > tr.info > td,
.table > tbody > tr.info > td,
.table > tfoot > tr.info > td,
.table > thead > tr.info > th,
.table > tbody > tr.info > th,
.table > tfoot > tr.info > th {
  background-color: #d9edf7;
}
.table-hover > tbody > tr > td.info:hover,
.table-hover > tbody > tr > th.info:hover,
.table-hover > tbody > tr.info:hover > td,
.table-hover > tbody > tr:hover > .info,
.table-hover > tbody > tr.info:hover > th {
  background-color: #c4e3f3;
}
.table > thead > tr > td.warning,
.table > tbody > tr > td.warning,
.table > tfoot > tr > td.warning,
.table > thead > tr > th.warning,
.table > tbody > tr > th.warning,
.table > tfoot > tr > th.warning,
.table > thead > tr.warning > td,
.table > tbody > tr.warning > td,
.table > tfoot > tr.warning > td,
.table > thead > tr.warning > th,
.table > tbody > tr.warning > th,
.table > tfoot > tr.warning > th {
  background-color: #fcf8e3;
}
.table-hover > tbody > tr > td.warning:hover,
.table-hover > tbody > tr > th.warning:hover,
.table-hover > tbody > tr.warning:hover > td,
.table-hover > tbody > tr:hover > .warning,
.table-hover > tbody > tr.warning:hover > th {
  background-color: #faf2cc;
}
.table > thead > tr > td.danger,
.table > tbody > tr > td.danger,
.table > tfoot > tr > td.danger,
.table > thead > tr > th.danger,
.table > tbody > tr > th.danger,
.table > tfoot > tr > th.danger,
.table > thead > tr.danger > td,
.table > tbody > tr.danger > td,
.table > tfoot > tr.danger > td,
.table > thead > tr.danger > th,
.table > tbody > tr.danger > th,
.table > tfoot > tr.danger > th {
  background-color: #f2dede;
}
.table-hover > tbody > tr > td.danger:hover,
.table-hover > tbody > tr > th.danger:hover,
.table-hover > tbody > tr.danger:hover > td,
.table-hover > tbody > tr:hover > .danger,
.table-hover > tbody > tr.danger:hover > th {
  background-color: #ebcccc;
}
.table-responsive {
  overflow-x: auto;
  min-height: 0.01%;
}
@media screen and (max-width: 767px) {
  .table-responsive {
    width: 100%;
    margin-bottom: 13.5px;
    overflow-y: hidden;
    -ms-overflow-style: -ms-autohiding-scrollbar;
    border: 1px solid #ddd;
  }
  .table-responsive > .table {
    margin-bottom: 0;
  }
  .table-responsive > .table > thead > tr > th,
  .table-responsive > .table > tbody > tr > th,
  .table-responsive > .table > tfoot > tr > th,
  .table-responsive > .table > thead > tr > td,
  .table-responsive > .table > tbody > tr > td,
  .table-responsive > .table > tfoot > tr > td {
    white-space: nowrap;
  }
  .table-responsive > .table-bordered {
    border: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:first-child,
  .table-responsive > .table-bordered > tbody > tr > th:first-child,
  .table-responsive > .table-bordered > tfoot > tr > th:first-child,
  .table-responsive > .table-bordered > thead > tr > td:first-child,
  .table-responsive > .table-bordered > tbody > tr > td:first-child,
  .table-responsive > .table-bordered > tfoot > tr > td:first-child {
    border-left: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:last-child,
  .table-responsive > .table-bordered > tbody > tr > th:last-child,
  .table-responsive > .table-bordered > tfoot > tr > th:last-child,
  .table-responsive > .table-bordered > thead > tr > td:last-child,
  .table-responsive > .table-bordered > tbody > tr > td:last-child,
  .table-responsive > .table-bordered > tfoot > tr > td:last-child {
    border-right: 0;
  }
  .table-responsive > .table-bordered > tbody > tr:last-child > th,
  .table-responsive > .table-bordered > tfoot > tr:last-child > th,
  .table-responsive > .table-bordered > tbody > tr:last-child > td,
  .table-responsive > .table-bordered > tfoot > tr:last-child > td {
    border-bottom: 0;
  }
}
fieldset {
  padding: 0;
  margin: 0;
  border: 0;
  min-width: 0;
}
legend {
  display: block;
  width: 100%;
  padding: 0;
  margin-bottom: 18px;
  font-size: 19.5px;
  line-height: inherit;
  color: #333333;
  border: 0;
  border-bottom: 1px solid #e5e5e5;
}
label {
  display: inline-block;
  max-width: 100%;
  margin-bottom: 5px;
  font-weight: bold;
}
input[type="search"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
input[type="radio"],
input[type="checkbox"] {
  margin: 4px 0 0;
  margin-top: 1px \9;
  line-height: normal;
}
input[type="file"] {
  display: block;
}
input[type="range"] {
  display: block;
  width: 100%;
}
select[multiple],
select[size] {
  height: auto;
}
input[type="file"]:focus,
input[type="radio"]:focus,
input[type="checkbox"]:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
output {
  display: block;
  padding-top: 7px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
}
.form-control {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
}
.form-control:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.form-control::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.form-control:-ms-input-placeholder {
  color: #999;
}
.form-control::-webkit-input-placeholder {
  color: #999;
}
.form-control::-ms-expand {
  border: 0;
  background-color: transparent;
}
.form-control[disabled],
.form-control[readonly],
fieldset[disabled] .form-control {
  background-color: #eeeeee;
  opacity: 1;
}
.form-control[disabled],
fieldset[disabled] .form-control {
  cursor: not-allowed;
}
textarea.form-control {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: none;
}
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  input[type="date"].form-control,
  input[type="time"].form-control,
  input[type="datetime-local"].form-control,
  input[type="month"].form-control {
    line-height: 32px;
  }
  input[type="date"].input-sm,
  input[type="time"].input-sm,
  input[type="datetime-local"].input-sm,
  input[type="month"].input-sm,
  .input-group-sm input[type="date"],
  .input-group-sm input[type="time"],
  .input-group-sm input[type="datetime-local"],
  .input-group-sm input[type="month"] {
    line-height: 30px;
  }
  input[type="date"].input-lg,
  input[type="time"].input-lg,
  input[type="datetime-local"].input-lg,
  input[type="month"].input-lg,
  .input-group-lg input[type="date"],
  .input-group-lg input[type="time"],
  .input-group-lg input[type="datetime-local"],
  .input-group-lg input[type="month"] {
    line-height: 45px;
  }
}
.form-group {
  margin-bottom: 15px;
}
.radio,
.checkbox {
  position: relative;
  display: block;
  margin-top: 10px;
  margin-bottom: 10px;
}
.radio label,
.checkbox label {
  min-height: 18px;
  padding-left: 20px;
  margin-bottom: 0;
  font-weight: normal;
  cursor: pointer;
}
.radio input[type="radio"],
.radio-inline input[type="radio"],
.checkbox input[type="checkbox"],
.checkbox-inline input[type="checkbox"] {
  position: absolute;
  margin-left: -20px;
  margin-top: 4px \9;
}
.radio + .radio,
.checkbox + .checkbox {
  margin-top: -5px;
}
.radio-inline,
.checkbox-inline {
  position: relative;
  display: inline-block;
  padding-left: 20px;
  margin-bottom: 0;
  vertical-align: middle;
  font-weight: normal;
  cursor: pointer;
}
.radio-inline + .radio-inline,
.checkbox-inline + .checkbox-inline {
  margin-top: 0;
  margin-left: 10px;
}
input[type="radio"][disabled],
input[type="checkbox"][disabled],
input[type="radio"].disabled,
input[type="checkbox"].disabled,
fieldset[disabled] input[type="radio"],
fieldset[disabled] input[type="checkbox"] {
  cursor: not-allowed;
}
.radio-inline.disabled,
.checkbox-inline.disabled,
fieldset[disabled] .radio-inline,
fieldset[disabled] .checkbox-inline {
  cursor: not-allowed;
}
.radio.disabled label,
.checkbox.disabled label,
fieldset[disabled] .radio label,
fieldset[disabled] .checkbox label {
  cursor: not-allowed;
}
.form-control-static {
  padding-top: 7px;
  padding-bottom: 7px;
  margin-bottom: 0;
  min-height: 31px;
}
.form-control-static.input-lg,
.form-control-static.input-sm {
  padding-left: 0;
  padding-right: 0;
}
.input-sm {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-sm {
  height: 30px;
  line-height: 30px;
}
textarea.input-sm,
select[multiple].input-sm {
  height: auto;
}
.form-group-sm .form-control {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.form-group-sm select.form-control {
  height: 30px;
  line-height: 30px;
}
.form-group-sm textarea.form-control,
.form-group-sm select[multiple].form-control {
  height: auto;
}
.form-group-sm .form-control-static {
  height: 30px;
  min-height: 30px;
  padding: 6px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.input-lg {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-lg {
  height: 45px;
  line-height: 45px;
}
textarea.input-lg,
select[multiple].input-lg {
  height: auto;
}
.form-group-lg .form-control {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.form-group-lg select.form-control {
  height: 45px;
  line-height: 45px;
}
.form-group-lg textarea.form-control,
.form-group-lg select[multiple].form-control {
  height: auto;
}
.form-group-lg .form-control-static {
  height: 45px;
  min-height: 35px;
  padding: 11px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.has-feedback {
  position: relative;
}
.has-feedback .form-control {
  padding-right: 40px;
}
.form-control-feedback {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 2;
  display: block;
  width: 32px;
  height: 32px;
  line-height: 32px;
  text-align: center;
  pointer-events: none;
}
.input-lg + .form-control-feedback,
.input-group-lg + .form-control-feedback,
.form-group-lg .form-control + .form-control-feedback {
  width: 45px;
  height: 45px;
  line-height: 45px;
}
.input-sm + .form-control-feedback,
.input-group-sm + .form-control-feedback,
.form-group-sm .form-control + .form-control-feedback {
  width: 30px;
  height: 30px;
  line-height: 30px;
}
.has-success .help-block,
.has-success .control-label,
.has-success .radio,
.has-success .checkbox,
.has-success .radio-inline,
.has-success .checkbox-inline,
.has-success.radio label,
.has-success.checkbox label,
.has-success.radio-inline label,
.has-success.checkbox-inline label {
  color: #3c763d;
}
.has-success .form-control {
  border-color: #3c763d;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-success .form-control:focus {
  border-color: #2b542c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
}
.has-success .input-group-addon {
  color: #3c763d;
  border-color: #3c763d;
  background-color: #dff0d8;
}
.has-success .form-control-feedback {
  color: #3c763d;
}
.has-warning .help-block,
.has-warning .control-label,
.has-warning .radio,
.has-warning .checkbox,
.has-warning .radio-inline,
.has-warning .checkbox-inline,
.has-warning.radio label,
.has-warning.checkbox label,
.has-warning.radio-inline label,
.has-warning.checkbox-inline label {
  color: #8a6d3b;
}
.has-warning .form-control {
  border-color: #8a6d3b;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-warning .form-control:focus {
  border-color: #66512c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
}
.has-warning .input-group-addon {
  color: #8a6d3b;
  border-color: #8a6d3b;
  background-color: #fcf8e3;
}
.has-warning .form-control-feedback {
  color: #8a6d3b;
}
.has-error .help-block,
.has-error .control-label,
.has-error .radio,
.has-error .checkbox,
.has-error .radio-inline,
.has-error .checkbox-inline,
.has-error.radio label,
.has-error.checkbox label,
.has-error.radio-inline label,
.has-error.checkbox-inline label {
  color: #a94442;
}
.has-error .form-control {
  border-color: #a94442;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-error .form-control:focus {
  border-color: #843534;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
}
.has-error .input-group-addon {
  color: #a94442;
  border-color: #a94442;
  background-color: #f2dede;
}
.has-error .form-control-feedback {
  color: #a94442;
}
.has-feedback label ~ .form-control-feedback {
  top: 23px;
}
.has-feedback label.sr-only ~ .form-control-feedback {
  top: 0;
}
.help-block {
  display: block;
  margin-top: 5px;
  margin-bottom: 10px;
  color: #404040;
}
@media (min-width: 768px) {
  .form-inline .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .form-inline .form-control-static {
    display: inline-block;
  }
  .form-inline .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .form-inline .input-group .input-group-addon,
  .form-inline .input-group .input-group-btn,
  .form-inline .input-group .form-control {
    width: auto;
  }
  .form-inline .input-group > .form-control {
    width: 100%;
  }
  .form-inline .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio,
  .form-inline .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio label,
  .form-inline .checkbox label {
    padding-left: 0;
  }
  .form-inline .radio input[type="radio"],
  .form-inline .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .form-inline .has-feedback .form-control-feedback {
    top: 0;
  }
}
.form-horizontal .radio,
.form-horizontal .checkbox,
.form-horizontal .radio-inline,
.form-horizontal .checkbox-inline {
  margin-top: 0;
  margin-bottom: 0;
  padding-top: 7px;
}
.form-horizontal .radio,
.form-horizontal .checkbox {
  min-height: 25px;
}
.form-horizontal .form-group {
  margin-left: 0px;
  margin-right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .control-label {
    text-align: right;
    margin-bottom: 0;
    padding-top: 7px;
  }
}
.form-horizontal .has-feedback .form-control-feedback {
  right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .form-group-lg .control-label {
    padding-top: 11px;
    font-size: 17px;
  }
}
@media (min-width: 768px) {
  .form-horizontal .form-group-sm .control-label {
    padding-top: 6px;
    font-size: 12px;
  }
}
.btn {
  display: inline-block;
  margin-bottom: 0;
  font-weight: normal;
  text-align: center;
  vertical-align: middle;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none;
  border: 1px solid transparent;
  white-space: nowrap;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  border-radius: 2px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.btn:focus,
.btn:active:focus,
.btn.active:focus,
.btn.focus,
.btn:active.focus,
.btn.active.focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
.btn:hover,
.btn:focus,
.btn.focus {
  color: #333;
  text-decoration: none;
}
.btn:active,
.btn.active {
  outline: 0;
  background-image: none;
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn.disabled,
.btn[disabled],
fieldset[disabled] .btn {
  cursor: not-allowed;
  opacity: 0.65;
  filter: alpha(opacity=65);
  -webkit-box-shadow: none;
  box-shadow: none;
}
a.btn.disabled,
fieldset[disabled] a.btn {
  pointer-events: none;
}
.btn-default {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.btn-default:focus,
.btn-default.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.btn-default:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active:hover,
.btn-default.active:hover,
.open > .dropdown-toggle.btn-default:hover,
.btn-default:active:focus,
.btn-default.active:focus,
.open > .dropdown-toggle.btn-default:focus,
.btn-default:active.focus,
.btn-default.active.focus,
.open > .dropdown-toggle.btn-default.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  background-image: none;
}
.btn-default.disabled:hover,
.btn-default[disabled]:hover,
fieldset[disabled] .btn-default:hover,
.btn-default.disabled:focus,
.btn-default[disabled]:focus,
fieldset[disabled] .btn-default:focus,
.btn-default.disabled.focus,
.btn-default[disabled].focus,
fieldset[disabled] .btn-default.focus {
  background-color: #fff;
  border-color: #ccc;
}
.btn-default .badge {
  color: #fff;
  background-color: #333;
}
.btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary:focus,
.btn-primary.focus {
  color: #fff;
  background-color: #286090;
  border-color: #122b40;
}
.btn-primary:hover {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active:hover,
.btn-primary.active:hover,
.open > .dropdown-toggle.btn-primary:hover,
.btn-primary:active:focus,
.btn-primary.active:focus,
.open > .dropdown-toggle.btn-primary:focus,
.btn-primary:active.focus,
.btn-primary.active.focus,
.open > .dropdown-toggle.btn-primary.focus {
  color: #fff;
  background-color: #204d74;
  border-color: #122b40;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  background-image: none;
}
.btn-primary.disabled:hover,
.btn-primary[disabled]:hover,
fieldset[disabled] .btn-primary:hover,
.btn-primary.disabled:focus,
.btn-primary[disabled]:focus,
fieldset[disabled] .btn-primary:focus,
.btn-primary.disabled.focus,
.btn-primary[disabled].focus,
fieldset[disabled] .btn-primary.focus {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary .badge {
  color: #337ab7;
  background-color: #fff;
}
.btn-success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success:focus,
.btn-success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.btn-success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active:hover,
.btn-success.active:hover,
.open > .dropdown-toggle.btn-success:hover,
.btn-success:active:focus,
.btn-success.active:focus,
.open > .dropdown-toggle.btn-success:focus,
.btn-success:active.focus,
.btn-success.active.focus,
.open > .dropdown-toggle.btn-success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  background-image: none;
}
.btn-success.disabled:hover,
.btn-success[disabled]:hover,
fieldset[disabled] .btn-success:hover,
.btn-success.disabled:focus,
.btn-success[disabled]:focus,
fieldset[disabled] .btn-success:focus,
.btn-success.disabled.focus,
.btn-success[disabled].focus,
fieldset[disabled] .btn-success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.btn-info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info:focus,
.btn-info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.btn-info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active:hover,
.btn-info.active:hover,
.open > .dropdown-toggle.btn-info:hover,
.btn-info:active:focus,
.btn-info.active:focus,
.open > .dropdown-toggle.btn-info:focus,
.btn-info:active.focus,
.btn-info.active.focus,
.open > .dropdown-toggle.btn-info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  background-image: none;
}
.btn-info.disabled:hover,
.btn-info[disabled]:hover,
fieldset[disabled] .btn-info:hover,
.btn-info.disabled:focus,
.btn-info[disabled]:focus,
fieldset[disabled] .btn-info:focus,
.btn-info.disabled.focus,
.btn-info[disabled].focus,
fieldset[disabled] .btn-info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.btn-warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning:focus,
.btn-warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.btn-warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active:hover,
.btn-warning.active:hover,
.open > .dropdown-toggle.btn-warning:hover,
.btn-warning:active:focus,
.btn-warning.active:focus,
.open > .dropdown-toggle.btn-warning:focus,
.btn-warning:active.focus,
.btn-warning.active.focus,
.open > .dropdown-toggle.btn-warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  background-image: none;
}
.btn-warning.disabled:hover,
.btn-warning[disabled]:hover,
fieldset[disabled] .btn-warning:hover,
.btn-warning.disabled:focus,
.btn-warning[disabled]:focus,
fieldset[disabled] .btn-warning:focus,
.btn-warning.disabled.focus,
.btn-warning[disabled].focus,
fieldset[disabled] .btn-warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.btn-danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger:focus,
.btn-danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.btn-danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active:hover,
.btn-danger.active:hover,
.open > .dropdown-toggle.btn-danger:hover,
.btn-danger:active:focus,
.btn-danger.active:focus,
.open > .dropdown-toggle.btn-danger:focus,
.btn-danger:active.focus,
.btn-danger.active.focus,
.open > .dropdown-toggle.btn-danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  background-image: none;
}
.btn-danger.disabled:hover,
.btn-danger[disabled]:hover,
fieldset[disabled] .btn-danger:hover,
.btn-danger.disabled:focus,
.btn-danger[disabled]:focus,
fieldset[disabled] .btn-danger:focus,
.btn-danger.disabled.focus,
.btn-danger[disabled].focus,
fieldset[disabled] .btn-danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger .badge {
  color: #d9534f;
  background-color: #fff;
}
.btn-link {
  color: #337ab7;
  font-weight: normal;
  border-radius: 0;
}
.btn-link,
.btn-link:active,
.btn-link.active,
.btn-link[disabled],
fieldset[disabled] .btn-link {
  background-color: transparent;
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn-link,
.btn-link:hover,
.btn-link:focus,
.btn-link:active {
  border-color: transparent;
}
.btn-link:hover,
.btn-link:focus {
  color: #23527c;
  text-decoration: underline;
  background-color: transparent;
}
.btn-link[disabled]:hover,
fieldset[disabled] .btn-link:hover,
.btn-link[disabled]:focus,
fieldset[disabled] .btn-link:focus {
  color: #777777;
  text-decoration: none;
}
.btn-lg,
.btn-group-lg > .btn {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.btn-sm,
.btn-group-sm > .btn {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-xs,
.btn-group-xs > .btn {
  padding: 1px 5px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-block {
  display: block;
  width: 100%;
}
.btn-block + .btn-block {
  margin-top: 5px;
}
input[type="submit"].btn-block,
input[type="reset"].btn-block,
input[type="button"].btn-block {
  width: 100%;
}
.fade {
  opacity: 0;
  -webkit-transition: opacity 0.15s linear;
  -o-transition: opacity 0.15s linear;
  transition: opacity 0.15s linear;
}
.fade.in {
  opacity: 1;
}
.collapse {
  display: none;
}
.collapse.in {
  display: block;
}
tr.collapse.in {
  display: table-row;
}
tbody.collapse.in {
  display: table-row-group;
}
.collapsing {
  position: relative;
  height: 0;
  overflow: hidden;
  -webkit-transition-property: height, visibility;
  transition-property: height, visibility;
  -webkit-transition-duration: 0.35s;
  transition-duration: 0.35s;
  -webkit-transition-timing-function: ease;
  transition-timing-function: ease;
}
.caret {
  display: inline-block;
  width: 0;
  height: 0;
  margin-left: 2px;
  vertical-align: middle;
  border-top: 4px dashed;
  border-top: 4px solid \9;
  border-right: 4px solid transparent;
  border-left: 4px solid transparent;
}
.dropup,
.dropdown {
  position: relative;
}
.dropdown-toggle:focus {
  outline: 0;
}
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1000;
  display: none;
  float: left;
  min-width: 160px;
  padding: 5px 0;
  margin: 2px 0 0;
  list-style: none;
  font-size: 13px;
  text-align: left;
  background-color: #fff;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.15);
  border-radius: 2px;
  -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  background-clip: padding-box;
}
.dropdown-menu.pull-right {
  right: 0;
  left: auto;
}
.dropdown-menu .divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.dropdown-menu > li > a {
  display: block;
  padding: 3px 20px;
  clear: both;
  font-weight: normal;
  line-height: 1.42857143;
  color: #333333;
  white-space: nowrap;
}
.dropdown-menu > li > a:hover,
.dropdown-menu > li > a:focus {
  text-decoration: none;
  color: #262626;
  background-color: #f5f5f5;
}
.dropdown-menu > .active > a,
.dropdown-menu > .active > a:hover,
.dropdown-menu > .active > a:focus {
  color: #fff;
  text-decoration: none;
  outline: 0;
  background-color: #337ab7;
}
.dropdown-menu > .disabled > a,
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  color: #777777;
}
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  text-decoration: none;
  background-color: transparent;
  background-image: none;
  filter: progid:DXImageTransform.Microsoft.gradient(enabled = false);
  cursor: not-allowed;
}
.open > .dropdown-menu {
  display: block;
}
.open > a {
  outline: 0;
}
.dropdown-menu-right {
  left: auto;
  right: 0;
}
.dropdown-menu-left {
  left: 0;
  right: auto;
}
.dropdown-header {
  display: block;
  padding: 3px 20px;
  font-size: 12px;
  line-height: 1.42857143;
  color: #777777;
  white-space: nowrap;
}
.dropdown-backdrop {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 990;
}
.pull-right > .dropdown-menu {
  right: 0;
  left: auto;
}
.dropup .caret,
.navbar-fixed-bottom .dropdown .caret {
  border-top: 0;
  border-bottom: 4px dashed;
  border-bottom: 4px solid \9;
  content: "";
}
.dropup .dropdown-menu,
.navbar-fixed-bottom .dropdown .dropdown-menu {
  top: auto;
  bottom: 100%;
  margin-bottom: 2px;
}
@media (min-width: 541px) {
  .navbar-right .dropdown-menu {
    left: auto;
    right: 0;
  }
  .navbar-right .dropdown-menu-left {
    left: 0;
    right: auto;
  }
}
.btn-group,
.btn-group-vertical {
  position: relative;
  display: inline-block;
  vertical-align: middle;
}
.btn-group > .btn,
.btn-group-vertical > .btn {
  position: relative;
  float: left;
}
.btn-group > .btn:hover,
.btn-group-vertical > .btn:hover,
.btn-group > .btn:focus,
.btn-group-vertical > .btn:focus,
.btn-group > .btn:active,
.btn-group-vertical > .btn:active,
.btn-group > .btn.active,
.btn-group-vertical > .btn.active {
  z-index: 2;
}
.btn-group .btn + .btn,
.btn-group .btn + .btn-group,
.btn-group .btn-group + .btn,
.btn-group .btn-group + .btn-group {
  margin-left: -1px;
}
.btn-toolbar {
  margin-left: -5px;
}
.btn-toolbar .btn,
.btn-toolbar .btn-group,
.btn-toolbar .input-group {
  float: left;
}
.btn-toolbar > .btn,
.btn-toolbar > .btn-group,
.btn-toolbar > .input-group {
  margin-left: 5px;
}
.btn-group > .btn:not(:first-child):not(:last-child):not(.dropdown-toggle) {
  border-radius: 0;
}
.btn-group > .btn:first-child {
  margin-left: 0;
}
.btn-group > .btn:first-child:not(:last-child):not(.dropdown-toggle) {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn:last-child:not(:first-child),
.btn-group > .dropdown-toggle:not(:first-child) {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group > .btn-group {
  float: left;
}
.btn-group > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group .dropdown-toggle:active,
.btn-group.open .dropdown-toggle {
  outline: 0;
}
.btn-group > .btn + .dropdown-toggle {
  padding-left: 8px;
  padding-right: 8px;
}
.btn-group > .btn-lg + .dropdown-toggle {
  padding-left: 12px;
  padding-right: 12px;
}
.btn-group.open .dropdown-toggle {
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn-group.open .dropdown-toggle.btn-link {
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn .caret {
  margin-left: 0;
}
.btn-lg .caret {
  border-width: 5px 5px 0;
  border-bottom-width: 0;
}
.dropup .btn-lg .caret {
  border-width: 0 5px 5px;
}
.btn-group-vertical > .btn,
.btn-group-vertical > .btn-group,
.btn-group-vertical > .btn-group > .btn {
  display: block;
  float: none;
  width: 100%;
  max-width: 100%;
}
.btn-group-vertical > .btn-group > .btn {
  float: none;
}
.btn-group-vertical > .btn + .btn,
.btn-group-vertical > .btn + .btn-group,
.btn-group-vertical > .btn-group + .btn,
.btn-group-vertical > .btn-group + .btn-group {
  margin-top: -1px;
  margin-left: 0;
}
.btn-group-vertical > .btn:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.btn-group-vertical > .btn:first-child:not(:last-child) {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn:last-child:not(:first-child) {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
.btn-group-vertical > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.btn-group-justified {
  display: table;
  width: 100%;
  table-layout: fixed;
  border-collapse: separate;
}
.btn-group-justified > .btn,
.btn-group-justified > .btn-group {
  float: none;
  display: table-cell;
  width: 1%;
}
.btn-group-justified > .btn-group .btn {
  width: 100%;
}
.btn-group-justified > .btn-group .dropdown-menu {
  left: auto;
}
[data-toggle="buttons"] > .btn input[type="radio"],
[data-toggle="buttons"] > .btn-group > .btn input[type="radio"],
[data-toggle="buttons"] > .btn input[type="checkbox"],
[data-toggle="buttons"] > .btn-group > .btn input[type="checkbox"] {
  position: absolute;
  clip: rect(0, 0, 0, 0);
  pointer-events: none;
}
.input-group {
  position: relative;
  display: table;
  border-collapse: separate;
}
.input-group[class*="col-"] {
  float: none;
  padding-left: 0;
  padding-right: 0;
}
.input-group .form-control {
  position: relative;
  z-index: 2;
  float: left;
  width: 100%;
  margin-bottom: 0;
}
.input-group .form-control:focus {
  z-index: 3;
}
.input-group-lg > .form-control,
.input-group-lg > .input-group-addon,
.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-group-lg > .form-control,
select.input-group-lg > .input-group-addon,
select.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  line-height: 45px;
}
textarea.input-group-lg > .form-control,
textarea.input-group-lg > .input-group-addon,
textarea.input-group-lg > .input-group-btn > .btn,
select[multiple].input-group-lg > .form-control,
select[multiple].input-group-lg > .input-group-addon,
select[multiple].input-group-lg > .input-group-btn > .btn {
  height: auto;
}
.input-group-sm > .form-control,
.input-group-sm > .input-group-addon,
.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-group-sm > .form-control,
select.input-group-sm > .input-group-addon,
select.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  line-height: 30px;
}
textarea.input-group-sm > .form-control,
textarea.input-group-sm > .input-group-addon,
textarea.input-group-sm > .input-group-btn > .btn,
select[multiple].input-group-sm > .form-control,
select[multiple].input-group-sm > .input-group-addon,
select[multiple].input-group-sm > .input-group-btn > .btn {
  height: auto;
}
.input-group-addon,
.input-group-btn,
.input-group .form-control {
  display: table-cell;
}
.input-group-addon:not(:first-child):not(:last-child),
.input-group-btn:not(:first-child):not(:last-child),
.input-group .form-control:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.input-group-addon,
.input-group-btn {
  width: 1%;
  white-space: nowrap;
  vertical-align: middle;
}
.input-group-addon {
  padding: 6px 12px;
  font-size: 13px;
  font-weight: normal;
  line-height: 1;
  color: #555555;
  text-align: center;
  background-color: #eeeeee;
  border: 1px solid #ccc;
  border-radius: 2px;
}
.input-group-addon.input-sm {
  padding: 5px 10px;
  font-size: 12px;
  border-radius: 1px;
}
.input-group-addon.input-lg {
  padding: 10px 16px;
  font-size: 17px;
  border-radius: 3px;
}
.input-group-addon input[type="radio"],
.input-group-addon input[type="checkbox"] {
  margin-top: 0;
}
.input-group .form-control:first-child,
.input-group-addon:first-child,
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group > .btn,
.input-group-btn:first-child > .dropdown-toggle,
.input-group-btn:last-child > .btn:not(:last-child):not(.dropdown-toggle),
.input-group-btn:last-child > .btn-group:not(:last-child) > .btn {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.input-group-addon:first-child {
  border-right: 0;
}
.input-group .form-control:last-child,
.input-group-addon:last-child,
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group > .btn,
.input-group-btn:last-child > .dropdown-toggle,
.input-group-btn:first-child > .btn:not(:first-child),
.input-group-btn:first-child > .btn-group:not(:first-child) > .btn {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.input-group-addon:last-child {
  border-left: 0;
}
.input-group-btn {
  position: relative;
  font-size: 0;
  white-space: nowrap;
}
.input-group-btn > .btn {
  position: relative;
}
.input-group-btn > .btn + .btn {
  margin-left: -1px;
}
.input-group-btn > .btn:hover,
.input-group-btn > .btn:focus,
.input-group-btn > .btn:active {
  z-index: 2;
}
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group {
  margin-right: -1px;
}
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group {
  z-index: 2;
  margin-left: -1px;
}
.nav {
  margin-bottom: 0;
  padding-left: 0;
  list-style: none;
}
.nav > li {
  position: relative;
  display: block;
}
.nav > li > a {
  position: relative;
  display: block;
  padding: 10px 15px;
}
.nav > li > a:hover,
.nav > li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.nav > li.disabled > a {
  color: #777777;
}
.nav > li.disabled > a:hover,
.nav > li.disabled > a:focus {
  color: #777777;
  text-decoration: none;
  background-color: transparent;
  cursor: not-allowed;
}
.nav .open > a,
.nav .open > a:hover,
.nav .open > a:focus {
  background-color: #eeeeee;
  border-color: #337ab7;
}
.nav .nav-divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.nav > li > a > img {
  max-width: none;
}
.nav-tabs {
  border-bottom: 1px solid #ddd;
}
.nav-tabs > li {
  float: left;
  margin-bottom: -1px;
}
.nav-tabs > li > a {
  margin-right: 2px;
  line-height: 1.42857143;
  border: 1px solid transparent;
  border-radius: 2px 2px 0 0;
}
.nav-tabs > li > a:hover {
  border-color: #eeeeee #eeeeee #ddd;
}
.nav-tabs > li.active > a,
.nav-tabs > li.active > a:hover,
.nav-tabs > li.active > a:focus {
  color: #555555;
  background-color: #fff;
  border: 1px solid #ddd;
  border-bottom-color: transparent;
  cursor: default;
}
.nav-tabs.nav-justified {
  width: 100%;
  border-bottom: 0;
}
.nav-tabs.nav-justified > li {
  float: none;
}
.nav-tabs.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-tabs.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-tabs.nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs.nav-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs.nav-justified > .active > a,
.nav-tabs.nav-justified > .active > a:hover,
.nav-tabs.nav-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs.nav-justified > .active > a,
  .nav-tabs.nav-justified > .active > a:hover,
  .nav-tabs.nav-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.nav-pills > li {
  float: left;
}
.nav-pills > li > a {
  border-radius: 2px;
}
.nav-pills > li + li {
  margin-left: 2px;
}
.nav-pills > li.active > a,
.nav-pills > li.active > a:hover,
.nav-pills > li.active > a:focus {
  color: #fff;
  background-color: #337ab7;
}
.nav-stacked > li {
  float: none;
}
.nav-stacked > li + li {
  margin-top: 2px;
  margin-left: 0;
}
.nav-justified {
  width: 100%;
}
.nav-justified > li {
  float: none;
}
.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs-justified {
  border-bottom: 0;
}
.nav-tabs-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs-justified > .active > a,
.nav-tabs-justified > .active > a:hover,
.nav-tabs-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs-justified > .active > a,
  .nav-tabs-justified > .active > a:hover,
  .nav-tabs-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.tab-content > .tab-pane {
  display: none;
}
.tab-content > .active {
  display: block;
}
.nav-tabs .dropdown-menu {
  margin-top: -1px;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar {
  position: relative;
  min-height: 30px;
  margin-bottom: 18px;
  border: 1px solid transparent;
}
@media (min-width: 541px) {
  .navbar {
    border-radius: 2px;
  }
}
@media (min-width: 541px) {
  .navbar-header {
    float: left;
  }
}
.navbar-collapse {
  overflow-x: visible;
  padding-right: 0px;
  padding-left: 0px;
  border-top: 1px solid transparent;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1);
  -webkit-overflow-scrolling: touch;
}
.navbar-collapse.in {
  overflow-y: auto;
}
@media (min-width: 541px) {
  .navbar-collapse {
    width: auto;
    border-top: 0;
    box-shadow: none;
  }
  .navbar-collapse.collapse {
    display: block !important;
    height: auto !important;
    padding-bottom: 0;
    overflow: visible !important;
  }
  .navbar-collapse.in {
    overflow-y: visible;
  }
  .navbar-fixed-top .navbar-collapse,
  .navbar-static-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    padding-left: 0;
    padding-right: 0;
  }
}
.navbar-fixed-top .navbar-collapse,
.navbar-fixed-bottom .navbar-collapse {
  max-height: 340px;
}
@media (max-device-width: 540px) and (orientation: landscape) {
  .navbar-fixed-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    max-height: 200px;
  }
}
.container > .navbar-header,
.container-fluid > .navbar-header,
.container > .navbar-collapse,
.container-fluid > .navbar-collapse {
  margin-right: 0px;
  margin-left: 0px;
}
@media (min-width: 541px) {
  .container > .navbar-header,
  .container-fluid > .navbar-header,
  .container > .navbar-collapse,
  .container-fluid > .navbar-collapse {
    margin-right: 0;
    margin-left: 0;
  }
}
.navbar-static-top {
  z-index: 1000;
  border-width: 0 0 1px;
}
@media (min-width: 541px) {
  .navbar-static-top {
    border-radius: 0;
  }
}
.navbar-fixed-top,
.navbar-fixed-bottom {
  position: fixed;
  right: 0;
  left: 0;
  z-index: 1030;
}
@media (min-width: 541px) {
  .navbar-fixed-top,
  .navbar-fixed-bottom {
    border-radius: 0;
  }
}
.navbar-fixed-top {
  top: 0;
  border-width: 0 0 1px;
}
.navbar-fixed-bottom {
  bottom: 0;
  margin-bottom: 0;
  border-width: 1px 0 0;
}
.navbar-brand {
  float: left;
  padding: 6px 0px;
  font-size: 17px;
  line-height: 18px;
  height: 30px;
}
.navbar-brand:hover,
.navbar-brand:focus {
  text-decoration: none;
}
.navbar-brand > img {
  display: block;
}
@media (min-width: 541px) {
  .navbar > .container .navbar-brand,
  .navbar > .container-fluid .navbar-brand {
    margin-left: 0px;
  }
}
.navbar-toggle {
  position: relative;
  float: right;
  margin-right: 0px;
  padding: 9px 10px;
  margin-top: -2px;
  margin-bottom: -2px;
  background-color: transparent;
  background-image: none;
  border: 1px solid transparent;
  border-radius: 2px;
}
.navbar-toggle:focus {
  outline: 0;
}
.navbar-toggle .icon-bar {
  display: block;
  width: 22px;
  height: 2px;
  border-radius: 1px;
}
.navbar-toggle .icon-bar + .icon-bar {
  margin-top: 4px;
}
@media (min-width: 541px) {
  .navbar-toggle {
    display: none;
  }
}
.navbar-nav {
  margin: 3px 0px;
}
.navbar-nav > li > a {
  padding-top: 10px;
  padding-bottom: 10px;
  line-height: 18px;
}
@media (max-width: 540px) {
  .navbar-nav .open .dropdown-menu {
    position: static;
    float: none;
    width: auto;
    margin-top: 0;
    background-color: transparent;
    border: 0;
    box-shadow: none;
  }
  .navbar-nav .open .dropdown-menu > li > a,
  .navbar-nav .open .dropdown-menu .dropdown-header {
    padding: 5px 15px 5px 25px;
  }
  .navbar-nav .open .dropdown-menu > li > a {
    line-height: 18px;
  }
  .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-nav .open .dropdown-menu > li > a:focus {
    background-image: none;
  }
}
@media (min-width: 541px) {
  .navbar-nav {
    float: left;
    margin: 0;
  }
  .navbar-nav > li {
    float: left;
  }
  .navbar-nav > li > a {
    padding-top: 6px;
    padding-bottom: 6px;
  }
}
.navbar-form {
  margin-left: 0px;
  margin-right: 0px;
  padding: 10px 0px;
  border-top: 1px solid transparent;
  border-bottom: 1px solid transparent;
  -webkit-box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  margin-top: -1px;
  margin-bottom: -1px;
}
@media (min-width: 768px) {
  .navbar-form .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .navbar-form .form-control-static {
    display: inline-block;
  }
  .navbar-form .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .navbar-form .input-group .input-group-addon,
  .navbar-form .input-group .input-group-btn,
  .navbar-form .input-group .form-control {
    width: auto;
  }
  .navbar-form .input-group > .form-control {
    width: 100%;
  }
  .navbar-form .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio,
  .navbar-form .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio label,
  .navbar-form .checkbox label {
    padding-left: 0;
  }
  .navbar-form .radio input[type="radio"],
  .navbar-form .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .navbar-form .has-feedback .form-control-feedback {
    top: 0;
  }
}
@media (max-width: 540px) {
  .navbar-form .form-group {
    margin-bottom: 5px;
  }
  .navbar-form .form-group:last-child {
    margin-bottom: 0;
  }
}
@media (min-width: 541px) {
  .navbar-form {
    width: auto;
    border: 0;
    margin-left: 0;
    margin-right: 0;
    padding-top: 0;
    padding-bottom: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
  }
}
.navbar-nav > li > .dropdown-menu {
  margin-top: 0;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar-fixed-bottom .navbar-nav > li > .dropdown-menu {
  margin-bottom: 0;
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.navbar-btn {
  margin-top: -1px;
  margin-bottom: -1px;
}
.navbar-btn.btn-sm {
  margin-top: 0px;
  margin-bottom: 0px;
}
.navbar-btn.btn-xs {
  margin-top: 4px;
  margin-bottom: 4px;
}
.navbar-text {
  margin-top: 6px;
  margin-bottom: 6px;
}
@media (min-width: 541px) {
  .navbar-text {
    float: left;
    margin-left: 0px;
    margin-right: 0px;
  }
}
@media (min-width: 541px) {
  .navbar-left {
    float: left !important;
    float: left;
  }
  .navbar-right {
    float: right !important;
    float: right;
    margin-right: 0px;
  }
  .navbar-right ~ .navbar-right {
    margin-right: 0;
  }
}
.navbar-default {
  background-color: #f8f8f8;
  border-color: #e7e7e7;
}
.navbar-default .navbar-brand {
  color: #777;
}
.navbar-default .navbar-brand:hover,
.navbar-default .navbar-brand:focus {
  color: #5e5e5e;
  background-color: transparent;
}
.navbar-default .navbar-text {
  color: #777;
}
.navbar-default .navbar-nav > li > a {
  color: #777;
}
.navbar-default .navbar-nav > li > a:hover,
.navbar-default .navbar-nav > li > a:focus {
  color: #333;
  background-color: transparent;
}
.navbar-default .navbar-nav > .active > a,
.navbar-default .navbar-nav > .active > a:hover,
.navbar-default .navbar-nav > .active > a:focus {
  color: #555;
  background-color: #e7e7e7;
}
.navbar-default .navbar-nav > .disabled > a,
.navbar-default .navbar-nav > .disabled > a:hover,
.navbar-default .navbar-nav > .disabled > a:focus {
  color: #ccc;
  background-color: transparent;
}
.navbar-default .navbar-toggle {
  border-color: #ddd;
}
.navbar-default .navbar-toggle:hover,
.navbar-default .navbar-toggle:focus {
  background-color: #ddd;
}
.navbar-default .navbar-toggle .icon-bar {
  background-color: #888;
}
.navbar-default .navbar-collapse,
.navbar-default .navbar-form {
  border-color: #e7e7e7;
}
.navbar-default .navbar-nav > .open > a,
.navbar-default .navbar-nav > .open > a:hover,
.navbar-default .navbar-nav > .open > a:focus {
  background-color: #e7e7e7;
  color: #555;
}
@media (max-width: 540px) {
  .navbar-default .navbar-nav .open .dropdown-menu > li > a {
    color: #777;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #333;
    background-color: transparent;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #555;
    background-color: #e7e7e7;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #ccc;
    background-color: transparent;
  }
}
.navbar-default .navbar-link {
  color: #777;
}
.navbar-default .navbar-link:hover {
  color: #333;
}
.navbar-default .btn-link {
  color: #777;
}
.navbar-default .btn-link:hover,
.navbar-default .btn-link:focus {
  color: #333;
}
.navbar-default .btn-link[disabled]:hover,
fieldset[disabled] .navbar-default .btn-link:hover,
.navbar-default .btn-link[disabled]:focus,
fieldset[disabled] .navbar-default .btn-link:focus {
  color: #ccc;
}
.navbar-inverse {
  background-color: #222;
  border-color: #080808;
}
.navbar-inverse .navbar-brand {
  color: #9d9d9d;
}
.navbar-inverse .navbar-brand:hover,
.navbar-inverse .navbar-brand:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-text {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a:hover,
.navbar-inverse .navbar-nav > li > a:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-nav > .active > a,
.navbar-inverse .navbar-nav > .active > a:hover,
.navbar-inverse .navbar-nav > .active > a:focus {
  color: #fff;
  background-color: #080808;
}
.navbar-inverse .navbar-nav > .disabled > a,
.navbar-inverse .navbar-nav > .disabled > a:hover,
.navbar-inverse .navbar-nav > .disabled > a:focus {
  color: #444;
  background-color: transparent;
}
.navbar-inverse .navbar-toggle {
  border-color: #333;
}
.navbar-inverse .navbar-toggle:hover,
.navbar-inverse .navbar-toggle:focus {
  background-color: #333;
}
.navbar-inverse .navbar-toggle .icon-bar {
  background-color: #fff;
}
.navbar-inverse .navbar-collapse,
.navbar-inverse .navbar-form {
  border-color: #101010;
}
.navbar-inverse .navbar-nav > .open > a,
.navbar-inverse .navbar-nav > .open > a:hover,
.navbar-inverse .navbar-nav > .open > a:focus {
  background-color: #080808;
  color: #fff;
}
@media (max-width: 540px) {
  .navbar-inverse .navbar-nav .open .dropdown-menu > .dropdown-header {
    border-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu .divider {
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a {
    color: #9d9d9d;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #fff;
    background-color: transparent;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #fff;
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #444;
    background-color: transparent;
  }
}
.navbar-inverse .navbar-link {
  color: #9d9d9d;
}
.navbar-inverse .navbar-link:hover {
  color: #fff;
}
.navbar-inverse .btn-link {
  color: #9d9d9d;
}
.navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link:focus {
  color: #fff;
}
.navbar-inverse .btn-link[disabled]:hover,
fieldset[disabled] .navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link[disabled]:focus,
fieldset[disabled] .navbar-inverse .btn-link:focus {
  color: #444;
}
.breadcrumb {
  padding: 8px 15px;
  margin-bottom: 18px;
  list-style: none;
  background-color: #f5f5f5;
  border-radius: 2px;
}
.breadcrumb > li {
  display: inline-block;
}
.breadcrumb > li + li:before {
  content: "/\00a0";
  padding: 0 5px;
  color: #5e5e5e;
}
.breadcrumb > .active {
  color: #777777;
}
.pagination {
  display: inline-block;
  padding-left: 0;
  margin: 18px 0;
  border-radius: 2px;
}
.pagination > li {
  display: inline;
}
.pagination > li > a,
.pagination > li > span {
  position: relative;
  float: left;
  padding: 6px 12px;
  line-height: 1.42857143;
  text-decoration: none;
  color: #337ab7;
  background-color: #fff;
  border: 1px solid #ddd;
  margin-left: -1px;
}
.pagination > li:first-child > a,
.pagination > li:first-child > span {
  margin-left: 0;
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.pagination > li:last-child > a,
.pagination > li:last-child > span {
  border-bottom-right-radius: 2px;
  border-top-right-radius: 2px;
}
.pagination > li > a:hover,
.pagination > li > span:hover,
.pagination > li > a:focus,
.pagination > li > span:focus {
  z-index: 2;
  color: #23527c;
  background-color: #eeeeee;
  border-color: #ddd;
}
.pagination > .active > a,
.pagination > .active > span,
.pagination > .active > a:hover,
.pagination > .active > span:hover,
.pagination > .active > a:focus,
.pagination > .active > span:focus {
  z-index: 3;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
  cursor: default;
}
.pagination > .disabled > span,
.pagination > .disabled > span:hover,
.pagination > .disabled > span:focus,
.pagination > .disabled > a,
.pagination > .disabled > a:hover,
.pagination > .disabled > a:focus {
  color: #777777;
  background-color: #fff;
  border-color: #ddd;
  cursor: not-allowed;
}
.pagination-lg > li > a,
.pagination-lg > li > span {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.pagination-lg > li:first-child > a,
.pagination-lg > li:first-child > span {
  border-bottom-left-radius: 3px;
  border-top-left-radius: 3px;
}
.pagination-lg > li:last-child > a,
.pagination-lg > li:last-child > span {
  border-bottom-right-radius: 3px;
  border-top-right-radius: 3px;
}
.pagination-sm > li > a,
.pagination-sm > li > span {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.pagination-sm > li:first-child > a,
.pagination-sm > li:first-child > span {
  border-bottom-left-radius: 1px;
  border-top-left-radius: 1px;
}
.pagination-sm > li:last-child > a,
.pagination-sm > li:last-child > span {
  border-bottom-right-radius: 1px;
  border-top-right-radius: 1px;
}
.pager {
  padding-left: 0;
  margin: 18px 0;
  list-style: none;
  text-align: center;
}
.pager li {
  display: inline;
}
.pager li > a,
.pager li > span {
  display: inline-block;
  padding: 5px 14px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 15px;
}
.pager li > a:hover,
.pager li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.pager .next > a,
.pager .next > span {
  float: right;
}
.pager .previous > a,
.pager .previous > span {
  float: left;
}
.pager .disabled > a,
.pager .disabled > a:hover,
.pager .disabled > a:focus,
.pager .disabled > span {
  color: #777777;
  background-color: #fff;
  cursor: not-allowed;
}
.label {
  display: inline;
  padding: .2em .6em .3em;
  font-size: 75%;
  font-weight: bold;
  line-height: 1;
  color: #fff;
  text-align: center;
  white-space: nowrap;
  vertical-align: baseline;
  border-radius: .25em;
}
a.label:hover,
a.label:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.label:empty {
  display: none;
}
.btn .label {
  position: relative;
  top: -1px;
}
.label-default {
  background-color: #777777;
}
.label-default[href]:hover,
.label-default[href]:focus {
  background-color: #5e5e5e;
}
.label-primary {
  background-color: #337ab7;
}
.label-primary[href]:hover,
.label-primary[href]:focus {
  background-color: #286090;
}
.label-success {
  background-color: #5cb85c;
}
.label-success[href]:hover,
.label-success[href]:focus {
  background-color: #449d44;
}
.label-info {
  background-color: #5bc0de;
}
.label-info[href]:hover,
.label-info[href]:focus {
  background-color: #31b0d5;
}
.label-warning {
  background-color: #f0ad4e;
}
.label-warning[href]:hover,
.label-warning[href]:focus {
  background-color: #ec971f;
}
.label-danger {
  background-color: #d9534f;
}
.label-danger[href]:hover,
.label-danger[href]:focus {
  background-color: #c9302c;
}
.badge {
  display: inline-block;
  min-width: 10px;
  padding: 3px 7px;
  font-size: 12px;
  font-weight: bold;
  color: #fff;
  line-height: 1;
  vertical-align: middle;
  white-space: nowrap;
  text-align: center;
  background-color: #777777;
  border-radius: 10px;
}
.badge:empty {
  display: none;
}
.btn .badge {
  position: relative;
  top: -1px;
}
.btn-xs .badge,
.btn-group-xs > .btn .badge {
  top: 0;
  padding: 1px 5px;
}
a.badge:hover,
a.badge:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.list-group-item.active > .badge,
.nav-pills > .active > a > .badge {
  color: #337ab7;
  background-color: #fff;
}
.list-group-item > .badge {
  float: right;
}
.list-group-item > .badge + .badge {
  margin-right: 5px;
}
.nav-pills > li > a > .badge {
  margin-left: 3px;
}
.jumbotron {
  padding-top: 30px;
  padding-bottom: 30px;
  margin-bottom: 30px;
  color: inherit;
  background-color: #eeeeee;
}
.jumbotron h1,
.jumbotron .h1 {
  color: inherit;
}
.jumbotron p {
  margin-bottom: 15px;
  font-size: 20px;
  font-weight: 200;
}
.jumbotron > hr {
  border-top-color: #d5d5d5;
}
.container .jumbotron,
.container-fluid .jumbotron {
  border-radius: 3px;
  padding-left: 0px;
  padding-right: 0px;
}
.jumbotron .container {
  max-width: 100%;
}
@media screen and (min-width: 768px) {
  .jumbotron {
    padding-top: 48px;
    padding-bottom: 48px;
  }
  .container .jumbotron,
  .container-fluid .jumbotron {
    padding-left: 60px;
    padding-right: 60px;
  }
  .jumbotron h1,
  .jumbotron .h1 {
    font-size: 59px;
  }
}
.thumbnail {
  display: block;
  padding: 4px;
  margin-bottom: 18px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: border 0.2s ease-in-out;
  -o-transition: border 0.2s ease-in-out;
  transition: border 0.2s ease-in-out;
}
.thumbnail > img,
.thumbnail a > img {
  margin-left: auto;
  margin-right: auto;
}
a.thumbnail:hover,
a.thumbnail:focus,
a.thumbnail.active {
  border-color: #337ab7;
}
.thumbnail .caption {
  padding: 9px;
  color: #000;
}
.alert {
  padding: 15px;
  margin-bottom: 18px;
  border: 1px solid transparent;
  border-radius: 2px;
}
.alert h4 {
  margin-top: 0;
  color: inherit;
}
.alert .alert-link {
  font-weight: bold;
}
.alert > p,
.alert > ul {
  margin-bottom: 0;
}
.alert > p + p {
  margin-top: 5px;
}
.alert-dismissable,
.alert-dismissible {
  padding-right: 35px;
}
.alert-dismissable .close,
.alert-dismissible .close {
  position: relative;
  top: -2px;
  right: -21px;
  color: inherit;
}
.alert-success {
  background-color: #dff0d8;
  border-color: #d6e9c6;
  color: #3c763d;
}
.alert-success hr {
  border-top-color: #c9e2b3;
}
.alert-success .alert-link {
  color: #2b542c;
}
.alert-info {
  background-color: #d9edf7;
  border-color: #bce8f1;
  color: #31708f;
}
.alert-info hr {
  border-top-color: #a6e1ec;
}
.alert-info .alert-link {
  color: #245269;
}
.alert-warning {
  background-color: #fcf8e3;
  border-color: #faebcc;
  color: #8a6d3b;
}
.alert-warning hr {
  border-top-color: #f7e1b5;
}
.alert-warning .alert-link {
  color: #66512c;
}
.alert-danger {
  background-color: #f2dede;
  border-color: #ebccd1;
  color: #a94442;
}
.alert-danger hr {
  border-top-color: #e4b9c0;
}
.alert-danger .alert-link {
  color: #843534;
}
@-webkit-keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
@keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
.progress {
  overflow: hidden;
  height: 18px;
  margin-bottom: 18px;
  background-color: #f5f5f5;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
}
.progress-bar {
  float: left;
  width: 0%;
  height: 100%;
  font-size: 12px;
  line-height: 18px;
  color: #fff;
  text-align: center;
  background-color: #337ab7;
  -webkit-box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  -webkit-transition: width 0.6s ease;
  -o-transition: width 0.6s ease;
  transition: width 0.6s ease;
}
.progress-striped .progress-bar,
.progress-bar-striped {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-size: 40px 40px;
}
.progress.active .progress-bar,
.progress-bar.active {
  -webkit-animation: progress-bar-stripes 2s linear infinite;
  -o-animation: progress-bar-stripes 2s linear infinite;
  animation: progress-bar-stripes 2s linear infinite;
}
.progress-bar-success {
  background-color: #5cb85c;
}
.progress-striped .progress-bar-success {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-info {
  background-color: #5bc0de;
}
.progress-striped .progress-bar-info {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-warning {
  background-color: #f0ad4e;
}
.progress-striped .progress-bar-warning {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-danger {
  background-color: #d9534f;
}
.progress-striped .progress-bar-danger {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.media {
  margin-top: 15px;
}
.media:first-child {
  margin-top: 0;
}
.media,
.media-body {
  zoom: 1;
  overflow: hidden;
}
.media-body {
  width: 10000px;
}
.media-object {
  display: block;
}
.media-object.img-thumbnail {
  max-width: none;
}
.media-right,
.media > .pull-right {
  padding-left: 10px;
}
.media-left,
.media > .pull-left {
  padding-right: 10px;
}
.media-left,
.media-right,
.media-body {
  display: table-cell;
  vertical-align: top;
}
.media-middle {
  vertical-align: middle;
}
.media-bottom {
  vertical-align: bottom;
}
.media-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.media-list {
  padding-left: 0;
  list-style: none;
}
.list-group {
  margin-bottom: 20px;
  padding-left: 0;
}
.list-group-item {
  position: relative;
  display: block;
  padding: 10px 15px;
  margin-bottom: -1px;
  background-color: #fff;
  border: 1px solid #ddd;
}
.list-group-item:first-child {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
}
.list-group-item:last-child {
  margin-bottom: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
a.list-group-item,
button.list-group-item {
  color: #555;
}
a.list-group-item .list-group-item-heading,
button.list-group-item .list-group-item-heading {
  color: #333;
}
a.list-group-item:hover,
button.list-group-item:hover,
a.list-group-item:focus,
button.list-group-item:focus {
  text-decoration: none;
  color: #555;
  background-color: #f5f5f5;
}
button.list-group-item {
  width: 100%;
  text-align: left;
}
.list-group-item.disabled,
.list-group-item.disabled:hover,
.list-group-item.disabled:focus {
  background-color: #eeeeee;
  color: #777777;
  cursor: not-allowed;
}
.list-group-item.disabled .list-group-item-heading,
.list-group-item.disabled:hover .list-group-item-heading,
.list-group-item.disabled:focus .list-group-item-heading {
  color: inherit;
}
.list-group-item.disabled .list-group-item-text,
.list-group-item.disabled:hover .list-group-item-text,
.list-group-item.disabled:focus .list-group-item-text {
  color: #777777;
}
.list-group-item.active,
.list-group-item.active:hover,
.list-group-item.active:focus {
  z-index: 2;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.list-group-item.active .list-group-item-heading,
.list-group-item.active:hover .list-group-item-heading,
.list-group-item.active:focus .list-group-item-heading,
.list-group-item.active .list-group-item-heading > small,
.list-group-item.active:hover .list-group-item-heading > small,
.list-group-item.active:focus .list-group-item-heading > small,
.list-group-item.active .list-group-item-heading > .small,
.list-group-item.active:hover .list-group-item-heading > .small,
.list-group-item.active:focus .list-group-item-heading > .small {
  color: inherit;
}
.list-group-item.active .list-group-item-text,
.list-group-item.active:hover .list-group-item-text,
.list-group-item.active:focus .list-group-item-text {
  color: #c7ddef;
}
.list-group-item-success {
  color: #3c763d;
  background-color: #dff0d8;
}
a.list-group-item-success,
button.list-group-item-success {
  color: #3c763d;
}
a.list-group-item-success .list-group-item-heading,
button.list-group-item-success .list-group-item-heading {
  color: inherit;
}
a.list-group-item-success:hover,
button.list-group-item-success:hover,
a.list-group-item-success:focus,
button.list-group-item-success:focus {
  color: #3c763d;
  background-color: #d0e9c6;
}
a.list-group-item-success.active,
button.list-group-item-success.active,
a.list-group-item-success.active:hover,
button.list-group-item-success.active:hover,
a.list-group-item-success.active:focus,
button.list-group-item-success.active:focus {
  color: #fff;
  background-color: #3c763d;
  border-color: #3c763d;
}
.list-group-item-info {
  color: #31708f;
  background-color: #d9edf7;
}
a.list-group-item-info,
button.list-group-item-info {
  color: #31708f;
}
a.list-group-item-info .list-group-item-heading,
button.list-group-item-info .list-group-item-heading {
  color: inherit;
}
a.list-group-item-info:hover,
button.list-group-item-info:hover,
a.list-group-item-info:focus,
button.list-group-item-info:focus {
  color: #31708f;
  background-color: #c4e3f3;
}
a.list-group-item-info.active,
button.list-group-item-info.active,
a.list-group-item-info.active:hover,
button.list-group-item-info.active:hover,
a.list-group-item-info.active:focus,
button.list-group-item-info.active:focus {
  color: #fff;
  background-color: #31708f;
  border-color: #31708f;
}
.list-group-item-warning {
  color: #8a6d3b;
  background-color: #fcf8e3;
}
a.list-group-item-warning,
button.list-group-item-warning {
  color: #8a6d3b;
}
a.list-group-item-warning .list-group-item-heading,
button.list-group-item-warning .list-group-item-heading {
  color: inherit;
}
a.list-group-item-warning:hover,
button.list-group-item-warning:hover,
a.list-group-item-warning:focus,
button.list-group-item-warning:focus {
  color: #8a6d3b;
  background-color: #faf2cc;
}
a.list-group-item-warning.active,
button.list-group-item-warning.active,
a.list-group-item-warning.active:hover,
button.list-group-item-warning.active:hover,
a.list-group-item-warning.active:focus,
button.list-group-item-warning.active:focus {
  color: #fff;
  background-color: #8a6d3b;
  border-color: #8a6d3b;
}
.list-group-item-danger {
  color: #a94442;
  background-color: #f2dede;
}
a.list-group-item-danger,
button.list-group-item-danger {
  color: #a94442;
}
a.list-group-item-danger .list-group-item-heading,
button.list-group-item-danger .list-group-item-heading {
  color: inherit;
}
a.list-group-item-danger:hover,
button.list-group-item-danger:hover,
a.list-group-item-danger:focus,
button.list-group-item-danger:focus {
  color: #a94442;
  background-color: #ebcccc;
}
a.list-group-item-danger.active,
button.list-group-item-danger.active,
a.list-group-item-danger.active:hover,
button.list-group-item-danger.active:hover,
a.list-group-item-danger.active:focus,
button.list-group-item-danger.active:focus {
  color: #fff;
  background-color: #a94442;
  border-color: #a94442;
}
.list-group-item-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.list-group-item-text {
  margin-bottom: 0;
  line-height: 1.3;
}
.panel {
  margin-bottom: 18px;
  background-color: #fff;
  border: 1px solid transparent;
  border-radius: 2px;
  -webkit-box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
}
.panel-body {
  padding: 15px;
}
.panel-heading {
  padding: 10px 15px;
  border-bottom: 1px solid transparent;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel-heading > .dropdown .dropdown-toggle {
  color: inherit;
}
.panel-title {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 15px;
  color: inherit;
}
.panel-title > a,
.panel-title > small,
.panel-title > .small,
.panel-title > small > a,
.panel-title > .small > a {
  color: inherit;
}
.panel-footer {
  padding: 10px 15px;
  background-color: #f5f5f5;
  border-top: 1px solid #ddd;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .list-group,
.panel > .panel-collapse > .list-group {
  margin-bottom: 0;
}
.panel > .list-group .list-group-item,
.panel > .panel-collapse > .list-group .list-group-item {
  border-width: 1px 0;
  border-radius: 0;
}
.panel > .list-group:first-child .list-group-item:first-child,
.panel > .panel-collapse > .list-group:first-child .list-group-item:first-child {
  border-top: 0;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .list-group:last-child .list-group-item:last-child,
.panel > .panel-collapse > .list-group:last-child .list-group-item:last-child {
  border-bottom: 0;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .panel-heading + .panel-collapse > .list-group .list-group-item:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.panel-heading + .list-group .list-group-item:first-child {
  border-top-width: 0;
}
.list-group + .panel-footer {
  border-top-width: 0;
}
.panel > .table,
.panel > .table-responsive > .table,
.panel > .panel-collapse > .table {
  margin-bottom: 0;
}
.panel > .table caption,
.panel > .table-responsive > .table caption,
.panel > .panel-collapse > .table caption {
  padding-left: 15px;
  padding-right: 15px;
}
.panel > .table:first-child,
.panel > .table-responsive:first-child > .table:first-child {
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child {
  border-top-left-radius: 1px;
  border-top-right-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:first-child {
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:last-child {
  border-top-right-radius: 1px;
}
.panel > .table:last-child,
.panel > .table-responsive:last-child > .table:last-child {
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child {
  border-bottom-left-radius: 1px;
  border-bottom-right-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:first-child {
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:last-child {
  border-bottom-right-radius: 1px;
}
.panel > .panel-body + .table,
.panel > .panel-body + .table-responsive,
.panel > .table + .panel-body,
.panel > .table-responsive + .panel-body {
  border-top: 1px solid #ddd;
}
.panel > .table > tbody:first-child > tr:first-child th,
.panel > .table > tbody:first-child > tr:first-child td {
  border-top: 0;
}
.panel > .table-bordered,
.panel > .table-responsive > .table-bordered {
  border: 0;
}
.panel > .table-bordered > thead > tr > th:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:first-child,
.panel > .table-bordered > tbody > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:first-child,
.panel > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-bordered > thead > tr > td:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:first-child,
.panel > .table-bordered > tbody > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:first-child,
.panel > .table-bordered > tfoot > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:first-child {
  border-left: 0;
}
.panel > .table-bordered > thead > tr > th:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:last-child,
.panel > .table-bordered > tbody > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:last-child,
.panel > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-bordered > thead > tr > td:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:last-child,
.panel > .table-bordered > tbody > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:last-child,
.panel > .table-bordered > tfoot > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:last-child {
  border-right: 0;
}
.panel > .table-bordered > thead > tr:first-child > td,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > td,
.panel > .table-bordered > tbody > tr:first-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > td,
.panel > .table-bordered > thead > tr:first-child > th,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > th,
.panel > .table-bordered > tbody > tr:first-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > th {
  border-bottom: 0;
}
.panel > .table-bordered > tbody > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > td,
.panel > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-bordered > tbody > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > th,
.panel > .table-bordered > tfoot > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > th {
  border-bottom: 0;
}
.panel > .table-responsive {
  border: 0;
  margin-bottom: 0;
}
.panel-group {
  margin-bottom: 18px;
}
.panel-group .panel {
  margin-bottom: 0;
  border-radius: 2px;
}
.panel-group .panel + .panel {
  margin-top: 5px;
}
.panel-group .panel-heading {
  border-bottom: 0;
}
.panel-group .panel-heading + .panel-collapse > .panel-body,
.panel-group .panel-heading + .panel-collapse > .list-group {
  border-top: 1px solid #ddd;
}
.panel-group .panel-footer {
  border-top: 0;
}
.panel-group .panel-footer + .panel-collapse .panel-body {
  border-bottom: 1px solid #ddd;
}
.panel-default {
  border-color: #ddd;
}
.panel-default > .panel-heading {
  color: #333333;
  background-color: #f5f5f5;
  border-color: #ddd;
}
.panel-default > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ddd;
}
.panel-default > .panel-heading .badge {
  color: #f5f5f5;
  background-color: #333333;
}
.panel-default > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ddd;
}
.panel-primary {
  border-color: #337ab7;
}
.panel-primary > .panel-heading {
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.panel-primary > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #337ab7;
}
.panel-primary > .panel-heading .badge {
  color: #337ab7;
  background-color: #fff;
}
.panel-primary > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #337ab7;
}
.panel-success {
  border-color: #d6e9c6;
}
.panel-success > .panel-heading {
  color: #3c763d;
  background-color: #dff0d8;
  border-color: #d6e9c6;
}
.panel-success > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #d6e9c6;
}
.panel-success > .panel-heading .badge {
  color: #dff0d8;
  background-color: #3c763d;
}
.panel-success > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #d6e9c6;
}
.panel-info {
  border-color: #bce8f1;
}
.panel-info > .panel-heading {
  color: #31708f;
  background-color: #d9edf7;
  border-color: #bce8f1;
}
.panel-info > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #bce8f1;
}
.panel-info > .panel-heading .badge {
  color: #d9edf7;
  background-color: #31708f;
}
.panel-info > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #bce8f1;
}
.panel-warning {
  border-color: #faebcc;
}
.panel-warning > .panel-heading {
  color: #8a6d3b;
  background-color: #fcf8e3;
  border-color: #faebcc;
}
.panel-warning > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #faebcc;
}
.panel-warning > .panel-heading .badge {
  color: #fcf8e3;
  background-color: #8a6d3b;
}
.panel-warning > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #faebcc;
}
.panel-danger {
  border-color: #ebccd1;
}
.panel-danger > .panel-heading {
  color: #a94442;
  background-color: #f2dede;
  border-color: #ebccd1;
}
.panel-danger > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ebccd1;
}
.panel-danger > .panel-heading .badge {
  color: #f2dede;
  background-color: #a94442;
}
.panel-danger > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ebccd1;
}
.embed-responsive {
  position: relative;
  display: block;
  height: 0;
  padding: 0;
  overflow: hidden;
}
.embed-responsive .embed-responsive-item,
.embed-responsive iframe,
.embed-responsive embed,
.embed-responsive object,
.embed-responsive video {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  height: 100%;
  width: 100%;
  border: 0;
}
.embed-responsive-16by9 {
  padding-bottom: 56.25%;
}
.embed-responsive-4by3 {
  padding-bottom: 75%;
}
.well {
  min-height: 20px;
  padding: 19px;
  margin-bottom: 20px;
  background-color: #f5f5f5;
  border: 1px solid #e3e3e3;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
}
.well blockquote {
  border-color: #ddd;
  border-color: rgba(0, 0, 0, 0.15);
}
.well-lg {
  padding: 24px;
  border-radius: 3px;
}
.well-sm {
  padding: 9px;
  border-radius: 1px;
}
.close {
  float: right;
  font-size: 19.5px;
  font-weight: bold;
  line-height: 1;
  color: #000;
  text-shadow: 0 1px 0 #fff;
  opacity: 0.2;
  filter: alpha(opacity=20);
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
  opacity: 0.5;
  filter: alpha(opacity=50);
}
button.close {
  padding: 0;
  cursor: pointer;
  background: transparent;
  border: 0;
  -webkit-appearance: none;
}
.modal-open {
  overflow: hidden;
}
.modal {
  display: none;
  overflow: hidden;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1050;
  -webkit-overflow-scrolling: touch;
  outline: 0;
}
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, -25%);
  -ms-transform: translate(0, -25%);
  -o-transform: translate(0, -25%);
  transform: translate(0, -25%);
  -webkit-transition: -webkit-transform 0.3s ease-out;
  -moz-transition: -moz-transform 0.3s ease-out;
  -o-transition: -o-transform 0.3s ease-out;
  transition: transform 0.3s ease-out;
}
.modal.in .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
.modal-open .modal {
  overflow-x: hidden;
  overflow-y: auto;
}
.modal-dialog {
  position: relative;
  width: auto;
  margin: 10px;
}
.modal-content {
  position: relative;
  background-color: #fff;
  border: 1px solid #999;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  background-clip: padding-box;
  outline: 0;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1040;
  background-color: #000;
}
.modal-backdrop.fade {
  opacity: 0;
  filter: alpha(opacity=0);
}
.modal-backdrop.in {
  opacity: 0.5;
  filter: alpha(opacity=50);
}
.modal-header {
  padding: 15px;
  border-bottom: 1px solid #e5e5e5;
}
.modal-header .close {
  margin-top: -2px;
}
.modal-title {
  margin: 0;
  line-height: 1.42857143;
}
.modal-body {
  position: relative;
  padding: 15px;
}
.modal-footer {
  padding: 15px;
  text-align: right;
  border-top: 1px solid #e5e5e5;
}
.modal-footer .btn + .btn {
  margin-left: 5px;
  margin-bottom: 0;
}
.modal-footer .btn-group .btn + .btn {
  margin-left: -1px;
}
.modal-footer .btn-block + .btn-block {
  margin-left: 0;
}
.modal-scrollbar-measure {
  position: absolute;
  top: -9999px;
  width: 50px;
  height: 50px;
  overflow: scroll;
}
@media (min-width: 768px) {
  .modal-dialog {
    width: 600px;
    margin: 30px auto;
  }
  .modal-content {
    -webkit-box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
  }
  .modal-sm {
    width: 300px;
  }
}
@media (min-width: 992px) {
  .modal-lg {
    width: 900px;
  }
}
.tooltip {
  position: absolute;
  z-index: 1070;
  display: block;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 12px;
  opacity: 0;
  filter: alpha(opacity=0);
}
.tooltip.in {
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.tooltip.top {
  margin-top: -3px;
  padding: 5px 0;
}
.tooltip.right {
  margin-left: 3px;
  padding: 0 5px;
}
.tooltip.bottom {
  margin-top: 3px;
  padding: 5px 0;
}
.tooltip.left {
  margin-left: -3px;
  padding: 0 5px;
}
.tooltip-inner {
  max-width: 200px;
  padding: 3px 8px;
  color: #fff;
  text-align: center;
  background-color: #000;
  border-radius: 2px;
}
.tooltip-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.tooltip.top .tooltip-arrow {
  bottom: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-left .tooltip-arrow {
  bottom: 0;
  right: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-right .tooltip-arrow {
  bottom: 0;
  left: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.right .tooltip-arrow {
  top: 50%;
  left: 0;
  margin-top: -5px;
  border-width: 5px 5px 5px 0;
  border-right-color: #000;
}
.tooltip.left .tooltip-arrow {
  top: 50%;
  right: 0;
  margin-top: -5px;
  border-width: 5px 0 5px 5px;
  border-left-color: #000;
}
.tooltip.bottom .tooltip-arrow {
  top: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-left .tooltip-arrow {
  top: 0;
  right: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-right .tooltip-arrow {
  top: 0;
  left: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.popover {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1060;
  display: none;
  max-width: 276px;
  padding: 1px;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 13px;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}
.popover.top {
  margin-top: -10px;
}
.popover.right {
  margin-left: 10px;
}
.popover.bottom {
  margin-top: 10px;
}
.popover.left {
  margin-left: -10px;
}
.popover-title {
  margin: 0;
  padding: 8px 14px;
  font-size: 13px;
  background-color: #f7f7f7;
  border-bottom: 1px solid #ebebeb;
  border-radius: 2px 2px 0 0;
}
.popover-content {
  padding: 9px 14px;
}
.popover > .arrow,
.popover > .arrow:after {
  position: absolute;
  display: block;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.popover > .arrow {
  border-width: 11px;
}
.popover > .arrow:after {
  border-width: 10px;
  content: "";
}
.popover.top > .arrow {
  left: 50%;
  margin-left: -11px;
  border-bottom-width: 0;
  border-top-color: #999999;
  border-top-color: rgba(0, 0, 0, 0.25);
  bottom: -11px;
}
.popover.top > .arrow:after {
  content: " ";
  bottom: 1px;
  margin-left: -10px;
  border-bottom-width: 0;
  border-top-color: #fff;
}
.popover.right > .arrow {
  top: 50%;
  left: -11px;
  margin-top: -11px;
  border-left-width: 0;
  border-right-color: #999999;
  border-right-color: rgba(0, 0, 0, 0.25);
}
.popover.right > .arrow:after {
  content: " ";
  left: 1px;
  bottom: -10px;
  border-left-width: 0;
  border-right-color: #fff;
}
.popover.bottom > .arrow {
  left: 50%;
  margin-left: -11px;
  border-top-width: 0;
  border-bottom-color: #999999;
  border-bottom-color: rgba(0, 0, 0, 0.25);
  top: -11px;
}
.popover.bottom > .arrow:after {
  content: " ";
  top: 1px;
  margin-left: -10px;
  border-top-width: 0;
  border-bottom-color: #fff;
}
.popover.left > .arrow {
  top: 50%;
  right: -11px;
  margin-top: -11px;
  border-right-width: 0;
  border-left-color: #999999;
  border-left-color: rgba(0, 0, 0, 0.25);
}
.popover.left > .arrow:after {
  content: " ";
  right: 1px;
  border-right-width: 0;
  border-left-color: #fff;
  bottom: -10px;
}
.carousel {
  position: relative;
}
.carousel-inner {
  position: relative;
  overflow: hidden;
  width: 100%;
}
.carousel-inner > .item {
  display: none;
  position: relative;
  -webkit-transition: 0.6s ease-in-out left;
  -o-transition: 0.6s ease-in-out left;
  transition: 0.6s ease-in-out left;
}
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  line-height: 1;
}
@media all and (transform-3d), (-webkit-transform-3d) {
  .carousel-inner > .item {
    -webkit-transition: -webkit-transform 0.6s ease-in-out;
    -moz-transition: -moz-transform 0.6s ease-in-out;
    -o-transition: -o-transform 0.6s ease-in-out;
    transition: transform 0.6s ease-in-out;
    -webkit-backface-visibility: hidden;
    -moz-backface-visibility: hidden;
    backface-visibility: hidden;
    -webkit-perspective: 1000px;
    -moz-perspective: 1000px;
    perspective: 1000px;
  }
  .carousel-inner > .item.next,
  .carousel-inner > .item.active.right {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.prev,
  .carousel-inner > .item.active.left {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.next.left,
  .carousel-inner > .item.prev.right,
  .carousel-inner > .item.active {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    left: 0;
  }
}
.carousel-inner > .active,
.carousel-inner > .next,
.carousel-inner > .prev {
  display: block;
}
.carousel-inner > .active {
  left: 0;
}
.carousel-inner > .next,
.carousel-inner > .prev {
  position: absolute;
  top: 0;
  width: 100%;
}
.carousel-inner > .next {
  left: 100%;
}
.carousel-inner > .prev {
  left: -100%;
}
.carousel-inner > .next.left,
.carousel-inner > .prev.right {
  left: 0;
}
.carousel-inner > .active.left {
  left: -100%;
}
.carousel-inner > .active.right {
  left: 100%;
}
.carousel-control {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 15%;
  opacity: 0.5;
  filter: alpha(opacity=50);
  font-size: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
  background-color: rgba(0, 0, 0, 0);
}
.carousel-control.left {
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#80000000', endColorstr='#00000000', GradientType=1);
}
.carousel-control.right {
  left: auto;
  right: 0;
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#00000000', endColorstr='#80000000', GradientType=1);
}
.carousel-control:hover,
.carousel-control:focus {
  outline: 0;
  color: #fff;
  text-decoration: none;
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.carousel-control .icon-prev,
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-left,
.carousel-control .glyphicon-chevron-right {
  position: absolute;
  top: 50%;
  margin-top: -10px;
  z-index: 5;
  display: inline-block;
}
.carousel-control .icon-prev,
.carousel-control .glyphicon-chevron-left {
  left: 50%;
  margin-left: -10px;
}
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-right {
  right: 50%;
  margin-right: -10px;
}
.carousel-control .icon-prev,
.carousel-control .icon-next {
  width: 20px;
  height: 20px;
  line-height: 1;
  font-family: serif;
}
.carousel-control .icon-prev:before {
  content: '\2039';
}
.carousel-control .icon-next:before {
  content: '\203a';
}
.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  z-index: 15;
  width: 60%;
  margin-left: -30%;
  padding-left: 0;
  list-style: none;
  text-align: center;
}
.carousel-indicators li {
  display: inline-block;
  width: 10px;
  height: 10px;
  margin: 1px;
  text-indent: -999px;
  border: 1px solid #fff;
  border-radius: 10px;
  cursor: pointer;
  background-color: #000 \9;
  background-color: rgba(0, 0, 0, 0);
}
.carousel-indicators .active {
  margin: 0;
  width: 12px;
  height: 12px;
  background-color: #fff;
}
.carousel-caption {
  position: absolute;
  left: 15%;
  right: 15%;
  bottom: 20px;
  z-index: 10;
  padding-top: 20px;
  padding-bottom: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
}
.carousel-caption .btn {
  text-shadow: none;
}
@media screen and (min-width: 768px) {
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-prev,
  .carousel-control .icon-next {
    width: 30px;
    height: 30px;
    margin-top: -10px;
    font-size: 30px;
  }
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .icon-prev {
    margin-left: -10px;
  }
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-next {
    margin-right: -10px;
  }
  .carousel-caption {
    left: 20%;
    right: 20%;
    padding-bottom: 30px;
  }
  .carousel-indicators {
    bottom: 20px;
  }
}
.clearfix:before,
.clearfix:after,
.dl-horizontal dd:before,
.dl-horizontal dd:after,
.container:before,
.container:after,
.container-fluid:before,
.container-fluid:after,
.row:before,
.row:after,
.form-horizontal .form-group:before,
.form-horizontal .form-group:after,
.btn-toolbar:before,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:before,
.btn-group-vertical > .btn-group:after,
.nav:before,
.nav:after,
.navbar:before,
.navbar:after,
.navbar-header:before,
.navbar-header:after,
.navbar-collapse:before,
.navbar-collapse:after,
.pager:before,
.pager:after,
.panel-body:before,
.panel-body:after,
.modal-header:before,
.modal-header:after,
.modal-footer:before,
.modal-footer:after,
.item_buttons:before,
.item_buttons:after {
  content: " ";
  display: table;
}
.clearfix:after,
.dl-horizontal dd:after,
.container:after,
.container-fluid:after,
.row:after,
.form-horizontal .form-group:after,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:after,
.nav:after,
.navbar:after,
.navbar-header:after,
.navbar-collapse:after,
.pager:after,
.panel-body:after,
.modal-header:after,
.modal-footer:after,
.item_buttons:after {
  clear: both;
}
.center-block {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.pull-right {
  float: right !important;
}
.pull-left {
  float: left !important;
}
.hide {
  display: none !important;
}
.show {
  display: block !important;
}
.invisible {
  visibility: hidden;
}
.text-hide {
  font: 0/0 a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
.hidden {
  display: none !important;
}
.affix {
  position: fixed;
}
@-ms-viewport {
  width: device-width;
}
.visible-xs,
.visible-sm,
.visible-md,
.visible-lg {
  display: none !important;
}
.visible-xs-block,
.visible-xs-inline,
.visible-xs-inline-block,
.visible-sm-block,
.visible-sm-inline,
.visible-sm-inline-block,
.visible-md-block,
.visible-md-inline,
.visible-md-inline-block,
.visible-lg-block,
.visible-lg-inline,
.visible-lg-inline-block {
  display: none !important;
}
@media (max-width: 767px) {
  .visible-xs {
    display: block !important;
  }
  table.visible-xs {
    display: table !important;
  }
  tr.visible-xs {
    display: table-row !important;
  }
  th.visible-xs,
  td.visible-xs {
    display: table-cell !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-block {
    display: block !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline {
    display: inline !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm {
    display: block !important;
  }
  table.visible-sm {
    display: table !important;
  }
  tr.visible-sm {
    display: table-row !important;
  }
  th.visible-sm,
  td.visible-sm {
    display: table-cell !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-block {
    display: block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline {
    display: inline !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md {
    display: block !important;
  }
  table.visible-md {
    display: table !important;
  }
  tr.visible-md {
    display: table-row !important;
  }
  th.visible-md,
  td.visible-md {
    display: table-cell !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-block {
    display: block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline {
    display: inline !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg {
    display: block !important;
  }
  table.visible-lg {
    display: table !important;
  }
  tr.visible-lg {
    display: table-row !important;
  }
  th.visible-lg,
  td.visible-lg {
    display: table-cell !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-block {
    display: block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline {
    display: inline !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline-block {
    display: inline-block !important;
  }
}
@media (max-width: 767px) {
  .hidden-xs {
    display: none !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .hidden-sm {
    display: none !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .hidden-md {
    display: none !important;
  }
}
@media (min-width: 1200px) {
  .hidden-lg {
    display: none !important;
  }
}
.visible-print {
  display: none !important;
}
@media print {
  .visible-print {
    display: block !important;
  }
  table.visible-print {
    display: table !important;
  }
  tr.visible-print {
    display: table-row !important;
  }
  th.visible-print,
  td.visible-print {
    display: table-cell !important;
  }
}
.visible-print-block {
  display: none !important;
}
@media print {
  .visible-print-block {
    display: block !important;
  }
}
.visible-print-inline {
  display: none !important;
}
@media print {
  .visible-print-inline {
    display: inline !important;
  }
}
.visible-print-inline-block {
  display: none !important;
}
@media print {
  .visible-print-inline-block {
    display: inline-block !important;
  }
}
@media print {
  .hidden-print {
    display: none !important;
  }
}
/*!
*
* Font Awesome
*
*/
/*!
 *  Font Awesome 4.7.0 by @davegandy - http://fontawesome.io - @fontawesome
 *  License - http://fontawesome.io/license (Font: SIL OFL 1.1, CSS: MIT License)
 */
/* FONT PATH
 * -------------------------- */
@font-face {
  font-family: 'FontAwesome';
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?v=4.7.0');
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?#iefix&v=4.7.0') format('embedded-opentype'), url('../components/font-awesome/fonts/fontawesome-webfont.woff2?v=4.7.0') format('woff2'), url('../components/font-awesome/fonts/fontawesome-webfont.woff?v=4.7.0') format('woff'), url('../components/font-awesome/fonts/fontawesome-webfont.ttf?v=4.7.0') format('truetype'), url('../components/font-awesome/fonts/fontawesome-webfont.svg?v=4.7.0#fontawesomeregular') format('svg');
  font-weight: normal;
  font-style: normal;
}
.fa {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
/* makes the font 33% larger relative to the icon container */
.fa-lg {
  font-size: 1.33333333em;
  line-height: 0.75em;
  vertical-align: -15%;
}
.fa-2x {
  font-size: 2em;
}
.fa-3x {
  font-size: 3em;
}
.fa-4x {
  font-size: 4em;
}
.fa-5x {
  font-size: 5em;
}
.fa-fw {
  width: 1.28571429em;
  text-align: center;
}
.fa-ul {
  padding-left: 0;
  margin-left: 2.14285714em;
  list-style-type: none;
}
.fa-ul > li {
  position: relative;
}
.fa-li {
  position: absolute;
  left: -2.14285714em;
  width: 2.14285714em;
  top: 0.14285714em;
  text-align: center;
}
.fa-li.fa-lg {
  left: -1.85714286em;
}
.fa-border {
  padding: .2em .25em .15em;
  border: solid 0.08em #eee;
  border-radius: .1em;
}
.fa-pull-left {
  float: left;
}
.fa-pull-right {
  float: right;
}
.fa.fa-pull-left {
  margin-right: .3em;
}
.fa.fa-pull-right {
  margin-left: .3em;
}
/* Deprecated as of 4.4.0 */
.pull-right {
  float: right;
}
.pull-left {
  float: left;
}
.fa.pull-left {
  margin-right: .3em;
}
.fa.pull-right {
  margin-left: .3em;
}
.fa-spin {
  -webkit-animation: fa-spin 2s infinite linear;
  animation: fa-spin 2s infinite linear;
}
.fa-pulse {
  -webkit-animation: fa-spin 1s infinite steps(8);
  animation: fa-spin 1s infinite steps(8);
}
@-webkit-keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
@keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
.fa-rotate-90 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=1)";
  -webkit-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
  transform: rotate(90deg);
}
.fa-rotate-180 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2)";
  -webkit-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  transform: rotate(180deg);
}
.fa-rotate-270 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=3)";
  -webkit-transform: rotate(270deg);
  -ms-transform: rotate(270deg);
  transform: rotate(270deg);
}
.fa-flip-horizontal {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=0, mirror=1)";
  -webkit-transform: scale(-1, 1);
  -ms-transform: scale(-1, 1);
  transform: scale(-1, 1);
}
.fa-flip-vertical {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2, mirror=1)";
  -webkit-transform: scale(1, -1);
  -ms-transform: scale(1, -1);
  transform: scale(1, -1);
}
:root .fa-rotate-90,
:root .fa-rotate-180,
:root .fa-rotate-270,
:root .fa-flip-horizontal,
:root .fa-flip-vertical {
  filter: none;
}
.fa-stack {
  position: relative;
  display: inline-block;
  width: 2em;
  height: 2em;
  line-height: 2em;
  vertical-align: middle;
}
.fa-stack-1x,
.fa-stack-2x {
  position: absolute;
  left: 0;
  width: 100%;
  text-align: center;
}
.fa-stack-1x {
  line-height: inherit;
}
.fa-stack-2x {
  font-size: 2em;
}
.fa-inverse {
  color: #fff;
}
/* Font Awesome uses the Unicode Private Use Area (PUA) to ensure screen
   readers do not read off random characters that represent icons */
.fa-glass:before {
  content: "\f000";
}
.fa-music:before {
  content: "\f001";
}
.fa-search:before {
  content: "\f002";
}
.fa-envelope-o:before {
  content: "\f003";
}
.fa-heart:before {
  content: "\f004";
}
.fa-star:before {
  content: "\f005";
}
.fa-star-o:before {
  content: "\f006";
}
.fa-user:before {
  content: "\f007";
}
.fa-film:before {
  content: "\f008";
}
.fa-th-large:before {
  content: "\f009";
}
.fa-th:before {
  content: "\f00a";
}
.fa-th-list:before {
  content: "\f00b";
}
.fa-check:before {
  content: "\f00c";
}
.fa-remove:before,
.fa-close:before,
.fa-times:before {
  content: "\f00d";
}
.fa-search-plus:before {
  content: "\f00e";
}
.fa-search-minus:before {
  content: "\f010";
}
.fa-power-off:before {
  content: "\f011";
}
.fa-signal:before {
  content: "\f012";
}
.fa-gear:before,
.fa-cog:before {
  content: "\f013";
}
.fa-trash-o:before {
  content: "\f014";
}
.fa-home:before {
  content: "\f015";
}
.fa-file-o:before {
  content: "\f016";
}
.fa-clock-o:before {
  content: "\f017";
}
.fa-road:before {
  content: "\f018";
}
.fa-download:before {
  content: "\f019";
}
.fa-arrow-circle-o-down:before {
  content: "\f01a";
}
.fa-arrow-circle-o-up:before {
  content: "\f01b";
}
.fa-inbox:before {
  content: "\f01c";
}
.fa-play-circle-o:before {
  content: "\f01d";
}
.fa-rotate-right:before,
.fa-repeat:before {
  content: "\f01e";
}
.fa-refresh:before {
  content: "\f021";
}
.fa-list-alt:before {
  content: "\f022";
}
.fa-lock:before {
  content: "\f023";
}
.fa-flag:before {
  content: "\f024";
}
.fa-headphones:before {
  content: "\f025";
}
.fa-volume-off:before {
  content: "\f026";
}
.fa-volume-down:before {
  content: "\f027";
}
.fa-volume-up:before {
  content: "\f028";
}
.fa-qrcode:before {
  content: "\f029";
}
.fa-barcode:before {
  content: "\f02a";
}
.fa-tag:before {
  content: "\f02b";
}
.fa-tags:before {
  content: "\f02c";
}
.fa-book:before {
  content: "\f02d";
}
.fa-bookmark:before {
  content: "\f02e";
}
.fa-print:before {
  content: "\f02f";
}
.fa-camera:before {
  content: "\f030";
}
.fa-font:before {
  content: "\f031";
}
.fa-bold:before {
  content: "\f032";
}
.fa-italic:before {
  content: "\f033";
}
.fa-text-height:before {
  content: "\f034";
}
.fa-text-width:before {
  content: "\f035";
}
.fa-align-left:before {
  content: "\f036";
}
.fa-align-center:before {
  content: "\f037";
}
.fa-align-right:before {
  content: "\f038";
}
.fa-align-justify:before {
  content: "\f039";
}
.fa-list:before {
  content: "\f03a";
}
.fa-dedent:before,
.fa-outdent:before {
  content: "\f03b";
}
.fa-indent:before {
  content: "\f03c";
}
.fa-video-camera:before {
  content: "\f03d";
}
.fa-photo:before,
.fa-image:before,
.fa-picture-o:before {
  content: "\f03e";
}
.fa-pencil:before {
  content: "\f040";
}
.fa-map-marker:before {
  content: "\f041";
}
.fa-adjust:before {
  content: "\f042";
}
.fa-tint:before {
  content: "\f043";
}
.fa-edit:before,
.fa-pencil-square-o:before {
  content: "\f044";
}
.fa-share-square-o:before {
  content: "\f045";
}
.fa-check-square-o:before {
  content: "\f046";
}
.fa-arrows:before {
  content: "\f047";
}
.fa-step-backward:before {
  content: "\f048";
}
.fa-fast-backward:before {
  content: "\f049";
}
.fa-backward:before {
  content: "\f04a";
}
.fa-play:before {
  content: "\f04b";
}
.fa-pause:before {
  content: "\f04c";
}
.fa-stop:before {
  content: "\f04d";
}
.fa-forward:before {
  content: "\f04e";
}
.fa-fast-forward:before {
  content: "\f050";
}
.fa-step-forward:before {
  content: "\f051";
}
.fa-eject:before {
  content: "\f052";
}
.fa-chevron-left:before {
  content: "\f053";
}
.fa-chevron-right:before {
  content: "\f054";
}
.fa-plus-circle:before {
  content: "\f055";
}
.fa-minus-circle:before {
  content: "\f056";
}
.fa-times-circle:before {
  content: "\f057";
}
.fa-check-circle:before {
  content: "\f058";
}
.fa-question-circle:before {
  content: "\f059";
}
.fa-info-circle:before {
  content: "\f05a";
}
.fa-crosshairs:before {
  content: "\f05b";
}
.fa-times-circle-o:before {
  content: "\f05c";
}
.fa-check-circle-o:before {
  content: "\f05d";
}
.fa-ban:before {
  content: "\f05e";
}
.fa-arrow-left:before {
  content: "\f060";
}
.fa-arrow-right:before {
  content: "\f061";
}
.fa-arrow-up:before {
  content: "\f062";
}
.fa-arrow-down:before {
  content: "\f063";
}
.fa-mail-forward:before,
.fa-share:before {
  content: "\f064";
}
.fa-expand:before {
  content: "\f065";
}
.fa-compress:before {
  content: "\f066";
}
.fa-plus:before {
  content: "\f067";
}
.fa-minus:before {
  content: "\f068";
}
.fa-asterisk:before {
  content: "\f069";
}
.fa-exclamation-circle:before {
  content: "\f06a";
}
.fa-gift:before {
  content: "\f06b";
}
.fa-leaf:before {
  content: "\f06c";
}
.fa-fire:before {
  content: "\f06d";
}
.fa-eye:before {
  content: "\f06e";
}
.fa-eye-slash:before {
  content: "\f070";
}
.fa-warning:before,
.fa-exclamation-triangle:before {
  content: "\f071";
}
.fa-plane:before {
  content: "\f072";
}
.fa-calendar:before {
  content: "\f073";
}
.fa-random:before {
  content: "\f074";
}
.fa-comment:before {
  content: "\f075";
}
.fa-magnet:before {
  content: "\f076";
}
.fa-chevron-up:before {
  content: "\f077";
}
.fa-chevron-down:before {
  content: "\f078";
}
.fa-retweet:before {
  content: "\f079";
}
.fa-shopping-cart:before {
  content: "\f07a";
}
.fa-folder:before {
  content: "\f07b";
}
.fa-folder-open:before {
  content: "\f07c";
}
.fa-arrows-v:before {
  content: "\f07d";
}
.fa-arrows-h:before {
  content: "\f07e";
}
.fa-bar-chart-o:before,
.fa-bar-chart:before {
  content: "\f080";
}
.fa-twitter-square:before {
  content: "\f081";
}
.fa-facebook-square:before {
  content: "\f082";
}
.fa-camera-retro:before {
  content: "\f083";
}
.fa-key:before {
  content: "\f084";
}
.fa-gears:before,
.fa-cogs:before {
  content: "\f085";
}
.fa-comments:before {
  content: "\f086";
}
.fa-thumbs-o-up:before {
  content: "\f087";
}
.fa-thumbs-o-down:before {
  content: "\f088";
}
.fa-star-half:before {
  content: "\f089";
}
.fa-heart-o:before {
  content: "\f08a";
}
.fa-sign-out:before {
  content: "\f08b";
}
.fa-linkedin-square:before {
  content: "\f08c";
}
.fa-thumb-tack:before {
  content: "\f08d";
}
.fa-external-link:before {
  content: "\f08e";
}
.fa-sign-in:before {
  content: "\f090";
}
.fa-trophy:before {
  content: "\f091";
}
.fa-github-square:before {
  content: "\f092";
}
.fa-upload:before {
  content: "\f093";
}
.fa-lemon-o:before {
  content: "\f094";
}
.fa-phone:before {
  content: "\f095";
}
.fa-square-o:before {
  content: "\f096";
}
.fa-bookmark-o:before {
  content: "\f097";
}
.fa-phone-square:before {
  content: "\f098";
}
.fa-twitter:before {
  content: "\f099";
}
.fa-facebook-f:before,
.fa-facebook:before {
  content: "\f09a";
}
.fa-github:before {
  content: "\f09b";
}
.fa-unlock:before {
  content: "\f09c";
}
.fa-credit-card:before {
  content: "\f09d";
}
.fa-feed:before,
.fa-rss:before {
  content: "\f09e";
}
.fa-hdd-o:before {
  content: "\f0a0";
}
.fa-bullhorn:before {
  content: "\f0a1";
}
.fa-bell:before {
  content: "\f0f3";
}
.fa-certificate:before {
  content: "\f0a3";
}
.fa-hand-o-right:before {
  content: "\f0a4";
}
.fa-hand-o-left:before {
  content: "\f0a5";
}
.fa-hand-o-up:before {
  content: "\f0a6";
}
.fa-hand-o-down:before {
  content: "\f0a7";
}
.fa-arrow-circle-left:before {
  content: "\f0a8";
}
.fa-arrow-circle-right:before {
  content: "\f0a9";
}
.fa-arrow-circle-up:before {
  content: "\f0aa";
}
.fa-arrow-circle-down:before {
  content: "\f0ab";
}
.fa-globe:before {
  content: "\f0ac";
}
.fa-wrench:before {
  content: "\f0ad";
}
.fa-tasks:before {
  content: "\f0ae";
}
.fa-filter:before {
  content: "\f0b0";
}
.fa-briefcase:before {
  content: "\f0b1";
}
.fa-arrows-alt:before {
  content: "\f0b2";
}
.fa-group:before,
.fa-users:before {
  content: "\f0c0";
}
.fa-chain:before,
.fa-link:before {
  content: "\f0c1";
}
.fa-cloud:before {
  content: "\f0c2";
}
.fa-flask:before {
  content: "\f0c3";
}
.fa-cut:before,
.fa-scissors:before {
  content: "\f0c4";
}
.fa-copy:before,
.fa-files-o:before {
  content: "\f0c5";
}
.fa-paperclip:before {
  content: "\f0c6";
}
.fa-save:before,
.fa-floppy-o:before {
  content: "\f0c7";
}
.fa-square:before {
  content: "\f0c8";
}
.fa-navicon:before,
.fa-reorder:before,
.fa-bars:before {
  content: "\f0c9";
}
.fa-list-ul:before {
  content: "\f0ca";
}
.fa-list-ol:before {
  content: "\f0cb";
}
.fa-strikethrough:before {
  content: "\f0cc";
}
.fa-underline:before {
  content: "\f0cd";
}
.fa-table:before {
  content: "\f0ce";
}
.fa-magic:before {
  content: "\f0d0";
}
.fa-truck:before {
  content: "\f0d1";
}
.fa-pinterest:before {
  content: "\f0d2";
}
.fa-pinterest-square:before {
  content: "\f0d3";
}
.fa-google-plus-square:before {
  content: "\f0d4";
}
.fa-google-plus:before {
  content: "\f0d5";
}
.fa-money:before {
  content: "\f0d6";
}
.fa-caret-down:before {
  content: "\f0d7";
}
.fa-caret-up:before {
  content: "\f0d8";
}
.fa-caret-left:before {
  content: "\f0d9";
}
.fa-caret-right:before {
  content: "\f0da";
}
.fa-columns:before {
  content: "\f0db";
}
.fa-unsorted:before,
.fa-sort:before {
  content: "\f0dc";
}
.fa-sort-down:before,
.fa-sort-desc:before {
  content: "\f0dd";
}
.fa-sort-up:before,
.fa-sort-asc:before {
  content: "\f0de";
}
.fa-envelope:before {
  content: "\f0e0";
}
.fa-linkedin:before {
  content: "\f0e1";
}
.fa-rotate-left:before,
.fa-undo:before {
  content: "\f0e2";
}
.fa-legal:before,
.fa-gavel:before {
  content: "\f0e3";
}
.fa-dashboard:before,
.fa-tachometer:before {
  content: "\f0e4";
}
.fa-comment-o:before {
  content: "\f0e5";
}
.fa-comments-o:before {
  content: "\f0e6";
}
.fa-flash:before,
.fa-bolt:before {
  content: "\f0e7";
}
.fa-sitemap:before {
  content: "\f0e8";
}
.fa-umbrella:before {
  content: "\f0e9";
}
.fa-paste:before,
.fa-clipboard:before {
  content: "\f0ea";
}
.fa-lightbulb-o:before {
  content: "\f0eb";
}
.fa-exchange:before {
  content: "\f0ec";
}
.fa-cloud-download:before {
  content: "\f0ed";
}
.fa-cloud-upload:before {
  content: "\f0ee";
}
.fa-user-md:before {
  content: "\f0f0";
}
.fa-stethoscope:before {
  content: "\f0f1";
}
.fa-suitcase:before {
  content: "\f0f2";
}
.fa-bell-o:before {
  content: "\f0a2";
}
.fa-coffee:before {
  content: "\f0f4";
}
.fa-cutlery:before {
  content: "\f0f5";
}
.fa-file-text-o:before {
  content: "\f0f6";
}
.fa-building-o:before {
  content: "\f0f7";
}
.fa-hospital-o:before {
  content: "\f0f8";
}
.fa-ambulance:before {
  content: "\f0f9";
}
.fa-medkit:before {
  content: "\f0fa";
}
.fa-fighter-jet:before {
  content: "\f0fb";
}
.fa-beer:before {
  content: "\f0fc";
}
.fa-h-square:before {
  content: "\f0fd";
}
.fa-plus-square:before {
  content: "\f0fe";
}
.fa-angle-double-left:before {
  content: "\f100";
}
.fa-angle-double-right:before {
  content: "\f101";
}
.fa-angle-double-up:before {
  content: "\f102";
}
.fa-angle-double-down:before {
  content: "\f103";
}
.fa-angle-left:before {
  content: "\f104";
}
.fa-angle-right:before {
  content: "\f105";
}
.fa-angle-up:before {
  content: "\f106";
}
.fa-angle-down:before {
  content: "\f107";
}
.fa-desktop:before {
  content: "\f108";
}
.fa-laptop:before {
  content: "\f109";
}
.fa-tablet:before {
  content: "\f10a";
}
.fa-mobile-phone:before,
.fa-mobile:before {
  content: "\f10b";
}
.fa-circle-o:before {
  content: "\f10c";
}
.fa-quote-left:before {
  content: "\f10d";
}
.fa-quote-right:before {
  content: "\f10e";
}
.fa-spinner:before {
  content: "\f110";
}
.fa-circle:before {
  content: "\f111";
}
.fa-mail-reply:before,
.fa-reply:before {
  content: "\f112";
}
.fa-github-alt:before {
  content: "\f113";
}
.fa-folder-o:before {
  content: "\f114";
}
.fa-folder-open-o:before {
  content: "\f115";
}
.fa-smile-o:before {
  content: "\f118";
}
.fa-frown-o:before {
  content: "\f119";
}
.fa-meh-o:before {
  content: "\f11a";
}
.fa-gamepad:before {
  content: "\f11b";
}
.fa-keyboard-o:before {
  content: "\f11c";
}
.fa-flag-o:before {
  content: "\f11d";
}
.fa-flag-checkered:before {
  content: "\f11e";
}
.fa-terminal:before {
  content: "\f120";
}
.fa-code:before {
  content: "\f121";
}
.fa-mail-reply-all:before,
.fa-reply-all:before {
  content: "\f122";
}
.fa-star-half-empty:before,
.fa-star-half-full:before,
.fa-star-half-o:before {
  content: "\f123";
}
.fa-location-arrow:before {
  content: "\f124";
}
.fa-crop:before {
  content: "\f125";
}
.fa-code-fork:before {
  content: "\f126";
}
.fa-unlink:before,
.fa-chain-broken:before {
  content: "\f127";
}
.fa-question:before {
  content: "\f128";
}
.fa-info:before {
  content: "\f129";
}
.fa-exclamation:before {
  content: "\f12a";
}
.fa-superscript:before {
  content: "\f12b";
}
.fa-subscript:before {
  content: "\f12c";
}
.fa-eraser:before {
  content: "\f12d";
}
.fa-puzzle-piece:before {
  content: "\f12e";
}
.fa-microphone:before {
  content: "\f130";
}
.fa-microphone-slash:before {
  content: "\f131";
}
.fa-shield:before {
  content: "\f132";
}
.fa-calendar-o:before {
  content: "\f133";
}
.fa-fire-extinguisher:before {
  content: "\f134";
}
.fa-rocket:before {
  content: "\f135";
}
.fa-maxcdn:before {
  content: "\f136";
}
.fa-chevron-circle-left:before {
  content: "\f137";
}
.fa-chevron-circle-right:before {
  content: "\f138";
}
.fa-chevron-circle-up:before {
  content: "\f139";
}
.fa-chevron-circle-down:before {
  content: "\f13a";
}
.fa-html5:before {
  content: "\f13b";
}
.fa-css3:before {
  content: "\f13c";
}
.fa-anchor:before {
  content: "\f13d";
}
.fa-unlock-alt:before {
  content: "\f13e";
}
.fa-bullseye:before {
  content: "\f140";
}
.fa-ellipsis-h:before {
  content: "\f141";
}
.fa-ellipsis-v:before {
  content: "\f142";
}
.fa-rss-square:before {
  content: "\f143";
}
.fa-play-circle:before {
  content: "\f144";
}
.fa-ticket:before {
  content: "\f145";
}
.fa-minus-square:before {
  content: "\f146";
}
.fa-minus-square-o:before {
  content: "\f147";
}
.fa-level-up:before {
  content: "\f148";
}
.fa-level-down:before {
  content: "\f149";
}
.fa-check-square:before {
  content: "\f14a";
}
.fa-pencil-square:before {
  content: "\f14b";
}
.fa-external-link-square:before {
  content: "\f14c";
}
.fa-share-square:before {
  content: "\f14d";
}
.fa-compass:before {
  content: "\f14e";
}
.fa-toggle-down:before,
.fa-caret-square-o-down:before {
  content: "\f150";
}
.fa-toggle-up:before,
.fa-caret-square-o-up:before {
  content: "\f151";
}
.fa-toggle-right:before,
.fa-caret-square-o-right:before {
  content: "\f152";
}
.fa-euro:before,
.fa-eur:before {
  content: "\f153";
}
.fa-gbp:before {
  content: "\f154";
}
.fa-dollar:before,
.fa-usd:before {
  content: "\f155";
}
.fa-rupee:before,
.fa-inr:before {
  content: "\f156";
}
.fa-cny:before,
.fa-rmb:before,
.fa-yen:before,
.fa-jpy:before {
  content: "\f157";
}
.fa-ruble:before,
.fa-rouble:before,
.fa-rub:before {
  content: "\f158";
}
.fa-won:before,
.fa-krw:before {
  content: "\f159";
}
.fa-bitcoin:before,
.fa-btc:before {
  content: "\f15a";
}
.fa-file:before {
  content: "\f15b";
}
.fa-file-text:before {
  content: "\f15c";
}
.fa-sort-alpha-asc:before {
  content: "\f15d";
}
.fa-sort-alpha-desc:before {
  content: "\f15e";
}
.fa-sort-amount-asc:before {
  content: "\f160";
}
.fa-sort-amount-desc:before {
  content: "\f161";
}
.fa-sort-numeric-asc:before {
  content: "\f162";
}
.fa-sort-numeric-desc:before {
  content: "\f163";
}
.fa-thumbs-up:before {
  content: "\f164";
}
.fa-thumbs-down:before {
  content: "\f165";
}
.fa-youtube-square:before {
  content: "\f166";
}
.fa-youtube:before {
  content: "\f167";
}
.fa-xing:before {
  content: "\f168";
}
.fa-xing-square:before {
  content: "\f169";
}
.fa-youtube-play:before {
  content: "\f16a";
}
.fa-dropbox:before {
  content: "\f16b";
}
.fa-stack-overflow:before {
  content: "\f16c";
}
.fa-instagram:before {
  content: "\f16d";
}
.fa-flickr:before {
  content: "\f16e";
}
.fa-adn:before {
  content: "\f170";
}
.fa-bitbucket:before {
  content: "\f171";
}
.fa-bitbucket-square:before {
  content: "\f172";
}
.fa-tumblr:before {
  content: "\f173";
}
.fa-tumblr-square:before {
  content: "\f174";
}
.fa-long-arrow-down:before {
  content: "\f175";
}
.fa-long-arrow-up:before {
  content: "\f176";
}
.fa-long-arrow-left:before {
  content: "\f177";
}
.fa-long-arrow-right:before {
  content: "\f178";
}
.fa-apple:before {
  content: "\f179";
}
.fa-windows:before {
  content: "\f17a";
}
.fa-android:before {
  content: "\f17b";
}
.fa-linux:before {
  content: "\f17c";
}
.fa-dribbble:before {
  content: "\f17d";
}
.fa-skype:before {
  content: "\f17e";
}
.fa-foursquare:before {
  content: "\f180";
}
.fa-trello:before {
  content: "\f181";
}
.fa-female:before {
  content: "\f182";
}
.fa-male:before {
  content: "\f183";
}
.fa-gittip:before,
.fa-gratipay:before {
  content: "\f184";
}
.fa-sun-o:before {
  content: "\f185";
}
.fa-moon-o:before {
  content: "\f186";
}
.fa-archive:before {
  content: "\f187";
}
.fa-bug:before {
  content: "\f188";
}
.fa-vk:before {
  content: "\f189";
}
.fa-weibo:before {
  content: "\f18a";
}
.fa-renren:before {
  content: "\f18b";
}
.fa-pagelines:before {
  content: "\f18c";
}
.fa-stack-exchange:before {
  content: "\f18d";
}
.fa-arrow-circle-o-right:before {
  content: "\f18e";
}
.fa-arrow-circle-o-left:before {
  content: "\f190";
}
.fa-toggle-left:before,
.fa-caret-square-o-left:before {
  content: "\f191";
}
.fa-dot-circle-o:before {
  content: "\f192";
}
.fa-wheelchair:before {
  content: "\f193";
}
.fa-vimeo-square:before {
  content: "\f194";
}
.fa-turkish-lira:before,
.fa-try:before {
  content: "\f195";
}
.fa-plus-square-o:before {
  content: "\f196";
}
.fa-space-shuttle:before {
  content: "\f197";
}
.fa-slack:before {
  content: "\f198";
}
.fa-envelope-square:before {
  content: "\f199";
}
.fa-wordpress:before {
  content: "\f19a";
}
.fa-openid:before {
  content: "\f19b";
}
.fa-institution:before,
.fa-bank:before,
.fa-university:before {
  content: "\f19c";
}
.fa-mortar-board:before,
.fa-graduation-cap:before {
  content: "\f19d";
}
.fa-yahoo:before {
  content: "\f19e";
}
.fa-google:before {
  content: "\f1a0";
}
.fa-reddit:before {
  content: "\f1a1";
}
.fa-reddit-square:before {
  content: "\f1a2";
}
.fa-stumbleupon-circle:before {
  content: "\f1a3";
}
.fa-stumbleupon:before {
  content: "\f1a4";
}
.fa-delicious:before {
  content: "\f1a5";
}
.fa-digg:before {
  content: "\f1a6";
}
.fa-pied-piper-pp:before {
  content: "\f1a7";
}
.fa-pied-piper-alt:before {
  content: "\f1a8";
}
.fa-drupal:before {
  content: "\f1a9";
}
.fa-joomla:before {
  content: "\f1aa";
}
.fa-language:before {
  content: "\f1ab";
}
.fa-fax:before {
  content: "\f1ac";
}
.fa-building:before {
  content: "\f1ad";
}
.fa-child:before {
  content: "\f1ae";
}
.fa-paw:before {
  content: "\f1b0";
}
.fa-spoon:before {
  content: "\f1b1";
}
.fa-cube:before {
  content: "\f1b2";
}
.fa-cubes:before {
  content: "\f1b3";
}
.fa-behance:before {
  content: "\f1b4";
}
.fa-behance-square:before {
  content: "\f1b5";
}
.fa-steam:before {
  content: "\f1b6";
}
.fa-steam-square:before {
  content: "\f1b7";
}
.fa-recycle:before {
  content: "\f1b8";
}
.fa-automobile:before,
.fa-car:before {
  content: "\f1b9";
}
.fa-cab:before,
.fa-taxi:before {
  content: "\f1ba";
}
.fa-tree:before {
  content: "\f1bb";
}
.fa-spotify:before {
  content: "\f1bc";
}
.fa-deviantart:before {
  content: "\f1bd";
}
.fa-soundcloud:before {
  content: "\f1be";
}
.fa-database:before {
  content: "\f1c0";
}
.fa-file-pdf-o:before {
  content: "\f1c1";
}
.fa-file-word-o:before {
  content: "\f1c2";
}
.fa-file-excel-o:before {
  content: "\f1c3";
}
.fa-file-powerpoint-o:before {
  content: "\f1c4";
}
.fa-file-photo-o:before,
.fa-file-picture-o:before,
.fa-file-image-o:before {
  content: "\f1c5";
}
.fa-file-zip-o:before,
.fa-file-archive-o:before {
  content: "\f1c6";
}
.fa-file-sound-o:before,
.fa-file-audio-o:before {
  content: "\f1c7";
}
.fa-file-movie-o:before,
.fa-file-video-o:before {
  content: "\f1c8";
}
.fa-file-code-o:before {
  content: "\f1c9";
}
.fa-vine:before {
  content: "\f1ca";
}
.fa-codepen:before {
  content: "\f1cb";
}
.fa-jsfiddle:before {
  content: "\f1cc";
}
.fa-life-bouy:before,
.fa-life-buoy:before,
.fa-life-saver:before,
.fa-support:before,
.fa-life-ring:before {
  content: "\f1cd";
}
.fa-circle-o-notch:before {
  content: "\f1ce";
}
.fa-ra:before,
.fa-resistance:before,
.fa-rebel:before {
  content: "\f1d0";
}
.fa-ge:before,
.fa-empire:before {
  content: "\f1d1";
}
.fa-git-square:before {
  content: "\f1d2";
}
.fa-git:before {
  content: "\f1d3";
}
.fa-y-combinator-square:before,
.fa-yc-square:before,
.fa-hacker-news:before {
  content: "\f1d4";
}
.fa-tencent-weibo:before {
  content: "\f1d5";
}
.fa-qq:before {
  content: "\f1d6";
}
.fa-wechat:before,
.fa-weixin:before {
  content: "\f1d7";
}
.fa-send:before,
.fa-paper-plane:before {
  content: "\f1d8";
}
.fa-send-o:before,
.fa-paper-plane-o:before {
  content: "\f1d9";
}
.fa-history:before {
  content: "\f1da";
}
.fa-circle-thin:before {
  content: "\f1db";
}
.fa-header:before {
  content: "\f1dc";
}
.fa-paragraph:before {
  content: "\f1dd";
}
.fa-sliders:before {
  content: "\f1de";
}
.fa-share-alt:before {
  content: "\f1e0";
}
.fa-share-alt-square:before {
  content: "\f1e1";
}
.fa-bomb:before {
  content: "\f1e2";
}
.fa-soccer-ball-o:before,
.fa-futbol-o:before {
  content: "\f1e3";
}
.fa-tty:before {
  content: "\f1e4";
}
.fa-binoculars:before {
  content: "\f1e5";
}
.fa-plug:before {
  content: "\f1e6";
}
.fa-slideshare:before {
  content: "\f1e7";
}
.fa-twitch:before {
  content: "\f1e8";
}
.fa-yelp:before {
  content: "\f1e9";
}
.fa-newspaper-o:before {
  content: "\f1ea";
}
.fa-wifi:before {
  content: "\f1eb";
}
.fa-calculator:before {
  content: "\f1ec";
}
.fa-paypal:before {
  content: "\f1ed";
}
.fa-google-wallet:before {
  content: "\f1ee";
}
.fa-cc-visa:before {
  content: "\f1f0";
}
.fa-cc-mastercard:before {
  content: "\f1f1";
}
.fa-cc-discover:before {
  content: "\f1f2";
}
.fa-cc-amex:before {
  content: "\f1f3";
}
.fa-cc-paypal:before {
  content: "\f1f4";
}
.fa-cc-stripe:before {
  content: "\f1f5";
}
.fa-bell-slash:before {
  content: "\f1f6";
}
.fa-bell-slash-o:before {
  content: "\f1f7";
}
.fa-trash:before {
  content: "\f1f8";
}
.fa-copyright:before {
  content: "\f1f9";
}
.fa-at:before {
  content: "\f1fa";
}
.fa-eyedropper:before {
  content: "\f1fb";
}
.fa-paint-brush:before {
  content: "\f1fc";
}
.fa-birthday-cake:before {
  content: "\f1fd";
}
.fa-area-chart:before {
  content: "\f1fe";
}
.fa-pie-chart:before {
  content: "\f200";
}
.fa-line-chart:before {
  content: "\f201";
}
.fa-lastfm:before {
  content: "\f202";
}
.fa-lastfm-square:before {
  content: "\f203";
}
.fa-toggle-off:before {
  content: "\f204";
}
.fa-toggle-on:before {
  content: "\f205";
}
.fa-bicycle:before {
  content: "\f206";
}
.fa-bus:before {
  content: "\f207";
}
.fa-ioxhost:before {
  content: "\f208";
}
.fa-angellist:before {
  content: "\f209";
}
.fa-cc:before {
  content: "\f20a";
}
.fa-shekel:before,
.fa-sheqel:before,
.fa-ils:before {
  content: "\f20b";
}
.fa-meanpath:before {
  content: "\f20c";
}
.fa-buysellads:before {
  content: "\f20d";
}
.fa-connectdevelop:before {
  content: "\f20e";
}
.fa-dashcube:before {
  content: "\f210";
}
.fa-forumbee:before {
  content: "\f211";
}
.fa-leanpub:before {
  content: "\f212";
}
.fa-sellsy:before {
  content: "\f213";
}
.fa-shirtsinbulk:before {
  content: "\f214";
}
.fa-simplybuilt:before {
  content: "\f215";
}
.fa-skyatlas:before {
  content: "\f216";
}
.fa-cart-plus:before {
  content: "\f217";
}
.fa-cart-arrow-down:before {
  content: "\f218";
}
.fa-diamond:before {
  content: "\f219";
}
.fa-ship:before {
  content: "\f21a";
}
.fa-user-secret:before {
  content: "\f21b";
}
.fa-motorcycle:before {
  content: "\f21c";
}
.fa-street-view:before {
  content: "\f21d";
}
.fa-heartbeat:before {
  content: "\f21e";
}
.fa-venus:before {
  content: "\f221";
}
.fa-mars:before {
  content: "\f222";
}
.fa-mercury:before {
  content: "\f223";
}
.fa-intersex:before,
.fa-transgender:before {
  content: "\f224";
}
.fa-transgender-alt:before {
  content: "\f225";
}
.fa-venus-double:before {
  content: "\f226";
}
.fa-mars-double:before {
  content: "\f227";
}
.fa-venus-mars:before {
  content: "\f228";
}
.fa-mars-stroke:before {
  content: "\f229";
}
.fa-mars-stroke-v:before {
  content: "\f22a";
}
.fa-mars-stroke-h:before {
  content: "\f22b";
}
.fa-neuter:before {
  content: "\f22c";
}
.fa-genderless:before {
  content: "\f22d";
}
.fa-facebook-official:before {
  content: "\f230";
}
.fa-pinterest-p:before {
  content: "\f231";
}
.fa-whatsapp:before {
  content: "\f232";
}
.fa-server:before {
  content: "\f233";
}
.fa-user-plus:before {
  content: "\f234";
}
.fa-user-times:before {
  content: "\f235";
}
.fa-hotel:before,
.fa-bed:before {
  content: "\f236";
}
.fa-viacoin:before {
  content: "\f237";
}
.fa-train:before {
  content: "\f238";
}
.fa-subway:before {
  content: "\f239";
}
.fa-medium:before {
  content: "\f23a";
}
.fa-yc:before,
.fa-y-combinator:before {
  content: "\f23b";
}
.fa-optin-monster:before {
  content: "\f23c";
}
.fa-opencart:before {
  content: "\f23d";
}
.fa-expeditedssl:before {
  content: "\f23e";
}
.fa-battery-4:before,
.fa-battery:before,
.fa-battery-full:before {
  content: "\f240";
}
.fa-battery-3:before,
.fa-battery-three-quarters:before {
  content: "\f241";
}
.fa-battery-2:before,
.fa-battery-half:before {
  content: "\f242";
}
.fa-battery-1:before,
.fa-battery-quarter:before {
  content: "\f243";
}
.fa-battery-0:before,
.fa-battery-empty:before {
  content: "\f244";
}
.fa-mouse-pointer:before {
  content: "\f245";
}
.fa-i-cursor:before {
  content: "\f246";
}
.fa-object-group:before {
  content: "\f247";
}
.fa-object-ungroup:before {
  content: "\f248";
}
.fa-sticky-note:before {
  content: "\f249";
}
.fa-sticky-note-o:before {
  content: "\f24a";
}
.fa-cc-jcb:before {
  content: "\f24b";
}
.fa-cc-diners-club:before {
  content: "\f24c";
}
.fa-clone:before {
  content: "\f24d";
}
.fa-balance-scale:before {
  content: "\f24e";
}
.fa-hourglass-o:before {
  content: "\f250";
}
.fa-hourglass-1:before,
.fa-hourglass-start:before {
  content: "\f251";
}
.fa-hourglass-2:before,
.fa-hourglass-half:before {
  content: "\f252";
}
.fa-hourglass-3:before,
.fa-hourglass-end:before {
  content: "\f253";
}
.fa-hourglass:before {
  content: "\f254";
}
.fa-hand-grab-o:before,
.fa-hand-rock-o:before {
  content: "\f255";
}
.fa-hand-stop-o:before,
.fa-hand-paper-o:before {
  content: "\f256";
}
.fa-hand-scissors-o:before {
  content: "\f257";
}
.fa-hand-lizard-o:before {
  content: "\f258";
}
.fa-hand-spock-o:before {
  content: "\f259";
}
.fa-hand-pointer-o:before {
  content: "\f25a";
}
.fa-hand-peace-o:before {
  content: "\f25b";
}
.fa-trademark:before {
  content: "\f25c";
}
.fa-registered:before {
  content: "\f25d";
}
.fa-creative-commons:before {
  content: "\f25e";
}
.fa-gg:before {
  content: "\f260";
}
.fa-gg-circle:before {
  content: "\f261";
}
.fa-tripadvisor:before {
  content: "\f262";
}
.fa-odnoklassniki:before {
  content: "\f263";
}
.fa-odnoklassniki-square:before {
  content: "\f264";
}
.fa-get-pocket:before {
  content: "\f265";
}
.fa-wikipedia-w:before {
  content: "\f266";
}
.fa-safari:before {
  content: "\f267";
}
.fa-chrome:before {
  content: "\f268";
}
.fa-firefox:before {
  content: "\f269";
}
.fa-opera:before {
  content: "\f26a";
}
.fa-internet-explorer:before {
  content: "\f26b";
}
.fa-tv:before,
.fa-television:before {
  content: "\f26c";
}
.fa-contao:before {
  content: "\f26d";
}
.fa-500px:before {
  content: "\f26e";
}
.fa-amazon:before {
  content: "\f270";
}
.fa-calendar-plus-o:before {
  content: "\f271";
}
.fa-calendar-minus-o:before {
  content: "\f272";
}
.fa-calendar-times-o:before {
  content: "\f273";
}
.fa-calendar-check-o:before {
  content: "\f274";
}
.fa-industry:before {
  content: "\f275";
}
.fa-map-pin:before {
  content: "\f276";
}
.fa-map-signs:before {
  content: "\f277";
}
.fa-map-o:before {
  content: "\f278";
}
.fa-map:before {
  content: "\f279";
}
.fa-commenting:before {
  content: "\f27a";
}
.fa-commenting-o:before {
  content: "\f27b";
}
.fa-houzz:before {
  content: "\f27c";
}
.fa-vimeo:before {
  content: "\f27d";
}
.fa-black-tie:before {
  content: "\f27e";
}
.fa-fonticons:before {
  content: "\f280";
}
.fa-reddit-alien:before {
  content: "\f281";
}
.fa-edge:before {
  content: "\f282";
}
.fa-credit-card-alt:before {
  content: "\f283";
}
.fa-codiepie:before {
  content: "\f284";
}
.fa-modx:before {
  content: "\f285";
}
.fa-fort-awesome:before {
  content: "\f286";
}
.fa-usb:before {
  content: "\f287";
}
.fa-product-hunt:before {
  content: "\f288";
}
.fa-mixcloud:before {
  content: "\f289";
}
.fa-scribd:before {
  content: "\f28a";
}
.fa-pause-circle:before {
  content: "\f28b";
}
.fa-pause-circle-o:before {
  content: "\f28c";
}
.fa-stop-circle:before {
  content: "\f28d";
}
.fa-stop-circle-o:before {
  content: "\f28e";
}
.fa-shopping-bag:before {
  content: "\f290";
}
.fa-shopping-basket:before {
  content: "\f291";
}
.fa-hashtag:before {
  content: "\f292";
}
.fa-bluetooth:before {
  content: "\f293";
}
.fa-bluetooth-b:before {
  content: "\f294";
}
.fa-percent:before {
  content: "\f295";
}
.fa-gitlab:before {
  content: "\f296";
}
.fa-wpbeginner:before {
  content: "\f297";
}
.fa-wpforms:before {
  content: "\f298";
}
.fa-envira:before {
  content: "\f299";
}
.fa-universal-access:before {
  content: "\f29a";
}
.fa-wheelchair-alt:before {
  content: "\f29b";
}
.fa-question-circle-o:before {
  content: "\f29c";
}
.fa-blind:before {
  content: "\f29d";
}
.fa-audio-description:before {
  content: "\f29e";
}
.fa-volume-control-phone:before {
  content: "\f2a0";
}
.fa-braille:before {
  content: "\f2a1";
}
.fa-assistive-listening-systems:before {
  content: "\f2a2";
}
.fa-asl-interpreting:before,
.fa-american-sign-language-interpreting:before {
  content: "\f2a3";
}
.fa-deafness:before,
.fa-hard-of-hearing:before,
.fa-deaf:before {
  content: "\f2a4";
}
.fa-glide:before {
  content: "\f2a5";
}
.fa-glide-g:before {
  content: "\f2a6";
}
.fa-signing:before,
.fa-sign-language:before {
  content: "\f2a7";
}
.fa-low-vision:before {
  content: "\f2a8";
}
.fa-viadeo:before {
  content: "\f2a9";
}
.fa-viadeo-square:before {
  content: "\f2aa";
}
.fa-snapchat:before {
  content: "\f2ab";
}
.fa-snapchat-ghost:before {
  content: "\f2ac";
}
.fa-snapchat-square:before {
  content: "\f2ad";
}
.fa-pied-piper:before {
  content: "\f2ae";
}
.fa-first-order:before {
  content: "\f2b0";
}
.fa-yoast:before {
  content: "\f2b1";
}
.fa-themeisle:before {
  content: "\f2b2";
}
.fa-google-plus-circle:before,
.fa-google-plus-official:before {
  content: "\f2b3";
}
.fa-fa:before,
.fa-font-awesome:before {
  content: "\f2b4";
}
.fa-handshake-o:before {
  content: "\f2b5";
}
.fa-envelope-open:before {
  content: "\f2b6";
}
.fa-envelope-open-o:before {
  content: "\f2b7";
}
.fa-linode:before {
  content: "\f2b8";
}
.fa-address-book:before {
  content: "\f2b9";
}
.fa-address-book-o:before {
  content: "\f2ba";
}
.fa-vcard:before,
.fa-address-card:before {
  content: "\f2bb";
}
.fa-vcard-o:before,
.fa-address-card-o:before {
  content: "\f2bc";
}
.fa-user-circle:before {
  content: "\f2bd";
}
.fa-user-circle-o:before {
  content: "\f2be";
}
.fa-user-o:before {
  content: "\f2c0";
}
.fa-id-badge:before {
  content: "\f2c1";
}
.fa-drivers-license:before,
.fa-id-card:before {
  content: "\f2c2";
}
.fa-drivers-license-o:before,
.fa-id-card-o:before {
  content: "\f2c3";
}
.fa-quora:before {
  content: "\f2c4";
}
.fa-free-code-camp:before {
  content: "\f2c5";
}
.fa-telegram:before {
  content: "\f2c6";
}
.fa-thermometer-4:before,
.fa-thermometer:before,
.fa-thermometer-full:before {
  content: "\f2c7";
}
.fa-thermometer-3:before,
.fa-thermometer-three-quarters:before {
  content: "\f2c8";
}
.fa-thermometer-2:before,
.fa-thermometer-half:before {
  content: "\f2c9";
}
.fa-thermometer-1:before,
.fa-thermometer-quarter:before {
  content: "\f2ca";
}
.fa-thermometer-0:before,
.fa-thermometer-empty:before {
  content: "\f2cb";
}
.fa-shower:before {
  content: "\f2cc";
}
.fa-bathtub:before,
.fa-s15:before,
.fa-bath:before {
  content: "\f2cd";
}
.fa-podcast:before {
  content: "\f2ce";
}
.fa-window-maximize:before {
  content: "\f2d0";
}
.fa-window-minimize:before {
  content: "\f2d1";
}
.fa-window-restore:before {
  content: "\f2d2";
}
.fa-times-rectangle:before,
.fa-window-close:before {
  content: "\f2d3";
}
.fa-times-rectangle-o:before,
.fa-window-close-o:before {
  content: "\f2d4";
}
.fa-bandcamp:before {
  content: "\f2d5";
}
.fa-grav:before {
  content: "\f2d6";
}
.fa-etsy:before {
  content: "\f2d7";
}
.fa-imdb:before {
  content: "\f2d8";
}
.fa-ravelry:before {
  content: "\f2d9";
}
.fa-eercast:before {
  content: "\f2da";
}
.fa-microchip:before {
  content: "\f2db";
}
.fa-snowflake-o:before {
  content: "\f2dc";
}
.fa-superpowers:before {
  content: "\f2dd";
}
.fa-wpexplorer:before {
  content: "\f2de";
}
.fa-meetup:before {
  content: "\f2e0";
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
/*!
*
* IPython base
*
*/
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
code {
  color: #000;
}
pre {
  font-size: inherit;
  line-height: inherit;
}
label {
  font-weight: normal;
}
/* Make the page background atleast 100% the height of the view port */
/* Make the page itself atleast 70% the height of the view port */
.border-box-sizing {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.corner-all {
  border-radius: 2px;
}
.no-padding {
  padding: 0px;
}
/* Flexible box model classes */
/* Taken from Alex Russell http://infrequently.org/2009/08/css-3-progress/ */
/* This file is a compatability layer.  It allows the usage of flexible box
model layouts accross multiple browsers, including older browsers.  The newest,
universal implementation of the flexible box model is used when available (see
`Modern browsers` comments below).  Browsers that are known to implement this
new spec completely include:

    Firefox 28.0+
    Chrome 29.0+
    Internet Explorer 11+
    Opera 17.0+

Browsers not listed, including Safari, are supported via the styling under the
`Old browsers` comments below.
*/
.hbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
.hbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.vbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
.vbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.hbox.reverse,
.vbox.reverse,
.reverse {
  /* Old browsers */
  -webkit-box-direction: reverse;
  -moz-box-direction: reverse;
  box-direction: reverse;
  /* Modern browsers */
  flex-direction: row-reverse;
}
.hbox.box-flex0,
.vbox.box-flex0,
.box-flex0 {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
  width: auto;
}
.hbox.box-flex1,
.vbox.box-flex1,
.box-flex1 {
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex,
.vbox.box-flex,
.box-flex {
  /* Old browsers */
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex2,
.vbox.box-flex2,
.box-flex2 {
  /* Old browsers */
  -webkit-box-flex: 2;
  -moz-box-flex: 2;
  box-flex: 2;
  /* Modern browsers */
  flex: 2;
}
.box-group1 {
  /*  Deprecated */
  -webkit-box-flex-group: 1;
  -moz-box-flex-group: 1;
  box-flex-group: 1;
}
.box-group2 {
  /* Deprecated */
  -webkit-box-flex-group: 2;
  -moz-box-flex-group: 2;
  box-flex-group: 2;
}
.hbox.start,
.vbox.start,
.start {
  /* Old browsers */
  -webkit-box-pack: start;
  -moz-box-pack: start;
  box-pack: start;
  /* Modern browsers */
  justify-content: flex-start;
}
.hbox.end,
.vbox.end,
.end {
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
}
.hbox.center,
.vbox.center,
.center {
  /* Old browsers */
  -webkit-box-pack: center;
  -moz-box-pack: center;
  box-pack: center;
  /* Modern browsers */
  justify-content: center;
}
.hbox.baseline,
.vbox.baseline,
.baseline {
  /* Old browsers */
  -webkit-box-pack: baseline;
  -moz-box-pack: baseline;
  box-pack: baseline;
  /* Modern browsers */
  justify-content: baseline;
}
.hbox.stretch,
.vbox.stretch,
.stretch {
  /* Old browsers */
  -webkit-box-pack: stretch;
  -moz-box-pack: stretch;
  box-pack: stretch;
  /* Modern browsers */
  justify-content: stretch;
}
.hbox.align-start,
.vbox.align-start,
.align-start {
  /* Old browsers */
  -webkit-box-align: start;
  -moz-box-align: start;
  box-align: start;
  /* Modern browsers */
  align-items: flex-start;
}
.hbox.align-end,
.vbox.align-end,
.align-end {
  /* Old browsers */
  -webkit-box-align: end;
  -moz-box-align: end;
  box-align: end;
  /* Modern browsers */
  align-items: flex-end;
}
.hbox.align-center,
.vbox.align-center,
.align-center {
  /* Old browsers */
  -webkit-box-align: center;
  -moz-box-align: center;
  box-align: center;
  /* Modern browsers */
  align-items: center;
}
.hbox.align-baseline,
.vbox.align-baseline,
.align-baseline {
  /* Old browsers */
  -webkit-box-align: baseline;
  -moz-box-align: baseline;
  box-align: baseline;
  /* Modern browsers */
  align-items: baseline;
}
.hbox.align-stretch,
.vbox.align-stretch,
.align-stretch {
  /* Old browsers */
  -webkit-box-align: stretch;
  -moz-box-align: stretch;
  box-align: stretch;
  /* Modern browsers */
  align-items: stretch;
}
div.error {
  margin: 2em;
  text-align: center;
}
div.error > h1 {
  font-size: 500%;
  line-height: normal;
}
div.error > p {
  font-size: 200%;
  line-height: normal;
}
div.traceback-wrapper {
  text-align: left;
  max-width: 800px;
  margin: auto;
}
div.traceback-wrapper pre.traceback {
  max-height: 600px;
  overflow: auto;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
body {
  background-color: #fff;
  /* This makes sure that the body covers the entire window and needs to
       be in a different element than the display: box in wrapper below */
  position: absolute;
  left: 0px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  overflow: visible;
}
body > #header {
  /* Initially hidden to prevent FLOUC */
  display: none;
  background-color: #fff;
  /* Display over codemirror */
  position: relative;
  z-index: 100;
}
body > #header #header-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 5px;
  padding-bottom: 5px;
  padding-top: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
body > #header .header-bar {
  width: 100%;
  height: 1px;
  background: #e7e7e7;
  margin-bottom: -1px;
}
@media print {
  body > #header {
    display: none !important;
  }
}
#header-spacer {
  width: 100%;
  visibility: hidden;
}
@media print {
  #header-spacer {
    display: none;
  }
}
#ipython_notebook {
  padding-left: 0px;
  padding-top: 1px;
  padding-bottom: 1px;
}
[dir="rtl"] #ipython_notebook {
  margin-right: 10px;
  margin-left: 0;
}
[dir="rtl"] #ipython_notebook.pull-left {
  float: right !important;
  float: right;
}
.flex-spacer {
  flex: 1;
}
#noscript {
  width: auto;
  padding-top: 16px;
  padding-bottom: 16px;
  text-align: center;
  font-size: 22px;
  color: red;
  font-weight: bold;
}
#ipython_notebook img {
  height: 28px;
}
#site {
  width: 100%;
  display: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  overflow: auto;
}
@media print {
  #site {
    height: auto !important;
  }
}
/* Smaller buttons */
.ui-button .ui-button-text {
  padding: 0.2em 0.8em;
  font-size: 77%;
}
input.ui-button {
  padding: 0.3em 0.9em;
}
span#kernel_logo_widget {
  margin: 0 10px;
}
span#login_widget {
  float: right;
}
[dir="rtl"] span#login_widget {
  float: left;
}
span#login_widget > .button,
#logout {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button:focus,
#logout:focus,
span#login_widget > .button.focus,
#logout.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
span#login_widget > .button:hover,
#logout:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active:hover,
#logout:active:hover,
span#login_widget > .button.active:hover,
#logout.active:hover,
.open > .dropdown-togglespan#login_widget > .button:hover,
.open > .dropdown-toggle#logout:hover,
span#login_widget > .button:active:focus,
#logout:active:focus,
span#login_widget > .button.active:focus,
#logout.active:focus,
.open > .dropdown-togglespan#login_widget > .button:focus,
.open > .dropdown-toggle#logout:focus,
span#login_widget > .button:active.focus,
#logout:active.focus,
span#login_widget > .button.active.focus,
#logout.active.focus,
.open > .dropdown-togglespan#login_widget > .button.focus,
.open > .dropdown-toggle#logout.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  background-image: none;
}
span#login_widget > .button.disabled:hover,
#logout.disabled:hover,
span#login_widget > .button[disabled]:hover,
#logout[disabled]:hover,
fieldset[disabled] span#login_widget > .button:hover,
fieldset[disabled] #logout:hover,
span#login_widget > .button.disabled:focus,
#logout.disabled:focus,
span#login_widget > .button[disabled]:focus,
#logout[disabled]:focus,
fieldset[disabled] span#login_widget > .button:focus,
fieldset[disabled] #logout:focus,
span#login_widget > .button.disabled.focus,
#logout.disabled.focus,
span#login_widget > .button[disabled].focus,
#logout[disabled].focus,
fieldset[disabled] span#login_widget > .button.focus,
fieldset[disabled] #logout.focus {
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button .badge,
#logout .badge {
  color: #fff;
  background-color: #333;
}
.nav-header {
  text-transform: none;
}
#header > span {
  margin-top: 10px;
}
.modal_stretch .modal-dialog {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  min-height: 80vh;
}
.modal_stretch .modal-dialog .modal-body {
  max-height: calc(100vh - 200px);
  overflow: auto;
  flex: 1;
}
.modal-header {
  cursor: move;
}
@media (min-width: 768px) {
  .modal .modal-dialog {
    width: 700px;
  }
}
@media (min-width: 768px) {
  select.form-control {
    margin-left: 12px;
    margin-right: 12px;
  }
}
/*!
*
* IPython auth
*
*/
.center-nav {
  display: inline-block;
  margin-bottom: -4px;
}
[dir="rtl"] .center-nav form.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] .center-nav .navbar-text {
  float: right;
}
[dir="rtl"] .navbar-inner {
  text-align: right;
}
[dir="rtl"] div.text-left {
  text-align: right;
}
/*!
*
* IPython tree view
*
*/
/* We need an invisible input field on top of the sentense*/
/* "Drag file onto the list ..." */
.alternate_upload {
  background-color: none;
  display: inline;
}
.alternate_upload.form {
  padding: 0;
  margin: 0;
}
.alternate_upload input.fileinput {
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
  overflow: hidden;
  cursor: pointer;
  opacity: 0;
  z-index: 2;
}
.alternate_upload .btn-xs > input.fileinput {
  margin: -1px -5px;
}
.alternate_upload .btn-upload {
  position: relative;
  height: 22px;
}
::-webkit-file-upload-button {
  cursor: pointer;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
ul#tabs {
  margin-bottom: 4px;
}
ul#tabs a {
  padding-top: 6px;
  padding-bottom: 4px;
}
[dir="rtl"] ul#tabs.nav-tabs > li {
  float: right;
}
[dir="rtl"] ul#tabs.nav.nav-tabs {
  padding-right: 0;
}
ul.breadcrumb a:focus,
ul.breadcrumb a:hover {
  text-decoration: none;
}
ul.breadcrumb i.icon-home {
  font-size: 16px;
  margin-right: 4px;
}
ul.breadcrumb span {
  color: #5e5e5e;
}
.list_toolbar {
  padding: 4px 0 4px 0;
  vertical-align: middle;
}
.list_toolbar .tree-buttons {
  padding-top: 1px;
}
[dir="rtl"] .list_toolbar .tree-buttons .pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .list_toolbar .col-sm-4,
[dir="rtl"] .list_toolbar .col-sm-8 {
  float: right;
}
.dynamic-buttons {
  padding-top: 3px;
  display: inline-block;
}
.list_toolbar [class*="span"] {
  min-height: 24px;
}
.list_header {
  font-weight: bold;
  background-color: #EEE;
}
.list_placeholder {
  font-weight: bold;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
}
.list_container {
  margin-top: 4px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 2px;
}
.list_container > div {
  border-bottom: 1px solid #ddd;
}
.list_container > div:hover .list-item {
  background-color: red;
}
.list_container > div:last-child {
  border: none;
}
.list_item:hover .list_item {
  background-color: #ddd;
}
.list_item a {
  text-decoration: none;
}
.list_item:hover {
  background-color: #fafafa;
}
.list_header > div,
.list_item > div {
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
.list_header > div input,
.list_item > div input {
  margin-right: 7px;
  margin-left: 14px;
  vertical-align: text-bottom;
  line-height: 22px;
  position: relative;
  top: -1px;
}
.list_header > div .item_link,
.list_item > div .item_link {
  margin-left: -1px;
  vertical-align: baseline;
  line-height: 22px;
}
[dir="rtl"] .list_item > div input {
  margin-right: 0;
}
.new-file input[type=checkbox] {
  visibility: hidden;
}
.item_name {
  line-height: 22px;
  height: 24px;
}
.item_icon {
  font-size: 14px;
  color: #5e5e5e;
  margin-right: 7px;
  margin-left: 7px;
  line-height: 22px;
  vertical-align: baseline;
}
.item_modified {
  margin-right: 7px;
  margin-left: 7px;
}
[dir="rtl"] .item_modified.pull-right {
  float: left !important;
  float: left;
}
.item_buttons {
  line-height: 1em;
  margin-left: -5px;
}
.item_buttons .btn,
.item_buttons .btn-group,
.item_buttons .input-group {
  float: left;
}
.item_buttons > .btn,
.item_buttons > .btn-group,
.item_buttons > .input-group {
  margin-left: 5px;
}
.item_buttons .btn {
  min-width: 13ex;
}
.item_buttons .running-indicator {
  padding-top: 4px;
  color: #5cb85c;
}
.item_buttons .kernel-name {
  padding-top: 4px;
  color: #5bc0de;
  margin-right: 7px;
  float: left;
}
[dir="rtl"] .item_buttons.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .item_buttons .kernel-name {
  margin-left: 7px;
  float: right;
}
.toolbar_info {
  height: 24px;
  line-height: 24px;
}
.list_item input:not([type=checkbox]) {
  padding-top: 3px;
  padding-bottom: 3px;
  height: 22px;
  line-height: 14px;
  margin: 0px;
}
.highlight_text {
  color: blue;
}
#project_name {
  display: inline-block;
  padding-left: 7px;
  margin-left: -2px;
}
#project_name > .breadcrumb {
  padding: 0px;
  margin-bottom: 0px;
  background-color: transparent;
  font-weight: bold;
}
.sort_button {
  display: inline-block;
  padding-left: 7px;
}
[dir="rtl"] .sort_button.pull-right {
  float: left !important;
  float: left;
}
#tree-selector {
  padding-right: 0px;
}
#button-select-all {
  min-width: 50px;
}
[dir="rtl"] #button-select-all.btn {
  float: right ;
}
#select-all {
  margin-left: 7px;
  margin-right: 2px;
  margin-top: 2px;
  height: 16px;
}
[dir="rtl"] #select-all.pull-left {
  float: right !important;
  float: right;
}
.menu_icon {
  margin-right: 2px;
}
.tab-content .row {
  margin-left: 0px;
  margin-right: 0px;
}
.folder_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f114";
}
.folder_icon:before.fa-pull-left {
  margin-right: .3em;
}
.folder_icon:before.fa-pull-right {
  margin-left: .3em;
}
.folder_icon:before.pull-left {
  margin-right: .3em;
}
.folder_icon:before.pull-right {
  margin-left: .3em;
}
.notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
}
.notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.notebook_icon:before.fa-pull-right {
  margin-left: .3em;
}
.notebook_icon:before.pull-left {
  margin-right: .3em;
}
.notebook_icon:before.pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
  color: #5cb85c;
}
.running_notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.fa-pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before.pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.pull-right {
  margin-left: .3em;
}
.file_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f016";
  position: relative;
  top: -2px;
}
.file_icon:before.fa-pull-left {
  margin-right: .3em;
}
.file_icon:before.fa-pull-right {
  margin-left: .3em;
}
.file_icon:before.pull-left {
  margin-right: .3em;
}
.file_icon:before.pull-right {
  margin-left: .3em;
}
#notebook_toolbar .pull-right {
  padding-top: 0px;
  margin-right: -1px;
}
ul#new-menu {
  left: auto;
  right: 0;
}
#new-menu .dropdown-header {
  font-size: 10px;
  border-bottom: 1px solid #e5e5e5;
  padding: 0 0 3px;
  margin: -3px 20px 0;
}
.kernel-menu-icon {
  padding-right: 12px;
  width: 24px;
  content: "\f096";
}
.kernel-menu-icon:before {
  content: "\f096";
}
.kernel-menu-icon-current:before {
  content: "\f00c";
}
#tab_content {
  padding-top: 20px;
}
#running .panel-group .panel {
  margin-top: 3px;
  margin-bottom: 1em;
}
#running .panel-group .panel .panel-heading {
  background-color: #EEE;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
#running .panel-group .panel .panel-heading a:focus,
#running .panel-group .panel .panel-heading a:hover {
  text-decoration: none;
}
#running .panel-group .panel .panel-body {
  padding: 0px;
}
#running .panel-group .panel .panel-body .list_container {
  margin-top: 0px;
  margin-bottom: 0px;
  border: 0px;
  border-radius: 0px;
}
#running .panel-group .panel .panel-body .list_container .list_item {
  border-bottom: 1px solid #ddd;
}
#running .panel-group .panel .panel-body .list_container .list_item:last-child {
  border-bottom: 0px;
}
.delete-button {
  display: none;
}
.duplicate-button {
  display: none;
}
.rename-button {
  display: none;
}
.move-button {
  display: none;
}
.download-button {
  display: none;
}
.shutdown-button {
  display: none;
}
.dynamic-instructions {
  display: inline-block;
  padding-top: 4px;
}
/*!
*
* IPython text editor webapp
*
*/
.selected-keymap i.fa {
  padding: 0px 5px;
}
.selected-keymap i.fa:before {
  content: "\f00c";
}
#mode-menu {
  overflow: auto;
  max-height: 20em;
}
.edit_app #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.edit_app #menubar .navbar {
  /* Use a negative 1 bottom margin, so the border overlaps the border of the
    header */
  margin-bottom: -1px;
}
.dirty-indicator {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator.pull-left {
  margin-right: .3em;
}
.dirty-indicator.pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-dirty.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty.pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-clean.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f00c";
}
.dirty-indicator-clean:before.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.pull-right {
  margin-left: .3em;
}
#filename {
  font-size: 16pt;
  display: table;
  padding: 0px 5px;
}
#current-mode {
  padding-left: 5px;
  padding-right: 5px;
}
#texteditor-backdrop {
  padding-top: 20px;
  padding-bottom: 20px;
}
@media not print {
  #texteditor-backdrop {
    background-color: #EEE;
  }
}
@media print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container {
    padding: 0px;
    background-color: #fff;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
.CodeMirror-dialog {
  background-color: #fff;
}
/*!
*
* IPython notebook
*
*/
/* CSS font colors for translated ANSI escape sequences */
/* The color values are a mix of
   http://www.xcolors.net/dl/baskerville-ivorylight and
   http://www.xcolors.net/dl/euphrasia */
.ansi-black-fg {
  color: #3E424D;
}
.ansi-black-bg {
  background-color: #3E424D;
}
.ansi-black-intense-fg {
  color: #282C36;
}
.ansi-black-intense-bg {
  background-color: #282C36;
}
.ansi-red-fg {
  color: #E75C58;
}
.ansi-red-bg {
  background-color: #E75C58;
}
.ansi-red-intense-fg {
  color: #B22B31;
}
.ansi-red-intense-bg {
  background-color: #B22B31;
}
.ansi-green-fg {
  color: #00A250;
}
.ansi-green-bg {
  background-color: #00A250;
}
.ansi-green-intense-fg {
  color: #007427;
}
.ansi-green-intense-bg {
  background-color: #007427;
}
.ansi-yellow-fg {
  color: #DDB62B;
}
.ansi-yellow-bg {
  background-color: #DDB62B;
}
.ansi-yellow-intense-fg {
  color: #B27D12;
}
.ansi-yellow-intense-bg {
  background-color: #B27D12;
}
.ansi-blue-fg {
  color: #208FFB;
}
.ansi-blue-bg {
  background-color: #208FFB;
}
.ansi-blue-intense-fg {
  color: #0065CA;
}
.ansi-blue-intense-bg {
  background-color: #0065CA;
}
.ansi-magenta-fg {
  color: #D160C4;
}
.ansi-magenta-bg {
  background-color: #D160C4;
}
.ansi-magenta-intense-fg {
  color: #A03196;
}
.ansi-magenta-intense-bg {
  background-color: #A03196;
}
.ansi-cyan-fg {
  color: #60C6C8;
}
.ansi-cyan-bg {
  background-color: #60C6C8;
}
.ansi-cyan-intense-fg {
  color: #258F8F;
}
.ansi-cyan-intense-bg {
  background-color: #258F8F;
}
.ansi-white-fg {
  color: #C5C1B4;
}
.ansi-white-bg {
  background-color: #C5C1B4;
}
.ansi-white-intense-fg {
  color: #A1A6B2;
}
.ansi-white-intense-bg {
  background-color: #A1A6B2;
}
.ansi-default-inverse-fg {
  color: #FFFFFF;
}
.ansi-default-inverse-bg {
  background-color: #000000;
}
.ansi-bold {
  font-weight: bold;
}
.ansi-underline {
  text-decoration: underline;
}
/* The following styles are deprecated an will be removed in a future version */
.ansibold {
  font-weight: bold;
}
.ansi-inverse {
  outline: 0.5px dotted;
}
/* use dark versions for foreground, to improve visibility */
.ansiblack {
  color: black;
}
.ansired {
  color: darkred;
}
.ansigreen {
  color: darkgreen;
}
.ansiyellow {
  color: #c4a000;
}
.ansiblue {
  color: darkblue;
}
.ansipurple {
  color: darkviolet;
}
.ansicyan {
  color: steelblue;
}
.ansigray {
  color: gray;
}
/* and light for background, for the same reason */
.ansibgblack {
  background-color: black;
}
.ansibgred {
  background-color: red;
}
.ansibggreen {
  background-color: green;
}
.ansibgyellow {
  background-color: yellow;
}
.ansibgblue {
  background-color: blue;
}
.ansibgpurple {
  background-color: magenta;
}
.ansibgcyan {
  background-color: cyan;
}
.ansibggray {
  background-color: gray;
}
div.cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-radius: 2px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border-width: 1px;
  border-style: solid;
  border-color: transparent;
  width: 100%;
  padding: 5px;
  /* This acts as a spacer between cells, that is outside the border */
  margin: 0px;
  outline: none;
  position: relative;
  overflow: visible;
}
div.cell:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: transparent;
}
div.cell.jupyter-soft-selected {
  border-left-color: #E3F2FD;
  border-left-width: 1px;
  padding-left: 5px;
  border-right-color: #E3F2FD;
  border-right-width: 1px;
  background: #E3F2FD;
}
@media print {
  div.cell.jupyter-soft-selected {
    border-color: transparent;
  }
}
div.cell.selected,
div.cell.selected.jupyter-soft-selected {
  border-color: #ababab;
}
div.cell.selected:before,
div.cell.selected.jupyter-soft-selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #42A5F5;
}
@media print {
  div.cell.selected,
  div.cell.selected.jupyter-soft-selected {
    border-color: transparent;
  }
}
.edit_mode div.cell.selected {
  border-color: #66BB6A;
}
.edit_mode div.cell.selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #66BB6A;
}
@media print {
  .edit_mode div.cell.selected {
    border-color: transparent;
  }
}
.prompt {
  /* This needs to be wide enough for 3 digit prompt numbers: In[100]: */
  min-width: 14ex;
  /* This padding is tuned to match the padding on the CodeMirror editor. */
  padding: 0.4em;
  margin: 0px;
  font-family: monospace;
  text-align: right;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
  /* Don't highlight prompt number selection */
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  /* Use default cursor */
  cursor: default;
}
@media (max-width: 540px) {
  .prompt {
    text-align: left;
  }
}
div.inner_cell {
  min-width: 0;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_area {
  border: 1px solid #cfcfcf;
  border-radius: 2px;
  background: #f7f7f7;
  line-height: 1.21429em;
}
/* This is needed so that empty prompt areas can collapse to zero height when there
   is no content in the output_subarea and the prompt. The main purpose of this is
   to make sure that empty JavaScript output_subareas have no height. */
div.prompt:empty {
  padding-top: 0;
  padding-bottom: 0;
}
div.unrecognized_cell {
  padding: 5px 5px 5px 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.unrecognized_cell .inner_cell {
  border-radius: 2px;
  padding: 5px;
  font-weight: bold;
  color: red;
  border: 1px solid #cfcfcf;
  background: #eaeaea;
}
div.unrecognized_cell .inner_cell a {
  color: inherit;
  text-decoration: none;
}
div.unrecognized_cell .inner_cell a:hover {
  color: inherit;
  text-decoration: none;
}
@media (max-width: 540px) {
  div.unrecognized_cell > div.prompt {
    display: none;
  }
}
div.code_cell {
  /* avoid page breaking on code cells when printing */
}
@media print {
  div.code_cell {
    page-break-inside: avoid;
  }
}
/* any special styling for code cells that are currently running goes here */
div.input {
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.input {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_prompt {
  color: #303F9F;
  border-top: 1px solid transparent;
}
div.input_area > div.highlight {
  margin: 0.4em;
  border: none;
  padding: 0px;
  background-color: transparent;
}
div.input_area > div.highlight > pre {
  margin: 0px;
  border: none;
  padding: 0px;
  background-color: transparent;
}
/* The following gets added to the <head> if it is detected that the user has a
 * monospace font with inconsistent normal/bold/italic height.  See
 * notebookmain.js.  Such fonts will have keywords vertically offset with
 * respect to the rest of the text.  The user should select a better font.
 * See: https://github.com/ipython/ipython/issues/1503
 *
 * .CodeMirror span {
 *      vertical-align: bottom;
 * }
 */
.CodeMirror {
  line-height: 1.21429em;
  /* Changed from 1em to our global default */
  font-size: 14px;
  height: auto;
  /* Changed to auto to autogrow */
  background: none;
  /* Changed from white to allow our bg to show through */
}
.CodeMirror-scroll {
  /*  The CodeMirror docs are a bit fuzzy on if overflow-y should be hidden or visible.*/
  /*  We have found that if it is visible, vertical scrollbars appear with font size changes.*/
  overflow-y: hidden;
  overflow-x: auto;
}
.CodeMirror-lines {
  /* In CM2, this used to be 0.4em, but in CM3 it went to 4px. We need the em value because */
  /* we have set a different line-height and want this to scale with that. */
  /* Note that this should set vertical padding only, since CodeMirror assumes
       that horizontal padding will be set on CodeMirror pre */
  padding: 0.4em 0;
}
.CodeMirror-linenumber {
  padding: 0 8px 0 4px;
}
.CodeMirror-gutters {
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.CodeMirror pre {
  /* In CM3 this went to 4px from 0 in CM2. This sets horizontal padding only,
    use .CodeMirror-lines for vertical */
  padding: 0 0.4em;
  border: 0;
  border-radius: 0;
}
.CodeMirror-cursor {
  border-left: 1.4px solid black;
}
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .CodeMirror-cursor {
    border-left: 2px solid black;
  }
}
@media screen and (min-width: 4320px) {
  .CodeMirror-cursor {
    border-left: 4px solid black;
  }
}
/*

Original style from softwaremaniacs.org (c) Ivan Sagalaev <Maniac@SoftwareManiacs.Org>
Adapted from GitHub theme

*/
.highlight-base {
  color: #000;
}
.highlight-variable {
  color: #000;
}
.highlight-variable-2 {
  color: #1a1a1a;
}
.highlight-variable-3 {
  color: #333333;
}
.highlight-string {
  color: #BA2121;
}
.highlight-comment {
  color: #408080;
  font-style: italic;
}
.highlight-number {
  color: #080;
}
.highlight-atom {
  color: #88F;
}
.highlight-keyword {
  color: #008000;
  font-weight: bold;
}
.highlight-builtin {
  color: #008000;
}
.highlight-error {
  color: #f00;
}
.highlight-operator {
  color: #AA22FF;
  font-weight: bold;
}
.highlight-meta {
  color: #AA22FF;
}
/* previously not defined, copying from default codemirror */
.highlight-def {
  color: #00f;
}
.highlight-string-2 {
  color: #f50;
}
.highlight-qualifier {
  color: #555;
}
.highlight-bracket {
  color: #997;
}
.highlight-tag {
  color: #170;
}
.highlight-attribute {
  color: #00c;
}
.highlight-header {
  color: blue;
}
.highlight-quote {
  color: #090;
}
.highlight-link {
  color: #00c;
}
/* apply the same style to codemirror */
.cm-s-ipython span.cm-keyword {
  color: #008000;
  font-weight: bold;
}
.cm-s-ipython span.cm-atom {
  color: #88F;
}
.cm-s-ipython span.cm-number {
  color: #080;
}
.cm-s-ipython span.cm-def {
  color: #00f;
}
.cm-s-ipython span.cm-variable {
  color: #000;
}
.cm-s-ipython span.cm-operator {
  color: #AA22FF;
  font-weight: bold;
}
.cm-s-ipython span.cm-variable-2 {
  color: #1a1a1a;
}
.cm-s-ipython span.cm-variable-3 {
  color: #333333;
}
.cm-s-ipython span.cm-comment {
  color: #408080;
  font-style: italic;
}
.cm-s-ipython span.cm-string {
  color: #BA2121;
}
.cm-s-ipython span.cm-string-2 {
  color: #f50;
}
.cm-s-ipython span.cm-meta {
  color: #AA22FF;
}
.cm-s-ipython span.cm-qualifier {
  color: #555;
}
.cm-s-ipython span.cm-builtin {
  color: #008000;
}
.cm-s-ipython span.cm-bracket {
  color: #997;
}
.cm-s-ipython span.cm-tag {
  color: #170;
}
.cm-s-ipython span.cm-attribute {
  color: #00c;
}
.cm-s-ipython span.cm-header {
  color: blue;
}
.cm-s-ipython span.cm-quote {
  color: #090;
}
.cm-s-ipython span.cm-link {
  color: #00c;
}
.cm-s-ipython span.cm-error {
  color: #f00;
}
.cm-s-ipython span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}
div.output_wrapper {
  /* this position must be relative to enable descendents to be absolute within it */
  position: relative;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  z-index: 1;
}
/* class for the output area when it should be height-limited */
div.output_scroll {
  /* ideally, this would be max-height, but FF barfs all over that */
  height: 24em;
  /* FF needs this *and the wrapper* to specify full width, or it will shrinkwrap */
  width: 100%;
  overflow: auto;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  display: block;
}
/* output div while it is collapsed */
div.output_collapsed {
  margin: 0px;
  padding: 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
div.out_prompt_overlay {
  height: 100%;
  padding: 0px 0.4em;
  position: absolute;
  border-radius: 2px;
}
div.out_prompt_overlay:hover {
  /* use inner shadow to get border that is computed the same on WebKit/FF */
  -webkit-box-shadow: inset 0 0 1px #000;
  box-shadow: inset 0 0 1px #000;
  background: rgba(240, 240, 240, 0.5);
}
div.output_prompt {
  color: #D84315;
}
/* This class is the outer container of all output sections. */
div.output_area {
  padding: 0px;
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.output_area .MathJax_Display {
  text-align: left !important;
}
div.output_area .rendered_html table {
  margin-left: 0;
  margin-right: 0;
}
div.output_area .rendered_html img {
  margin-left: 0;
  margin-right: 0;
}
div.output_area img,
div.output_area svg {
  max-width: 100%;
  height: auto;
}
div.output_area img.unconfined,
div.output_area svg.unconfined {
  max-width: none;
}
div.output_area .mglyph > img {
  max-width: none;
}
/* This is needed to protect the pre formating from global settings such
   as that of bootstrap */
.output {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.output_area {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
div.output_area pre {
  margin: 0;
  padding: 1px 0 1px 0;
  border: 0;
  vertical-align: baseline;
  color: black;
  background-color: transparent;
  border-radius: 0;
}
/* This class is for the output subarea inside the output_area and after
   the prompt div. */
div.output_subarea {
  overflow-x: auto;
  padding: 0.4em;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
  max-width: calc(100% - 14ex);
}
div.output_scroll div.output_subarea {
  overflow-x: visible;
}
/* The rest of the output_* classes are for special styling of the different
   output types */
/* all text output has this class: */
div.output_text {
  text-align: left;
  color: #000;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
}
/* stdout/stderr are 'text' as well as 'stream', but execute_result/error are *not* streams */
div.output_stderr {
  background: #fdd;
  /* very light red background for stderr */
}
div.output_latex {
  text-align: left;
}
/* Empty output_javascript divs should have no height */
div.output_javascript:empty {
  padding: 0;
}
.js-error {
  color: darkred;
}
/* raw_input styles */
div.raw_input_container {
  line-height: 1.21429em;
  padding-top: 5px;
}
pre.raw_input_prompt {
  /* nothing needed here. */
}
input.raw_input {
  font-family: monospace;
  font-size: inherit;
  color: inherit;
  width: auto;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
}
input.raw_input:focus {
  box-shadow: none;
}
p.p-space {
  margin-bottom: 10px;
}
div.output_unrecognized {
  padding: 5px;
  font-weight: bold;
  color: red;
}
div.output_unrecognized a {
  color: inherit;
  text-decoration: none;
}
div.output_unrecognized a:hover {
  color: inherit;
  text-decoration: none;
}
.rendered_html {
  color: #000;
  /* any extras will just be numbers: */
}
.rendered_html em {
  font-style: italic;
}
.rendered_html strong {
  font-weight: bold;
}
.rendered_html u {
  text-decoration: underline;
}
.rendered_html :link {
  text-decoration: underline;
}
.rendered_html :visited {
  text-decoration: underline;
}
.rendered_html h1 {
  font-size: 185.7%;
  margin: 1.08em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h2 {
  font-size: 157.1%;
  margin: 1.27em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h3 {
  font-size: 128.6%;
  margin: 1.55em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h4 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h5 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h6 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h1:first-child {
  margin-top: 0.538em;
}
.rendered_html h2:first-child {
  margin-top: 0.636em;
}
.rendered_html h3:first-child {
  margin-top: 0.777em;
}
.rendered_html h4:first-child {
  margin-top: 1em;
}
.rendered_html h5:first-child {
  margin-top: 1em;
}
.rendered_html h6:first-child {
  margin-top: 1em;
}
.rendered_html ul:not(.list-inline),
.rendered_html ol:not(.list-inline) {
  padding-left: 2em;
}
.rendered_html ul {
  list-style: disc;
}
.rendered_html ul ul {
  list-style: square;
  margin-top: 0;
}
.rendered_html ul ul ul {
  list-style: circle;
}
.rendered_html ol {
  list-style: decimal;
}
.rendered_html ol ol {
  list-style: upper-alpha;
  margin-top: 0;
}
.rendered_html ol ol ol {
  list-style: lower-alpha;
}
.rendered_html ol ol ol ol {
  list-style: lower-roman;
}
.rendered_html ol ol ol ol ol {
  list-style: decimal;
}
.rendered_html * + ul {
  margin-top: 1em;
}
.rendered_html * + ol {
  margin-top: 1em;
}
.rendered_html hr {
  color: black;
  background-color: black;
}
.rendered_html pre {
  margin: 1em 2em;
  padding: 0px;
  background-color: #fff;
}
.rendered_html code {
  background-color: #eff0f1;
}
.rendered_html p code {
  padding: 1px 5px;
}
.rendered_html pre code {
  background-color: #fff;
}
.rendered_html pre,
.rendered_html code {
  border: 0;
  color: #000;
  font-size: 100%;
}
.rendered_html blockquote {
  margin: 1em 2em;
}
.rendered_html table {
  margin-left: auto;
  margin-right: auto;
  border: none;
  border-collapse: collapse;
  border-spacing: 0;
  color: black;
  font-size: 12px;
  table-layout: fixed;
}
.rendered_html thead {
  border-bottom: 1px solid black;
  vertical-align: bottom;
}
.rendered_html tr,
.rendered_html th,
.rendered_html td {
  text-align: right;
  vertical-align: middle;
  padding: 0.5em 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}
.rendered_html th {
  font-weight: bold;
}
.rendered_html tbody tr:nth-child(odd) {
  background: #f5f5f5;
}
.rendered_html tbody tr:hover {
  background: rgba(66, 165, 245, 0.2);
}
.rendered_html * + table {
  margin-top: 1em;
}
.rendered_html p {
  text-align: left;
}
.rendered_html * + p {
  margin-top: 1em;
}
.rendered_html img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.rendered_html * + img {
  margin-top: 1em;
}
.rendered_html img,
.rendered_html svg {
  max-width: 100%;
  height: auto;
}
.rendered_html img.unconfined,
.rendered_html svg.unconfined {
  max-width: none;
}
.rendered_html .alert {
  margin-bottom: initial;
}
.rendered_html * + .alert {
  margin-top: 1em;
}
[dir="rtl"] .rendered_html p {
  text-align: right;
}
div.text_cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.text_cell > div.prompt {
    display: none;
  }
}
div.text_cell_render {
  /*font-family: "Helvetica Neue", Arial, Helvetica, Geneva, sans-serif;*/
  outline: none;
  resize: none;
  width: inherit;
  border-style: none;
  padding: 0.5em 0.5em 0.5em 0.4em;
  color: #000;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
a.anchor-link:link {
  text-decoration: none;
  padding: 0px 20px;
  visibility: hidden;
}
h1:hover .anchor-link,
h2:hover .anchor-link,
h3:hover .anchor-link,
h4:hover .anchor-link,
h5:hover .anchor-link,
h6:hover .anchor-link {
  visibility: visible;
}
.text_cell.rendered .input_area {
  display: none;
}
.text_cell.rendered .rendered_html {
  overflow-x: auto;
  overflow-y: hidden;
}
.text_cell.rendered .rendered_html tr,
.text_cell.rendered .rendered_html th,
.text_cell.rendered .rendered_html td {
  max-width: none;
}
.text_cell.unrendered .text_cell_render {
  display: none;
}
.text_cell .dropzone .input_area {
  border: 2px dashed #bababa;
  margin: -1px;
}
.cm-header-1,
.cm-header-2,
.cm-header-3,
.cm-header-4,
.cm-header-5,
.cm-header-6 {
  font-weight: bold;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
.cm-header-1 {
  font-size: 185.7%;
}
.cm-header-2 {
  font-size: 157.1%;
}
.cm-header-3 {
  font-size: 128.6%;
}
.cm-header-4 {
  font-size: 110%;
}
.cm-header-5 {
  font-size: 100%;
  font-style: italic;
}
.cm-header-6 {
  font-size: 100%;
  font-style: italic;
}
/*!
*
* IPython notebook webapp
*
*/
@media (max-width: 767px) {
  .notebook_app {
    padding-left: 0px;
    padding-right: 0px;
  }
}
#ipython-main-app {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook_panel {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook {
  font-size: 14px;
  line-height: 20px;
  overflow-y: hidden;
  overflow-x: auto;
  width: 100%;
  /* This spaces the page away from the edge of the notebook area */
  padding-top: 20px;
  margin: 0px;
  outline: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  min-height: 100%;
}
@media not print {
  #notebook-container {
    padding: 15px;
    background-color: #fff;
    min-height: 0;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
@media print {
  #notebook-container {
    width: 100%;
  }
}
div.ui-widget-content {
  border: 1px solid #ababab;
  outline: none;
}
pre.dialog {
  background-color: #f7f7f7;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0.4em;
  padding-left: 2em;
}
p.dialog {
  padding: 0.2em;
}
/* Word-wrap output correctly.  This is the CSS3 spelling, though Firefox seems
   to not honor it correctly.  Webkit browsers (Chrome, rekonq, Safari) do.
 */
pre,
code,
kbd,
samp {
  white-space: pre-wrap;
}
#fonttest {
  font-family: monospace;
}
p {
  margin-bottom: 0;
}
.end_space {
  min-height: 100px;
  transition: height .2s ease;
}
.notebook_app > #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
@media not print {
  .notebook_app {
    background-color: #EEE;
  }
}
kbd {
  border-style: solid;
  border-width: 1px;
  box-shadow: none;
  margin: 2px;
  padding-left: 2px;
  padding-right: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
.jupyter-keybindings {
  padding: 1px;
  line-height: 24px;
  border-bottom: 1px solid gray;
}
.jupyter-keybindings input {
  margin: 0;
  padding: 0;
  border: none;
}
.jupyter-keybindings i {
  padding: 6px;
}
.well code {
  background-color: #ffffff;
  border-color: #ababab;
  border-width: 1px;
  border-style: solid;
  padding: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
/* CSS for the cell toolbar */
.celltoolbar {
  border: thin solid #CFCFCF;
  border-bottom: none;
  background: #EEE;
  border-radius: 2px 2px 0px 0px;
  width: 100%;
  height: 29px;
  padding-right: 4px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
  display: -webkit-flex;
}
@media print {
  .celltoolbar {
    display: none;
  }
}
.ctb_hideshow {
  display: none;
  vertical-align: bottom;
}
/* ctb_show is added to the ctb_hideshow div to show the cell toolbar.
   Cell toolbars are only shown when the ctb_global_show class is also set.
*/
.ctb_global_show .ctb_show.ctb_hideshow {
  display: block;
}
.ctb_global_show .ctb_show + .input_area,
.ctb_global_show .ctb_show + div.text_cell_input,
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border-top-right-radius: 0px;
  border-top-left-radius: 0px;
}
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border: 1px solid #cfcfcf;
}
.celltoolbar {
  font-size: 87%;
  padding-top: 3px;
}
.celltoolbar select {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  width: inherit;
  font-size: inherit;
  height: 22px;
  padding: 0px;
  display: inline-block;
}
.celltoolbar select:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.celltoolbar select::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.celltoolbar select:-ms-input-placeholder {
  color: #999;
}
.celltoolbar select::-webkit-input-placeholder {
  color: #999;
}
.celltoolbar select::-ms-expand {
  border: 0;
  background-color: transparent;
}
.celltoolbar select[disabled],
.celltoolbar select[readonly],
fieldset[disabled] .celltoolbar select {
  background-color: #eeeeee;
  opacity: 1;
}
.celltoolbar select[disabled],
fieldset[disabled] .celltoolbar select {
  cursor: not-allowed;
}
textarea.celltoolbar select {
  height: auto;
}
select.celltoolbar select {
  height: 30px;
  line-height: 30px;
}
textarea.celltoolbar select,
select[multiple].celltoolbar select {
  height: auto;
}
.celltoolbar label {
  margin-left: 5px;
  margin-right: 5px;
}
.tags_button_container {
  width: 100%;
  display: flex;
}
.tag-container {
  display: flex;
  flex-direction: row;
  flex-grow: 1;
  overflow: hidden;
  position: relative;
}
.tag-container > * {
  margin: 0 4px;
}
.remove-tag-btn {
  margin-left: 4px;
}
.tags-input {
  display: flex;
}
.cell-tag:last-child:after {
  content: "";
  position: absolute;
  right: 0;
  width: 40px;
  height: 100%;
  /* Fade to background color of cell toolbar */
  background: linear-gradient(to right, rgba(0, 0, 0, 0), #EEE);
}
.tags-input > * {
  margin-left: 4px;
}
.cell-tag,
.tags-input input,
.tags-input button {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  box-shadow: none;
  width: inherit;
  font-size: inherit;
  height: 22px;
  line-height: 22px;
  padding: 0px 4px;
  display: inline-block;
}
.cell-tag:focus,
.tags-input input:focus,
.tags-input button:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.cell-tag::-moz-placeholder,
.tags-input input::-moz-placeholder,
.tags-input button::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.cell-tag:-ms-input-placeholder,
.tags-input input:-ms-input-placeholder,
.tags-input button:-ms-input-placeholder {
  color: #999;
}
.cell-tag::-webkit-input-placeholder,
.tags-input input::-webkit-input-placeholder,
.tags-input button::-webkit-input-placeholder {
  color: #999;
}
.cell-tag::-ms-expand,
.tags-input input::-ms-expand,
.tags-input button::-ms-expand {
  border: 0;
  background-color: transparent;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
.cell-tag[readonly],
.tags-input input[readonly],
.tags-input button[readonly],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  background-color: #eeeeee;
  opacity: 1;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  cursor: not-allowed;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button {
  height: auto;
}
select.cell-tag,
select.tags-input input,
select.tags-input button {
  height: 30px;
  line-height: 30px;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button,
select[multiple].cell-tag,
select[multiple].tags-input input,
select[multiple].tags-input button {
  height: auto;
}
.cell-tag,
.tags-input button {
  padding: 0px 4px;
}
.cell-tag {
  background-color: #fff;
  white-space: nowrap;
}
.tags-input input[type=text]:focus {
  outline: none;
  box-shadow: none;
  border-color: #ccc;
}
.completions {
  position: absolute;
  z-index: 110;
  overflow: hidden;
  border: 1px solid #ababab;
  border-radius: 2px;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  line-height: 1;
}
.completions select {
  background: white;
  outline: none;
  border: none;
  padding: 0px;
  margin: 0px;
  overflow: auto;
  font-family: monospace;
  font-size: 110%;
  color: #000;
  width: auto;
}
.completions select option.context {
  color: #286090;
}
#kernel_logo_widget .current_kernel_logo {
  display: none;
  margin-top: -1px;
  margin-bottom: -1px;
  width: 32px;
  height: 32px;
}
[dir="rtl"] #kernel_logo_widget {
  float: left !important;
  float: left;
}
.modal .modal-body .move-path {
  display: flex;
  flex-direction: row;
  justify-content: space;
  align-items: center;
}
.modal .modal-body .move-path .server-root {
  padding-right: 20px;
}
.modal .modal-body .move-path .path-input {
  flex: 1;
}
#menubar {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  margin-top: 1px;
}
#menubar .navbar {
  border-top: 1px;
  border-radius: 0px 0px 2px 2px;
  margin-bottom: 0px;
}
#menubar .navbar-toggle {
  float: left;
  padding-top: 7px;
  padding-bottom: 7px;
  border: none;
}
#menubar .navbar-collapse {
  clear: left;
}
[dir="rtl"] #menubar .navbar-toggle {
  float: right;
}
[dir="rtl"] #menubar .navbar-collapse {
  clear: right;
}
[dir="rtl"] #menubar .navbar-nav {
  float: right;
}
[dir="rtl"] #menubar .nav {
  padding-right: 0px;
}
[dir="rtl"] #menubar .navbar-nav > li {
  float: right;
}
[dir="rtl"] #menubar .navbar-right {
  float: left !important;
}
[dir="rtl"] ul.dropdown-menu {
  text-align: right;
  left: auto;
}
[dir="rtl"] ul#new-menu.dropdown-menu {
  right: auto;
  left: 0;
}
.nav-wrapper {
  border-bottom: 1px solid #e7e7e7;
}
i.menu-icon {
  padding-top: 4px;
}
[dir="rtl"] i.menu-icon.pull-right {
  float: left !important;
  float: left;
}
ul#help_menu li a {
  overflow: hidden;
  padding-right: 2.2em;
}
ul#help_menu li a i {
  margin-right: -1.2em;
}
[dir="rtl"] ul#help_menu li a {
  padding-left: 2.2em;
}
[dir="rtl"] ul#help_menu li a i {
  margin-right: 0;
  margin-left: -1.2em;
}
[dir="rtl"] ul#help_menu li a i.pull-right {
  float: left !important;
  float: left;
}
.dropdown-submenu {
  position: relative;
}
.dropdown-submenu > .dropdown-menu {
  top: 0;
  left: 100%;
  margin-top: -6px;
  margin-left: -1px;
}
[dir="rtl"] .dropdown-submenu > .dropdown-menu {
  right: 100%;
  margin-right: -1px;
}
.dropdown-submenu:hover > .dropdown-menu {
  display: block;
}
.dropdown-submenu > a:after {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: block;
  content: "\f0da";
  float: right;
  color: #333333;
  margin-top: 2px;
  margin-right: -10px;
}
.dropdown-submenu > a:after.fa-pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.fa-pull-right {
  margin-left: .3em;
}
.dropdown-submenu > a:after.pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.pull-right {
  margin-left: .3em;
}
[dir="rtl"] .dropdown-submenu > a:after {
  float: left;
  content: "\f0d9";
  margin-right: 0;
  margin-left: -10px;
}
.dropdown-submenu:hover > a:after {
  color: #262626;
}
.dropdown-submenu.pull-left {
  float: none;
}
.dropdown-submenu.pull-left > .dropdown-menu {
  left: -100%;
  margin-left: 10px;
}
#notification_area {
  float: right !important;
  float: right;
  z-index: 10;
}
[dir="rtl"] #notification_area {
  float: left !important;
  float: left;
}
.indicator_area {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
[dir="rtl"] .indicator_area {
  float: left !important;
  float: left;
}
#kernel_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  border-left: 1px solid;
}
#kernel_indicator .kernel_indicator_name {
  padding-left: 5px;
  padding-right: 5px;
}
[dir="rtl"] #kernel_indicator {
  float: left !important;
  float: left;
  border-left: 0;
  border-right: 1px solid;
}
#modal_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
[dir="rtl"] #modal_indicator {
  float: left !important;
  float: left;
}
#readonly-indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  margin-top: 2px;
  margin-bottom: 0px;
  margin-left: 0px;
  margin-right: 0px;
  display: none;
}
.modal_indicator:before {
  width: 1.28571429em;
  text-align: center;
}
.edit_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f040";
}
.edit_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
}
.edit_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: ' ';
}
.command_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f10c";
}
.kernel_idle_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f111";
}
.kernel_busy_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f1e2";
}
.kernel_dead_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f127";
}
.kernel_disconnected_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.pull-right {
  margin-left: .3em;
}
.notification_widget {
  color: #777;
  z-index: 10;
  background: rgba(240, 240, 240, 0.5);
  margin-right: 4px;
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget:focus,
.notification_widget.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.notification_widget:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active:hover,
.notification_widget.active:hover,
.open > .dropdown-toggle.notification_widget:hover,
.notification_widget:active:focus,
.notification_widget.active:focus,
.open > .dropdown-toggle.notification_widget:focus,
.notification_widget:active.focus,
.notification_widget.active.focus,
.open > .dropdown-toggle.notification_widget.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  background-image: none;
}
.notification_widget.disabled:hover,
.notification_widget[disabled]:hover,
fieldset[disabled] .notification_widget:hover,
.notification_widget.disabled:focus,
.notification_widget[disabled]:focus,
fieldset[disabled] .notification_widget:focus,
.notification_widget.disabled.focus,
.notification_widget[disabled].focus,
fieldset[disabled] .notification_widget.focus {
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget .badge {
  color: #fff;
  background-color: #333;
}
.notification_widget.warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning:focus,
.notification_widget.warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.notification_widget.warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active:hover,
.notification_widget.warning.active:hover,
.open > .dropdown-toggle.notification_widget.warning:hover,
.notification_widget.warning:active:focus,
.notification_widget.warning.active:focus,
.open > .dropdown-toggle.notification_widget.warning:focus,
.notification_widget.warning:active.focus,
.notification_widget.warning.active.focus,
.open > .dropdown-toggle.notification_widget.warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  background-image: none;
}
.notification_widget.warning.disabled:hover,
.notification_widget.warning[disabled]:hover,
fieldset[disabled] .notification_widget.warning:hover,
.notification_widget.warning.disabled:focus,
.notification_widget.warning[disabled]:focus,
fieldset[disabled] .notification_widget.warning:focus,
.notification_widget.warning.disabled.focus,
.notification_widget.warning[disabled].focus,
fieldset[disabled] .notification_widget.warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.notification_widget.success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success:focus,
.notification_widget.success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.notification_widget.success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active:hover,
.notification_widget.success.active:hover,
.open > .dropdown-toggle.notification_widget.success:hover,
.notification_widget.success:active:focus,
.notification_widget.success.active:focus,
.open > .dropdown-toggle.notification_widget.success:focus,
.notification_widget.success:active.focus,
.notification_widget.success.active.focus,
.open > .dropdown-toggle.notification_widget.success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  background-image: none;
}
.notification_widget.success.disabled:hover,
.notification_widget.success[disabled]:hover,
fieldset[disabled] .notification_widget.success:hover,
.notification_widget.success.disabled:focus,
.notification_widget.success[disabled]:focus,
fieldset[disabled] .notification_widget.success:focus,
.notification_widget.success.disabled.focus,
.notification_widget.success[disabled].focus,
fieldset[disabled] .notification_widget.success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.notification_widget.info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info:focus,
.notification_widget.info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.notification_widget.info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active:hover,
.notification_widget.info.active:hover,
.open > .dropdown-toggle.notification_widget.info:hover,
.notification_widget.info:active:focus,
.notification_widget.info.active:focus,
.open > .dropdown-toggle.notification_widget.info:focus,
.notification_widget.info:active.focus,
.notification_widget.info.active.focus,
.open > .dropdown-toggle.notification_widget.info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  background-image: none;
}
.notification_widget.info.disabled:hover,
.notification_widget.info[disabled]:hover,
fieldset[disabled] .notification_widget.info:hover,
.notification_widget.info.disabled:focus,
.notification_widget.info[disabled]:focus,
fieldset[disabled] .notification_widget.info:focus,
.notification_widget.info.disabled.focus,
.notification_widget.info[disabled].focus,
fieldset[disabled] .notification_widget.info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.notification_widget.danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger:focus,
.notification_widget.danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.notification_widget.danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active:hover,
.notification_widget.danger.active:hover,
.open > .dropdown-toggle.notification_widget.danger:hover,
.notification_widget.danger:active:focus,
.notification_widget.danger.active:focus,
.open > .dropdown-toggle.notification_widget.danger:focus,
.notification_widget.danger:active.focus,
.notification_widget.danger.active.focus,
.open > .dropdown-toggle.notification_widget.danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  background-image: none;
}
.notification_widget.danger.disabled:hover,
.notification_widget.danger[disabled]:hover,
fieldset[disabled] .notification_widget.danger:hover,
.notification_widget.danger.disabled:focus,
.notification_widget.danger[disabled]:focus,
fieldset[disabled] .notification_widget.danger:focus,
.notification_widget.danger.disabled.focus,
.notification_widget.danger[disabled].focus,
fieldset[disabled] .notification_widget.danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger .badge {
  color: #d9534f;
  background-color: #fff;
}
div#pager {
  background-color: #fff;
  font-size: 14px;
  line-height: 20px;
  overflow: hidden;
  display: none;
  position: fixed;
  bottom: 0px;
  width: 100%;
  max-height: 50%;
  padding-top: 8px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  /* Display over codemirror */
  z-index: 100;
  /* Hack which prevents jquery ui resizable from changing top. */
  top: auto !important;
}
div#pager pre {
  line-height: 1.21429em;
  color: #000;
  background-color: #f7f7f7;
  padding: 0.4em;
}
div#pager #pager-button-area {
  position: absolute;
  top: 8px;
  right: 20px;
}
div#pager #pager-contents {
  position: relative;
  overflow: auto;
  width: 100%;
  height: 100%;
}
div#pager #pager-contents #pager-container {
  position: relative;
  padding: 15px 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
div#pager .ui-resizable-handle {
  top: 0px;
  height: 8px;
  background: #f7f7f7;
  border-top: 1px solid #cfcfcf;
  border-bottom: 1px solid #cfcfcf;
  /* This injects handle bars (a short, wide = symbol) for
        the resize handle. */
}
div#pager .ui-resizable-handle::after {
  content: '';
  top: 2px;
  left: 50%;
  height: 3px;
  width: 30px;
  margin-left: -15px;
  position: absolute;
  border-top: 1px solid #cfcfcf;
}
.quickhelp {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  line-height: 1.8em;
}
.shortcut_key {
  display: inline-block;
  width: 21ex;
  text-align: right;
  font-family: monospace;
}
.shortcut_descr {
  display: inline-block;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
span.save_widget {
  height: 30px;
  margin-top: 4px;
  display: flex;
  justify-content: flex-start;
  align-items: baseline;
  width: 50%;
  flex: 1;
}
span.save_widget span.filename {
  height: 100%;
  line-height: 1em;
  margin-left: 16px;
  border: none;
  font-size: 146.5%;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
  border-radius: 2px;
}
span.save_widget span.filename:hover {
  background-color: #e6e6e6;
}
[dir="rtl"] span.save_widget.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] span.save_widget span.filename {
  margin-left: 0;
  margin-right: 16px;
}
span.checkpoint_status,
span.autosave_status {
  font-size: small;
  white-space: nowrap;
  padding: 0 5px;
}
@media (max-width: 767px) {
  span.save_widget {
    font-size: small;
    padding: 0 0 0 5px;
  }
  span.checkpoint_status,
  span.autosave_status {
    display: none;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  span.checkpoint_status {
    display: none;
  }
  span.autosave_status {
    font-size: x-small;
  }
}
.toolbar {
  padding: 0px;
  margin-left: -5px;
  margin-top: 2px;
  margin-bottom: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.toolbar select,
.toolbar label {
  width: auto;
  vertical-align: middle;
  margin-right: 2px;
  margin-bottom: 0px;
  display: inline;
  font-size: 92%;
  margin-left: 0.3em;
  margin-right: 0.3em;
  padding: 0px;
  padding-top: 3px;
}
.toolbar .btn {
  padding: 2px 8px;
}
.toolbar .btn-group {
  margin-top: 0px;
  margin-left: 5px;
}
.toolbar-btn-label {
  margin-left: 6px;
}
#maintoolbar {
  margin-bottom: -3px;
  margin-top: -8px;
  border: 0px;
  min-height: 27px;
  margin-left: 0px;
  padding-top: 11px;
  padding-bottom: 3px;
}
#maintoolbar .navbar-text {
  float: none;
  vertical-align: middle;
  text-align: right;
  margin-left: 5px;
  margin-right: 0px;
  margin-top: 0px;
}
.select-xs {
  height: 24px;
}
[dir="rtl"] .btn-group > .btn,
.btn-group-vertical > .btn {
  float: right;
}
.pulse,
.dropdown-menu > li > a.pulse,
li.pulse > a.dropdown-toggle,
li.pulse.open > a.dropdown-toggle {
  background-color: #F37626;
  color: white;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
/** WARNING IF YOU ARE EDITTING THIS FILE, if this is a .css file, It has a lot
 * of chance of beeing generated from the ../less/[samename].less file, you can
 * try to get back the less file by reverting somme commit in history
 **/
/*
 * We'll try to get something pretty, so we
 * have some strange css to have the scroll bar on
 * the left with fix button on the top right of the tooltip
 */
@-moz-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-webkit-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-moz-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/*properties of tooltip after "expand"*/
.bigtooltip {
  overflow: auto;
  height: 200px;
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
}
/*properties of tooltip before "expand"*/
.smalltooltip {
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
  text-overflow: ellipsis;
  overflow: hidden;
  height: 80px;
}
.tooltipbuttons {
  position: absolute;
  padding-right: 15px;
  top: 0px;
  right: 0px;
}
.tooltiptext {
  /*avoid the button to overlap on some docstring*/
  padding-right: 30px;
}
.ipython_tooltip {
  max-width: 700px;
  /*fade-in animation when inserted*/
  -webkit-animation: fadeOut 400ms;
  -moz-animation: fadeOut 400ms;
  animation: fadeOut 400ms;
  -webkit-animation: fadeIn 400ms;
  -moz-animation: fadeIn 400ms;
  animation: fadeIn 400ms;
  vertical-align: middle;
  background-color: #f7f7f7;
  overflow: visible;
  border: #ababab 1px solid;
  outline: none;
  padding: 3px;
  margin: 0px;
  padding-left: 7px;
  font-family: monospace;
  min-height: 50px;
  -moz-box-shadow: 0px 6px 10px -1px #adadad;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  border-radius: 2px;
  position: absolute;
  z-index: 1000;
}
.ipython_tooltip a {
  float: right;
}
.ipython_tooltip .tooltiptext pre {
  border: 0;
  border-radius: 0;
  font-size: 100%;
  background-color: #f7f7f7;
}
.pretooltiparrow {
  left: 0px;
  margin: 0px;
  top: -16px;
  width: 40px;
  height: 16px;
  overflow: hidden;
  position: absolute;
}
.pretooltiparrow:before {
  background-color: #f7f7f7;
  border: 1px #ababab solid;
  z-index: 11;
  content: "";
  position: absolute;
  left: 15px;
  top: 10px;
  width: 25px;
  height: 25px;
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
}
ul.typeahead-list i {
  margin-left: -10px;
  width: 18px;
}
[dir="rtl"] ul.typeahead-list i {
  margin-left: 0;
  margin-right: -10px;
}
ul.typeahead-list {
  max-height: 80vh;
  overflow: auto;
}
ul.typeahead-list > li > a {
  /** Firefox bug **/
  /* see https://github.com/jupyter/notebook/issues/559 */
  white-space: normal;
}
ul.typeahead-list  > li > a.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .typeahead-list {
  text-align: right;
}
.cmd-palette .modal-body {
  padding: 7px;
}
.cmd-palette form {
  background: white;
}
.cmd-palette input {
  outline: none;
}
.no-shortcut {
  min-width: 20px;
  color: transparent;
}
[dir="rtl"] .no-shortcut.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .command-shortcut.pull-right {
  float: left !important;
  float: left;
}
.command-shortcut:before {
  content: "(command mode)";
  padding-right: 3px;
  color: #777777;
}
.edit-shortcut:before {
  content: "(edit)";
  padding-right: 3px;
  color: #777777;
}
[dir="rtl"] .edit-shortcut.pull-right {
  float: left !important;
  float: left;
}
#find-and-replace #replace-preview .match,
#find-and-replace #replace-preview .insert {
  background-color: #BBDEFB;
  border-color: #90CAF9;
  border-style: solid;
  border-width: 1px;
  border-radius: 0px;
}
[dir="ltr"] #find-and-replace .input-group-btn + .form-control {
  border-left: none;
}
[dir="rtl"] #find-and-replace .input-group-btn + .form-control {
  border-right: none;
}
#find-and-replace #replace-preview .replace .match {
  background-color: #FFCDD2;
  border-color: #EF9A9A;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .insert {
  background-color: #C8E6C9;
  border-color: #A5D6A7;
  border-radius: 0px;
}
#find-and-replace #replace-preview {
  max-height: 60vh;
  overflow: auto;
}
#find-and-replace #replace-preview pre {
  padding: 5px 10px;
}
.terminal-app {
  background: #EEE;
}
.terminal-app #header {
  background: #fff;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.terminal-app .terminal {
  width: 100%;
  float: left;
  font-family: monospace;
  color: white;
  background: black;
  padding: 0.4em;
  border-radius: 2px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
}
.terminal-app .terminal,
.terminal-app .terminal dummy-screen {
  line-height: 1em;
  font-size: 14px;
}
.terminal-app .terminal .xterm-rows {
  padding: 10px;
}
.terminal-app .terminal-cursor {
  color: black;
  background: white;
}
.terminal-app #terminado-container {
  margin-top: 20px;
}
/*# sourceMappingURL=style.min.css.map */
    </style>
<style type="text/css">
    .highlight .hll { background-color: #ffffcc }
.highlight  { background: #f8f8f8; }
.highlight .c { color: #408080; font-style: italic } /* Comment */
.highlight .err { border: 1px solid #FF0000 } /* Error */
.highlight .k { color: #008000; font-weight: bold } /* Keyword */
.highlight .o { color: #666666 } /* Operator */
.highlight .ch { color: #408080; font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: #408080; font-style: italic } /* Comment.Multiline */
.highlight .cp { color: #BC7A00 } /* Comment.Preproc */
.highlight .cpf { color: #408080; font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: #408080; font-style: italic } /* Comment.Single */
.highlight .cs { color: #408080; font-style: italic } /* Comment.Special */
.highlight .gd { color: #A00000 } /* Generic.Deleted */
.highlight .ge { font-style: italic } /* Generic.Emph */
.highlight .gr { color: #FF0000 } /* Generic.Error */
.highlight .gh { color: #000080; font-weight: bold } /* Generic.Heading */
.highlight .gi { color: #00A000 } /* Generic.Inserted */
.highlight .go { color: #888888 } /* Generic.Output */
.highlight .gp { color: #000080; font-weight: bold } /* Generic.Prompt */
.highlight .gs { font-weight: bold } /* Generic.Strong */
.highlight .gu { color: #800080; font-weight: bold } /* Generic.Subheading */
.highlight .gt { color: #0044DD } /* Generic.Traceback */
.highlight .kc { color: #008000; font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: #008000; font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: #008000; font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: #008000 } /* Keyword.Pseudo */
.highlight .kr { color: #008000; font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: #B00040 } /* Keyword.Type */
.highlight .m { color: #666666 } /* Literal.Number */
.highlight .s { color: #BA2121 } /* Literal.String */
.highlight .na { color: #7D9029 } /* Name.Attribute */
.highlight .nb { color: #008000 } /* Name.Builtin */
.highlight .nc { color: #0000FF; font-weight: bold } /* Name.Class */
.highlight .no { color: #880000 } /* Name.Constant */
.highlight .nd { color: #AA22FF } /* Name.Decorator */
.highlight .ni { color: #999999; font-weight: bold } /* Name.Entity */
.highlight .ne { color: #D2413A; font-weight: bold } /* Name.Exception */
.highlight .nf { color: #0000FF } /* Name.Function */
.highlight .nl { color: #A0A000 } /* Name.Label */
.highlight .nn { color: #0000FF; font-weight: bold } /* Name.Namespace */
.highlight .nt { color: #008000; font-weight: bold } /* Name.Tag */
.highlight .nv { color: #19177C } /* Name.Variable */
.highlight .ow { color: #AA22FF; font-weight: bold } /* Operator.Word */
.highlight .w { color: #bbbbbb } /* Text.Whitespace */
.highlight .mb { color: #666666 } /* Literal.Number.Bin */
.highlight .mf { color: #666666 } /* Literal.Number.Float */
.highlight .mh { color: #666666 } /* Literal.Number.Hex */
.highlight .mi { color: #666666 } /* Literal.Number.Integer */
.highlight .mo { color: #666666 } /* Literal.Number.Oct */
.highlight .sa { color: #BA2121 } /* Literal.String.Affix */
.highlight .sb { color: #BA2121 } /* Literal.String.Backtick */
.highlight .sc { color: #BA2121 } /* Literal.String.Char */
.highlight .dl { color: #BA2121 } /* Literal.String.Delimiter */
.highlight .sd { color: #BA2121; font-style: italic } /* Literal.String.Doc */
.highlight .s2 { color: #BA2121 } /* Literal.String.Double */
.highlight .se { color: #BB6622; font-weight: bold } /* Literal.String.Escape */
.highlight .sh { color: #BA2121 } /* Literal.String.Heredoc */
.highlight .si { color: #BB6688; font-weight: bold } /* Literal.String.Interpol */
.highlight .sx { color: #008000 } /* Literal.String.Other */
.highlight .sr { color: #BB6688 } /* Literal.String.Regex */
.highlight .s1 { color: #BA2121 } /* Literal.String.Single */
.highlight .ss { color: #19177C } /* Literal.String.Symbol */
.highlight .bp { color: #008000 } /* Name.Builtin.Pseudo */
.highlight .fm { color: #0000FF } /* Name.Function.Magic */
.highlight .vc { color: #19177C } /* Name.Variable.Class */
.highlight .vg { color: #19177C } /* Name.Variable.Global */
.highlight .vi { color: #19177C } /* Name.Variable.Instance */
.highlight .vm { color: #19177C } /* Name.Variable.Magic */
.highlight .il { color: #666666 } /* Literal.Number.Integer.Long */
    </style>


<style type="text/css">
/* Overrides of notebook CSS for static HTML export */
body {
  overflow: visible;
  padding: 8px;
}

div#notebook {
  overflow: visible;
  border-top: none;
}@media print {
  div.cell {
    display: block;
    page-break-inside: avoid;
  }
  div.output_wrapper {
    display: block;
    page-break-inside: avoid;
  }
  div.output {
    display: block;
    page-break-inside: avoid;
  }
}
</style>

<!-- Custom stylesheet, it must be in the same directory as the html file -->
<link rel="stylesheet" href="custom.css">

<!-- Loading mathjax macro -->
<!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-AMS_HTML"></script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
            processEscapes: true,
            processEnvironments: true
        },
        // Center justify equations in code and markdown cells. Elsewhere
        // we use CSS to left justify single line equations in code cells.
        displayAlign: 'center',
        "HTML-CSS": {
            styles: {'.MathJax_Display': {"margin": 0}},
            linebreaks: { automatic: true }
        }
    });
    </script>
    <!-- End of mathjax configuration --></head>
<body>
  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">

<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Machine-Learning-and-Breast-Cancer-Detection">Machine Learning and Breast Cancer Detection<a class="anchor-link" href="#Machine-Learning-and-Breast-Cancer-Detection">&#182;</a></h1><h3 id="Brandon-May">Brandon May<a class="anchor-link" href="#Brandon-May">&#182;</a></h3><p>Breast cancer continues to be a significant culprit of morbidity and mortality, even today with our current medical advances.  The data that this dataset consists of was actually published in a medical journal article and data was collected at the University of Wisconsin (Wolberg, M.D. et al.¸1995). While this source is somewhat dated, my main goal with this project is to demonstrate that machine learning algorithms could be used to assist in cancer detection as adjunct to physician expertise.</p>
<p><strong>Dataset Description:</strong></p>
<p>The data is from the University of California - Irvine Machine Learning Repository and can be found here:  <a href="https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29">https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29</a></p>
<p>This data was collected at the University of Wisconsin in 1995.  The file is in a csv format in which microscopic images of Fine Needle Aspirates (a type of biopsy) of suspicious breast tissue was digitized.  There are a total of 32 variables with 570 subjects.  They were examining suspicious masses in those without evidence of metastasis (distant spread of cancer to other parts of the body).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Loading Basic Packages</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>

<span class="c1">#Silencing Warnings</span>
<span class="kn">import</span> <span class="nn">warnings</span>
<span class="n">warnings</span><span class="o">.</span><span class="n">filterwarnings</span><span class="p">(</span><span class="s1">&#39;ignore&#39;</span><span class="p">)</span>

<span class="c1">#Importing Dataset and Viewing It</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;breast_cancer.csv&#39;</span><span class="p">)</span>
<span class="n">df</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[1]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>diagnosis</th>
      <th>radius_mean</th>
      <th>texture_mean</th>
      <th>perimeter_mean</th>
      <th>area_mean</th>
      <th>smoothness_mean</th>
      <th>compactness_mean</th>
      <th>concavity_mean</th>
      <th>concave points_mean</th>
      <th>...</th>
      <th>radius_worst</th>
      <th>texture_worst</th>
      <th>perimeter_worst</th>
      <th>area_worst</th>
      <th>smoothness_worst</th>
      <th>compactness_worst</th>
      <th>concavity_worst</th>
      <th>concave points_worst</th>
      <th>symmetry_worst</th>
      <th>fractal_dimension_worst</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>842302</td>
      <td>M</td>
      <td>17.99</td>
      <td>10.38</td>
      <td>122.80</td>
      <td>1001.0</td>
      <td>0.11840</td>
      <td>0.27760</td>
      <td>0.30010</td>
      <td>0.14710</td>
      <td>...</td>
      <td>25.380</td>
      <td>17.33</td>
      <td>184.60</td>
      <td>2019.0</td>
      <td>0.16220</td>
      <td>0.66560</td>
      <td>0.7119</td>
      <td>0.2654</td>
      <td>0.4601</td>
      <td>0.11890</td>
    </tr>
    <tr>
      <th>1</th>
      <td>842517</td>
      <td>M</td>
      <td>20.57</td>
      <td>17.77</td>
      <td>132.90</td>
      <td>1326.0</td>
      <td>0.08474</td>
      <td>0.07864</td>
      <td>0.08690</td>
      <td>0.07017</td>
      <td>...</td>
      <td>24.990</td>
      <td>23.41</td>
      <td>158.80</td>
      <td>1956.0</td>
      <td>0.12380</td>
      <td>0.18660</td>
      <td>0.2416</td>
      <td>0.1860</td>
      <td>0.2750</td>
      <td>0.08902</td>
    </tr>
    <tr>
      <th>2</th>
      <td>84300903</td>
      <td>M</td>
      <td>19.69</td>
      <td>21.25</td>
      <td>130.00</td>
      <td>1203.0</td>
      <td>0.10960</td>
      <td>0.15990</td>
      <td>0.19740</td>
      <td>0.12790</td>
      <td>...</td>
      <td>23.570</td>
      <td>25.53</td>
      <td>152.50</td>
      <td>1709.0</td>
      <td>0.14440</td>
      <td>0.42450</td>
      <td>0.4504</td>
      <td>0.2430</td>
      <td>0.3613</td>
      <td>0.08758</td>
    </tr>
    <tr>
      <th>3</th>
      <td>84348301</td>
      <td>M</td>
      <td>11.42</td>
      <td>20.38</td>
      <td>77.58</td>
      <td>386.1</td>
      <td>0.14250</td>
      <td>0.28390</td>
      <td>0.24140</td>
      <td>0.10520</td>
      <td>...</td>
      <td>14.910</td>
      <td>26.50</td>
      <td>98.87</td>
      <td>567.7</td>
      <td>0.20980</td>
      <td>0.86630</td>
      <td>0.6869</td>
      <td>0.2575</td>
      <td>0.6638</td>
      <td>0.17300</td>
    </tr>
    <tr>
      <th>4</th>
      <td>84358402</td>
      <td>M</td>
      <td>20.29</td>
      <td>14.34</td>
      <td>135.10</td>
      <td>1297.0</td>
      <td>0.10030</td>
      <td>0.13280</td>
      <td>0.19800</td>
      <td>0.10430</td>
      <td>...</td>
      <td>22.540</td>
      <td>16.67</td>
      <td>152.20</td>
      <td>1575.0</td>
      <td>0.13740</td>
      <td>0.20500</td>
      <td>0.4000</td>
      <td>0.1625</td>
      <td>0.2364</td>
      <td>0.07678</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>564</th>
      <td>926424</td>
      <td>M</td>
      <td>21.56</td>
      <td>22.39</td>
      <td>142.00</td>
      <td>1479.0</td>
      <td>0.11100</td>
      <td>0.11590</td>
      <td>0.24390</td>
      <td>0.13890</td>
      <td>...</td>
      <td>25.450</td>
      <td>26.40</td>
      <td>166.10</td>
      <td>2027.0</td>
      <td>0.14100</td>
      <td>0.21130</td>
      <td>0.4107</td>
      <td>0.2216</td>
      <td>0.2060</td>
      <td>0.07115</td>
    </tr>
    <tr>
      <th>565</th>
      <td>926682</td>
      <td>M</td>
      <td>20.13</td>
      <td>28.25</td>
      <td>131.20</td>
      <td>1261.0</td>
      <td>0.09780</td>
      <td>0.10340</td>
      <td>0.14400</td>
      <td>0.09791</td>
      <td>...</td>
      <td>23.690</td>
      <td>38.25</td>
      <td>155.00</td>
      <td>1731.0</td>
      <td>0.11660</td>
      <td>0.19220</td>
      <td>0.3215</td>
      <td>0.1628</td>
      <td>0.2572</td>
      <td>0.06637</td>
    </tr>
    <tr>
      <th>566</th>
      <td>926954</td>
      <td>M</td>
      <td>16.60</td>
      <td>28.08</td>
      <td>108.30</td>
      <td>858.1</td>
      <td>0.08455</td>
      <td>0.10230</td>
      <td>0.09251</td>
      <td>0.05302</td>
      <td>...</td>
      <td>18.980</td>
      <td>34.12</td>
      <td>126.70</td>
      <td>1124.0</td>
      <td>0.11390</td>
      <td>0.30940</td>
      <td>0.3403</td>
      <td>0.1418</td>
      <td>0.2218</td>
      <td>0.07820</td>
    </tr>
    <tr>
      <th>567</th>
      <td>927241</td>
      <td>M</td>
      <td>20.60</td>
      <td>29.33</td>
      <td>140.10</td>
      <td>1265.0</td>
      <td>0.11780</td>
      <td>0.27700</td>
      <td>0.35140</td>
      <td>0.15200</td>
      <td>...</td>
      <td>25.740</td>
      <td>39.42</td>
      <td>184.60</td>
      <td>1821.0</td>
      <td>0.16500</td>
      <td>0.86810</td>
      <td>0.9387</td>
      <td>0.2650</td>
      <td>0.4087</td>
      <td>0.12400</td>
    </tr>
    <tr>
      <th>568</th>
      <td>92751</td>
      <td>B</td>
      <td>7.76</td>
      <td>24.54</td>
      <td>47.92</td>
      <td>181.0</td>
      <td>0.05263</td>
      <td>0.04362</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>...</td>
      <td>9.456</td>
      <td>30.37</td>
      <td>59.16</td>
      <td>268.6</td>
      <td>0.08996</td>
      <td>0.06444</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.2871</td>
      <td>0.07039</td>
    </tr>
  </tbody>
</table>
<p>569 rows × 32 columns</p>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Checking for Missing Values</span>
<span class="n">df</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[2]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>diagnosis</th>
      <th>radius_mean</th>
      <th>texture_mean</th>
      <th>perimeter_mean</th>
      <th>area_mean</th>
      <th>smoothness_mean</th>
      <th>compactness_mean</th>
      <th>concavity_mean</th>
      <th>concave points_mean</th>
      <th>...</th>
      <th>radius_worst</th>
      <th>texture_worst</th>
      <th>perimeter_worst</th>
      <th>area_worst</th>
      <th>smoothness_worst</th>
      <th>compactness_worst</th>
      <th>concavity_worst</th>
      <th>concave points_worst</th>
      <th>symmetry_worst</th>
      <th>fractal_dimension_worst</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>564</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>565</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>566</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>567</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>568</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>569 rows × 32 columns</p>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Manually inspecting the dataframe reveals there to be no null values.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Checking Datatypes to Ensure Coded Correctly</span>
<span class="n">df</span><span class="o">.</span><span class="n">dtypes</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[3]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>id                           int64
diagnosis                   object
radius_mean                float64
texture_mean               float64
perimeter_mean             float64
area_mean                  float64
smoothness_mean            float64
compactness_mean           float64
concavity_mean             float64
concave points_mean        float64
symmetry_mean              float64
fractal_dimension_mean     float64
radius_se                  float64
texture_se                 float64
perimeter_se               float64
area_se                    float64
smoothness_se              float64
compactness_se             float64
concavity_se               float64
concave points_se          float64
symmetry_se                float64
fractal_dimension_se       float64
radius_worst               float64
texture_worst              float64
perimeter_worst            float64
area_worst                 float64
smoothness_worst           float64
compactness_worst          float64
concavity_worst            float64
concave points_worst       float64
symmetry_worst             float64
fractal_dimension_worst    float64
dtype: object</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>The target variable is categorical and is coded as M for malignant and B for benign.  There are no missing data in the CSV file.  There are case identifiers but other demographic information such as age, co-morbidities, and family history are not available.</strong></p>
<p><strong>The variables examined include measurements of digitized images on both cell size and shape.  These were already identified as either benign or malignant.  The data aims to determine if these specific characteristics can be used to predict whether a tumor was malignant or benign.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Description-of-the-Variables">Description of the Variables<a class="anchor-link" href="#Description-of-the-Variables">&#182;</a></h3><p><strong>Id:</strong> Number signifying unique samples (Integer)</p>
<p><strong>Diagnosis:</strong> M for Malignant, B for Benign (Categorical) – the Target</p>
<p><strong>Radius_mean:</strong> Mean of distance from center to points on the perimeter of tumor cell, cell size measure (Float)</p>
<p><strong>Texture_mean:</strong> Mean of grey-scale values of image (Float)</p>
<p><strong>Perimeter_mean:</strong> Expression of both cell size and shape (Float)</p>
<p><strong>Area_mean:</strong> Mean area of cell size (Float)</p>
<p><strong>Smoothness:</strong> Mean of cell smoothness and shape (Float)</p>
<p><strong>Compactness:</strong> Mean of cell compactness and shape (Float)</p>
<p><strong>Concavity_mean:</strong>  Mean of cell concavity of image (Float)</p>
<p><strong>Concave points_mean:</strong> Mean of concave points (Float)</p>
<p><strong>Symmetry_mean:</strong> Mean of cell symmetry (Float)</p>
<p><strong>Fractal_dimension_mean:</strong> Mean of fractal dimension, measure of cell shape (Float)</p>
<p><strong>Radius_se:</strong> Standard error of distance from center to points on the perimeter of tumor cell, cell size measure (Float)</p>
<p><strong>Texture_se:</strong> Standard error of grey-scale values of image (Float)</p>
<p><strong>Perimeter_se:</strong> Standard error of both cell size and shape (Float)</p>
<p><strong>Area_se:</strong> Standard error of cell size area (Float)</p>
<p><strong>Smoothness_se:</strong> Standard error of cell smoothness (Float)</p>
<p><strong>Compactness_se:</strong> Standard error of cell compactness (Float)</p>
<p><strong>Concavity_se:</strong>  Standard error of cell concavity of image (Float)</p>
<p><strong>Concave points_se:</strong> Standard error of concave points (Float)</p>
<p><strong>Symmetry_se:</strong> Standard error of cell symmetry (Float)</p>
<p><strong>Fractal_dimension_se:</strong> Standard error of fractal dimension (Float)</p>
<p><strong>Radius_worst:</strong> Worst measurement of distance from center to points on the perimeter of tumor cell, cell size measure (Float)</p>
<p><strong>Texture_worst:</strong> Worst measurement of grey-scale values of image (Float)</p>
<p><strong>Perimeter_worst:</strong> Worst measurement of both cell size and shape (Float)</p>
<p><strong>Area_worst:</strong> Worst measurement of cell size area (Float)</p>
<p><strong>Smoothness_worst:</strong> Worst measurement of cell smoothness (Float)</p>
<p><strong>Compactness_worst:</strong> Worst measurement of cell compactness (Float)</p>
<p><strong>Concavity_worst:</strong>  Worst measurement of cell concavity of image (Float)</p>
<p><strong>Concave points_worst:</strong> Worst measurement of concave points (Float)</p>
<p><strong>Symmetry_worst:</strong> Worst measurement of cell symmetry (Float)</p>
<p><strong>Fractal_dimension_worst:</strong> Worst measurement of fractal dimension (Float)</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Dropping the ID column</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="n">columns</span> <span class="o">=</span> <span class="s2">&quot;id&quot;</span><span class="p">)</span>

<span class="c1">#Renaming Columns with Spaces in the Names</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">rename</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;concave points_mean&#39;</span><span class="p">:</span> <span class="s1">&#39;concavepoints_mean&#39;</span><span class="p">,</span> <span class="s1">&#39;concave points_se&#39;</span><span class="p">:</span> <span class="s1">&#39;concavepoints_se&#39;</span><span class="p">,</span> <span class="s1">&#39;concave points_worst&#39;</span><span class="p">:</span> <span class="s1">&#39;concavepoints_worst&#39;</span><span class="p">})</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Describing Dataset</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Dataset Descriptive Statistics for Numerical Variables&#39;</span><span class="p">)</span>
<span class="n">df</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Dataset Descriptive Statistics for Numerical Variables
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[5]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>radius_mean</th>
      <th>texture_mean</th>
      <th>perimeter_mean</th>
      <th>area_mean</th>
      <th>smoothness_mean</th>
      <th>compactness_mean</th>
      <th>concavity_mean</th>
      <th>concavepoints_mean</th>
      <th>symmetry_mean</th>
      <th>fractal_dimension_mean</th>
      <th>...</th>
      <th>radius_worst</th>
      <th>texture_worst</th>
      <th>perimeter_worst</th>
      <th>area_worst</th>
      <th>smoothness_worst</th>
      <th>compactness_worst</th>
      <th>concavity_worst</th>
      <th>concavepoints_worst</th>
      <th>symmetry_worst</th>
      <th>fractal_dimension_worst</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>...</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
      <td>569.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>14.127292</td>
      <td>19.289649</td>
      <td>91.969033</td>
      <td>654.889104</td>
      <td>0.096360</td>
      <td>0.104341</td>
      <td>0.088799</td>
      <td>0.048919</td>
      <td>0.181162</td>
      <td>0.062798</td>
      <td>...</td>
      <td>16.269190</td>
      <td>25.677223</td>
      <td>107.261213</td>
      <td>880.583128</td>
      <td>0.132369</td>
      <td>0.254265</td>
      <td>0.272188</td>
      <td>0.114606</td>
      <td>0.290076</td>
      <td>0.083946</td>
    </tr>
    <tr>
      <th>std</th>
      <td>3.524049</td>
      <td>4.301036</td>
      <td>24.298981</td>
      <td>351.914129</td>
      <td>0.014064</td>
      <td>0.052813</td>
      <td>0.079720</td>
      <td>0.038803</td>
      <td>0.027414</td>
      <td>0.007060</td>
      <td>...</td>
      <td>4.833242</td>
      <td>6.146258</td>
      <td>33.602542</td>
      <td>569.356993</td>
      <td>0.022832</td>
      <td>0.157336</td>
      <td>0.208624</td>
      <td>0.065732</td>
      <td>0.061867</td>
      <td>0.018061</td>
    </tr>
    <tr>
      <th>min</th>
      <td>6.981000</td>
      <td>9.710000</td>
      <td>43.790000</td>
      <td>143.500000</td>
      <td>0.052630</td>
      <td>0.019380</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.106000</td>
      <td>0.049960</td>
      <td>...</td>
      <td>7.930000</td>
      <td>12.020000</td>
      <td>50.410000</td>
      <td>185.200000</td>
      <td>0.071170</td>
      <td>0.027290</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.156500</td>
      <td>0.055040</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>11.700000</td>
      <td>16.170000</td>
      <td>75.170000</td>
      <td>420.300000</td>
      <td>0.086370</td>
      <td>0.064920</td>
      <td>0.029560</td>
      <td>0.020310</td>
      <td>0.161900</td>
      <td>0.057700</td>
      <td>...</td>
      <td>13.010000</td>
      <td>21.080000</td>
      <td>84.110000</td>
      <td>515.300000</td>
      <td>0.116600</td>
      <td>0.147200</td>
      <td>0.114500</td>
      <td>0.064930</td>
      <td>0.250400</td>
      <td>0.071460</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>13.370000</td>
      <td>18.840000</td>
      <td>86.240000</td>
      <td>551.100000</td>
      <td>0.095870</td>
      <td>0.092630</td>
      <td>0.061540</td>
      <td>0.033500</td>
      <td>0.179200</td>
      <td>0.061540</td>
      <td>...</td>
      <td>14.970000</td>
      <td>25.410000</td>
      <td>97.660000</td>
      <td>686.500000</td>
      <td>0.131300</td>
      <td>0.211900</td>
      <td>0.226700</td>
      <td>0.099930</td>
      <td>0.282200</td>
      <td>0.080040</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>15.780000</td>
      <td>21.800000</td>
      <td>104.100000</td>
      <td>782.700000</td>
      <td>0.105300</td>
      <td>0.130400</td>
      <td>0.130700</td>
      <td>0.074000</td>
      <td>0.195700</td>
      <td>0.066120</td>
      <td>...</td>
      <td>18.790000</td>
      <td>29.720000</td>
      <td>125.400000</td>
      <td>1084.000000</td>
      <td>0.146000</td>
      <td>0.339100</td>
      <td>0.382900</td>
      <td>0.161400</td>
      <td>0.317900</td>
      <td>0.092080</td>
    </tr>
    <tr>
      <th>max</th>
      <td>28.110000</td>
      <td>39.280000</td>
      <td>188.500000</td>
      <td>2501.000000</td>
      <td>0.163400</td>
      <td>0.345400</td>
      <td>0.426800</td>
      <td>0.201200</td>
      <td>0.304000</td>
      <td>0.097440</td>
      <td>...</td>
      <td>36.040000</td>
      <td>49.540000</td>
      <td>251.200000</td>
      <td>4254.000000</td>
      <td>0.222600</td>
      <td>1.058000</td>
      <td>1.252000</td>
      <td>0.291000</td>
      <td>0.663800</td>
      <td>0.207500</td>
    </tr>
  </tbody>
</table>
<p>8 rows × 30 columns</p>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Dataset Description for Categorical Variable</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Dataset Descriptive Statistics for Categorical Variable&#39;</span><span class="p">)</span>
<span class="n">df</span><span class="o">.</span><span class="n">describe</span><span class="p">(</span><span class="n">include</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;O&#39;</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Dataset Descriptive Statistics for Categorical Variable
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[6]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>diagnosis</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>569</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>2</td>
    </tr>
    <tr>
      <th>top</th>
      <td>B</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>357</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[7]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Performing Correlation Matrix to Look For High Levels of Correlation (&gt;0.95)</span>
<span class="n">corr_matrix</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">corr</span><span class="p">()</span><span class="o">.</span><span class="n">abs</span><span class="p">()</span>
<span class="n">corr_matrix</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[7]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>radius_mean</th>
      <th>texture_mean</th>
      <th>perimeter_mean</th>
      <th>area_mean</th>
      <th>smoothness_mean</th>
      <th>compactness_mean</th>
      <th>concavity_mean</th>
      <th>concavepoints_mean</th>
      <th>symmetry_mean</th>
      <th>fractal_dimension_mean</th>
      <th>...</th>
      <th>radius_worst</th>
      <th>texture_worst</th>
      <th>perimeter_worst</th>
      <th>area_worst</th>
      <th>smoothness_worst</th>
      <th>compactness_worst</th>
      <th>concavity_worst</th>
      <th>concavepoints_worst</th>
      <th>symmetry_worst</th>
      <th>fractal_dimension_worst</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>radius_mean</th>
      <td>1.000000</td>
      <td>0.323782</td>
      <td>0.997855</td>
      <td>0.987357</td>
      <td>0.170581</td>
      <td>0.506124</td>
      <td>0.676764</td>
      <td>0.822529</td>
      <td>0.147741</td>
      <td>0.311631</td>
      <td>...</td>
      <td>0.969539</td>
      <td>0.297008</td>
      <td>0.965137</td>
      <td>0.941082</td>
      <td>0.119616</td>
      <td>0.413463</td>
      <td>0.526911</td>
      <td>0.744214</td>
      <td>0.163953</td>
      <td>0.007066</td>
    </tr>
    <tr>
      <th>texture_mean</th>
      <td>0.323782</td>
      <td>1.000000</td>
      <td>0.329533</td>
      <td>0.321086</td>
      <td>0.023389</td>
      <td>0.236702</td>
      <td>0.302418</td>
      <td>0.293464</td>
      <td>0.071401</td>
      <td>0.076437</td>
      <td>...</td>
      <td>0.352573</td>
      <td>0.912045</td>
      <td>0.358040</td>
      <td>0.343546</td>
      <td>0.077503</td>
      <td>0.277830</td>
      <td>0.301025</td>
      <td>0.295316</td>
      <td>0.105008</td>
      <td>0.119205</td>
    </tr>
    <tr>
      <th>perimeter_mean</th>
      <td>0.997855</td>
      <td>0.329533</td>
      <td>1.000000</td>
      <td>0.986507</td>
      <td>0.207278</td>
      <td>0.556936</td>
      <td>0.716136</td>
      <td>0.850977</td>
      <td>0.183027</td>
      <td>0.261477</td>
      <td>...</td>
      <td>0.969476</td>
      <td>0.303038</td>
      <td>0.970387</td>
      <td>0.941550</td>
      <td>0.150549</td>
      <td>0.455774</td>
      <td>0.563879</td>
      <td>0.771241</td>
      <td>0.189115</td>
      <td>0.051019</td>
    </tr>
    <tr>
      <th>area_mean</th>
      <td>0.987357</td>
      <td>0.321086</td>
      <td>0.986507</td>
      <td>1.000000</td>
      <td>0.177028</td>
      <td>0.498502</td>
      <td>0.685983</td>
      <td>0.823269</td>
      <td>0.151293</td>
      <td>0.283110</td>
      <td>...</td>
      <td>0.962746</td>
      <td>0.287489</td>
      <td>0.959120</td>
      <td>0.959213</td>
      <td>0.123523</td>
      <td>0.390410</td>
      <td>0.512606</td>
      <td>0.722017</td>
      <td>0.143570</td>
      <td>0.003738</td>
    </tr>
    <tr>
      <th>smoothness_mean</th>
      <td>0.170581</td>
      <td>0.023389</td>
      <td>0.207278</td>
      <td>0.177028</td>
      <td>1.000000</td>
      <td>0.659123</td>
      <td>0.521984</td>
      <td>0.553695</td>
      <td>0.557775</td>
      <td>0.584792</td>
      <td>...</td>
      <td>0.213120</td>
      <td>0.036072</td>
      <td>0.238853</td>
      <td>0.206718</td>
      <td>0.805324</td>
      <td>0.472468</td>
      <td>0.434926</td>
      <td>0.503053</td>
      <td>0.394309</td>
      <td>0.499316</td>
    </tr>
    <tr>
      <th>compactness_mean</th>
      <td>0.506124</td>
      <td>0.236702</td>
      <td>0.556936</td>
      <td>0.498502</td>
      <td>0.659123</td>
      <td>1.000000</td>
      <td>0.883121</td>
      <td>0.831135</td>
      <td>0.602641</td>
      <td>0.565369</td>
      <td>...</td>
      <td>0.535315</td>
      <td>0.248133</td>
      <td>0.590210</td>
      <td>0.509604</td>
      <td>0.565541</td>
      <td>0.865809</td>
      <td>0.816275</td>
      <td>0.815573</td>
      <td>0.510223</td>
      <td>0.687382</td>
    </tr>
    <tr>
      <th>concavity_mean</th>
      <td>0.676764</td>
      <td>0.302418</td>
      <td>0.716136</td>
      <td>0.685983</td>
      <td>0.521984</td>
      <td>0.883121</td>
      <td>1.000000</td>
      <td>0.921391</td>
      <td>0.500667</td>
      <td>0.336783</td>
      <td>...</td>
      <td>0.688236</td>
      <td>0.299879</td>
      <td>0.729565</td>
      <td>0.675987</td>
      <td>0.448822</td>
      <td>0.754968</td>
      <td>0.884103</td>
      <td>0.861323</td>
      <td>0.409464</td>
      <td>0.514930</td>
    </tr>
    <tr>
      <th>concavepoints_mean</th>
      <td>0.822529</td>
      <td>0.293464</td>
      <td>0.850977</td>
      <td>0.823269</td>
      <td>0.553695</td>
      <td>0.831135</td>
      <td>0.921391</td>
      <td>1.000000</td>
      <td>0.462497</td>
      <td>0.166917</td>
      <td>...</td>
      <td>0.830318</td>
      <td>0.292752</td>
      <td>0.855923</td>
      <td>0.809630</td>
      <td>0.452753</td>
      <td>0.667454</td>
      <td>0.752399</td>
      <td>0.910155</td>
      <td>0.375744</td>
      <td>0.368661</td>
    </tr>
    <tr>
      <th>symmetry_mean</th>
      <td>0.147741</td>
      <td>0.071401</td>
      <td>0.183027</td>
      <td>0.151293</td>
      <td>0.557775</td>
      <td>0.602641</td>
      <td>0.500667</td>
      <td>0.462497</td>
      <td>1.000000</td>
      <td>0.479921</td>
      <td>...</td>
      <td>0.185728</td>
      <td>0.090651</td>
      <td>0.219169</td>
      <td>0.177193</td>
      <td>0.426675</td>
      <td>0.473200</td>
      <td>0.433721</td>
      <td>0.430297</td>
      <td>0.699826</td>
      <td>0.438413</td>
    </tr>
    <tr>
      <th>fractal_dimension_mean</th>
      <td>0.311631</td>
      <td>0.076437</td>
      <td>0.261477</td>
      <td>0.283110</td>
      <td>0.584792</td>
      <td>0.565369</td>
      <td>0.336783</td>
      <td>0.166917</td>
      <td>0.479921</td>
      <td>1.000000</td>
      <td>...</td>
      <td>0.253691</td>
      <td>0.051269</td>
      <td>0.205151</td>
      <td>0.231854</td>
      <td>0.504942</td>
      <td>0.458798</td>
      <td>0.346234</td>
      <td>0.175325</td>
      <td>0.334019</td>
      <td>0.767297</td>
    </tr>
    <tr>
      <th>radius_se</th>
      <td>0.679090</td>
      <td>0.275869</td>
      <td>0.691765</td>
      <td>0.732562</td>
      <td>0.301467</td>
      <td>0.497473</td>
      <td>0.631925</td>
      <td>0.698050</td>
      <td>0.303379</td>
      <td>0.000111</td>
      <td>...</td>
      <td>0.715065</td>
      <td>0.194799</td>
      <td>0.719684</td>
      <td>0.751548</td>
      <td>0.141919</td>
      <td>0.287103</td>
      <td>0.380585</td>
      <td>0.531062</td>
      <td>0.094543</td>
      <td>0.049559</td>
    </tr>
    <tr>
      <th>texture_se</th>
      <td>0.097317</td>
      <td>0.386358</td>
      <td>0.086761</td>
      <td>0.066280</td>
      <td>0.068406</td>
      <td>0.046205</td>
      <td>0.076218</td>
      <td>0.021480</td>
      <td>0.128053</td>
      <td>0.164174</td>
      <td>...</td>
      <td>0.111690</td>
      <td>0.409003</td>
      <td>0.102242</td>
      <td>0.083195</td>
      <td>0.073658</td>
      <td>0.092439</td>
      <td>0.068956</td>
      <td>0.119638</td>
      <td>0.128215</td>
      <td>0.045655</td>
    </tr>
    <tr>
      <th>perimeter_se</th>
      <td>0.674172</td>
      <td>0.281673</td>
      <td>0.693135</td>
      <td>0.726628</td>
      <td>0.296092</td>
      <td>0.548905</td>
      <td>0.660391</td>
      <td>0.710650</td>
      <td>0.313893</td>
      <td>0.039830</td>
      <td>...</td>
      <td>0.697201</td>
      <td>0.200371</td>
      <td>0.721031</td>
      <td>0.730713</td>
      <td>0.130054</td>
      <td>0.341919</td>
      <td>0.418899</td>
      <td>0.554897</td>
      <td>0.109930</td>
      <td>0.085433</td>
    </tr>
    <tr>
      <th>area_se</th>
      <td>0.735864</td>
      <td>0.259845</td>
      <td>0.744983</td>
      <td>0.800086</td>
      <td>0.246552</td>
      <td>0.455653</td>
      <td>0.617427</td>
      <td>0.690299</td>
      <td>0.223970</td>
      <td>0.090170</td>
      <td>...</td>
      <td>0.757373</td>
      <td>0.196497</td>
      <td>0.761213</td>
      <td>0.811408</td>
      <td>0.125389</td>
      <td>0.283257</td>
      <td>0.385100</td>
      <td>0.538166</td>
      <td>0.074126</td>
      <td>0.017539</td>
    </tr>
    <tr>
      <th>smoothness_se</th>
      <td>0.222600</td>
      <td>0.006614</td>
      <td>0.202694</td>
      <td>0.166777</td>
      <td>0.332375</td>
      <td>0.135299</td>
      <td>0.098564</td>
      <td>0.027653</td>
      <td>0.187321</td>
      <td>0.401964</td>
      <td>...</td>
      <td>0.230691</td>
      <td>0.074743</td>
      <td>0.217304</td>
      <td>0.182195</td>
      <td>0.314457</td>
      <td>0.055558</td>
      <td>0.058298</td>
      <td>0.102007</td>
      <td>0.107342</td>
      <td>0.101480</td>
    </tr>
    <tr>
      <th>compactness_se</th>
      <td>0.206000</td>
      <td>0.191975</td>
      <td>0.250744</td>
      <td>0.212583</td>
      <td>0.318943</td>
      <td>0.738722</td>
      <td>0.670279</td>
      <td>0.490424</td>
      <td>0.421659</td>
      <td>0.559837</td>
      <td>...</td>
      <td>0.204607</td>
      <td>0.143003</td>
      <td>0.260516</td>
      <td>0.199371</td>
      <td>0.227394</td>
      <td>0.678780</td>
      <td>0.639147</td>
      <td>0.483208</td>
      <td>0.277878</td>
      <td>0.590973</td>
    </tr>
    <tr>
      <th>concavity_se</th>
      <td>0.194204</td>
      <td>0.143293</td>
      <td>0.228082</td>
      <td>0.207660</td>
      <td>0.248396</td>
      <td>0.570517</td>
      <td>0.691270</td>
      <td>0.439167</td>
      <td>0.342627</td>
      <td>0.446630</td>
      <td>...</td>
      <td>0.186904</td>
      <td>0.100241</td>
      <td>0.226680</td>
      <td>0.188353</td>
      <td>0.168481</td>
      <td>0.484858</td>
      <td>0.662564</td>
      <td>0.440472</td>
      <td>0.197788</td>
      <td>0.439329</td>
    </tr>
    <tr>
      <th>concavepoints_se</th>
      <td>0.376169</td>
      <td>0.163851</td>
      <td>0.407217</td>
      <td>0.372320</td>
      <td>0.380676</td>
      <td>0.642262</td>
      <td>0.683260</td>
      <td>0.615634</td>
      <td>0.393298</td>
      <td>0.341198</td>
      <td>...</td>
      <td>0.358127</td>
      <td>0.086741</td>
      <td>0.394999</td>
      <td>0.342271</td>
      <td>0.215351</td>
      <td>0.452888</td>
      <td>0.549592</td>
      <td>0.602450</td>
      <td>0.143116</td>
      <td>0.310655</td>
    </tr>
    <tr>
      <th>symmetry_se</th>
      <td>0.104321</td>
      <td>0.009127</td>
      <td>0.081629</td>
      <td>0.072497</td>
      <td>0.200774</td>
      <td>0.229977</td>
      <td>0.178009</td>
      <td>0.095351</td>
      <td>0.449137</td>
      <td>0.345007</td>
      <td>...</td>
      <td>0.128121</td>
      <td>0.077473</td>
      <td>0.103753</td>
      <td>0.110343</td>
      <td>0.012662</td>
      <td>0.060255</td>
      <td>0.037119</td>
      <td>0.030413</td>
      <td>0.389402</td>
      <td>0.078079</td>
    </tr>
    <tr>
      <th>fractal_dimension_se</th>
      <td>0.042641</td>
      <td>0.054458</td>
      <td>0.005523</td>
      <td>0.019887</td>
      <td>0.283607</td>
      <td>0.507318</td>
      <td>0.449301</td>
      <td>0.257584</td>
      <td>0.331786</td>
      <td>0.688132</td>
      <td>...</td>
      <td>0.037488</td>
      <td>0.003195</td>
      <td>0.001000</td>
      <td>0.022736</td>
      <td>0.170568</td>
      <td>0.390159</td>
      <td>0.379975</td>
      <td>0.215204</td>
      <td>0.111094</td>
      <td>0.591328</td>
    </tr>
    <tr>
      <th>radius_worst</th>
      <td>0.969539</td>
      <td>0.352573</td>
      <td>0.969476</td>
      <td>0.962746</td>
      <td>0.213120</td>
      <td>0.535315</td>
      <td>0.688236</td>
      <td>0.830318</td>
      <td>0.185728</td>
      <td>0.253691</td>
      <td>...</td>
      <td>1.000000</td>
      <td>0.359921</td>
      <td>0.993708</td>
      <td>0.984015</td>
      <td>0.216574</td>
      <td>0.475820</td>
      <td>0.573975</td>
      <td>0.787424</td>
      <td>0.243529</td>
      <td>0.093492</td>
    </tr>
    <tr>
      <th>texture_worst</th>
      <td>0.297008</td>
      <td>0.912045</td>
      <td>0.303038</td>
      <td>0.287489</td>
      <td>0.036072</td>
      <td>0.248133</td>
      <td>0.299879</td>
      <td>0.292752</td>
      <td>0.090651</td>
      <td>0.051269</td>
      <td>...</td>
      <td>0.359921</td>
      <td>1.000000</td>
      <td>0.365098</td>
      <td>0.345842</td>
      <td>0.225429</td>
      <td>0.360832</td>
      <td>0.368366</td>
      <td>0.359755</td>
      <td>0.233027</td>
      <td>0.219122</td>
    </tr>
    <tr>
      <th>perimeter_worst</th>
      <td>0.965137</td>
      <td>0.358040</td>
      <td>0.970387</td>
      <td>0.959120</td>
      <td>0.238853</td>
      <td>0.590210</td>
      <td>0.729565</td>
      <td>0.855923</td>
      <td>0.219169</td>
      <td>0.205151</td>
      <td>...</td>
      <td>0.993708</td>
      <td>0.365098</td>
      <td>1.000000</td>
      <td>0.977578</td>
      <td>0.236775</td>
      <td>0.529408</td>
      <td>0.618344</td>
      <td>0.816322</td>
      <td>0.269493</td>
      <td>0.138957</td>
    </tr>
    <tr>
      <th>area_worst</th>
      <td>0.941082</td>
      <td>0.343546</td>
      <td>0.941550</td>
      <td>0.959213</td>
      <td>0.206718</td>
      <td>0.509604</td>
      <td>0.675987</td>
      <td>0.809630</td>
      <td>0.177193</td>
      <td>0.231854</td>
      <td>...</td>
      <td>0.984015</td>
      <td>0.345842</td>
      <td>0.977578</td>
      <td>1.000000</td>
      <td>0.209145</td>
      <td>0.438296</td>
      <td>0.543331</td>
      <td>0.747419</td>
      <td>0.209146</td>
      <td>0.079647</td>
    </tr>
    <tr>
      <th>smoothness_worst</th>
      <td>0.119616</td>
      <td>0.077503</td>
      <td>0.150549</td>
      <td>0.123523</td>
      <td>0.805324</td>
      <td>0.565541</td>
      <td>0.448822</td>
      <td>0.452753</td>
      <td>0.426675</td>
      <td>0.504942</td>
      <td>...</td>
      <td>0.216574</td>
      <td>0.225429</td>
      <td>0.236775</td>
      <td>0.209145</td>
      <td>1.000000</td>
      <td>0.568187</td>
      <td>0.518523</td>
      <td>0.547691</td>
      <td>0.493838</td>
      <td>0.617624</td>
    </tr>
    <tr>
      <th>compactness_worst</th>
      <td>0.413463</td>
      <td>0.277830</td>
      <td>0.455774</td>
      <td>0.390410</td>
      <td>0.472468</td>
      <td>0.865809</td>
      <td>0.754968</td>
      <td>0.667454</td>
      <td>0.473200</td>
      <td>0.458798</td>
      <td>...</td>
      <td>0.475820</td>
      <td>0.360832</td>
      <td>0.529408</td>
      <td>0.438296</td>
      <td>0.568187</td>
      <td>1.000000</td>
      <td>0.892261</td>
      <td>0.801080</td>
      <td>0.614441</td>
      <td>0.810455</td>
    </tr>
    <tr>
      <th>concavity_worst</th>
      <td>0.526911</td>
      <td>0.301025</td>
      <td>0.563879</td>
      <td>0.512606</td>
      <td>0.434926</td>
      <td>0.816275</td>
      <td>0.884103</td>
      <td>0.752399</td>
      <td>0.433721</td>
      <td>0.346234</td>
      <td>...</td>
      <td>0.573975</td>
      <td>0.368366</td>
      <td>0.618344</td>
      <td>0.543331</td>
      <td>0.518523</td>
      <td>0.892261</td>
      <td>1.000000</td>
      <td>0.855434</td>
      <td>0.532520</td>
      <td>0.686511</td>
    </tr>
    <tr>
      <th>concavepoints_worst</th>
      <td>0.744214</td>
      <td>0.295316</td>
      <td>0.771241</td>
      <td>0.722017</td>
      <td>0.503053</td>
      <td>0.815573</td>
      <td>0.861323</td>
      <td>0.910155</td>
      <td>0.430297</td>
      <td>0.175325</td>
      <td>...</td>
      <td>0.787424</td>
      <td>0.359755</td>
      <td>0.816322</td>
      <td>0.747419</td>
      <td>0.547691</td>
      <td>0.801080</td>
      <td>0.855434</td>
      <td>1.000000</td>
      <td>0.502528</td>
      <td>0.511114</td>
    </tr>
    <tr>
      <th>symmetry_worst</th>
      <td>0.163953</td>
      <td>0.105008</td>
      <td>0.189115</td>
      <td>0.143570</td>
      <td>0.394309</td>
      <td>0.510223</td>
      <td>0.409464</td>
      <td>0.375744</td>
      <td>0.699826</td>
      <td>0.334019</td>
      <td>...</td>
      <td>0.243529</td>
      <td>0.233027</td>
      <td>0.269493</td>
      <td>0.209146</td>
      <td>0.493838</td>
      <td>0.614441</td>
      <td>0.532520</td>
      <td>0.502528</td>
      <td>1.000000</td>
      <td>0.537848</td>
    </tr>
    <tr>
      <th>fractal_dimension_worst</th>
      <td>0.007066</td>
      <td>0.119205</td>
      <td>0.051019</td>
      <td>0.003738</td>
      <td>0.499316</td>
      <td>0.687382</td>
      <td>0.514930</td>
      <td>0.368661</td>
      <td>0.438413</td>
      <td>0.767297</td>
      <td>...</td>
      <td>0.093492</td>
      <td>0.219122</td>
      <td>0.138957</td>
      <td>0.079647</td>
      <td>0.617624</td>
      <td>0.810455</td>
      <td>0.686511</td>
      <td>0.511114</td>
      <td>0.537848</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
<p>30 rows × 30 columns</p>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Selecting Upper Triangle of Correlation Matrix</span>
<span class="n">upper</span> <span class="o">=</span> <span class="n">corr_matrix</span><span class="o">.</span><span class="n">where</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">triu</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">ones</span><span class="p">(</span><span class="n">corr_matrix</span><span class="o">.</span><span class="n">shape</span><span class="p">),</span><span class="n">k</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">bool</span><span class="p">))</span>

<span class="c1">#Find Index of Feature Columns with Correlations &gt;0.90</span>
<span class="n">to_drop</span> <span class="o">=</span> <span class="p">[</span><span class="n">column</span> <span class="k">for</span> <span class="n">column</span> <span class="ow">in</span> <span class="n">upper</span><span class="o">.</span><span class="n">columns</span> <span class="k">if</span> <span class="nb">any</span> <span class="p">(</span><span class="n">upper</span><span class="p">[</span><span class="n">column</span><span class="p">]</span> <span class="o">&gt;</span><span class="mf">0.95</span><span class="p">)]</span>
<span class="n">to_drop</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[8]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>[&#39;perimeter_mean&#39;,
 &#39;area_mean&#39;,
 &#39;perimeter_se&#39;,
 &#39;area_se&#39;,
 &#39;radius_worst&#39;,
 &#39;perimeter_worst&#39;,
 &#39;area_worst&#39;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[9]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Visualizing Using Correlation Plot</span>
<span class="n">plt</span><span class="o">.</span><span class="n">rcParams</span><span class="p">[</span><span class="s1">&#39;figure.figsize&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="p">(</span><span class="mi">20</span><span class="p">,</span><span class="mi">20</span><span class="p">)</span>

<span class="c1">#Importing Seaborn</span>
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>

<span class="n">sns</span><span class="o">.</span><span class="n">heatmap</span><span class="p">(</span><span class="n">corr_matrix</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Given the high rates of correlation of the above variables, we will drop them from the dataframe.  With a correlation &gt;0.95, these are likely redundant and may introduce instability in our final algorithms.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Dropping Highly Correlated Variables</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;perimeter_mean&#39;</span><span class="p">,</span> <span class="s1">&#39;area_mean&#39;</span><span class="p">,</span> <span class="s1">&#39;perimeter_se&#39;</span><span class="p">,</span> <span class="s1">&#39;area_se&#39;</span><span class="p">,</span> <span class="s1">&#39;radius_worst&#39;</span><span class="p">,</span> <span class="s1">&#39;perimeter_worst&#39;</span><span class="p">,</span> <span class="s1">&#39;area_worst&#39;</span><span class="p">])</span>
<span class="n">df</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[10]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>diagnosis</th>
      <th>radius_mean</th>
      <th>texture_mean</th>
      <th>smoothness_mean</th>
      <th>compactness_mean</th>
      <th>concavity_mean</th>
      <th>concavepoints_mean</th>
      <th>symmetry_mean</th>
      <th>fractal_dimension_mean</th>
      <th>radius_se</th>
      <th>...</th>
      <th>concavepoints_se</th>
      <th>symmetry_se</th>
      <th>fractal_dimension_se</th>
      <th>texture_worst</th>
      <th>smoothness_worst</th>
      <th>compactness_worst</th>
      <th>concavity_worst</th>
      <th>concavepoints_worst</th>
      <th>symmetry_worst</th>
      <th>fractal_dimension_worst</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>M</td>
      <td>17.99</td>
      <td>10.38</td>
      <td>0.11840</td>
      <td>0.27760</td>
      <td>0.30010</td>
      <td>0.14710</td>
      <td>0.2419</td>
      <td>0.07871</td>
      <td>1.0950</td>
      <td>...</td>
      <td>0.01587</td>
      <td>0.03003</td>
      <td>0.006193</td>
      <td>17.33</td>
      <td>0.16220</td>
      <td>0.66560</td>
      <td>0.7119</td>
      <td>0.2654</td>
      <td>0.4601</td>
      <td>0.11890</td>
    </tr>
    <tr>
      <th>1</th>
      <td>M</td>
      <td>20.57</td>
      <td>17.77</td>
      <td>0.08474</td>
      <td>0.07864</td>
      <td>0.08690</td>
      <td>0.07017</td>
      <td>0.1812</td>
      <td>0.05667</td>
      <td>0.5435</td>
      <td>...</td>
      <td>0.01340</td>
      <td>0.01389</td>
      <td>0.003532</td>
      <td>23.41</td>
      <td>0.12380</td>
      <td>0.18660</td>
      <td>0.2416</td>
      <td>0.1860</td>
      <td>0.2750</td>
      <td>0.08902</td>
    </tr>
    <tr>
      <th>2</th>
      <td>M</td>
      <td>19.69</td>
      <td>21.25</td>
      <td>0.10960</td>
      <td>0.15990</td>
      <td>0.19740</td>
      <td>0.12790</td>
      <td>0.2069</td>
      <td>0.05999</td>
      <td>0.7456</td>
      <td>...</td>
      <td>0.02058</td>
      <td>0.02250</td>
      <td>0.004571</td>
      <td>25.53</td>
      <td>0.14440</td>
      <td>0.42450</td>
      <td>0.4504</td>
      <td>0.2430</td>
      <td>0.3613</td>
      <td>0.08758</td>
    </tr>
    <tr>
      <th>3</th>
      <td>M</td>
      <td>11.42</td>
      <td>20.38</td>
      <td>0.14250</td>
      <td>0.28390</td>
      <td>0.24140</td>
      <td>0.10520</td>
      <td>0.2597</td>
      <td>0.09744</td>
      <td>0.4956</td>
      <td>...</td>
      <td>0.01867</td>
      <td>0.05963</td>
      <td>0.009208</td>
      <td>26.50</td>
      <td>0.20980</td>
      <td>0.86630</td>
      <td>0.6869</td>
      <td>0.2575</td>
      <td>0.6638</td>
      <td>0.17300</td>
    </tr>
    <tr>
      <th>4</th>
      <td>M</td>
      <td>20.29</td>
      <td>14.34</td>
      <td>0.10030</td>
      <td>0.13280</td>
      <td>0.19800</td>
      <td>0.10430</td>
      <td>0.1809</td>
      <td>0.05883</td>
      <td>0.7572</td>
      <td>...</td>
      <td>0.01885</td>
      <td>0.01756</td>
      <td>0.005115</td>
      <td>16.67</td>
      <td>0.13740</td>
      <td>0.20500</td>
      <td>0.4000</td>
      <td>0.1625</td>
      <td>0.2364</td>
      <td>0.07678</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>564</th>
      <td>M</td>
      <td>21.56</td>
      <td>22.39</td>
      <td>0.11100</td>
      <td>0.11590</td>
      <td>0.24390</td>
      <td>0.13890</td>
      <td>0.1726</td>
      <td>0.05623</td>
      <td>1.1760</td>
      <td>...</td>
      <td>0.02454</td>
      <td>0.01114</td>
      <td>0.004239</td>
      <td>26.40</td>
      <td>0.14100</td>
      <td>0.21130</td>
      <td>0.4107</td>
      <td>0.2216</td>
      <td>0.2060</td>
      <td>0.07115</td>
    </tr>
    <tr>
      <th>565</th>
      <td>M</td>
      <td>20.13</td>
      <td>28.25</td>
      <td>0.09780</td>
      <td>0.10340</td>
      <td>0.14400</td>
      <td>0.09791</td>
      <td>0.1752</td>
      <td>0.05533</td>
      <td>0.7655</td>
      <td>...</td>
      <td>0.01678</td>
      <td>0.01898</td>
      <td>0.002498</td>
      <td>38.25</td>
      <td>0.11660</td>
      <td>0.19220</td>
      <td>0.3215</td>
      <td>0.1628</td>
      <td>0.2572</td>
      <td>0.06637</td>
    </tr>
    <tr>
      <th>566</th>
      <td>M</td>
      <td>16.60</td>
      <td>28.08</td>
      <td>0.08455</td>
      <td>0.10230</td>
      <td>0.09251</td>
      <td>0.05302</td>
      <td>0.1590</td>
      <td>0.05648</td>
      <td>0.4564</td>
      <td>...</td>
      <td>0.01557</td>
      <td>0.01318</td>
      <td>0.003892</td>
      <td>34.12</td>
      <td>0.11390</td>
      <td>0.30940</td>
      <td>0.3403</td>
      <td>0.1418</td>
      <td>0.2218</td>
      <td>0.07820</td>
    </tr>
    <tr>
      <th>567</th>
      <td>M</td>
      <td>20.60</td>
      <td>29.33</td>
      <td>0.11780</td>
      <td>0.27700</td>
      <td>0.35140</td>
      <td>0.15200</td>
      <td>0.2397</td>
      <td>0.07016</td>
      <td>0.7260</td>
      <td>...</td>
      <td>0.01664</td>
      <td>0.02324</td>
      <td>0.006185</td>
      <td>39.42</td>
      <td>0.16500</td>
      <td>0.86810</td>
      <td>0.9387</td>
      <td>0.2650</td>
      <td>0.4087</td>
      <td>0.12400</td>
    </tr>
    <tr>
      <th>568</th>
      <td>B</td>
      <td>7.76</td>
      <td>24.54</td>
      <td>0.05263</td>
      <td>0.04362</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.1587</td>
      <td>0.05884</td>
      <td>0.3857</td>
      <td>...</td>
      <td>0.00000</td>
      <td>0.02676</td>
      <td>0.002783</td>
      <td>30.37</td>
      <td>0.08996</td>
      <td>0.06444</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.2871</td>
      <td>0.07039</td>
    </tr>
  </tbody>
</table>
<p>569 rows × 24 columns</p>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[11]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Finding Outliers Using Interquartile Range</span>

<span class="c1">#Loading Packages</span>
<span class="kn">from</span> <span class="nn">scipy</span> <span class="kn">import</span> <span class="n">stats</span>

<span class="c1">#Calculating Interquartile Range</span>
<span class="n">q1</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">quantile</span><span class="p">(</span><span class="mf">0.25</span><span class="p">)</span>
<span class="n">q3</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">quantile</span><span class="p">(</span><span class="mf">0.75</span><span class="p">)</span>
<span class="n">IQR</span> <span class="o">=</span> <span class="n">q3</span><span class="o">-</span><span class="n">q1</span>
<span class="nb">print</span><span class="p">(</span><span class="n">IQR</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>radius_mean                4.080000
texture_mean               5.630000
smoothness_mean            0.018930
compactness_mean           0.065480
concavity_mean             0.101140
concavepoints_mean         0.053690
symmetry_mean              0.033800
fractal_dimension_mean     0.008420
radius_se                  0.246500
texture_se                 0.640100
smoothness_se              0.002977
compactness_se             0.019370
concavity_se               0.026960
concavepoints_se           0.007072
symmetry_se                0.008320
fractal_dimension_se       0.002310
texture_worst              8.640000
smoothness_worst           0.029400
compactness_worst          0.191900
concavity_worst            0.268400
concavepoints_worst        0.096470
symmetry_worst             0.067500
fractal_dimension_worst    0.020620
dtype: float64
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[12]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Checking Which Values Fall Outside the Interquartile Range</span>
<span class="p">(</span><span class="n">df</span> <span class="o">&lt;</span> <span class="p">(</span><span class="n">q1</span> <span class="o">-</span> <span class="mf">1.5</span> <span class="o">*</span> <span class="n">IQR</span><span class="p">))</span> <span class="o">|</span> <span class="p">(</span><span class="n">df</span> <span class="o">&gt;</span> <span class="p">(</span><span class="n">q3</span> <span class="o">+</span> <span class="mf">1.5</span> <span class="o">*</span> <span class="n">IQR</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[12]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>compactness_mean</th>
      <th>compactness_se</th>
      <th>compactness_worst</th>
      <th>concavepoints_mean</th>
      <th>concavepoints_se</th>
      <th>concavepoints_worst</th>
      <th>concavity_mean</th>
      <th>concavity_se</th>
      <th>concavity_worst</th>
      <th>diagnosis</th>
      <th>...</th>
      <th>radius_se</th>
      <th>smoothness_mean</th>
      <th>smoothness_se</th>
      <th>smoothness_worst</th>
      <th>symmetry_mean</th>
      <th>symmetry_se</th>
      <th>symmetry_worst</th>
      <th>texture_mean</th>
      <th>texture_se</th>
      <th>texture_worst</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>564</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>565</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>566</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>567</th>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>568</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>569 rows × 24 columns</p>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>There were several outliers identified using the interquartile range.  There were various categories where the outliers were identified with a wide variety of variables.  The most common variable where it was noted was compactness.  The majority of these outliers were mostly identified as malignant though there were some benign diagnoses with outliers in the compactness variables.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[13]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Visualizing Distributions of Numerical Data</span>

<span class="c1">#Setting Figure Size</span>
<span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">[</span><span class="mi">100</span><span class="p">,</span><span class="mi">100</span><span class="p">])</span>

<span class="n">f</span><span class="p">,</span><span class="n">a</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">subplots</span><span class="p">(</span><span class="mi">8</span><span class="p">,</span><span class="mi">3</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">40</span><span class="p">,</span><span class="mi">40</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">subplots_adjust</span><span class="p">(</span><span class="n">hspace</span><span class="o">=</span><span class="mf">0.25</span><span class="p">,</span> <span class="n">wspace</span> <span class="o">=</span> <span class="mf">0.25</span><span class="p">)</span>

<span class="n">a</span> <span class="o">=</span> <span class="n">a</span><span class="o">.</span><span class="n">ravel</span><span class="p">()</span>
<span class="k">for</span> <span class="n">idx</span><span class="p">,</span><span class="n">ax</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">a</span><span class="p">):</span>
    <span class="n">ax</span><span class="o">.</span><span class="n">hist</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">iloc</span><span class="p">[:,</span><span class="n">idx</span><span class="p">],</span> <span class="n">bins</span><span class="o">=</span><span class="mi">100</span><span class="p">)</span>
    <span class="n">ax</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">columns</span><span class="p">[</span><span class="n">idx</span><span class="p">])</span>
    <span class="n">ax</span><span class="o">.</span><span class="n">set_ylabel</span><span class="p">(</span><span class="s1">&#39;Counts&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_text output_subarea ">
<pre>&lt;Figure size 7200x7200 with 0 Axes&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Many of these variables are positively skewed.  The only variables that appear to be mostly normally distributed are symmetry_mean and possible fractal_dimension_mean.  Concave_points_worst actually appears to be bimodal.</strong></p>
<p><strong>Our target variable has approximately 150 more benign samples than malignant samples.  While it is expected that benign values would likely outnumber malignant values, this means that accuracy as a target metric for our machine learning algorithms will be deceptively high.  We will focus on the F1, precision, and recall scores instead.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>While these values are skewed which could affect the model, the outliers could also be possibly correlated with more malignant disease.  I will not transform these skewed values to be as accurate as possible.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[14]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Comparing Target Variable with our Explanatory Variables</span>

<span class="c1">#Setting Parameters</span>
<span class="n">categories</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">diagnosis</span>

<span class="n">fig</span><span class="p">,</span><span class="n">axs</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">subplots</span><span class="p">(</span><span class="mi">8</span><span class="p">,</span><span class="mi">3</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">30</span><span class="p">,</span><span class="mi">30</span><span class="p">))</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">radius_mean</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Radius Mean Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">texture_mean</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Texture Mean Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">smoothness_mean</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Smoothness Mean Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">1</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">compactness_mean</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">1</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Compactness Mean Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">1</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">concavity_mean</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">1</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Concavity Mean Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">1</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">concavepoints_mean</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">1</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Concave Points Mean Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">2</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">symmetry_mean</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">2</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Symmetry Mean Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">2</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">fractal_dimension_mean</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">2</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Fractal Dimension Mean Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">2</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">radius_se</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">2</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Radius S.E. Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">3</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">texture_se</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">3</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Texture S.E. Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">3</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">smoothness_se</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">3</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Smoothness S.E. Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">3</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">compactness_se</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">3</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Compactness S.E. Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">4</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">concavity_se</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">4</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Concavity S.E. Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">4</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">concavepoints_se</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">4</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Concave Points S.E. Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">4</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">symmetry_se</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">4</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Symmetry S.E. Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">5</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">fractal_dimension_se</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">5</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Fractal Dimension S.E. Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">5</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">texture_worst</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">5</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Texture Worst Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">5</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">smoothness_worst</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">5</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Smoothness Worst Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">6</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">compactness_worst</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">6</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Compactness Worst Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">6</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">concavity_worst</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">6</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Concavity Worst Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">6</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">concavepoints_worst</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">6</span><span class="p">,</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Concave Points Worst Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">7</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">symmetry_worst</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">7</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Symmetry Worst Values&#39;</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">7</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">fractal_dimension_worst</span><span class="p">)</span>
<span class="n">axs</span><span class="p">[</span><span class="mi">7</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Benign/Malignant vs. Fractal Dimension Worst Values&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[14]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>Text(0.5, 1.0, &#39;Benign/Malignant vs. Fractal Dimension Worst Values&#39;)</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Looking at the comparisons of our predictor variables vs. their diagnosis of malignant or benign, there are several interesting factors.  While there were some outliers, I still will keep these in the datasets for now.  In general, the malignant tumors seemed to have higher worst symmetry scores, worst concave points, worst concavity, worst compactness, and texture worst values.</strong></p>
<p><strong>In general, the radius mean tended to be larger with malignant tumors.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[15]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Running Logistic Regression Method to Predict Malignant or Benign</span>

<span class="c1">#Importing Packages</span>
<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="kn">import</span> <span class="n">train_test_split</span>
<span class="kn">from</span> <span class="nn">sklearn.linear_model</span> <span class="kn">import</span> <span class="n">LogisticRegression</span>
<span class="kn">from</span> <span class="nn">sklearn.preprocessing</span> <span class="kn">import</span> <span class="n">StandardScaler</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="kn">import</span> <span class="n">classification_report</span><span class="p">,</span> <span class="n">confusion_matrix</span>

<span class="c1">#Creating Features and Target Objects</span>
<span class="n">features</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">loc</span><span class="p">[:,</span> <span class="n">df</span><span class="o">.</span><span class="n">columns</span> <span class="o">!=</span> <span class="s1">&#39;diagnosis&#39;</span><span class="p">]</span>
<span class="n">target</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;diagnosis&#39;</span><span class="p">]</span>

<span class="c1">#Creating Standardizer</span>
<span class="n">standardizer</span> <span class="o">=</span> <span class="n">StandardScaler</span><span class="p">()</span>

<span class="c1">#Creating Logistic Regression Object</span>
<span class="n">logit</span> <span class="o">=</span> <span class="n">LogisticRegression</span><span class="p">()</span>

<span class="c1">#Standardizing Features</span>
<span class="n">features_standardized</span> <span class="o">=</span> <span class="n">standardizer</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">features</span><span class="p">)</span>

<span class="c1">#Train Test 80/20 Split</span>
<span class="n">features_train</span><span class="p">,</span> <span class="n">features_test</span><span class="p">,</span> <span class="n">target_train</span><span class="p">,</span> <span class="n">target_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">features_standardized</span><span class="p">,</span> <span class="n">target</span><span class="p">,</span> <span class="n">test_size</span> <span class="o">=</span> <span class="mf">0.2</span><span class="p">,</span> <span class="n">random_state</span> <span class="o">=</span><span class="mi">1</span><span class="p">)</span>

<span class="c1">#Fitting Data to Logistic Regression Classifier</span>
<span class="n">logreg</span> <span class="o">=</span> <span class="n">logit</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">features_train</span><span class="p">,</span> <span class="n">target_train</span><span class="p">)</span>

<span class="c1">#Generating Confusion Matrix/Classification Report</span>
<span class="n">target_pred</span> <span class="o">=</span> <span class="n">logit</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">features_test</span><span class="p">)</span>
<span class="n">test0</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">target_test</span><span class="p">)</span>
<span class="n">predictions0</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">target_pred</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Confusion Matrix:</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">,</span> <span class="n">confusion_matrix</span><span class="p">(</span><span class="n">test0</span><span class="p">,</span> <span class="n">predictions0</span><span class="p">),</span><span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Classification Report:</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">,</span> <span class="n">classification_report</span><span class="p">(</span><span class="n">test0</span><span class="p">,</span> <span class="n">predictions0</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Confusion Matrix:
 [[71  1]
 [ 2 40]]

Classification Report:
               precision    recall  f1-score   support

           B       0.97      0.99      0.98        72
           M       0.98      0.95      0.96        42

    accuracy                           0.97       114
   macro avg       0.97      0.97      0.97       114
weighted avg       0.97      0.97      0.97       114

</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>This model performed quite well.  There were 2 misclassifications of benign lesions that were actually malignant.  F1 score for benign lesions was 0.98 and malignant lesions was 0.96 which are quite high.  Next we will check the feature importance of the different factors in the model based on their coefficients.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[16]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Checking Feature Importance Based on Coefficients</span>

<span class="c1">#Importing Packages</span>
<span class="kn">from</span> <span class="nn">yellowbrick.model_selection</span> <span class="kn">import</span> <span class="n">FeatureImportances</span>

<span class="c1">#Getting Labels and Checking Feature Importances For Logistic Regression Model</span>
<span class="n">labels</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">map</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">x</span><span class="o">.</span><span class="n">title</span><span class="p">(),</span> <span class="n">features</span><span class="p">))</span>
<span class="n">viz</span> <span class="o">=</span> <span class="n">FeatureImportances</span><span class="p">(</span><span class="n">logreg</span><span class="p">,</span> <span class="n">labels</span><span class="o">=</span><span class="n">labels</span><span class="p">)</span>
<span class="n">viz</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">features_train</span><span class="p">,</span> <span class="n">features_test</span><span class="p">)</span>
<span class="n">viz</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[16]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.axes._subplots.AxesSubplot at 0x2219a37f400&gt;</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Looking at the relative feature importance using the logistic regression model, radius_se, radius_mean, concavepoints_mean, texture/concavepoints/symmetry worst and concavity_mean/worst all had fairly high relative importances based on their coefficients.</strong></p>
<p><strong>It is not surprising that the radius mean and standard error values were highly important in the model since cell size is proportional to malignant cells (generally).  It is also interesting that there were a lot of variables with worst values that were highly important.  This could suggest that the values that are the most abnormal could be associated with predicting malignant or benign lesions.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[17]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Running KNN To Predict Malignant or Benign</span>

<span class="c1">#Using Same Features and Target as Previous Example though Will Need to Get Dummy Variables for Target</span>
<span class="n">target</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">get_dummies</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;diagnosis&#39;</span><span class="p">])</span>

<span class="c1">#Importing Packages</span>
<span class="kn">from</span> <span class="nn">sklearn.neighbors</span> <span class="kn">import</span> <span class="n">KNeighborsClassifier</span>
<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="kn">import</span> <span class="n">GridSearchCV</span><span class="p">,</span> <span class="n">RandomizedSearchCV</span>

<span class="c1">#Creating Standardizer</span>
<span class="n">standardizer</span> <span class="o">=</span> <span class="n">StandardScaler</span><span class="p">()</span>

<span class="c1">#Standardizing Features</span>
<span class="n">features_standardized</span> <span class="o">=</span> <span class="n">standardizer</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">features</span><span class="p">)</span>

<span class="c1">#Train/Teset 80/20 Split</span>
<span class="n">features_train</span><span class="p">,</span> <span class="n">features_test</span><span class="p">,</span> <span class="n">target_train</span><span class="p">,</span> <span class="n">target_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">features_standardized</span><span class="p">,</span> <span class="n">target</span><span class="p">,</span> <span class="n">test_size</span> <span class="o">=</span> <span class="mf">0.2</span><span class="p">,</span> <span class="n">random_state</span> <span class="o">=</span> <span class="mi">1</span><span class="p">)</span>

<span class="c1">#Creating KNN Object With K of 3 Before Hyperparameter Tuning</span>
<span class="n">knn</span> <span class="o">=</span> <span class="n">KNeighborsClassifier</span><span class="p">(</span><span class="n">n_neighbors</span> <span class="o">=</span> <span class="mi">3</span><span class="p">,</span> <span class="n">n_jobs</span> <span class="o">=</span> <span class="o">-</span><span class="mi">1</span><span class="p">)</span>

<span class="c1">#Fitting Classifier on Training Data</span>
<span class="n">knn</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">features_train</span><span class="p">,</span> <span class="n">target_train</span><span class="p">)</span>

<span class="c1">#Creating Confusion Matrix/Classification Report</span>
<span class="n">target_pred</span> <span class="o">=</span> <span class="n">knn</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">features_test</span><span class="p">)</span>
<span class="n">test</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">target_test</span><span class="p">)</span><span class="o">.</span><span class="n">argmax</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
<span class="n">predictions</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">target_pred</span><span class="p">)</span><span class="o">.</span><span class="n">argmax</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Confusion Matrix:</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">,</span> <span class="n">confusion_matrix</span><span class="p">(</span><span class="n">test</span><span class="p">,</span> <span class="n">predictions</span><span class="p">),</span><span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Classification Report:</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">,</span> <span class="n">classification_report</span><span class="p">(</span><span class="n">test</span><span class="p">,</span> <span class="n">predictions</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Confusion Matrix:
 [[69  3]
 [ 7 35]]

Classification Report:
               precision    recall  f1-score   support

           0       0.91      0.96      0.93        72
           1       0.92      0.83      0.88        42

    accuracy                           0.91       114
   macro avg       0.91      0.90      0.90       114
weighted avg       0.91      0.91      0.91       114

</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[18]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Hyperparameter Tuning for KNN Using GridSearch CV</span>

<span class="c1">#Creating Hyperparameter Grid</span>
<span class="n">param_dist1</span> <span class="o">=</span> <span class="p">{</span><span class="s2">&quot;leaf_size&quot;</span><span class="p">:</span> <span class="nb">list</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">50</span><span class="p">)),</span>
              <span class="s2">&quot;n_neighbors&quot;</span><span class="p">:</span> <span class="nb">list</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">30</span><span class="p">)),</span>
              <span class="s2">&quot;p&quot;</span><span class="p">:</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span><span class="mi">2</span><span class="p">]}</span>

<span class="c1">#Creating New KNN Object</span>
<span class="n">knn_2</span> <span class="o">=</span> <span class="n">KNeighborsClassifier</span><span class="p">()</span>

<span class="c1">#Using GridSearch Object</span>
<span class="n">clf</span> <span class="o">=</span> <span class="n">GridSearchCV</span><span class="p">(</span><span class="n">knn_2</span><span class="p">,</span> <span class="n">param_dist1</span><span class="p">,</span> <span class="n">cv</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span> <span class="n">n_jobs</span> <span class="o">=</span> <span class="o">-</span><span class="mi">1</span><span class="p">)</span>

<span class="c1">#Fitting Model</span>
<span class="n">best_model</span> <span class="o">=</span> <span class="n">clf</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">features_standardized</span><span class="p">,</span> <span class="n">target</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Best Leaf Size:&#39;</span><span class="p">,</span> <span class="n">best_model</span><span class="o">.</span><span class="n">best_estimator_</span><span class="o">.</span><span class="n">get_params</span><span class="p">()[</span><span class="s1">&#39;leaf_size&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Best p:&#39;</span><span class="p">,</span> <span class="n">best_model</span><span class="o">.</span><span class="n">best_estimator_</span><span class="o">.</span><span class="n">get_params</span><span class="p">()[</span><span class="s1">&#39;p&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Best n_neighbors:&#39;</span><span class="p">,</span> <span class="n">best_model</span><span class="o">.</span><span class="n">best_estimator_</span><span class="o">.</span><span class="n">get_params</span><span class="p">()[</span><span class="s1">&#39;n_neighbors&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Best Metric:&#39;</span><span class="p">,</span> <span class="n">best_model</span><span class="o">.</span><span class="n">best_estimator_</span><span class="o">.</span><span class="n">get_params</span><span class="p">()[</span><span class="s1">&#39;metric&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Best Weights:&#39;</span><span class="p">,</span> <span class="n">best_model</span><span class="o">.</span><span class="n">best_estimator_</span><span class="o">.</span><span class="n">get_params</span><span class="p">()[</span><span class="s1">&#39;weights&#39;</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Best Leaf Size: 1
Best p: 1
Best n_neighbors: 7
Best Metric: minkowski
Best Weights: uniform
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[20]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Rerunning KNN Using Our Tuned Parameters</span>

<span class="c1">#Creating Standardizer</span>
<span class="n">standardizer</span> <span class="o">=</span> <span class="n">StandardScaler</span><span class="p">()</span>

<span class="c1">#Standardizing Features</span>
<span class="n">features_standardized</span> <span class="o">=</span> <span class="n">standardizer</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">features</span><span class="p">)</span>

<span class="c1">#Train/Teset 80/20 Split</span>
<span class="n">features_train</span><span class="p">,</span> <span class="n">features_test</span><span class="p">,</span> <span class="n">target_train</span><span class="p">,</span> <span class="n">target_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">features_standardized</span><span class="p">,</span> <span class="n">target</span><span class="p">,</span> <span class="n">test_size</span> <span class="o">=</span> <span class="mf">0.2</span><span class="p">,</span> <span class="n">random_state</span> <span class="o">=</span> <span class="mi">1</span><span class="p">)</span>

<span class="c1">#Creating KNN Object With K of 3 Before Hyperparameter Tuning</span>
<span class="n">knn</span> <span class="o">=</span> <span class="n">KNeighborsClassifier</span><span class="p">(</span><span class="n">n_neighbors</span> <span class="o">=</span> <span class="mi">7</span><span class="p">,</span> <span class="n">p</span> <span class="o">=</span> <span class="mi">1</span><span class="p">,</span> <span class="n">leaf_size</span> <span class="o">=</span> <span class="mi">1</span><span class="p">,</span> <span class="n">metric</span> <span class="o">=</span> <span class="s2">&quot;minkowski&quot;</span><span class="p">,</span> <span class="n">weights</span> <span class="o">=</span> <span class="s2">&quot;uniform&quot;</span><span class="p">,</span> <span class="n">n_jobs</span> <span class="o">=</span> <span class="o">-</span><span class="mi">1</span><span class="p">)</span>

<span class="c1">#Fitting Classifier on Training Data</span>
<span class="n">knn</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">features_train</span><span class="p">,</span> <span class="n">target_train</span><span class="p">)</span>

<span class="c1">#Creating Confusion Matrix/Classification Report</span>
<span class="n">target_pred</span> <span class="o">=</span> <span class="n">knn</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">features_test</span><span class="p">)</span>
<span class="n">test</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">target_test</span><span class="p">)</span><span class="o">.</span><span class="n">argmax</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
<span class="n">predictions</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">target_pred</span><span class="p">)</span><span class="o">.</span><span class="n">argmax</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Confusion Matrix:</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">,</span> <span class="n">confusion_matrix</span><span class="p">(</span><span class="n">test</span><span class="p">,</span> <span class="n">predictions</span><span class="p">),</span><span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Classification Report:</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">,</span> <span class="n">classification_report</span><span class="p">(</span><span class="n">test</span><span class="p">,</span> <span class="n">predictions</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Confusion Matrix:
 [[70  2]
 [ 7 35]]

Classification Report:
               precision    recall  f1-score   support

           0       0.91      0.97      0.94        72
           1       0.95      0.83      0.89        42

    accuracy                           0.92       114
   macro avg       0.93      0.90      0.91       114
weighted avg       0.92      0.92      0.92       114

</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Feature importance was not done on the KNN model since it is not directly applicable to this algorithm.  However, this model performed worse than the logistic regression model with F1-scores of 0.94 for benign lesions and 0.89 for malignant lesions.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[21]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Running Random Forest Algorithm on Data</span>

<span class="c1">#Importing Packages</span>
<span class="kn">from</span> <span class="nn">sklearn.ensemble</span> <span class="kn">import</span> <span class="n">RandomForestClassifier</span>

<span class="c1">#Resetting Features and Targets</span>
<span class="n">features</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">loc</span><span class="p">[:,</span> <span class="n">df</span><span class="o">.</span><span class="n">columns</span> <span class="o">!=</span> <span class="s1">&#39;diagnosis&#39;</span><span class="p">]</span>
<span class="n">target</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;diagnosis&#39;</span><span class="p">]</span>

<span class="c1">#Creating Standardizer</span>
<span class="n">standardizer</span> <span class="o">=</span> <span class="n">StandardScaler</span><span class="p">()</span>

<span class="c1">#Standardizing Features</span>
<span class="n">features_standardized</span> <span class="o">=</span> <span class="n">standardizer</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">features</span><span class="p">)</span>

<span class="c1">#Train/Teset 80/20 Split</span>
<span class="n">features_train</span><span class="p">,</span> <span class="n">features_test</span><span class="p">,</span> <span class="n">target_train</span><span class="p">,</span> <span class="n">target_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">features_standardized</span><span class="p">,</span> <span class="n">target</span><span class="p">,</span> <span class="n">test_size</span> <span class="o">=</span> <span class="mf">0.2</span><span class="p">,</span> <span class="n">random_state</span> <span class="o">=</span> <span class="mi">1</span><span class="p">)</span>

<span class="c1">#Creating Random Forest Object</span>
<span class="n">rf</span> <span class="o">=</span> <span class="n">RandomForestClassifier</span><span class="p">(</span><span class="n">n_estimators</span><span class="o">=</span> <span class="mi">100</span><span class="p">,</span> <span class="n">random_state</span> <span class="o">=</span> <span class="mi">1</span><span class="p">)</span>

<span class="c1">#Fitting Classifier on Training Data</span>
<span class="n">rf</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">features_train</span><span class="p">,</span> <span class="n">target_train</span><span class="p">)</span>

<span class="c1">#Creating Confusion Matrix/Classification Report</span>
<span class="n">target_pred</span> <span class="o">=</span> <span class="n">rf</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">features_test</span><span class="p">)</span>
<span class="n">test</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">target_test</span><span class="p">)</span>
<span class="n">predictions</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">target_pred</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Confusion Matrix:</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">,</span> <span class="n">confusion_matrix</span><span class="p">(</span><span class="n">test</span><span class="p">,</span> <span class="n">predictions</span><span class="p">),</span><span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Classification Report:</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">,</span> <span class="n">classification_report</span><span class="p">(</span><span class="n">test</span><span class="p">,</span> <span class="n">predictions</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Confusion Matrix:
 [[72  0]
 [ 5 37]]

Classification Report:
               precision    recall  f1-score   support

           B       0.94      1.00      0.97        72
           M       1.00      0.88      0.94        42

    accuracy                           0.96       114
   macro avg       0.97      0.94      0.95       114
weighted avg       0.96      0.96      0.96       114

</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>The random forest model performed slightly better than the KNN model with an F1 score of 0.97 for benign lesions and an F1 score of 0.94 for malignant lesions.  Of more concern is that 5 benign lesions were classified as benign when they were actually malignant.</strong></p>
<p><strong>Next, for comparison between this and the logistic regression model, we'll rank feature importance in this model as well.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[22]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Ranking Feature Importance Based on the Random Forest Algorithm</span>

<span class="n">labels1</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">map</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">x</span><span class="o">.</span><span class="n">title</span><span class="p">(),</span> <span class="n">features</span><span class="p">))</span>
<span class="n">viz</span> <span class="o">=</span> <span class="n">FeatureImportances</span><span class="p">(</span><span class="n">rf</span><span class="p">,</span> <span class="n">labels</span><span class="o">=</span><span class="n">labels</span><span class="p">)</span>
<span class="n">viz</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">features_train</span><span class="p">,</span> <span class="n">features_test</span><span class="p">)</span>
<span class="n">viz</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[22]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.axes._subplots.AxesSubplot at 0x2219a28b970&gt;</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>The results of this were quite interesting as well.  Concavepoints_worst, concavepoints_mean, radius_mean, concavity_mean, and concavity_worst were all ranked highly with relative importance.  These are very similar to the logistic regression model.</strong></p>
<p><strong>This would seem to suggest that radius_mean and concavepoints_worst/mean all seem to be important whichever model you are using and perhaps could be a focus of future projects.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Overall, the Logistic Regression model seems to be the best option of the three models tested.  Due to the imbalanced target class, accuracy alone is not a good measure of performance since in an unbalanced class, the algorithm by chance could be more likely to guess a certain outcome because it knows that that is the most likely answer.</strong></p>
<p><strong>The F1 scores for the Logistic Regression model were the highest of the 3 models tested.  This model also minimized the number of false negatives or missed cancer diagnoses.</strong></p>
<p><strong>Limitations of this dataset include older data as well as limited data points.  Further projects would require thousands, perhaps millions of more current data points.  Healthcare demographics as well as cancer diagnosis and treatment standards of care change rapidly so current data is paramount.</strong></p>
<p><strong>This project demonstrates that machine learning could be potentially useful as an adjunct to standard patient care.  The goal is not to replace doctors; on the contrary, doctors are required to be on the forefront treating patients and are still experts in the field.  However, the goal should be to use machine learning models as an adjunct to flag potentially high-risk findings that should be further investigated before disregarding.  This could be something as simple as the model indicating that there are several highly suspicious features of malignancy and have a physician review for final diagnosis to either concur or dispute that result.  Outcome improvement is paramount; a healthcare system must strive to deliver the best quality care as possible.  This is a basic tenet of treating patients and this project suggests that machine learning could potentially help healthcare workers improve outcomes and make patient’s lives better.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span>
</pre></div>

    </div>
</div>
</div>

</div>
    </div>
  </div>
</body>




</html>