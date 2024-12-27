# Solana Governance Program Documentation

## Project Overview
This is a DAO governance program built on Solana that allows token holders to:
- Create and manage proposals
- Vote on proposals
- Execute approved proposals
- Manage token-weighted voting

## Important Addresses
1. Program ID: [REDACTED]
2. Governance Token: [REDACTED]
3. Token Account: [REDACTED]

## Program Features

### 1. Initialize DAO
- Creates a new DAO instance
- Sets minimum vote weight required
- Sets voting period duration
- Assigns governance token

### 2. Create Proposal
- Any user can create a proposal
- Requires title and description
- Automatically sets start/end time
- Tracks proposal number

### 3. Cast Vote
- Token holders can vote yes/no
- Vote weight based on token balance
- Prevents double voting
- Tracks vote counts

### 4. Execute Proposal
- Can execute after voting period ends
- Requires minimum yes votes
- Can only execute once
- Marks proposal as executed

## Account Structures

### DAO Account
- Authority: Pubkey
- Governance Token: Pubkey
- Min Vote Weight: u64
- Voting Period: i64
- Proposal Count: u64

### Proposal Account
- Proposer: Pubkey
- Title: String
- Description: String
- Yes Votes: u64
- No Votes: u64
- Executed: bool
- Proposal Number: u64
- Start Time: i64
- End Time: i64

### Vote Record Account
- Has Voted: bool
- Vote: bool

## Error Codes
1. VotingEnded - When trying to vote after period ends
2. AlreadyVoted - When voter tries to vote twice
3. VoteOverflow - When vote calculation overflows
4. VotingNotEnded - When trying to execute before period ends
5. ProposalNotApproved - When yes votes < min_vote_weight
6. ProposalAlreadyExecuted - When trying to execute twice

## Dependencies
- anchor-lang = "0.27.0"
- anchor-spl = "0.27.0"
- solana-program = "1.14.17"

## Development Setup
1. Install Solana CLI (v1.14.17)
2. Install Anchor CLI (v0.27.0)
3. Install Rust and Cargo
4. Configure Solana for localnet development

## Build Instructions
1. Clone repository
2. Install dependencies
3. Build program: `cargo build-sbf`
4. Deploy program: `solana program deploy <program.so>`

## Testing
Run tests with: `anchor test`

## Frontend Integration
The program can be integrated with any frontend using:
1. @solana/web3.js
2. @project-serum/anchor
3. @solana/wallet-adapter-react

## Security Considerations
1. Token-weighted voting system
2. Vote record tracking to prevent double voting
3. Timestamp-based voting periods
4. Safe math operations for vote counting

## Known Issues
1. Build system compatibility issues on some systems
2. Local validator setup issues on some macOS versions

## Next Steps
1. Frontend development
2. Additional governance features
3. Security audits
4. Community testing

## Support
For technical support or questions, please create an issue in the repository.

## License
This project is open source and available under the MIT license. 
