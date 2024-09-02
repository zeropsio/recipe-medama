# Zerops x Medama

[Medama](https://oss.medama.io/) Analytics is an open-source project dedicated to providing self-hostable, cookie-free website analytics. With a lightweight tracker of less than 1KB, it aims to offer useful analytics while prioritising user privacy.

Medama on Zerops is selfhosting binary running with database files on HA shared storage.

## Prerequisites

- Zerops account - [sign up here](https://app.zerops.io/registration)

## Deploy Medama to Zerops

Locate "Import project" in the menu top left corner and paste following yaml:

```
project:
  name: recipe-medama
services:
  - hostname: sharedstorage0
    type: shared-storage
    mode: HA
    priority: 10
  
  - hostname: app
    type: go@1
    enableSubdomainAccess: true
    buildFromGit: "https://github.com/zeropsio/recipe-medama"
    zeropsSetup: app
    priority: 1
    mount: 
      - sharedstorage0
```

## Login to Medama 
When deploy is complete, go to `recipe-medama` project detail and in the left menu locate `IP Addresses & Public Routing Overview`, where you can find a subdomain link to open Medama frontend.
Open it and make your first login into Medama as `admin` with password `CHANGE_ME_ON_FIRST_LOGIN` and enjoy :-)

## Tracking snippet 
How to embed Medama tracking snippet follow the instruction on [Medama Tracking snippet page](https://oss.medama.io/config/tracking-snippet).
