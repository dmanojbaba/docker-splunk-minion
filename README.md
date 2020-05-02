# Docker Splunk Minion

This repository enables users to build and manage a [Splunk Enterprise](https://www.splunk.com/) sandbox on a Local Machine using Docker.

---

## Prerequisites:
* [Docker](https://www.docker.com/)

## Getting Started:
* Clone or download this repository
* Change current working directory to the cloned location
  * Example `cd docker-splunk-minion`
* As required, add/edit the conf files in the `sandbox-app` directory
* Run: `./minion run` to pull & run the latest `splunk/splunk` docker image
  * To run a [specific Splunk version](https://hub.docker.com/r/splunk/splunk/tags), run `./minion run [DOCKER_IMAGE_TAG]` [*e.g.: `./minion run 8.0`*]

## Next Steps:
* After starting Splunk, access the web interface using default credentials `admin:changeme` at http://localhost:8000/app/sandbox-app/
* After manually editing the objects via conf files in `sandbox-app` directory,
  * Restart Splunk using web interface server controls at http://localhost:8000/manager/system/control
  * Alternatively, restart the Splunk docker sandbox using `./minion restart` command
* To persistently save the required knowledge objects outside the Splunk docker sandbox, ensure the objects are saved in `sandbox-app` and Sharing permissions are set to App ["This app"] or Global ["All apps"]
  * See All configurations at http://localhost:8000/manager/sandbox-app/admin/directory
* To stop the Splunk docker sandbox and resume later, run: `./minion stop` and `./minion start` respectively
* Run: `./minion rm` to remove all indexed data, private objects, and objects saved in other apps
* Run: `./minion rmi` to remove the docker image
* As required, edit the `SPLUNK_PASSWORD`, `DOCKER_IMAGE_TAG`, and other variable values in the `minion` script file

## Usage:
```
./minion [option]
```

| Option | Description | Example |
|--------|-------------|---------|
| run [TAG] | Run the Splunk Image.<br/>If no tag is provided, `latest` tag is used. | `./minion run`<br/>`./minion run 7.3.5` |
| start | Start the Splunk instance on the docker sandbox | `./minion start` |
| stop | Stop the Splunk instance on the docker sandbox | `./minion stop` |
| restart | Stop and Start the Splunk instance on the docker sandbox | `./minion restart` |
| status | Status of the Splunk instance on the docker sandbox | `./minion status` |
| splunk [command] | Execute a Splunk command | `./minion splunk list monitor`<br/>`./minion splunk btool inputs list` |
| shell | Enter the interactive `bash` shell on the docker container | `./minion shell`<br/>`./minion bash` |
| exec [command] | Execute a command on the docker container | `./minion exec tail /opt/splunk/var/log/splunk/splunkd.log` |
| rm | Remove the docker container | `./minion rm`<br/>`./minion remove` |
| rmi [TAG] | Remove the docker image.<br/>If no tag is provided, `latest` tag is used. | `./minion rmi`<br/>`./minion rmi 7.3.5` |


---
## References:
* https://hub.docker.com/r/splunk/splunk
* https://github.com/splunk/docker-splunk
* https://www.splunk.com/en_us/blog/tips-and-tricks/hands-on-lab-sandboxing-with-splunk-with-docker.html

---
#### For bugs, enhancements, or other requests create an issue in this repository
---