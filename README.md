# The setup I use on my own server to self host several services

## Introduction

I use Docker in order to simplify the maintenance of these services and to isolate them.

The different apps are executed behind a nginx reverse proxy (launched using `docker-compose up -d` in the root folder) which automatically creates Let's Encrypt
certificates and renew them.

Each app is then launched separately using `docker up -d` in their folder.

## Installation

You should first install Docker (see https://docs.docker.com/get-docker/) and Docker Compose (see https://docs.docker.com/compose/install/).

Then clone this repository, update the secrets and the domain names in each `apps/*/docker-compose.yml` before launching the different
components of this repository using `docker-compose up -d` in each directory.
