# DroneForce

DroneForce is a decentralized drone task management system that connects drone operators with clients needing drone services. The platform uses blockchain technology to ensure secure, transparent transactions and task verification.

## Architecture

The system is composed of five interconnected repositories, each serving a specific function in the overall workflow:

### 1. Edge Repo (Drone/Edge AI)

Responsible for drone task execution and log management:

- **Execute Drone Task**: Drones perform tasks based on specified parameters (location, altitude, etc.)
- **Generate Logs**: Creates comprehensive logs including mission status, sensor data, and captured images
- **Push Logs to Backend**: Automatically uploads logs to the backend for validation (with manual upload option if needed)

### 2. Backend Repo (Backend Services)

Handles log validation and permanent storage:

- **Validate Task Logs**: Ensures uploaded logs meet completion criteria
- **Upload Logs to Arweave**: Transfers validated logs to Arweave for permanent, decentralized storage
- **Task Status Update**: Updates task status on the smart contract after validation

### 3. Functions Repo (Firebase Functions)

Contains cloud functions to manage task verification and background processes:

- **Task Verification**: Validates uploaded log files against required criteria
- **Log Upload to Arweave**: Handles permanent storage of validated logs
- **Task Status Update**: Updates smart contract with verification status
- **Escrow Release**: Triggers payment release to operators upon successful verification

### 4. App Repo (React Web App)

Provides the user interface for all system interactions:

- **Task Creation** (Issuer): Interface for creating tasks and locking funds in escrow
- **Task Acceptance** (Operator): Allows operators to browse and accept available tasks
- **Log Upload** (Operator): Manual upload option for logs if automated system fails
- **Task Verification**: Displays real-time task status updates
- **Payment Withdrawal**: Interface for operators to withdraw completed task payments

### 5. Contracts Repo (Solana Smart Contracts)

Manages blockchain interactions for secure payments and task tracking:

- **Initialize Escrow**: Locks client funds when tasks are created
- **Accept Payment**: Releases funds to operators after verification
- **Task State Management**: Tracks task lifecycle (created → accepted → completed → verified)
- **Escrow Cancellation**: Allows fund reclamation if tasks are canceled

The escrow implementation is based on the [Non-Custodial Escrow example from Solana Anchor docs](https://examples.anchor-lang.com/docs/non-custodial-escrow).

## System Workflow

1. **Task Creation**: Client creates a task via the App, locking payment in escrow through the smart contract
2. **Task Acceptance**: Drone operator accepts the task, with funds remaining in escrow
3. **Task Execution**: Edge system directs drone execution and log generation
4. **Log Submission**: Logs are automatically (or manually) uploaded to the backend
5. **Validation**: Backend validates logs and uploads them to Arweave
6. **Verification**: Firebase functions verify task completion and update the smart contract
7. **Payment**: Smart contract releases escrow payment to the operator
8. **Withdrawal**: Operator withdraws payment through the App interface

## Getting Started

*Instructions for setup, installation, and configuration will be added as repositories are integrated.*

## Development

DroneForce is structured as a monorepo with submodules for each component:

- Edge (Drone/Edge AI)
- Backend Services
- Firebase Functions
- React Web App
- Solana Smart Contracts

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Contact

- [AdityaMulgundkar](https://github.com/AdityaMulgundkar)
- [munjaal7](https://github.com/munjaal7)
