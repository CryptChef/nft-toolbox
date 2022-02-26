## CRYPT-CHEF NFT - All in one  Toolbox
### CC NFT - TOOLBOX
![CRYPT-CHEF TOOL BOX](CC-TB.png)

## [Download Latest release](https://github.com/CryptChef/nft-toolbox/releases/tag/v0.0.1)

**CC - NFT-TOOLBOX** is a tool for manage your all nft related tasks without worrying devlopment

Thier are lot of task in nft world as a designer need a help from developers. such as 

1. Generate Collection from art work
2. Publish your collection
3. Mint your collection

We are ready to provide support for all of these tasks
First of all we are happy to introduce our **Brand New NFT ToolBox** core with support of

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
      3.  Base URI
      4. Forcecombination
      5. Incompatible Traits
      6. Default Layer order configuration included

- **Generate project**
    - Base on configuration file
    - Support for multiple workers
    - Check all required details at the start
      - Layers
      - Traits
      - Possible Unique asset count
  

- **Get Rarity Table**

  ![###](assets/rarity-table.jpg)

- **Get Summary**
    - Number of layers
    - Number of Traits
    - Number of Uniques assets
    - Total collection size



How to use
----------


##### 1. Initialize Project
 ```
  nftgen.exe project init
  ```

* User can create project config.json
* Identify Layers and insert them into 


* Options
  | Option | Default         | Description  |
  | ------ | --------------- | ------------ |
  | path   | Excution folder | Project path |

- Ex : 

  - Without project
    ```nftgen.exe project```

  - With project path
    ```nftgen.exe project --path "<projectPath>"```


##### 2. Export Collection
```
nftgen.exe project generate
```

- **Options**
  | Option  | Default         | Description                         |
  | ------- | --------------- | ----------------------------------- |
  | path    | Excution folder | Project path                        |
  | workers | 1               | Number of parallel process          |
  | regen   | false           | Regenerate without change attribues |

##### 3. View Collection Summary
```
nftgen.exe project summary
```
- **Options**
  | Option | Default         | Description  |
  | ------ | --------------- | ------------ |
  | path   | Excution folder | Project path |
##### 4. View Rarity Table
```
nftgen.exe project rarity
```
- **Options**
  | Option | Default         | Description  |
  | ------ | --------------- | ------------ |
  | path   | Excution folder | Project path |

Support Configurations
----------------------

##### 1. Layer Order
   ```json
   "layerConfigurations":[
     {
        "growEditionSizeTo": 10000,
			  "layersOrder": [{
					"name": "<Layer Folder Name>"
				}
      ]
    }]
   ```

      * We can have multiple layerConfiguration in here  and layerConfiguration can have one layerOrder


##### 2. Incompatible Layers
   ```json
    "incompatible": {
      "<TraiType/LayerName>*<TraitName>": [
        "<TraiType/LayerName>*<TraitName>",
         "<TraiType/LayerName>*<TraitName>",
      ]
    }
   ```
    - Some traits are not compatible with some other traits. 


    **Ex**
    ```json

    "incompatible": {
    "Sunglass*1-01.png": [
      "Beard*1-01.png",
      "Mouth*1-01.png"
    ]}
    ```
    In here you need **Sunglass*1-01.png** not combined with [**Beard*1-01.png**, **Mouth*1-01.png**]

##### 3. Forced Combined Layers
    ```json
      "forcedCombinations": {
      "<TraiType/LayerName>*<TraitName>": [
        "<TraiType/LayerName>*<TraitName>",
        "<TraiType/LayerName>*<TraitName>"
    ]}
    ```
    Some trait required another trait by force

    **Ex**
    ```json
    "forcedCombinations": {
      "Sunglass*1-01.png": [
        "Hat*2-01.png",
        "Pipe*1-01.png"
      ]
    }
    ```
    In here you need **Sunglass*1-01.png** with **Hat*2-01.png** and **Pipe*1-01.png**


##### 4. Project Description
    ```json
    "description": "<text>",
    ```
##### 5. Number of unique items
   ```json
    "uniqueDnaTorrance":<int>
   ```
    Using this variable system will generate unique number of assets without repeating

##### 6. Extra Attributes
    ```json
    "extraAttributes": [{
      "<name-1>": "<text>",
      "<name-2>": <value>
    }]
    ```

    These extra data can append with original asset metadata attributes


##### 7. Extra Meta Data
    ```json
        "extraMetadata": {
            "testName": "testValue"
          },
    ```   

  These extra meta data append to the original asset metadata

##### 8. Hash Image
    ```json
      "hashImages": false,
    ```

    Image need uniques hash value you have to make this true

##### 9. Base URI

    ```json
    "baseURI": "<baseurl>"
    ```
  In here system update all meta data with your collection baseURI 


Contributing
------------

Want to help develop/improve CC NFT-TOOLBOX? Check out our
[contributing documentation](CONTRIBUTING.md).

If you find an issue, please report it on the
[issue tracker](https://github.com/CryptChef/nft-toolbox/issues).