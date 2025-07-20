# CivicTrack Smart Contract

CivicTrack is a decentralized civic issue reporting system built on the Stacks blockchain using Clarity smart contracts. It enables users to submit, track, and resolve civic issues in a transparent and tamper-proof manner.

## Features

 **Submit Issues:** Users can report civic issues with a type and location.
 **Track Issues:** Each issue is stored with a unique ID, reporter, status, and timestamp.
 **Resolve Issues:** Only the contract owner can resolve (close) issues.
 **Query Issues:** Retrieve issue details and the total number of issues.

## Data Structures

### Issue Map

| Field        | Type               | Description                  |
|--------------|--------------------|------------------------------|
| `id`         | `uint`             | Unique issue identifier      |
| `reporter`   | `principal`        | Address of the reporter      |
| `issue-type` | `string-ascii(30)` | Type/category of the issue   |
| `location`   | `string-ascii(50)` | Location description         |
| `status`     | `string-ascii(10)` | "OPEN" or "CLOSED"           |
| `timestamp`  | `uint`             | Block height when submitted  |

## Smart Contract Functions

### Public Functions

- `submit-issue(issue-type, location)`  
  Submit a new civic issue. Returns the new issue ID on success.

- `resolve-issue(issue-id)`  
  Resolve (close) an existing issue. Only the contract owner can call this.

### Read-Only Functions

- `get-issue(issue-id)`  
  Returns the details of a specific issue.

- `get-issue-count()`  
  Returns the total number of issues submitted.

## Error Codes

- `u403`: Invalid input (string too long or empty)
- `"UNAUTHORIZED"`: Only contract owner can resolve issues
- `"INVALID_ISSUE_ID"`: Issue ID does not exist
- `"ISSUE_NOT_FOUND"`: Issue not found in the map

## Getting Started

### Prerequisites

- [Clarity Language](https://docs.stacks.co/write-smart-contracts/clarity-lang)
- [Clarinet](https://docs.hiro.so/clarinet/get-started) for local development and testing

### Setup

1. Clone the repository:
    ```sh
    git clone https://github.com/yourusername/CivicTrack.git
    cd CivicTrack
    ```
2. Install dependencies and tools as needed.
3. Run tests:
    ```sh
    clarinet test
    ```

## Security

- Only the contract owner can resolve issues.
- Input validation prevents malformed or oversized data.
