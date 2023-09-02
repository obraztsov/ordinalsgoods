# 💡 Protocol introduction

On the base layer, the protocol uses the Ordinals Inscriptions concept first introduced together with the Ordinal Theory release.

{% hint style="info" %}
Ordinal Theory (introduced in early 2023) imbues satoshis with numismatic value, allowing them to be collected and traded as curios. Individual satoshis can be inscribed with arbitrary content, creating unique Bitcoin-native digital artifacts that can be held in Bitcoin wallets and transferred using Bitcoin transactions. Inscriptions are as durable, immutable, secure, and decentralized as Bitcoin itself.

Essentially inscriptions with the data attached act both as data storage and an NFT token simultaneously. Ordinals protocol allows the implementation of various indexers and state machines over the immutable storage layer of the Bitcoin blockchain.
{% endhint %}

Inscriptions can be transferred unlimitedly and securely on Bitcoin Layer-1 and can be traded in a completely decentralized fashion using a special smart contract technology known as PSBT (partially signed Bitcoin transaction) and widely supported in the Ordinals ecosystem.

One of the known examples of an outer indexer is a BRC-20 protocol, already thriving in the Ordinals ecosystem. BRC-20 uses individual inscriptions as instructions for balance changes of the "virtual" ledger accounting fungible token balances. The state of this ledger at any point in time can be recalculated using solely the ledger of the Bitcoin itself. When the user wants to transfer or trade a portion of the balance of his asset, he inscribes this intention (token ticker, amount to transfer) as an instruction inscription on Bitcoin, and if the instruction is validated by the indexer as correct – it updates the state of the token ledger.

We employ similar accounting principles for the implementation of the Ordinals(goods) protocol and subscription logic. The protocol will be self-sustainable, with all accounting data to be defined using solely the data stored in the Bitcoin ledger as the content of Ordinals inscriptions, effectively meaning that the subscription agreement is a smart contract secured by the Bitcoin ledger itself.
