# 🧩 Product catalog

Ordinals Goods protocol is designed to deal with large quantities of tokens representing items of a small set of "products" - kinds of goods offered by the business. Naturally, products can be represented as a tree with one-to-many relationships, where at the top will be large categories, and leaves will be very specific instances of products offered to end customers.

Businesses would want to offer bakers more general terms of subscriptions (even potentially weight-specific, like "1 kilo of honey per month"), while customers would want to redeem specific instances, like "2 cans, 250gr oak honey", also having a wide offered range of different products, potentially redeeming different kinds of goods every month, trading on the marketplace, etc.&#x20;

To maintain this logic, organizations must maintain correct weight values when defining products, and fine-tune subscription logic (and a list of product options available for a subscription) with subscription "level" field in protocol messages.

A product catalog built with recursive inscriptions solves the issue. Each product in addition can be configured as not allowing direct redemptions (for categories and top-level products), and can have a different URL for connecting with the business CRM system for redemptions.
