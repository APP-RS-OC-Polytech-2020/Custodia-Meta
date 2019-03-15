# Custodia-Meta
Custodia-Meta

This repo in meant as a meta-repos for Custodia project. Custodia is kinda big project involving controlling a Robotino robot using a Raspberry pi ([Custodia-rpi](https://github.com/APP-RS-OC-Polytech-2020/custodia-rpi)) which uses a [Webcam](https://github.com/APP-RS-OC-Polytech-2020/JavaCamServer.git) and reports to a central server ([JavaRepeatServer](https://github.com/APP-RS-OC-Polytech-2020/JavaRepeatServer)), written in Java. This central server is also charged with relaying messages from various sensors ([Custodia-sensors](https://github.com/APP-RS-OC-Polytech-2020/custodia-sensors)) and a web interface ([Custodia-web](https://github.com/APP-RS-OC-Polytech-2020/custodia-web)).

It is meant to be used in conjunction with [meta](https://github.com/mateodelnorte/meta), a tool for checking out and keeping track of many different git Repositories.

# Installing this project

## 1. Grab projects
### 1.1 Install Meta

Go on [meta's repo](https://github.com/mateodelnorte/meta) and follow the instruction there. Basically, install nodeJs, install npm and run `npm i -g meta`

### 1.2 Grab projects using Meta

Launch your favorite console with node and meta installed, go to the folder where you want the project and run `meta git clone https://github.com/APP-RS-OC-Polytech-2020/Custodia-Meta.git`. Follow the prompts and Enjoy !

### 1.1 (alt) Checkout each project manually.

Open the [meta file](.meta) and do a `git clone` of each url under `"projects"`. You should get about the same result as doing it with meta.

## 2. Running the project
### 1.1 Pre-requisites
As this project is still under developpement, some part aren't standalone, at all. Basically, most of the project needs [JavaRepeatServer](https://github.com/APP-RS-OC-Polytech-2020/JavaRepeatServer) to work properly. The rest is more or less optional, although you'll definetly need [Custodia-web](https://github.com/APP-RS-OC-Polytech-2020/custodia-web) if you want any kind of interface.

#### JavaRepeatServer and Custodia-rpi
You'll want to make sure you have something that can compile and run Java apps. We used [Eclipse IDE](https://www.eclipse.org/ide/), and you may find some project files for this ide in the repos. You'll need it for the [Custodia-rpi](https://github.com/APP-RS-OC-Polytech-2020/custodia-rpi), [JavaRepeatServer](https://github.com/APP-RS-OC-Polytech-2020/JavaRepeatServer), and [Webcam](https://github.com/APP-RS-OC-Polytech-2020/JavaCamServer.git) projects.

#### Custodia-web
You'll also want to make sure you have something that can run PHP code and show webpages. Like a webserver. Or at least [grab and configure a simple PHP server](http://php.net/manual/en/features.commandline.webserver.php). We only had a PHP 4 server on hand, so you may find some deprecated code in the web repo, but it should run fine on modern PHP. You'll also want to get a MySQL DB running. It's optional, but recommended as some parts of the project ([Custodia-web](https://github.com/APP-RS-OC-Polytech-2020/custodia-web)) will not work without it.

#### Custodia-rpi (again)
*Hardware is important*, especially if you want to run [Custodia-rpi](https://github.com/APP-RS-OC-Polytech-2020/custodia-rpi), as it depends on a [Robotino robot](http://en.wikipedia.org/wiki/Robotino) and, to a lesser extent, a Raspberry pi (even though due to the nature of java, it'll run fine on a PC with almost any OS). You'll want to make sure you have your robotino properly configured to send and receive info from the API wrapper.

#### Custodia-sensors
You'll also need a bunch of hardware for [Custodia-sensors](https://github.com/APP-RS-OC-Polytech-2020/custodia-sensors). At least an ESP 8.266 Node MCU to run the code and some familiarity with arduino developement. You might want to get some of the sensors we had (laser, temp, gasses).

Once you have all of this, it gets easier.

### 1.2 Actually running the thing
We'll go on project by project.
> :warning: **NOTE:** This doc may not exactly follows the child repos. When in doubt **follow the README of the child repos** they're usually more up to date than this one.

#### 1.2.1 JavaRepeatServer
Import the project into your IDE or compile the classes under /src/. Run `main.java` and it should go on pretty smoothly.
> :information_source: You'll need this part for all other parts to work as intended. The rest is more or less optional

#### 1.2.2 Custodia-Web
Move the project files to the root of the web server. Run using `index.php`. If you have the pre-requisites, it should go down smoothly.
> :information_source: This part has the only human-facing interface.

#### 1.2.3 WebCam
Import the project into you IDE or compile the classes under /src/ or [grab one of the releases](https://github.com/APP-RS-OC-Polytech-2020/JavaCamServer/releases). Run using the jar (and read the help !) or using `main.java` (for full console support) or using `WebCamAPICameraStream.java` for more simple support.

> :information_source: You'll need a supported webcam for that. The code is pretty generic and should work with most USB webcam on windows and linux.

> :warning: Some IPs are hardcoded in. You'll want to edit them. They're in `WebCamAPICameraStream.java`

#### 1.2.4 Custodia-rpi
Import the project into your IDE or compile the classes. Make sure you have the dependencies for robotino-api as well as the java wrapper for it. And a robotino robot. Run using `Main.java`.

> :warning: IPs for robotino and server are hardcoded in. You'll have to edit them. They're in `Main.java`

#### 1.2.5 Custodia-sensors
Grab the project. Upload to ESP using your favorite method. Switch on ESP.
