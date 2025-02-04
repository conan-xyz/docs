---
sidebar_position: 1
---

# Introduction

This data pool validates and archives state-sync snapshots from dYdX and makes them permanently
available with Arweave and Bundlr.

## Overview

- **Runtime**: @kyvejs/tendermint-ssync
- **Data Source**: KSYNC (over serve-snapshots)
- **Data**: state-sync snapshots every 5,000 blocks from genesis ongoing
- **Storage Provider**: Bundlr
- **Networks**
  - [Kaon](https://app.kaon.kyve.network/#/pools/9) (Pool Id: 9)
  - [Korellia](https://app.korellia.kyve.network/#/pools/43) (Pool Id: 43)
- **Min Hardware Requirements**
  - 4 or more physical CPU cores
  - 32 GB RAM
  - 150 GB DISK
  - 100mbps network bandwidth

## General Setup

If you want to participate in the dYdX // State-Sync pool you will have to run KSYNC with a set up dYdX node which will act as the
data source for the KYVE protocol validator.

This is required because KSYNC enables the requesting of deterministic state-sync snapshots in order to validate
and archive them. Therefore, KSYNC is using already validated dYdX data of the [dYdX pool](https://app.kaon.kyve.network/#/pools/6)
to feed the node with blocks and serves the created snapshots through an implemented server. With that setup, a user who wants to join this pool first has to sync
his dYdX node with KSYNC to the current height of the latest created snapshot and then start the
actual KYVE protocol validator.

This architecture diagram summarizes the setup of the dYdX // State-Sync integration on KYVE:

<p align="center">
  <img width="90%" src="/img/tendermint-ssync-archway.png" />
</p>

Here, the tendermint-ssync runtime is responsible for communicating with KSYNC, and forwarding the data to the KYVE core protocol. The KYVE core then handles the communication with the pool. This entire process (yellow) is the KYVE protocol validator. The resulting
data are the state-sync snapshots from the tendermint application - validated and permanently stored on a storage provider like Arweave.

## Goal

The goal of this pool is to validate and archive state-sync snapshots from dYdX permanently and decentralized. With this
data, we want to make it possible for other nodes to state-sync the data from KYVE, making expensive archival nodes
on dYdX obsolete in the long run. More information on how to perform state-sync with KYVE visit the documentation about
KSYNC [here](https://github.com/KYVENetwork/ksync).
KSYNC [here](https://github.com/KYVENetwork/ksync).
