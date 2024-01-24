# Pet Paws Guard

<img src="/ref/logo.png" align="right" width="210">

> Pet project for implementation of authorization gRPC service


[![GitHub go.mod Go version of a Go
module](https://img.shields.io/github/go-mod/go-version/waffle-frame/PetPawsGuard)](https://github.com/gomods/athens)
[![wakatime](https://wakatime.com/badge/user/ec493241-c2a0-40a9-8ff1-637bdb54b2f1/project/018d35f3-8797-4caa-bcfa-2bcac96acca2.svg)](https://wakatime.com/badge/user/ec493241-c2a0-40a9-8ff1-637bdb54b2f1/project/018d35f3-8797-4caa-bcfa-2bcac96acca2)

The project provides for the implementation of **gRPC** authorization in the future. Golang programming. This service is intended for the presentation and demonstration of vozmoznostei gRPC in the context of authentication and authorization by police

The main functionality of the project includes:

   1. Creation and management of users: registration, authentication, authorization password change and other operations
   2. Using the gRPC protocol for data exchange between client and server
   3. Working with access tokens and ensuring data security

---

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=10 orderedList=false} -->

<!-- code_chunk_output -->

1. [Pet Paws Guard](#pet-paws-guard)
   1. [Project Navigation](#project-navigation)
   2. [Installation](#installation)
      1. [Step 1. Check dependencies](#step-1-check-dependencies)
      2. [Step 2. Setting up the environment](#step-2-setting-up-the-environment)
         1. [2.1 Database creation](#21-database-creation)
         2. [2.2 Сonfiguration file setup](#22-сonfiguration-file-setup)
         3. [2.3 Swagger setup (Option)](#23-swagger-setup-option)
   3. [Run](#run)

<!-- /code_chunk_output -->

## Project Navigation

| Name           | Link                     |
| -------------- | ------------------------ |
| Source Docs    | <https://grpc.io/>       |

## Installation

### Step 1. Check dependencies

Clone project from GitHub:

```bash
git clone https://github.com/waffle-frame/clean-architecture-template.git
cd clean-architecture-template
```

Before running or building a project, make sure that all the necessary dependencies are installed on your OS.
This will also install the dependencies required by the golong application and install them if necessary.

To find out information about it, you can use the command:

```bash
make check-dependencies
```

**Note**: To add one or more applications to the list of dependencies, you will need to edit the `DEPENDENCIES` variable in the `Makefile`

Example:

```makefile
# Project dependencies
DEPENDENCIES = Golang="go version" \
                Keycloak="docker exec 1ca7b3a28abb cat /opt/keycloak/version.txt" \
                ...
```

In this example I accessed the docker image and got the keycloak version

### Step 2. Setting up the environment

#### 2.1 Database creation

```bash
sudo -u postgres psql -c 'CREATE DATABASE pet_paws_guard;'
```

#### 2.2 Сonfiguration file setup

An instance of the config file is located along the [path](ref/example-config.json).
You can supplement it with your own data. Also, in order for you to be able to use the configurations in the application, you need to add an identical structure in [config.go](pkg/config/module.go) file.

If successful, the `ImportConfigs` function will return your entry in the content.

**Note**: If you don't want to populate the config file, you can use the instance using the following command:

```bash
cp ref/example-config.json config.json
```

#### 2.3 Swagger setup (Option)

For the swagger to work properly, you need to replace the `{{}}` constructs in the [swagger.go](pkg/docs/swagger.go) file.
The names of the variables speak for themselves, so there is no need to explain the meaning of the variables.

To apply the changes, you need to run the command:

```bash
make docs
```

## Run

To run in development mode, use the command:

```bash
make run
```

To build the application, use the command:

```bash
make
# or
make build
```

> The assembly contains a dependency check, the generation of a swagger file and the assembly itself
> The binary file will be located on the path ./build/app

---
