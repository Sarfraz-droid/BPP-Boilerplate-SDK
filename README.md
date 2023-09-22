# BeckN BPP Boilerplate UI + Backend SDK

## What is BeckN BPP Boilerplate UI + Beckend SDK?

The Boilerplate UI + Backend Framework project allows developers to quickly become beckn enabled and beckn protocol-based software quickly. The Backend Framework SDK gives the developer a defined structure to build beckn systems. 
Moreover, the project also includes a set of Fulfillment Applications and Admin UI connected with various BPPs.

## Getting Started

### Setup Instructions

- **Clone the repo**

  ```
    git clone <repo-link>
  ```

- **Installing Dependencies**

  - Run `make setup` to run the setup suite.
  - This will run the setup suite, install dependencies, build the sdk, and cli application.
  - After this, generate your sdk file and run the boilerplate.
    Example

  ```

  ✔ Enter the mongo uri … mongodb://localhost:27017/beckn
  ✔ Enter the gateway uri … https://gateway.becknprotocol.io/bg
  ✔ Enter the gateway register uri … https://registry.becknprotocol.io/subscribers
  ✔ Enter the subscribe uri … sarfraz-bpp-dsep
  ✔ Enter the app unique id … sarfraz-bpp-dsep-key
  ✔ Enter the app uri … https://sarfraz-bpp.loca.lt
  ✔ Enter the app public key … YcnZ8xyT2M2onkgI+t6W9Ct+6FnsBuiSCa8WqPDLy8k=
  ✔ Enter the app private key … SiVZmCtmzKdhZ3VUG5ONYKLDdtF1slRPEGZWHMS3DhthydnzHJPYzaieSAj63pb0K37oWewG6JIJrxao8MvLyQ==
  ✔ Enter the open api spec path … /home/sarfraz/coding/BPP-Boilerplate-SDK/apps/server/transaction.yaml

  ```

-

## Table of content:

- [Demo](#demo)
- [Pre-requisites](#pre-requisites)
- [Project Setup](#item-three)
- [Folder Structure](#folder-structure)
- [Project Architecture](#project-architecture)

### Demo

[Video Link](https://drive.google.com/drive/folders/1oq_WaSFB_w2BoajKSJiPsFr1_UCQ3f8X)

<a id="pre-requisites"></a>

### Pre-requisites

<table>
  <tr>
    <td>NodeJS</td>
    <td>>=16</td>
  </tr>
  <tr>
    <td>Redis</td>
    <td> <span/> </td>
  </tr>
  <tr>
    <td>MongoDB</td>
    <td> <span/> </td> 
  </tr>
</table>

<a id="project-setup"></a>

### Project Setup

#### Using Docker

**STEP 1: Run your docker containers**

- Simply run docker compose by running `docker-compose up`.
- The docker-compose file contains the following containers:
  - **sarfalam/simple-beckn-bap-ride-hailing:1:** BAP service based on simple-beckn (https://github.com/Sarfraz-droid/simple-beckn)
  - **sarfalam/bpp-boilerplate-ride-hailing:1.0.0:** This includes the boilerplate admin ui, server and android application.
  - **mongodb:** MongoDB Server
  - **redis:** Redis Server

**STEP 2: Exposing the ports**

- For the **BAPs,BPPs,Android and Admin UI** to interact you must expose the ports. For docker, run the following command on your machine.

```bash
make install
```

- Then expose the ports by running:

```bash
make expose
```

**STEP 3: Connecting to the APPs**

- Wait for a few minutes till all the containers are up and running.
- Check out [Connecting to Apps](#connecting-to-apps) section to connect to the apps.

#### Local Setup

- Setup the application by running `make setup`. This will setup all the necessary cli, sdk and configurations. Follow the prompts and generate your config.
- Run the application by running `make local-dev`. This will run the **Server**, **Admin UI** and the **Android Application**.
  **Alternatively,** you can run the **Server**, **Admin UI** and **Android Application** separately by running `make local-dev-server`, `make local-dev-admin` and `make local-dev-android` respectively.
- Check out [Connecting to Apps](#connecting-to-apps) section to connect to the apps.

<a id="connecting-to-apps"></a>

#### Connecting to Apps

- Then connect to the admin UI by visiting `http://localhost:4173`.
- BAP server is running at `http://localhost:3001`.
- BPP server is running at `http://localhost:4000` being the rest api and `http://localhost:4001` being the socket server.
- You can connect to the android application by running the android application on the [Expo App](https://expo.dev/). Once the app is installed, connect the app with your URL as `exp://YOUR-IPV4-ADDRESS:8081`.

<a id="folder-structure"></a>

### Folder Structure

```bash
├── apps/
│   ├── admin/ # Admin UI React App
│   ├── agent/ # Fulfillment Agent Application (React Native)
│   └── server/ # BPP Backend Server
│   └── webhook/ # BPP Webhook
├── packages/
│   ├── bpp-sdk/ # BPP SDK Library
│   └── shared-utils/ # Shared Utility Library
└── package.json
```

<a id="project-architecture"></a>

### Project Architecture

The workflow of the project goes as
![image](https://github.com/Sarfraz-droid/BPP-Boilerplate-SDK/assets/73013838/838a6642-9a14-4085-8b6b-fb2ff371a512)

The project utilizes Turbo Repo to manage multiple monorepos

#### BPP SDK

The BPP SDK includes a set of utilities and libraries to generate and build beckn-enabled bpp applications.
Technology Stack: **Node.JS, Express.JS, Typescript, Open API 3.0, Rollup, Mongoose**

#### BPP Server

The network-facing BPP Server application. Developed with the BPP SDK, the server interacts with the network and BAPs via Beckn Protocol.
Technology Stack: **Node.JS, Express.JS, Websockets(Socket.IO), Typescript, Open API 3.0**

#### Fulfillment UI Application

The fulfillment UI Application is an Android application to accepts orders from any connected client. For example, confirming the order requested by a client for a transit ticket.
Technology Stack: **React Native, WebSockets, Typescript**

### Admin UI

The Admin UI application includes a dashboard for all the BPPs and providers. This allows the admins to view the orders and connected admins, fulfillment apps, and BAPs. It also shows the certifications, BPP details, and network.
Technology Stack: **React, WebSockets, Typescript**
