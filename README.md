# Hubz Scalable Airdrop System

This repository contains a **Scalable Airdrop System** for the TON blockchain, designed exclusively for **Hubz**. It enables efficient token distribution (Jettons) to users, allowing them to claim tokens seamlessly.

## Features

- **Efficient Token Distribution**: Utilizes a Merkle tree for scalability and cost-efficiency.
- **User-Friendly Claims**: Simplified claiming process for end-users.

## Getting Started

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/cumberlandlabs/hubz_airdrop.git
   cd hubz_airdrop
   ```

2. **Install Dependencies**:
   Use npm to install required dependencies:
   ```bash
   npm install
   ```

3. **Run the Airdrop Feature**:
   Use **NPX Blueprint** to compile and deploy the airdrop system:
   ```bash
   npx blueprint run
   ```

4. **Prepare Airdrop Entries**:
   Create a list of recipient addresses and token amounts. Convert these into a Merkle tree for efficient handling.

   Example:
   ```ts
   const entries = [
       { address: Address.parse('EQ...'), amount: toNano('100') },
       { address: Address.parse('EQ...'), amount: toNano('200') },
   ];
   const dict = generateEntriesDictionary(entries);
   const merkleRoot = BigInt('0x' + beginCell().storeDictDirect(dict).endCell().hash().toString('hex'));
   ```

5. **Deploy the Airdrop**:
   Deploy the contract using the `deployAirdrop.ts` script:
   ```ts
   await airdrop.sendDeploy(provider.sender(), toNano('0.05'), walletAddress);
   ```

6. **Claim Tokens**:
   Users can claim tokens by providing the Merkle proof via the `sendClaim` method.

   Example:
   ```ts
   await helper.sendClaim(0n, proof);
   ```

## Important Links

- **Hubz Official Website**: [https://hubz.io/](https://hubz.io/)
- **Hubz Support**: [https://t.me/hubz_support_bot](https://t.me/hubz_support_bot)
- **Hubz Documentation**: [https://resources.hubz.io/](https://resources.hubz.io/)
- **Hubz Announcements**: [https://t.me/Hubz_News](https://t.me/Hubz_News)

---