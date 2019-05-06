# Custodia-Meta
Custodia-Meta

This repo in meant as a meta-repos for Custodia project. Custodia is kinda big project involving controlling a Robotino robot using a Raspberry pi ([Custodia-rpi]) which uses a Webcam ([JavaCamServer]) and reports to a central server ([JavaRepeatServer]), written in Java. This central server is also charged with relaying messages from various sensors ([Custodia-sensors]) and a web interface ([Custodia-web]).

It is meant to be used in conjunction with [meta], a tool for checking out and keeping track of many different git Repositories.

[JavaCamServer]:https://github.com/APP-RS-OC-Polytech-2020/JavaCamServer
[Custodia-rpi]:https://github.com/APP-RS-OC-Polytech-2020/custodia-rpi
[JavaRepeatServer]:https://github.com/APP-RS-OC-Polytech-2020/JavaRepeatServer
[Custodia-sensors]:https://github.com/APP-RS-OC-Polytech-2020/custodia-sensors
[Custodia-web]:https://github.com/APP-RS-OC-Polytech-2020/custodia-web
[meta]:https://github.com/mateodelnorte/meta


# Installing this project

## 1. Grab projects
### 1.1 The Meta Way
#### 1.1.1 Install Meta

Go on [meta's repo](https://github.com/mateodelnorte/meta) and follow the instruction there. Basically, install nodeJs, install npm and run `npm i -g meta`

#### 1.1.2 Grab projects using Meta

Launch your favorite console with node and meta installed, go to the folder where you want the project and run `meta git clone https://github.com/APP-RS-OC-Polytech-2020/Custodia-Meta.git`. Follow the prompts and Enjoy !

### 1.1 (alt) The manual way

Open the [meta file](.meta) and do a `git clone` of each url under `"projects"`. You should get about the same result as doing it with meta.

## 2. Running the project
### 1.1 Pre-requisites
As this project is still under developpement, some part aren't standalone, at all. Basically, most of the project needs [JavaRepeatServer] (and thus, a JVM of your choice) to work properly. The rest is more or less optional, although you'll definetly need [Custodia-web] if you want any kind of human interface.

#### Custodia-rpi
You'll want to make sure you have something that can compile and run Java apps. We used [Eclipse IDE](https://www.eclipse.org/ide/), and you may find some project files for this ide in the repos. You'll need it for the [Custodia-rpi] project.

Please note that *Hardware is important*, especially if you want to run [Custodia-rpi], as it depends on a [Robotino robot][2] and, to a lesser extent, a Raspberry pi (even though due to the nature of java, it'll run fine on a PC with almost any OS). You'll want to make sure you have your robotino properly configured to send and receive info from the API wrapper.

[2]:http://en.wikipedia.org/wiki/Robotino

#### Custodia-web
You'll also want to make sure you have something that can run PHP code and show webpages. Like a webserver. Or at least [grab and configure a simple PHP server][1]. We only had a PHP 4 server on hand, so you may find some deprecated code in the web repo, but it should run fine on modern PHP. You'll also want to get a MySQL DB running. It's optional, but recommended as some parts of the project ([Custodia-web]) will not work without it.

[1]:http://php.net/manual/en/features.commandline.webserver.php

#### Custodia-sensors
You'll also need a bunch of hardware for [Custodia-sensors]. At least an ESP 8.266 Node MCU to run the code and some familiarity with arduino developement. You might want to get some of the sensors we had (laser, temp, gasses).

Once you have all of this, it gets easier.

### 1.2 Actually running the thing
We'll go on project by project.

> :warning: **NOTE:** This doc may not exactly follows the child repos. When in doubt **follow the README of the child repos** they're usually more up to date than this one.

#### 1.2.1 JavaRepeatServer
[Grab one of the releases][JavaRepeatServerReleases] and run in your favorite console. If in doubt run with `-help`.
Or go the long way and import the project into your IDE or compile the classes under /src/, runnable class is `main.java`.

> :information_source: You'll need this part for all other parts to work as intended. The rest is more or less optional

[JavaRepeatServerReleases]:https://github.com/APP-RS-OC-Polytech-2020/JavaRepeatServer/releases

#### 1.2.2 Custodia-Web
Move the project files to the root of the web server. Run using `index.php`. If you have the pre-requisites, it should go down smoothly.

> :information_source: This part has the only human-facing interface.

#### 1.2.3 WebCam
[Grab one of the releases][JavaCamReleases] and run using the jar (if unsure, run with `-help`, it'll tell you what it needs). Or you can go the long way and import the project into you IDE or compile the classes under /src/. Runnable classes are `main.java` for full console support or `WebCamAPICameraStream.java` for simplier support.

[JavaCamReleases]:https://github.com/APP-RS-OC-Polytech-2020/JavaCamServer/releases

> :information_source: You'll need a supported webcam for that. The code is pretty generic and should work with most USB webcam on windows and linux.

> :warning: Some IPs are hardcoded in if you run without console support. You'll want to edit them. They're in `WebCamAPICameraStream.java`

#### 1.2.4 Custodia-rpi
Import the project into your IDE or compile the classes. Make sure you have the dependencies for robotino-api as well as the java wrapper for it. And a robotino robot. Run using `Main.java`.

> :warning: IPs for robotino and server are hardcoded in. You'll have to edit them. They're in `Main.java`

#### 1.2.5 Custodia-sensors
Grab the project. Change wifi infos to your liking inside the code. Upload to ESP using your favorite method. Switch on ESP.
