# BiB

<img src="https://i.imgsafe.org/95ab99dfdf.jpg" width="500" height="400">


## Library Management Application for Elementary Schools

**BiB** is OpenSource and independent from any OS because it runs completely in a browser. 

It comprises of these parts:

* A client-side UI 
* A backend based on HapiJS
* An SQL-database (MariaDB by default, or similar databases)

All of these parts are completely OpenSource Software and impose no restrictions regarding OS and usage.

The only real requirement is one of the modern browsers like Chrome, Firefox, IE11, or Edge.

**BiB** supports retrieval of library content via WorldCat. 

*Technologies*

BiB is based on these fine projects, packages & languages:

* TypeScript

* Angular 2

* HapiJS 

* jQuery Plugins: 

                 datatables.net
                 jquery.contextmenu
                 jquery.confirm 
                 jquery.select2

* Toastr

* SCSS

* Bootstrap 3

* HammerJS

* ng2-translate

## Preparations

* Database

    Before you can use this application you'll have to provide a properly defined database. 
    The script for automatic database creation is located in the config-folder. 

* NodeJS
    
    Execute 
    
    `npm install` 
    
    to download all needed packages. 
    
    *Notice*: If you're using a Windows machine you'll have to 
    provide a complete Visual Studio Build Environment because the NodeJS installation procedure will try to 
    build a Windows-compatible binary of the MariaDB package.

## Running

This application can either be run in a development mode directly from console or as a complete web application that
resides in a www-directory of one of the available web-servers. 

If you're planning to develop this app then you should use 

`npm run start:client` 

to run it under the WebPack DevServer. 

To run it as a complete web app use 

`npm run build:prod`

to create a new productive build under the dist folder. Afterwards, copy the contents of this folder to a directory inside 
the root of your preferred web server.

In either case your application will need a proper backend that has to be run with:

`npm run start:server`

Because the server-side scripts are written in TypeScript too you'll need a Node version called *ts-node* that understands this JavaScript dialect.
The installation of ts-node is usually done with the initial install from above but if you experience any problems with compiling TypeScript files,
please, check if you maybe have different versions of your globa/local packages. The same applies to your TypeScript and WebPack versions.

The server-side scripts run with HapiJS on port 10000. By default there are no additional security measures, like SSL, applied as this application is intended to run
on a single machine without any internet connection. The only exception is the ISBN data-retrieval that needs a working internet connection.

## APIs

The server provides an API for managing the following: 

* Media 
* Lending
* Reader Management
* User Management
* Statistics 
* Translations
* Access Control
* Library Data Retrieval via ISBN

The opposite of it is the *BibAPI* that's located in [app/apis/bib.api.ts](https://github.com/brakmic/BiB/blob/master/src/app/apis/bib.api.ts). 

This is the client-side API and all future developments should follow its initial design. This API is quite big as it strives to abstract away all of the more low-level stuff like HTTP requests, JSON parsing etc. 

The complete list of all currently available API calls is located here.

## User Management 

<img src="https://i.imgsafe.org/95a3d23a72.png">

**BiB** supports user- and group-based Access Control Lists. In current version only group-based ACLs are active but the technical capability to enforce more fine-grained access control is 
already available. Future versions will also include additional options for UI-based user rights management. Internally, **BiB** relies on Angular 2 Decorators to enforce restrictions on certain system tasks that can 
manipulate database and other vital data. 

## System Configuration 

Both the server and client use a file called config.json to (de)activate certain behaviors. This file is quite complex as it includes many different entries that deal with important aspects on both sides of the system.
For easier management and future development of **BiB** there exists a corresponding IConfig.ts interface that maps to all available properties from config.js.

The most frequently used options are:

| Option     | Type   | Description           | Example  |
| -------------|:----: |:-------------:| -----:|
| bib_server   | string  | DNS-entry of the backend | "localhost" |
| bib_server_port | number | Port number of the backend  |   10000 |
| bib_server_baseUrl | string | web app base path    |  "/bib" |
| bib_overdue_days | number | Maximum loan period in days | 14 |
| bib_localstorage | string  | Name of localStorage object | "bib-app" |
| bib_logon_mask_logo | string  | b64-encoded image for login | string with prepended `data:image/TYPE;base64,` |
| bib_use_fake_isbn_server | boolean | Fake WorldCat access | false |
| bib_datetime_format | string | Date format | "DD.MM.YYYY" |

## Internationalization

**BiB** is completely i18n-capable via language files that are located in the assets/i18n folder. Currently there are language files for these languages although only German and English are complely translated and othes simply fall back to English. 

    German
    English
    French
    Italian
    Russian
    Turkish


Any help regarding new languages or extending the existing ones is greatly appreciated.

<img src="https://i.imgsafe.org/95a1f41e3f.png">


## License 

MIT


