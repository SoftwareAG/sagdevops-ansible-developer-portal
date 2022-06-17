# sagdevops-ansible-developer-portal
ansible roles dedicated to the configuration of developer portal

Roles:
- developerportal-files-configurator
  - These are configuration tasks that modify the files on webMethods Developer Portal server(s) (and as such, these tasks must be run on the target servers)
- developerportal-rest-configurator
  - These are configuration tasks that strictly leverage the REST APIs provided by webMethods Developer Portal (and as such, these tasks can be run from anywhere with network access to the target webMethods Developer Portal REST endpoints)

**Note:**
For a sample Infrastructure-as-Code (IaC) project that leverages these roles, head on over to [webmethods-ansible-api-gateway](https://github.com/softwareag-government-solutions/webmethods-ansible-api-gateway), maintained by [SoftwareAG Government Solutions's](https://www.softwareaggov.com)

# Authors
Fabien Sanglier
- Emails: [@Software AG](mailto:fabien.sanglier@softwareag.com) [@Software AG Government Solutions](mailto:fabien.sanglier@softwareaggov.com)
- Github: 
  - [Fabien Sanglier @ SoftwareAG Government Solutions](https://github.com/fabien-sanglier-saggs)
  - [Fabien Sanglier](https://github.com/lanimall)

## Project dependencies:

Some of the tasks in these roles will have dependencies on tasks defined in [sagdevops-ansible-common](https://github.com/SoftwareAG/sagdevops-ansible-common)
As such, make sure to include sagdevops-ansible-common in your automation solution.

## Role: developerportal-files-configurator

Documentation Details TBD

## Role: developerportal-rest-configurator

Documentation Details TBD

## Using Containers

### Building the containers

To build containers for the configurators

First set some environment variables to specify the build arguments:

```
export REG=
export TAG=0.0.1
export SAGDEVOPS_BASE_ANSIBLE=${REG}sagdevops-ansible-common:0.0.1
```

Then, build the configurators by running:

```
docker build --rm -f Dockerfile.rest -t ${REG}developerportal-rest-configurator:${TAG} --build-arg BASE_ANSIBLE_IMAGE=${SAGDEVOPS_BASE_ANSIBLE} .

docker build --rm -f Dockerfile.files -t ${REG}developerportal-files-configurator:${TAG} --build-arg BASE_ANSIBLE_IMAGE=${SAGDEVOPS_BASE_ANSIBLE} .
```

This will create 2 containers:
 - ${REG}developerportal-rest-configurator:${TAG}
 - ${REG}developerportal-rest-configurator:${TAG}

### Testing validity of the containers

Test developerportal-rest-configurator:

```
docker run ${REG}developerportal-rest-configurator:${TAG} ping.yml
```

Test developerportal-files-configurator:

```
docker run ${REG}developerportal-files-configurator:${TAG} ping.yml
```

______________________
These tools are provided as-is and without warranty or support. They do not constitute part of the Software AG product suite. Users are free to use, fork and modify them, subject to the license agreement. While Software AG welcomes contributions, we cannot guarantee to include every contribution in the master project.
_____________
For more information you can Ask a Question in the [TECHcommunity Forums](http://tech.forums.softwareag.com/techjforum/forums/list.page?product=webmethods).

You can find additional information in the [Software AG TECHcommunity](http://techcommunity.softwareag.com/home/-/product/name/webmethods).
_____________
Contact us at [TECHcommunity](mailto:technologycommunity@softwareag.com?subject=Github/SoftwareAG) if you have any questions.
