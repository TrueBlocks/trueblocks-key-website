---
# Banner
banner:
  title: "Everything that ever happened anywhere on the chain"
  content: "Get a complete historical list of appearances (block number, transaction id) for any Ethereum address"
  button:
    enable: true
    label: "Try on QuickNode Marketplace"
    link: ""

# Features
features:
  - title: "Appearance Index API"
    content: "A single API endpoint returns significantly more appearances (block number, transaction ID) than other indexers. Includes:"
    bulletpoints:
      - "regular transactions"
      - "internal transactions"
      - "logs"
      - "token transfers"
      - "withdrawals"
      - "mining and uncle rewards"
      - "and more..."
    footer: "The API can also return number of appearances (i.e., count) for any Ethereum address."
    button:
      enable: true
      label: "Read docs"
      link: "/docs/appearance/"

  - title: "On the roadmap"
    content: ""
    bulletpoints:
      - "**Appearance Index API:** we're adding additional endpoints here including date and time queries and deeper analysis of an address's history (age, first appearance, etc.)"
      - "**Neighbors API:** Given any Ethereum address, this endpoint will return a list of all other addresses that appeared in the same transactions as the given address. If one were to ever solve the Sybil problem, the solution would start with a list of neighbors. Neighbor addresses are called neighbors because they live on the same block."
      - "**The Unchained Index API:** The [Unchained Index](https://trueblocks.io/papers/2023/specification-for-the-unchained-index-v2.0.0-release.pdf) is a novel way to distribute immutable databases such as our Appearance Index using IPFS. This endpoint will return a list of IPFS hashes for the portions of the index relevant to a given address. End uers may download these portions making it impossible for anyone (even us) to censor your access later."
      - "**The FourByte API:** Given a collection of `n` function names and `m` function signatures, this API generates `n x m` fourbyte signatures. When coupled with a frequency tag garnered from on-chain data, this allows 3rd party applications to more easily decode call data and event topics without the need for hard-to-find ABIs or a reliance outside sources. We've already generated many 100s of millions of fourbytes. We're only waiting to deploy them."
      - "**Dalle-dresses:** You're gonna love this when it goes live. Stay tuned."
      - "**Applications:** A collection of local-first, blazingly-fast, perfectly-private desktop applications demonstrating the power of TrueBlocks Key, TrueBlocks Core, and The Unchained Index."
      - "**Insert Your API Here:** Do you have a need in mind that doesn't appear above? We have you covered. Our core code can index anything including performing data extraction customized for your smart contract's needs. (Or any other need for that matter.) Contact us."
    button:
      enable: false
      label: "Get Started Now"
      link: "https://github.com/zeon-studio/hugoplate"

  - title: "Based on the Unchained Index -- a true public good"
    content: "TrueBlocks Key uses the index of appearances created by TrueBlocks Core, which publishes the index as a public good through the Unchained Index smart contract. Unlike Key, Core is fully local, fully decentralized, and open sourced. Both systems are designed to work with any EVM-based blockchain. TrueBlocks Key provides a simple, easy-to-use, cloud-based Web 2.0 interface to this index. "
    button:
      enable: true
      label: "Learn more about TrueBlocks"
      link: "https://trueblocks.io"
---
