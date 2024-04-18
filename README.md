# oatpp-template

Starter project of oat++ (AKA oatpp) application. Based on oatpp Async API.

See more:

-   [Oat++ Website](https://oatpp.io/)
-   [Oat++ Github Repository](https://github.com/oatpp/oatpp)
-   [Get Started](https://oatpp.io/docs/start)

## Note

Async API suits best for services dedicated to a single type of tasks that run at high concurrency levels.
Example:

-   Simultanious download of multiple files.
-   Streaming to large number of clients (1K or more).
-   Chats.

For all other purposes use [Simple API](https://github.com/oatpp/oatpp-starter).

## Before you start

Read:

-   [Simple API vs Async API](https://oatpp.io/docs/simple-vs-async/)
-   [Async](https://oatpp.io/docs/async/)
-   [Oatpp-Coroutines](https://oatpp.io/docs/oatpp-coroutines/)
-   [ENDPOINT_ASYNC](https://oatpp.io/docs/components/api-controller/#endpoint-async-specifics)

## Overview

### Project layout

```
|- CMakeLists.txt                        // projects CMakeLists.txt
|- src/
|    |
|    |- controller/                      // Folder containing UserController where all endpoints are declared
|    |- dto/                             // DTOs are declared here
|    |- AppComponent.hpp                 // Service config
|    |- App.cpp                          // main() is here
|
|- test/                                 // test folder
|- utility/install-oatpp-modules.sh      // utility script to install required oatpp-modules.
|- docker-compose-dev.yml                // docker compose file for development
|- docker-compose-test.yml               // docker compose file for testing
|- Dockerfile.build                            // Dockerfile for building the project
```

---

### Build and Run

#### Using CMake

**Requires**

-   `oatpp` module installed. You may run `utility/install-oatpp-modules.sh`
    script to install required oatpp modules.

```
mkdir build && cd build
cmake ..
make
./App-exe

```

#### In Docker

to build and run the project in docker container in development mode use the following command:

```
docker compose -f docker-compose-dev.yml up --build
```

and to run the tests in the container use the following command:

```
docker compose -f docker-compose-test.yml up --build
```

### Access the API

You can access the API at [http://0.0.0.0:3000](http://0.0.0.0:3000)
