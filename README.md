# Docker Splunk Minion

This repository enables Splunk Users to build and manage a Splunk Enterprise sandbox on a Local Machine using Docker.

---

## Prerequisites:
* Docker

## Run:
* Clone or download this repository
* Change current working directory to the cloned location
  * Example `cd docker-splunk-minion`
* As required, add/edit the conf files in the `sandbox-app` directory
* Run `./minion run` to pull & run the latest `splunk/splunk` docker image
  * To run a [specific version](https://hub.docker.com/r/splunk/splunk/tags), run `./minion run [DOCKER_IMAGE_TAG]` [*e.g.: `./minion run 8.0`*]
* To start, stop or restart the Splunk instance on the docker container, run `./minion start | stop | restart`
* To execute a Splunk command, run `./minion splunk [command]` [*e.g.: `./minion splunk list monitor`*]
* To enter the interactive `bash` shell on the docker container, run `./minion shell | bash`
* To execute a command on the docker container, run `./minion exec [command]` [*e.g.: `./minion exec tail /opt/splunk/var/log/splunk/splunkd.log`*]
* To remove the docker container, run `./minion remove | rm`
* As required, edit the `DOCKER_IMAGE_TAG`, `SPLUNK_PASSWORD`, and other variable values in the `minion` script file

## Usage:
* After starting Splunk, access the web interface using default credentials `admin:changeme` at http://localhost:8000/app/sandbox-app/
* After manually editing the objects via conf files in `sandbox-app` directory,
  * Restart Splunk using web interface server controls at http://localhost:8000/manager/system/control
  * Alternatively, restart the docker container using `./minion restart` command
* To persistently save the objects outside the docker container,
  * Ensure the objects are saved in `sandbox-app` and Sharing permissions are set to App ["This app"] or Global ["All apps"]
  * http://localhost:8000/manager/sandbox-app/admin/directory
* To stop the docker container and resume later, run `./minion stop` and `./minion start`
* Using `./minion remove | rm` will remove all indexed data, private objects, and objects saved in other apps

#### For bugs, enhancements, or other requests create an issue in this repository

---
Credits:
* https://hub.docker.com/r/splunk/splunk
* https://github.com/splunk/docker-splunk
* https://www.splunk.com/en_us/blog/tips-and-tricks/hands-on-lab-sandboxing-with-splunk-with-docker.html

---
