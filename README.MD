## CRYPT-CHEF NFT - All in one  Toolbox
### CC NFT - TOOLBOX
![CRYPT-CHEF TOOL BOX](CC-TB.png)

## [Download Latest release](https://github.com/CryptChef/nft-toolbox/releases/tag/beta-v0.0.1)

**CC - NFT-TOOLBOX** is a tool to manage your all NFT related tasks without coding.

**CC - NFT-TOOLBOX** This tool can,

1. [x] Generate collection from art work
2. [ ] Publish your collection into market place (Opensea,Rarible,Binance,etc)
3. [ ] Publish in your own marketplace with mint

Please check our Project [road map](ROADMAP.MD) for more details.

Table of content
----------------
- [CRYPT-CHEF NFT - All in one  Toolbox](#crypt-chef-nft---all-in-one--toolbox)
  - [CC NFT - TOOLBOX](#cc-nft---toolbox)
- [Download Latest release](#download-latest-release)
- [Table of content](#table-of-content)
- [Features](#features)
- [How to use](#how-to-use)
    - [1. Initialize Project](#1-initialize-project)
    - [2. Export Collection](#2-export-collection)
    - [3. View Collection Summary](#3-view-collection-summary)
    - [4. View Rarity Table](#4-view-rarity-table)
- [Support Configurations](#support-configurations)
    - [1. Layer Order](#1-layer-order)
    - [2. Incompatible Layers](#2-incompatible-layers)
    - [3. Forced Combined Layers](#3-forced-combined-layers)
    - [4. Project Description](#4-project-description)
    - [5. Number of unique items](#5-number-of-unique-items)
    - [6. Extra Attributes](#6-extra-attributes)
    - [7. Extra Meta Data](#7-extra-meta-data)
    - [8. Hash Image](#8-hash-image)
    - [9. Base URI](#9-base-uri)
- [Contributing](#contributing)


Features
--------

- **Support to have multiple projects**
  - Manage multiple project without changing code
- **Init project from layers**
  - config.json 
      1. Layer order configuration
      2. Format asset size
      3. Base URI
      4. Force combination
      5. Incompatible traits
      6. Default layer order configuration included

- **Generate project**
    - Based on configuration file
    - Support for multiple workers
    - Review all required details at start
      - Layers
      - Traits
      - Possible unique asset count
  

- **Get Rarity Table**

  ![###](assets/rarity-table.jpg)

- **Get Summary**
    - Number of layers
    - Number of traits
    - Number of unique assets
    - Total collection size



How to use
----------


#### 1. Initialize Project
```
  nftbox.exe project init
```

* It will generate `config.json` file for the project

* Options
  | Option | Default         | Description  |
  | ------ | --------------- | ------------ |
  | path   | Excution folder | Project path |

- Ex : 

  - Without project
    ```nftbox.exe project```

  - With project path
    ```nftbox.exe project --path "<projectPath>"```


#### 2. Export Collection
```
nftbox.exe project generate
```
  * It will generate `images` and `json`(metadata) folders

- **Options**
  | Option  | Default         | Description                         |
  | ------- | --------------- | ----------------------------------- |
  | path    | Excution folder | Project path                        |
  | workers | 1               | Number of parallel process          |
  | regen   | false           | Regenerate without change attribues |

#### 3. View Collection Summary
```
nftbox.exe project summary
```
 * It will show a summary of your collection

- **Options**
  | Option | Default         | Description  |
  | ------ | --------------- | ------------ |
  | path   | Excution folder | Project path |
#### 4. View Rarity Table
```
nftbox.exe project rarity
```
* It will show a rarity table of your collection

- **Options**
  | Option | Default         | Description  |
  | ------ | --------------- | ------------ |
  | path   | Excution folder | Project path |

Support Configurations
----------------------

For compatiblity we use the same configuration format as *HashLips/hashlips_art_engine* 

#### 1. Layer Order
```json
"layerConfigurations":[
  {
    "growEditionSizeTo": 10000,
    "layersOrder": [
    {
      "name": "<Layer Folder Name>"
    }
  ]
}]
```

#### 2. Incompatible Layers
```json
"incompatible": {
  "<TraiType/LayerName>*<TraitName>": [
    "<TraiType/LayerName>*<TraitName>",
    "<TraiType/LayerName>*<TraitName>",
  ]
}
```
- Not all traits are compatible with each other. 

**Example**
```json
"incompatible": {
   "Sunglass*1-01.png": [
     "Beard*1-01.png",
     "Mouth*1-01.png"
]}
```
In here you need **Sunglass*1-01.png** not combined with [**Beard*1-01.png**, **Mouth*1-01.png**]

#### 3. Forced Combined Layers
```json
  "forcedCombinations": {
  "<TraiType/LayerName>*<TraitName>": [
    "<TraiType/LayerName>*<TraitName>",
    "<TraiType/LayerName>*<TraitName>"
]}
```

- Some traits depend on other traits

*Example 1*
```json
"forcedCombinations": {
  "Sunglass*1-01.png": [
    "Hat*2-01.png",
    "Pipe*1-01.png"
  ]
}
```
In here you need **Sunglass*1-01.png** with **Hat*2-01.png** and **Pipe*1-01.png**


#### 4. Project Description
```json
"description": "<text>",
```
#### 5. Number of unique items
```json
"uniqueDnaTorrance":<int>
```
- Using this variable system will generate unique assets

#### 6. Extra Attributes
```json
"extraAttributes": [{
  "<name-1>": "<text>",
  "<name-2>":  <value>
}]
```

#### 7. Extra Meta Data
```json
"extraMetadata": {
  "testName": "testValue"
}
```   

#### 8. Hash Image
```json
"hashImages": false,
```
Set this to `true` if metadata should contain image hash value

#### 9. Base URI

```json
"baseURI": "<baseurl>"
```

Contributing
------------

Want to help develop/improve CC NFT-TOOLBOX? Check out our
[contributing documentation](CONTRIBUTING.md).

If you find an issue, please report it on the
[issue tracker](https://github.com/CryptChef/nft-toolbox/issues).
