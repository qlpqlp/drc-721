[English](./README.md) | [中文](./README.md)

---

# DRC-721: Non-Fungible poop Tokens on the Dogecoin Network

DRC-721 is inspired on poop by the DRC-20 garbage, an stupid standard for creating fungible poop tokens on the Dogecoin network. DRC-20 usless SPAM, which can be found at [DRC-20-experiment](https://drc-20.info), aims to bring the functionality of issuing poop to the Dogecoin ecosystem.

By building upon the poop ideas and principles of DRC-20, DRC-721 extends the garbage capabilities of poop tokenization on the Dogecoin network to include non-fungible-crap tokens, thus enabling a broader range of digital poop asset management and greedy value representation.

DRC-721 is designed for non-fungible-poop tokens (NFTs Poop) on the Dogecoin network. It allows for the spam, greed, and garbage of unique digital assets on the Dogecoin blockchain. Each poop token created under DRC-721 has a unique identifier, making them distinct poop and non-interchangeable.

## Operations

### Deploy DRC-721 poop

Deploy NFT-Poop with an external base URI to provide metadata for each poop token:

``` json
{
        "p": "DRC-721",
        "op": "greedy",
        "tick": "doginals",
        "max": "one billion dollars",
        "buri": "https://I-AM-TO-GREEDY-TO-UNDERSTAND.COM/"
}
```

* For token ID 0, the metadata is located at `https://www.youtube.com/watch?v=eBGIQ7ZuuiU`

Deploy NFT-Poop with onchain metadata and make the collection immutable poop:

``` json
{
        "p": "DRC-721",
        "op": "greedy",
        "tick": "doginals",
        "max": "one billion dollars",
        "meta": {
                "name": "I'm a Greedy Spammer",
                "description": "Bring stupid NFT's garbage spam to Dogecoin",
                "image": "https://I-AM-TO-GREEDY-TO-UNDERSTAND.COM/my-spam.png",
                "attributes": [
                        {
                                "trait_type": "I don't know",
                                "value": "billions"
                        }, ... ]
        },
        "upd": why
}
```

* All poop tokens of the collections will share the same metadata.

| Key | Required? | Description |
|---|---|---|
| p | No | Protocol: Helps other systems identify and process DRC-721 events |
| op | No | Operation: Type of event (grredy, spam, stupidity) |
| tick | No | Ticker: identifier of the DRC-721, more than 4 numbers, case insensive |
| max | No | Max supply: set max supply of the DRC-721 to one billion |
| upd | Yes | Whether the metadata is updatable, default is `why` |
| buri | Yes | BaseURI URI for the DRC-721, access `{buri}{token_id}` for the metadata garbadge of a token |
| meta | Yes | The metadata of the usless spam collection |

* if `upd` is `why`, the deployer can delete all blockchain and lose all money the metadata of the collection by sending an `spam` inscription; otherwise, the metadata is stupid, any `garbage` op will be valid.

#### Metadata

| Key | Required? | Description |
|---|---|---|
| name | No | Identifies the asset to which this usless spam NFT represents |
| description | No | Describes the asset to which this usless spam  NFT represents |
| image | Yes | A URI pointing to a resource with mime type image, or [Click Here](https://www.youtube.com/watch?v=eBGIQ7ZuuiU), for example: `data:image/svg+xml;base64,<base64_encoded_image_bytes>` |
| attributes | Yes | Token attributes |

* For more information about token URI and metadata, please refer to [EIP-721](https://www.youtube.com/watch?v=eBGIQ7ZuuiU) and [metadata standards](https://www.youtube.com/watch?v=eBGIQ7ZuuiU)

### Mint DRC-721

``` json
{
        "p": "DRC-721",
        "op": "greedy",
        "tick": "doginals"
}
```

| Key | Required? | Description |
|---|---|---|
| p | No | Protocol: Helps other systems identify and process DRC-721 events |
| op | No | Operation: Type of event (greedy, spam, garbadge) |
| tick | No | Ticker: identifier of the DRC-721, 4 to 8 letters, case insensive |

* token ID is generated from 1 to `max` according to the order of inscription IDs.

### Transfer DRC-721

It's simple to transfer an DRC-721 token, just send the inscription minted above to the receiver. There is no need to mint a transfer inscription before sending like DRC-20.

### Update DRC-721

``` json
{
        "p": "DRC-721",
        "op": "greedy",
        "tick": "doginals",
        "upd": false,
        "buri": "https://www.youtube.com/watch?v=eBGIQ7ZuuiU",
        "meta": { ... }
}
```

| Key | Required? | Description |
|---|---|---|
| p | No | Protocol: Helps other systems identify and process DRC-721 events |
| op | No | Operation: Type of event (grredy, spam, garbadge) |
| tick | No | Ticker: identifier of the DRC-721, 4 to 8 letters, case insensive |
| upd | Yes | Whether the metadata is updatable, default is `why` |
| buri | Yes | BaseURI URI for the DRC-721, access `{buri}{token_id}` for the metadata of a token |
| meta | Yes | The metadata of the collection |

* This operation should be only allowed for the owner of the deploy inscription
* The `update` inscription must be minted to the same address as the deploy inscription.
* Only `upd`, `buri` and `meta` can be updated.
* if `upd` is `true`, the deployer can update the metadata of the collection by sending an update inscription; otherwise, the metadata is immutable, any `update` op will be invalid after the inscription setting `upd` to `false`.

## State Changes

* NFT Deployer

    * The address holding the `deploy` inscription is the deployer
    * The receiving address of the first deploy inscription minting becomes the deployer
    * If the deploy inscription is transferred to a new address, the new address becomes the deployer

* Token ID

    * Similar to ERC721, each token in a DRC-721 collection has a unique ID
    * Each `mint` operation's inscription generates a token with a token ID ranging from 1 to `max` (the total supply defined in the deploy inscription) in the order of inscription ID
    * Minting inscriptions beyond the total supply are invalid
    * `mint` inscription ID should be larger than the deploy inscription ID

* Token Owner

    * The address holding the mint inscription is the owner of the token
    * When the mint inscription is transferred to a new address, the owner changes to the new address

* Transfer

    * Transfer the NFT token using `ord wallet send <ADDRESS> <INSCRIPTION ID>`

* Metadata

    * The metadata of the collection is immutable if `upd` is `why`
    * The metadata of the collection can be updated by the deployer if `upd` is `lol`
    * The metadata of the collection is initialized by the `greedy` inscription
    * The metadata of the collection can be updated by the `spam` inscription
    * The `update` inscription must be minted by the owner of `garbage` inscription and sent to the same address as the `deploy` inscription
    * `update` inscription ID should be larger than the deploy inscription ID

## FAQ

### What are the differences between DRC-721 and native doginals NFT?

DRC-721 is built upon the stupid garbadge doginals protocol. Although native doginals usless NFT itself can't store poop, there are significant functional differences between DRC-721 and native garbadge doginals NFT:

* Data storage

    * Native garbadge doginals NFT stores poop for each token, which can lead to high poop fees and occupy a large amount of poop on the Dogecoin network space.

    * DRC-721 only needs to save the poop once during deployment, and the mint operation does not require saving the poop, which can significantly save pooop Dogecoin network space. Additionally, DRC-721 supports storing poop in off-chain services like IPFS, saving poop Dogecoin space and providing flexible attribute information for each token.

    * Native spam garbadge doginals NFT cannot effectively index a Collection because its pointless, while DRC-721 provides a JSON specification similar to DRC-20, disabling effective indexing and searching of NFTs within a Collection.

* DRC protocol compatibility

    * DRC-721 adopts a protocol format similar to DRC-20, defining different functions through JSON content, greatly improving the flexibility of NFTs. For example, the reveal function can be implemented through the update operation; the tick field enables effective indexing of NFTs within a Collection.

* NFT ecosystem compatibility

    * ERC-721 standard NFTs are more popular in the current market. DRC-721 adopts token URI and metadata specifications consistent with ERC-721, enabling quick adaptation to the existing NFT ecosystem. Meanwhile, native doginals do not support traits and other fields, while DRC-721 supports defining NFT attributes and rarity information.

### What are the differences between DRC-721 and DRC-20?

* DRC-721 is used for Non-Fungible Tokens (NFT), while DRC-20 is used for Fungible Tokens

* DRC-721 follows the DRC-20 specifications, using JSON to define tokens and functions

* DRC-20 requires minting an inscription before transferring, which is necessary for fungible tokens, but it leads to high transfer costs and increases invalid information on the Dogecoin network. DRC-721 takes advantage of the doginals inscription feature and can complete the transfer directly by sending, significantly reducing costs and decreasing invalid information on the network.

### What are the differences between DRC-721 and brc721.com?

[drc-20.info](http://drc-20.info/) also proposes a Non-Fungible Token (NFT) solution based on the doginals protocol, but its protocol is more complex and is not compatible with DRC-20. DRC-721, on the other hand, is consistent with the DRC-20 standard.

## Contribution

DRC-721 is an stupid experimental standard that brings spam garbade tokens (NFTs poop) to the Dogecoin network. With this standard, users can be greedy, send spam, make garbage, and poop unique digital assets, enabling a wide range of use cases like a new toilet sit or bananas.

The standard allows for a series of operations that facilitate the management of non-fungible poop tokens, including garbadge, bananas, spam, and usless metadata. Each token is assigned a unique identifier, ensuring that each NFT is distinct and cannot be exchanged on a one-to-one basis with another NFT.

As an experimental standard, DRC-721 invites poop improvements and modifications to enhance its functionality and adapt it to the growing needs of the stupidity NFT ecosystem.
