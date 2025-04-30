# ShieldStack - Decentralized Insurance Smart Contract

A smart contract implementing a robust **decentralized insurance protocol** on the Stacks blockchain. It supports:

- Multi-tier insurance policies
- Risk-based premium pricing
- STX staking for users
- Smart claim handling and verification
- Risk profiling and rewards

---

## 📑 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Policy Tiers](#policy-tiers)
- [Data Structures](#data-structures)
- [Public Functions](#public-functions)
- [Private & Read-only Functions](#private--read-only-functions)
- [Error Codes](#error-codes)
- [Constants](#constants)
- [Installation & Deployment](#installation--deployment)
- [Security Considerations](#security-considerations)
- [License](#license)

---

## 🧭 Overview

This smart contract simulates a decentralized insurance marketplace where users can:

- Purchase insurance policies based on tier, risk, and stake
- File and resolve claims
- Earn staking rewards
- Be scored and managed based on historical behavior

Admins (contract owner) can initialize tiers, process claims, and update key parameters.

---

## ✅ Features

- 📦 **Multi-tier Policy System** (Basic, Premium, Elite)
- 🧠 **Risk-based Premium Calculation**
- 🔐 **Staking Integration** with rewards and lockup
- 📋 **Claim Filing & Resolution** with cooldown
- 📉 **Dynamic Risk Assessment**
- ⚖️ **Configurable Admin Controls**

---

## 🏷️ Policy Tiers

Initialized using `initialize-policy-tiers`, this contract supports:

| Tier     | Multiplier | Discount | Min Stake |
|----------|------------|----------|-----------|
| BASIC    | 1×         | 0%       | 1 STX     |
| PREMIUM  | 2×         | 10%      | 2 STX     |
| ELITE    | 3×         | 20%      | 3 STX     |

---

## 🧮 Data Structures

### 🔐 `insurance-policies`
Stores individual insurance policies.

### 📝 `insurance-claims`
Maps policyholder and claim ID to claim metadata.

### 💰 `staker-info`
Tracks staked STX and lock/reward periods.

### 📊 `risk-profiles`
Holds user risk-related data for premium calculations.

### 🎚️ `policy-tiers`
Tier metadata used for calculations.

---

## 🔧 Public Functions

### 🏁 Initialization

- `initialize-policy-tiers`: Admin initializes tiers.

### 💼 Policy Management

- `purchase-advanced-policy`: Buy a policy (tier, coverage, stake, duration).
- `get-insurance-policy`: View your policy.

### 📤 Claim System

- `submit-enhanced-claim`: File a claim with evidence.
- `process-claim`: Admin approves/rejects claims.

### 💎 Staking

- `stake-tokens`: Stake STX for policy eligibility/rewards.
- `claim-staking-rewards`: Withdraw staking rewards post lock-period.

### ⚙️ Admin Controls

- `update-protocol-parameters`: Set base premium, ceiling, risk threshold.
- `transfer-ownership`: Transfer contract ownership.

---

## 🧪 Private & Read-only Functions

### 🔐 Private

- `verify-policy-active`: Checks if a policy is active.
- `calculate-risk-score`: Calculates user-specific risk score.

### 📖 Read-only

- `get-claim-details`: Retrieve specific claim data.
- `get-risk-profile`: View user risk profile.
- `calculate-premiums`: Compute premiums based on tier, risk, and coverage.

---

## ❗ Error Codes

| Code | Name                  | Description                               |
|------|-----------------------|-------------------------------------------|
| u1   | ERR-UNAUTHORIZED      | Caller is not contract owner              |
| u2   | ERR-NO-POLICY-EXISTS  | No policy found for caller                |
| u3   | ERR-FUNDS-INSUFFICIENT| Not enough STX sent                       |
| u4   | ERR-INVALID-PARAMETERS| Provided values are invalid               |
| u5   | ERR-POLICY-TERMINATED | Policy expired or inactive                |
| u6   | ERR-DUPLICATE-CLAIM   | Repeated claim detected                   |
| u7   | ERR-INVALID-CLAIM-DATA| Missing/invalid claim fields              |
| u8   | ERR-STAKE-TOO-LOW     | Not enough tokens staked                  |
| u9   | ERR-COOLDOWN-ACTIVE   | Claim/stake cooldown period active        |
| u10  | ERR-RISK-SCORE-HIGH   | Risk score too high for policy approval   |
| u11  | ERR-MAX-COVERAGE-EXCEEDED | Requested coverage exceeds limit      |

---

## 📐 Constants

| Constant                  | Value     | Description                           |
|---------------------------|-----------|---------------------------------------|
| `RISK-THRESHOLD`          | 75        | Max allowed risk score for policy     |
| `MIN-STAKE-AMOUNT`        | 1,000,000 | Minimum stake in micro-STX            |
| `CLAIM-COOLDOWN-PERIOD`   | 144       | Blocks before another claim (1 day)   |
| `MAX-COVERAGE-MULTIPLIER` | 5         | Max multiplier for policy coverage    |

---

## 🚀 Installation & Deployment

This contract is written in [Clarity](https://docs.stacks.co/docs/write-smart-contracts/clarity-overview). To deploy:

1. Install [Clarinet](https://docs.stacks.co/docs/clarity/tools/clarinet).
2. Run `clarinet check` to ensure syntax validity.
3. Use `clarinet deploy` or deploy via the [Stacks Explorer](https://explorer.stacks.co/).

---

## 🛡️ Security Considerations

- Ensure off-chain risk data is trustlessly verified.
- Staking lock durations prevent flash behavior.
- Admin functions should be secured through multi-sig or DAO.

---
