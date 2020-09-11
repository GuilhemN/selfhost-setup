# The setup I use on my own server to self host several services

## Introduction

I wanted to get rid of several third-party services so I started to self host some of them:

- Nextcloud to have a self hosted drive (with end-to-end encryption) and to manage my RSS feeds through Nextcloud News
- Etesync to sync my calendar and contacts (with end-to-end encryption)
- RSS-Bridge to fetch public news from Facebook without having an account

I use Docker in order to simplify the maintenance of the services I self host and to isolate them.

The different apps are executed behind a nginx reverse proxy (launched using `docker-compose up -d` in the root folder) which automatically creates Let's Encrypt
certificates and renew them.

Each app is then launched separately using `docker up -d` in their folder.

## Installation

You should first install Docker (see https://docs.docker.com/get-docker/) and Docker Compose (see https://docs.docker.com/compose/install/).

Then clone this repository and update the secrets and the domain names in each `apps/*/docker-compose.yml`.

You will then have to create a Docker network to allow the different apps to communicate with the nginx reverse proxy: `docker network create nginx-proxy`.

Finally, launch the different components of this repository using `docker-compose up -d` in each directory.
