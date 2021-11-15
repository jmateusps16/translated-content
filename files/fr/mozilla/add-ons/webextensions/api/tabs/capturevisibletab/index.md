---
title: tabs.captureVisibleTab()
slug: Mozilla/Add-ons/WebExtensions/API/tabs/captureVisibleTab
tags:
  - API
  - Add-ons
  - Extensions
  - Méthode
  - Non-standard
  - Reference
  - WebExtensions
  - captureVisibleTab
  - tabs
translation_of: Mozilla/Add-ons/WebExtensions/API/tabs/captureVisibleTab
---
<div>{{AddonSidebar()}}</div>

<p>Crée une URI de données codant une image de la zone visible de l'onglet actuellement actif dans la fenêtre spécifiée. Vous devez avoir la  <a href="/fr/Add-ons/WebExtensions/manifest.json/permissions">permission</a> <code>&lt;all_urls&gt;</code> pour utiliser cette méthode. (Alternativement, Chrome permet l'utilisation de cette méthode avec la <a href="/fr/Add-ons/WebExtensions/manifest.json/permissions">permission</a> <code>activeTab</code> et un geste utilisateur qualifiant).</p>

<p>C'est une fonction asynchrone qui renvoie une <code><a href="/fr/docs/Web/JavaScript/Reference/Objets_globaux/Promise">Promise</a></code>.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">var capturing = browser.tabs.captureVisibleTab(
  windowId,               // optional integer
  options                 // optional extensionTypes.ImageDetails
)
</pre>

<h3 id="Paramètres">Paramètres</h3>

<dl>
 <dt><code>windowId</code>{{optional_inline}}</dt>
 <dd><code>integer</code>. La fenêtre cible Par défaut à la fenêtre actuelle.</dd>
 <dt><code>options</code>{{optional_inline}}</dt>
 <dd>{{WebExtAPIRef('extensionTypes.ImageDetails')}}.</dd>
</dl>

<h3 id="Valeur_retournée">Valeur retournée</h3>

<p>Une <code><a href="/fr/docs/Web/JavaScript/Reference/Objets_globaux/Promise">Promise</a></code> qui sera remplie avec une URL de données qui code une image de la zone visible de l'onglet capturé. Peut être affecté à la propriété 'src' d'un élément HTML Image pour l'affichage. Si une erreur se produit, la promesse sera rejetée avec un message d'erreur.</p>

<h2 id="Exemples">Exemples</h2>

<p>Capturez une image de l'onglet actif dans la fenêtre actuelle, avec les paramètres par défaut :</p>

<pre class="brush: js">function onCaptured(imageUri) {
  console.log(imageUri);
}

function onError(error) {
  console.log(`Error: ${error}`);
}

browser.browserAction.onClicked.addListener(function() {
  var capturing = browser.tabs.captureVisibleTab();
  capturing.then(onCaptured, onError);
});
</pre>

<p>{{WebExtExamples}}</p>

<h2 id="Compatibilité_du_navigateur">Compatibilité du navigateur</h2>

<p>{{Compat("webextensions.api.tabs.captureVisibleTab")}}</p>

<div class="note"><p><strong>Note :</strong></p>

<p>Cette API est basée sur l'API Chromium <a href="https://developer.chrome.com/extensions/tabs#method-executeScript"><code>chrome.tabs</code></a>. Cette documentation est dérivée de <a href="https://chromium.googlesource.com/chromium/src/+/master/chrome/common/extensions/api/tabs.json"><code>tabs.json</code></a> dans le code de Chromium code.</p>

<p>Les données de compatibilité relatives à Microsoft Edge sont fournies par Microsoft Corporation et incluses ici sous la licence Creative Commons Attribution 3.0 pour les États-Unis.</p>
</div>

<div class="hidden">
<pre>// Copyright 2015 The Chromium Authors. All rights reserved.
//
// Redistribution and use in source and binary forms, with or without
// modification, are permitted provided that the following conditions are
// met:
//
//    * Redistributions of source code must retain the above copyright
// notice, this list of conditions and the following disclaimer.
//    * Redistributions in binary form must reproduce the above
// copyright notice, this list of conditions and the following disclaimer
// in the documentation and/or other materials provided with the
// distribution.
//    * Neither the name of Google Inc. nor the names of its
// contributors may be used to endorse or promote products derived from
// this software without specific prior written permission.
//
// THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
// "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
// LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
// A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
// OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
// SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
// LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
// DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
// THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
// (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
// OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
</pre>
</div>