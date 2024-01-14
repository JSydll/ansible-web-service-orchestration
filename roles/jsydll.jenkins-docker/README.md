Jenkins with Docker (and Traefik)
=========

Ansible role installing the Docker setup for running Jenkins on a server.

Essentially a port to ansible from https://www.cloudbees.com/blog/how-to-install-and-run-jenkins-with-docker-compose.

Attention: Credentials must be created with `ssh-keygen -m PEM -t rsa -b 4096` (note the `-m PEM` option).
In general, compliance with https://github.com/jenkinsci/ssh-slaves-plugin/blob/main/doc/CONFIGURE.md#integration-with-ssh-credentials-plugin is needed.

After setting up Jenkins and the agent, the latter might require additional installation steps
to support building the projects at hand.

For configuring Jenkins, [this page](https://secops-sandbox-documentation.readthedocs.io/en/latest/jenkins_github_integration.html) could be helpful.

And to display the Jenkins Badge on GitHub [this page](https://www.vegait.rs/media-center/knowledge-base/how-to-display-jenkins-build-status-badge-on-github) shows how to configure Jenkins.

Requirements
------------

...

Role Variables
--------------

...

Dependencies
------------

- geerlingguy.docker
- jotbe.traefik-docker


Example Playbook
----------------

...

License
-------

MIT
