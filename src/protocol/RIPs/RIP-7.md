---
sidebarDepth: 2
---

# RIP-7: Registered Asset Sources

## Abstract

RIP-7 is used to describe and qualify the asset sources that can be indexed by RSS3.

## Motivation

The RSS3 protocol does not restrict what source can be used for asset, which creates uncertainty in implementation and use.

## Source List

| Source ID | Source Name | Source Website | Account Platform | Networks |
| -- | -- | -- | -- | -- |
| 0 | Crossbell | TODO | Ethereum | Crossbell |
| 1 | Ethereum NFT | <https://ethereum.org/en/nft/> | Ethereum | Ethereum, Polygon, Binance Smart Chain, Arbitrum, Avalanche, Fantom, Gnosis |
| 2 | Ethereum Cryptocurrency | <https://ethereum.org/en/developers/docs/standards/tokens/erc-20/>, <https://ethereum.org/en/developers/docs/intro-to-ether/> | Ethereum | Ethereum, Polygon, Binance Smart Chain, Arbitrum, Avalanche, Fantom, Gnosis |
| 3 | Solana NFT | <https://solana.com> | Solana | Solana |
| 4 | Flow NFT | <https://www.onflow.org/> | Flow | Flow |
| 5 | PlayStation Trophy | <https://www.playstation.com/> | PlayStation | PlayStation |
| 6 | GitHub Achievement | <https://github.com/> | GitHub | GitHub |

## Responses

```ts
type Asset = {
    identifier: AssetInstanceURI;
    date_created: string;
    date_updated: string;

    related_urls?: string[];

    links: LinksURI;
    backlinks: BacklinksURI;

    tags?: string[];
    authors: AccountInstanceURI[];
    title?: string;
    summary?: string;
    attachments?: {
        type?: string;
        content?: string;
        address?: URI;
        mime_type: string;
        size_in_bytes?: number;
    }[];

    source: AssetSource;

    metadata?: {
        network: Network;
        proof: string;

        [key: string]: any;
    };
}
```

### Crossbell

TODO

### Ethereum NFT and Solana NFT and Flow NFT

#### `related_urls`

URL of NFT page if avaiable.

#### `tags`

```json
"tags": [
    "NFT"
]
```

#### `title`

NFT name.

#### `summary`

NFT description.

#### `attachments`

```json
"attachments": [
    {
        "type": "object",
        "address": "<object_address>",
        "mime_type": "<object_mime_type>",
        "size_in_bytes": <object_size_in_bytes>
    },
    {
        "type": "preview",
        "address": "<preview_address>",
        "mime_type": "<preview_mime_type>",
        "size_in_bytes": <preview_size_in_bytes>
    },
    {
        "type": "attributes",
        "content": "{\"<attribute_key>\":\"<attribute_value>\",...}",
        "mime_type": "text/json"
    },
    {
        "type": "external_url",
        "content": "<external_url>",
        "mime_type": "text/uri-list"
    }
]
```

#### `metadata`

```json
"metadata": {
    "network": "<network_name>",
    "proof": "<collection_address>-<token_id>",

    "token_standard": "<token_standard>",
    "token_id": "<token_id>",
    "token_symbol": "<token_symbol>",

    "collection_address": "<collection_address>",
    "collection_name": "<collection_name>",
}
```

#### Examples

RSS3 Whitepaper #1800

[Chain Explorer](https://etherscan.io/nft/0xb9619cf4f875cdf0e3ce48b28a1c725bc4f6c0fb/1800)

```json
{
    "identifier":  "rss3://asset:0xb9619cf4f875cdf0e3ce48b28a1c725bc4f6c0fb-1800@ethereum",
    "date_created": "2022-01-19T02:06:38.000Z",
    "date_updated": "2022-01-19T02:06:38.000Z",

    "related_urls": [
        "https://etherscan.io/nft/0xb9619cf4f875cdf0e3ce48b28a1c725bc4f6c0fb/1800",
        "https://opensea.io/assets/0xb9619cf4f875cdf0e3ce48b28a1c725bc4f6c0fb/1800"
    ],

    "links": "rss3://asset:0xb9619cf4f875cdf0e3ce48b28a1c725bc4f6c0fb-1800@ethereum/links",
    "backlinks": "rss3://asset:0xb9619cf4f875cdf0e3ce48b28a1c725bc4f6c0fb-1800@ethereum/backlinks",

    "tags": [
        "NFT"
    ],
    "authors": [
        "rss3://account:0xC8b960D09C0078c18Dcbe7eB9AB9d816BcCa8944@ethereum"
    ],

    "title": "RSS3 Whitepaper v1.0",
    "summary": "RSS3 Whitepaper v1.0 - Commemorative & Limited Edition",

    "attachments": [
        {
            "type": "object",
            "address": "ipfs://bafybeicij6vw6xcsgwldofnmmh3c3j4w5yiocs6l72yubpbcldxcglkvqe/rss3-whitepaper-no-1800.glb",
            "mime_type": "model/gltf-binary",
            "size_in_bytes": 3983376
        },
        {
            "type": "preview",
            "address": "ipfs://bafybeianto7koyrfwkdjymx7byjrs3hzy7ldipfxc343vra2t7pbd557sy/rss3-whitepaper-no-1800.png",
            "mime_type": "image/png",
            "size_in_bytes": 117310
        },
        {
            "type": "attributes",
            "content": "{\"Author(s)\":\"Natural Selection Labs\",\"Edition\":\"First Edition\",\"Edition Language\":\"English\",\"File Format\":\"PDF\",\"No.\":1800,\"date\":1610323200}",
            "mime_type": "text/json"
        },
        {
            "type": "external_url",
            "content": "https://rss3.io/RSS3-Whitepaper.pdf",
            "mime_type": "text/uri-list"
        }
    ],

    "source": "Ethereum NFT",

    "metadata": {
        "network": "Ethereum",
        "proof": "0xb9619cf4f875cdf0e3ce48b28a1c725bc4f6c0fb-1800",

        "token_standard": "ERC-721",
        "token_id": "1800",
        "token_symbol": "RWP",

        "collection_address": "0xb9619cf4f875cdf0e3ce48b28a1c725bc4f6c0fb",
        "collection_name": "RSS3 Whitepaper"
    }
}
```

### PlayStation Trophy

TODO

### GitHub Achievement

TODO
