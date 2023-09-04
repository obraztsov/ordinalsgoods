# 🍀 Inscriptions format

All inscriptions used to define protocol-related data will be stored in the Bitcoin ledger as lightweight HTML documents. The reasoning behind this choice is to maintain compatibility with Ordinals explorers and marketplaces, leveraging Ordinals recursion to safely store complex object structures and simultaneously allowing users to see images instead of code, JSON, or texts. Suppose somebody will list an inscription of the product on the marketplace. In that case, the users of the marketplace will see an image of the product, and not the useless protocol info and inscription references.

The actual info related to the protocol will be included in the embedded XML document in the content of the HTML, thus easily readable by machine.

The requirement of the protocol will be to have a very specific HTML format, maintaining the safety of the Ordinals' recursion and information security (protection of unwanted script injections in the user-generated content). At first, we require an HTML document to be a valid XML document. HTML inscriptions that are not validated as XML and can't be parsed as XML are not considered for validation and wouldn't be included into the state.

We allow HTML documents to contain only one tag in the `body` that is either `img`, or `iframe`, and no executable scripts at all. It is also prohibited to define any event listeners or to include any stylesheet inscriptions not from the whitelist.

For ease of indexing, we also require to have all tags and attribute names in lowercase. All inscriptions not meeting these criteria will be considered invalid by the protocol and not included in indexed collections.

{% hint style="info" %}
The complete messages protocol is unambiguously defined by XML schema, which is itself inscribed on ordinals. The inscription of the XML schema acts as an identifier of the version of the protocol and, configured in the validator instance, as a qualifier to filter the stream of inscriptions for validation.
{% endhint %}

The suggested recursive HTML inscriptions format is easily extensible. Documents can contain additional XML scripts besides Ordinals:goods protocol data. Nested recursive HTML inscriptions can dynamically load documents and easily access the content and protocol data.
