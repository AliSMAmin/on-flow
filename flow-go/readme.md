Flow Go

Flow is a fast, secure, and developer-friendly blockchain built to support the next generation of games, apps and the digital assets that power them. Read more about it here.
Table of Contents

    Getting started
    Documentation
    Installation
        Clone Repository
        Install Dependencies
    Development Workflow
        Testing
        Building
        Local Network
        Code Generation

Getting started

    To install all dependencies and tools, see the project setup guide
    To dig into more documentation about Flow, see the documentation
    To learn how to contribute, see the contributing guide
    To see information on developing Flow, see the development workflow

Documentation

You can find an overview of the Flow architecture on the documentation website.

Development on Flow is divided into work streams. Each work stream has a home directory containing high-level documentation for the stream, as well as links to documentation for relevant components used by that work stream.

The following table lists all work streams and links to their home directory and documentation:
Work Stream 	Home directory
Access Node 	/cmd/access
Collection Node 	/cmd/collection
Consensus Node 	/cmd/consensus
Execution Node 	/cmd/execution
Verification Node 	/cmd/verification
Observer Service 	/cmd/observer
HotStuff 	/consensus/hotstuff
Storage 	/storage
Ledger 	/ledger
Networking 	/network
Cryptography 	/crypto
Installation
Clone Repository

    Clone this repository

    Clone this repository's submodules:

    git submodule update --init --recursive

Install Dependencies

    Install Go (Flow supports Go 1.18 and later)

    Install CMake, which is used for building the crypto library

    Install Docker, which is used for running a local network and integration tests

    Make sure the GOPATH and GOBIN environment variables are set, and GOBIN is added to your path:

    export GOPATH=$(go env GOPATH)
    export GOBIN=$GOPATH/bin
    export PATH=$PATH:$GOBIN

    Add these to your shell profile to persist them for future runs.

    Then, run the following command:

    make install-tools

At this point, you should be ready to build, test, and run Flow! tada

Note: Whenever the crypto module version imported by "go.mod" is updated to a version that was never locally imported before, the crypto dependency needs to be set-up. If not, you should notice errors about "relic" or "crypto". Run the following command to set-up the new module version:

make crypto_setup_gopath

Development Workflow
Testing

Flow has a unit test suite and an integration test suite. Unit tests for a module live within the module they are testing. Integration tests live in integration/tests.

Run the unit test suite:

make test

Run the integration test suite:

make integration-test

Building

The recommended way to build and run Flow for local development is using Docker.

Build a Docker image for all nodes:

make docker-build-flow

Build a Docker image for a particular node role (replace $ROLE with collection, consensus, etc.):

make docker-build-$ROLE

Local Network

A local version of the network can be run for manual testing and integration. See the Local Network Guide for instructions.
Code Generation

Generated code is kept up to date in the repository, so should be committed whenever it changes.

Run all code generators:

make generate

Generate protobuf stubs:

make generate-proto

Generate OpenAPI schema models:

make generate-openapi

Generate mocks used for unit tests:

make generate-mocks
