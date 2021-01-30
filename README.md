# Autoscript

The reason for this project is to provide an npm package for autoscript.js so it's easier to use it from your JS projects. I have created the NPM package under the scope @doncicuto in case of autoscript developers choose to upload an official npm package under autoscript name.

This package contains autoscript.js, a README explaining what's Autofirma and Autoscript, some quick notes of usage, and the demo files provided with Autoscript on how to launch and use Autofirma from the browser.

Autoscript.js is a javascript file developed by the Government of Spain to launch and use Autofirma from a web browser.

Please, note that all credits for the source code and the demo files are for the Government of Spain developers and maintainer, this project only allows you to download and use autoscript.js from npmjs.

## What is Autofirma and Autoscript?

Autofirma is an electronic signature application developed by the then Ministry of Finance and Public Administrations. This application, being able to be executed from the browser with Autosign.js, allows the signature on Electronic Administration pages when the signature is required in an administrative procedure.

Autofirma is part of the @firma suite of electronic signature and identification solutions offered as free software with GPL 2+ and EUPL 1.1 licenses. Autofirma can be downloaded from [https://firmaelectronica.gob.es/Home/Descargas.html](https://firmaelectronica.gob.es/Home/Descargas.html).

Autoscript.js is publicly available in the Autoscript section of the Download Area of ​​the Technology Transfer Center of the Electronic Administration Portal (CTT). The url of the download area is [https://administracionelectronica.gob.es/ctt/clienteafirma/descargas](https://administracionelectronica.gob.es/ctt/clienteafirma/descargas). The source code is available at [Autofirma's Github repository](https://github.com/ctt-gob-es/clienteafirma/) in the following path 'afirma-ui-miniapplet-deploy/src/main/webapp/js/autoscript.js'.

There's more information about Autocript in a PDF document called 'Manual Integrador' whis has been written in Spanish that can be downloaded from the Download Area of ​​the Technology Transfer Center of the Electronic Administration Portal (CTT).

## Sample code about Autoscript

Government of Spain provides two html files that use autoscript.js and a constantes.js file. Those files are cliente-batch.html and cliente-full.html that are located inside the demo folder of this package (node_modules/autoscript).

## Usage

You can use install autoscript using npm or yarn using:

`npm install autoscript`

or

`yarn add autoscript`

You can use Autofirma using the Autoscript object that will be available as a global variable once you add it to your html code using the following script tag:

`<script src='node_modules/@doncicuto/autoscript/autoscript.js'></script>`

Here's an html demo page, that will open Autofirma and allow you to select an X509 certificate from your browser's cert store.

```(html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Autoscript Demo</title>
</head>
<body>
  <button onclick="selectCertificate()">Select certificate</button>
  <script src='node_modules/@doncicuto/autoscript/autoscript.js'></script>
  <script>
    function selectCertificate() {
      try {
        AutoScript.selectCertificate(
          "",
          function(certificate) {
            console.log(certificate)
          },
          function(type,message) {
            console.log("Type: " + type + "\nMessage: " + message);
          }
        );
      } catch(e) {
        console.log("Type: " + AutoScript.getErrorType() + "\nMessage: " + AutoScript.getErrorMessage());
      }
    }
    AutoScript.cargarAppAfirma(); // Opens Autofirma
  </script>
</body>
</html>
```
