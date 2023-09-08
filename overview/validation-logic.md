# 🛠 Validation logic

The core inscription for each subscription’s issuance will be the DAO-defining inscription, inscribed by the DAO founders, and containing the information defining the legal background of the business. The DAO inscription reference will be further used as the identifier for all subscriptions and products managed by the DAO.

The business logic will be mostly defined by subscription inscriptions, containing the conditions of the “prepayment for goods” subscription contract (i.e. “receive X packs of Y product per T time period”). These inscriptions will be sold during the public fundraising campaign.

The parameters of the subscription will be encoded and inscribed by the DAO, and first inscribed in the “genesis tx” sent to the DAO address – therefore the validator-indexer will consider subscription inscriptions as valid if they’re inscribed (sent in the genesis tx) to the address of the DAO, specified in the DAO’s specification inscription. It is also necessary to check the origination address of the satoshi offset of the inscription, therefore preventing any PSBT misuse and ensuring subscription inscriptions authenticity

To make a protocol self-sustainable, the reference time period of the subscription will be calculated in the Bitcoin blocks.

Every individual product package will also be represented as an inscription, and since the minting of inscriptions will be automatically done by subscription holders, the validator-indexer will employ a complex logic to decide whether the product inscription is valid.

The validator-indexer will consider product instance inscriptions valid if:

1. inscribed (sent in the genesis tx) on the satoshi owned by a subscription holder, sent to the address of the associated subscription holder, and have a valid Ordinal Recursion reference to the correct subscription inscription;
2. at the time (block height) of the inscription tx’s confirmation, and considering the history of mints for the specified subscription (sorting by inscription globally unique number), there is an unclaimed balance of the product for the specified subscription.

{% hint style="info" %}
To support popular wallets and marketplaces that are separating addresses with Ordinals with BTC addresses, Ordinals:goods protocol supports an alternative way of verifying user-inscribed protocol messages authenticity via Orindlas Provenance (child inscriptions).
{% endhint %}

Protocol also enables every DAO to issue (inscribe) product instance inscriptions not tied to a subscription (i.e. to simply tokenize goods for distribution on the marketplaces). In that case, the subscription reference in the inscription content will be empty, and the validator will consider these inscriptions valid if they were inscribed on the satoshi sent from the address of the DAO.&#x20;

The goods inscriptions (product instances) also will have a reference to an external product description inscription, together with a subscription inscription, to simplify marketplace listings and goods filtering. The protocol enables one goods inscription to carry several identical items of physical product, to optimize usage of Bitcoin transactions.
