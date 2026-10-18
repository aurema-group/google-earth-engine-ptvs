# google-earth-engine-ptvs
Confidential geospatial oracle bridge connecting Google Earth Engine with the Prop Trust Verified Standard (PTVS v1.0) and ERC-3643 for MiCA-compliant Real World Asset (RWA) verification.
# Google Earth Engine - PTVS Confidential Oracle Bridge

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Standard](https://img.shields.io/badge/PTVS-v1.0-blue.svg)](https://proptrustverified.com)
[![Compliance](https://img.shields.io/badge/Compliance-MiCA_eIDAS_2.0-green.svg)](https://forensics-oracle.org)

## Overview

The **Google Earth Engine - PTVS Bridge** is an open-source reference implementation of a **Physical Forensic Oracle (PFO)**. It is designed to bridge remote sensing geospatial data with on-chain identity and compliance layers (`ERC-3643 / ONCHAINID`).

This module enables real-time, tamper-proof verification of Real-World Asset (RWA) physical parameters—such as land surface area, agricultural yield, structural footprint changes, or environmental risk metrics. It achieves this by fetching data securely from **Google Earth Engine (GEE)**, processing it within a **Google Cloud Confidential Space**, and injecting cryptographically signed verifiable claims directly via the `PTVSClaimInjector.sol` smart contract.

---

## Architecture Flow

1. **Spatial Query:** The off-chain oracle queries Google Earth Engine APIs for historical and real-time geospatial telemetry of the target asset parcel.
2. **Confidential Computation:** Data is processed within a secure Google Cloud Confidential VM to eliminate infrastructure operator interference and guarantee data integrity.
3. **Forensic Signing:** The computed metrics are bundled with an eIDAS 2.0-compliant cryptographic signature and hashed (SHA-256).
4. **On-Chain Injection:** The signed verifiable claim is pushed to the blockchain via `PTVSClaimInjector.sol`, updating the asset's *Prudential Risk Rating (PRRB)* in real-time.

---

## Installation & Quick Start

### Prerequisites
* Python 3.10+
* Node.js v18+ & Hardhat
* Google Earth Engine Python API credentials (`ee.Initialize()`)
* Google Cloud Confidential VM environment (recommended for production nodes)

### 1. Clone the repository
```bash
git clone https://github.com/aurema-group/google-earth-engine-ptvs.git
cd google-earth-engine-ptvs
