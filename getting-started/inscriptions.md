# 🛠 Inscriptions

Every inscription of the protocol must have a parent inscription, either image (with supported formats being JPG, PNG, WEBP, SVG, GIF - the image formats not allowing recursion) or other inscription of the protocol (HTML recursion).

The inscriptions of the protocol must have only one visible element in HTML - `img` or `iframe` containing the reference of the parent inscription. And the `script` element in head, that must have an element using the ordinals goods XML schema and defining the data related to the protocol.

<details>

<summary>DAO deploy inscription</summary>

DAO deployment inscription is inscribed by DAO founders (SME LLC) and defines Bitcoin Taproot addresses of the DAO address (treasury wallet) and burn wallet. Once inscribed and the inscription id is given, the DAO inscription will be further referenced by all other inscriptions used in the scope of the Ordinals(goods) protocol.

The inscription exists in the network as an immutable data reference, and ownership of the inscription doesn’t have any meaning in the scope of the Ordinals(goods) protocol.

The DAO deployment inscription is defined by the `deploy` XML element in the HTML `script` and uses the inscription with the DAO logo as the parent inscription.

</details>

<details>

<summary>Product specification inscription</summary>

The purpose of product specification inscriptions is to define the nomenclature of goods offered by the DAO. The inscription id will serve as the prime unique identifier of the good and will be referenced in all other types of protocol inscriptions and supported in the off-chain CRM/supply chain system of the SME LLC.

The product inscription is identified by the product element and uses a product logo as the parent inscription, therefore every inscription that will base on the product inscription will display the logo of the product if previewed by the marketplace or Ordinals explorer.&#x20;

The inscription also must reference the DAO (deploy) inscription id in the metadata. The product inscription can have an optional "url" field to override the DAO-defined URL of the redemption webhook, thus enabling product-specific redemption configuration.

The inscription exists in the network as an immutable data reference, and ownership of the inscription doesn’t have any meaning in the scope of the Ordinals(goods) protocol.

</details>

<details>

<summary>Subscription inscription</summary>

Subscription inscriptions define the contracts allowing qualified owners to inscribe (“mint”) goods inscriptions. The parameters of the subscription “kind” and “num” define the product that is offered by a subscription, and a quantity that the subscription holder has the right to claim within a specified period of time, referenced as subscription cycle "blk", defined by the number of elapsed Bitcoin blockchain blocks (each one once in 10 minutes, secured by the Proof of Work).

The period is calculated since the subscription’s genesis block (a block in which the subscription’s genesis tx was mined). For every newly inscribed goods inscription (product instance), the validator-indexer will calculate the number of cycles elapsed since the creation of the inscription, multiply it by “num”, and then compare the given number with the number of all valid goods inscriptions that were inscribed by subscription owners (a number of products already claimed). The validator can efficiently filter these inscriptions by reference to the subscription (inscription number).

If the number of claimed products is less than the total allowed number for the subscription, at the genesis block of the goods inscription, the validator-indexer will declare the goods inscription as valid and include it in the collection index.

The subscription inscription uses the product inscription as the parent inscription. Indexers when processing the subscription inscription must read the product inscription to get the info necessary for validation and future indexing, such as the DAO information.

The validation logic that should be applied for all newly minted subscription inscriptions is provided above in the Protocol section of the whitepaper. For the purpose of validation, the protocol will primarily consider inscription numbers to establish the natural ordering.

Subscription inscriptions can be transferred or sold on the PBST marketplace, and the nature of the protocol allows the buyer to claim the goods inscriptions that were not claimed by the previous owner (seller).&#x20;

The protocol also supports burning subscription inscriptions by sending them to the DAO burn address.

Since subscriptions can be used as a means of lightweight fundraising for businesses, the protocol allows users to further configure business logic for the DAO governance, granting subscription holders voting power. The number of votes will be configured by the "blt" field of the subscription inscription.&#x20;

</details>

<details>

<summary>Item inscription</summary>

Item inscriptions will be the most circulating in the Ordinals(goods) protocol and the ones providing the direct link to the goods in the physical world. All item inscriptions will have a product inscription as the parent inscription, and through it - a reference to the DAO root inscription, therefore unambiguously defining the goods. Suppose the item inscription is created in the scope of the subscription. In that case, it will also contain the reference to the subscription inscription (inscription id) provided in the item tag in the metadata.

Item inscription can have (through an optional field) a quantity parameter, enabling to representation of a set of identical items for shipments. If for example, a subscription holder has some unclaimed balance of items, he can mint a single item inscription with the whole balance, and redeem all items at once.

The cornerstone of the protocol is the validation rules for goods inscriptions, enabling tracking of only authentic goods inscriptions, supporting marketplace collections listings, and organizing physical goods redemptions. To process this task, the validator-indexer will process all new goods inscriptions, and employ complex logic to decide whether or not to include the inscription in a collection and further track as valid.

The first check will consider the “genesis owner” of the inscription: an address, receiving the sat with the inscription in the inscriptions' genesis transaction. The genesis owner must be equal to the address of the current holder of the referenced subscription. In addition, the indexer will check the previous owner of the satoshi on which the item is inscribed, to prevent unauthorized item mints even without ownership violation.

Alternatively, the subscription holder can use his subscription inscription as a parent inscription for an item leveraging Ordinals Provenance. The third potential way of minting valid items is for the DAO, to inscribe an item on the satoshi owned by the DAO address.&#x20;

If the goods inscription is created in the scope of the subscription, the validator will run an unambiguous test to determine the subscription holder’s eligibility to inscribe the goods by quantity (the whole logic of the validation was described in the paragraph about subscription inscriptions).

If the change of ownership of the subscription appeared in the same block when the Item inscription was confirmed for the purpose of validation the previous owner will be granted the ownership right (considering the "confirmed" ledger state at the time the inscription tx was signed).

If the inscription was issued to the DAO address it can be valid without being tied to a subscription, so it’s necessary to check whether the tx was originated by the DAO itself: at least one input of the tx should be of the DAO address.

Goods inscription will be freely traded on PSBT marketplaces and exchanges, potentially with the ability to be used in DeFi instruments when more complex smart contract solutions will appear on Ordinals.

</details>

<details>

<summary>Certificate inscription</summary>

Certificate inscriptions contain a key-value pair, along with the type field setting the type of the certificate. Certificate inscriptions can be inscribed both by goods inscription holders and by the DAO. However, item or subscription holders can inscribe only certificates of the type "message". Indexer applies logic similar to validating subscription items, to the validation of messages issued by holders.

The protocol doesn't limit the set of types to enable extensibility. A few types are reserved, such as "message", "certificate", and "bearer". Messages are intended to carry important data that will be appended to the goods, such as redemptions and redemption statuses, and maintenance/warranty events. Also, messages can be used in applications extending Ordinals Goods protocol, in PSBT contracts for supply chain management, verifiable customer reviews for products, etc.

Inscriptions with the types "certificate" and "bearer" only can be issued by the business (DAO) and thus are intended for important status updates, such as redemption, business-integrated supply chain events, or various tickets and loyalty coupons.

Once inscriptions with message and certificate types are inscribed and considered to be valid by the protocol, information from inscriptions will be permanently bound to the item inscription. Satoshi contained in the certificate inscriptions can be recycled, or the owner can decide to hold them for future easy proof without relying on history records.

Bearer certificates will, on the other end, represent transferable tokens, such as tickets for private events, discount coupons, or any other form of customer engagement.

</details>
