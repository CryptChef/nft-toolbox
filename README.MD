## CRYPT-CHEF NFT - All in one NFT Toolbox

![CRYPT-CHEF TOOL BOX](CC-TB.png)




- [CRYPT-CHEF NFT - All in one NFT Toolbox](#crypt-chef-nft---all-in-one-nft-toolbox)
- [Features](#features)
- [How to use](#how-to-use)
      - [1. Initialize Project](#1-initialize-project)
      - [2. Export Collection](#2-export-collection)
      - [3. View Collection Summary](#3-view-collection-summary)
      - [4. View Rarity Table](#4-view-rarity-table)
  - [Support Configurations](#support-configurations)



## Features

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



## How to use


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

### Support Configurations

1. Layer Order
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


2. Incompatible Layers
   ```json
    "incompatible": {
      "<TraiType/LayerName>*<TraitName>": [
        "<TraiType/LayerName>*<TraitName>",
         "<TraiType/LayerName>*<TraitName>",
      ]
    }
   ```
     - Ex
    ```json

    "incompatible": {
    "testSunglass*1-01.png": [
      "Beard*1-01.png",
      "Mouth*1-01.png"
    ]}
    ```


3. Forced Combined Layers
    ```json
      "forcedCombinations": {
      "<TraiType/LayerName>*<TraitName>": [
        "<TraiType/LayerName>*<TraitName>",
        "<TraiType/LayerName>*<TraitName>"
    ]}
    ```
    - Ex
    ```json
    "forcedCombinations": {
      "Sunglass*1-01.png": [
        "Hat*2-01.png"
      ],
      "Hat*3-01.png": [
        "Pipe*1-01.png"
      ]
    }
    ```
4. Project Description
    ```json
    "description": "<text>",
    ```
5. Number of unique items
   ```json
    "uniqueDnaTorrance":<int>
   ```
6. Extra Attributes
    ```json
    "extraAttributes": [{
      "<name-1>": "<text>",
      "<name-2>": <value>
    }]
    ```
7. Extra Meta Data
    ```json
        "extraMetadata": {
            "testName": "testValue"
          },
    ```   
8. Hash Image
    ```json
      "hashImages": false,
    ```
9. Base URI

    ```json
    "baseURI": "<baseurl>"
    ```



