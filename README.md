# X World Games NFTDS

## Introduction

The NFTDS (NFT Data Service) is a service that provides unified access to data resources for all X World Games NFT products. You can get all public data resources through this service.

## Metadata Service

### Hosts

#### Production

```
https://metadata.nft.xwg.games/
```

#### Development

```
https://metadata-dev.nft.xwg.games/
```

### URL Templates

#### Parameters

| Name           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `collectionId` | The collection ID of the token.<br/>- `1` DreamCard Characters<br/>- `2` DreamCard Equipments<br/>- `3` DreamCard Mystery Boxes of Equipment<br/>- `4` DreamCard Level Assets<br/>- `5` DreamCard Level Prizes<br/>- `6` DreamCard Equipment Consumables<br/>- `7` DreamCard Talents<br/>- `8` DreamCard Talent Consumables<br/>- `9` DreamCard Lucid<br/>- `10` DreamCard Character Pieces                                                                                      |
| `tokenId`      | The ID of the token.<br/><br/>The ID of the DreamCard Equipment Consumables:<br/>- `1` DreamCard Equipment Essences<br/><br/>The ID of the DreamCard Talent Consumables:<br/>- `1` DreamCard Talent Debris<br/><br/>The ID of the DreamCard Lucid:<br/>- `769` DreamCard Lucid Basic<br/>- `515` DreamCard Lucid Magic<br/>- `516` DreamCard Lucid Super<br/><br/>The ID of the DreamCard Character Pieces:<br/>`tokenId = characterNum &#124; element << 16 &#124; grade << 24` |

#### Get a Token's Metadata

```
/{collectionId}/{tokenId}
```

## Image Service

### Hosts

#### Production

```
https://image.nft.xwg.games/
```

#### Development

```
https://image-dev.nft.xwg.games/
```

### URL Templates

#### NFT Images

##### Parameters

| Name           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `collectionId` | The collection ID of the token.<br/>- `1` DreamCard Characters<br/>- `2` DreamCard Equipments<br/>- `3` DreamCard Mystery Boxes of Equipment<br/>- `4` DreamCard Level Assets<br/>- `5` DreamCard Level Prizes<br/>- `6` DreamCard Equipment Consumables<br/>- `7` DreamCard Talents<br/>- `8` DreamCard Talent Consumables<br/>- `9` DreamCard Lucid<br/>- `10` DreamCard Character Pieces                                                                                      |
| `tokenId`      | The ID of the token.<br/><br/>The ID of the DreamCard Equipment Consumables:<br/>- `1` DreamCard Equipment Essences<br/><br/>The ID of the DreamCard Talent Consumables:<br/>- `1` DreamCard Talent Debris<br/><br/>The ID of the DreamCard Lucid:<br/>- `769` DreamCard Lucid Basic<br/>- `515` DreamCard Lucid Magic<br/>- `516` DreamCard Lucid Super<br/><br/>The ID of the DreamCard Character Pieces:<br/>`tokenId = characterNum &#124; element << 16 &#124; grade << 24` |

##### Get a Token's Image

```
/tokens/{collectionId}/{tokenId}
```

#### Characters Image Assets

##### Parameters

| Name            | Description                                                                                                                |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------|
| `characterId`   | The ID of character generated by the NFTDS.                                                                                |
| `characterCode` | The code of the character starts with `COL`.                                                                               |
| `grade`         | The grade of the character.<br/>- `1` Common<br/>- `2` Rare<br/>- `3` Epic<br/>- `4` Legendary<br/>- `5` Myth              |
| `element`       | The element of the character.<br/>- `0` None<br/>- `1` Metal<br/>- `2` Wood<br/>- `3` Water<br/>- `4` Fire<br/>- `5` Earth |
| `skillId`       | The skill ID generated by the NFTDS.                                                                                       |
| `skillCode`     | The skill code starts with `SKL`.                                                                                          |
| `version`       | The version of the DreamCard.<br/>- `1` 1.0<br/>- `2` 2.0                                                                  |

##### Get a Token's Image with Base Stat

```
/assets/1/tokens/{characterId}/{grade}-{element}
/assets/1/tokens/{characterCode}/{grade}-{element}
```

##### Get a Character's Full Body Painting

```
/assets/1/characters/paintings/{characterId}
/assets/1/characters/paintings/{characterCode}
```

##### Get a Character's Avatar

```
/assets/1/characters/avatars/{characterId}
/assets/1/characters/avatars/{characterCode}
```

##### Get a Skill's Icon

```
/assets/1/skills/icons/{skillId}
/assets/1/skills/icons/{version}/{skillCode}
```

#### Equipments Image Assets

##### Parameters

| Name               | Description                                                                                                                                                                   |
|:-------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `equipmentId`      | The ID of equipment generated by the NFTDS.                                                                                                                                   |
| `equipmentCode`    | The code of the equipment calculated from `class` and `classEquipmentId`.<br/>Pseudocode:<br/>`(class.toString(16) + classEquipmentId.toString(16)).toNumber(10)`             |
| `class`            | The character class that can be equipped. Which is the `role` parameter in the contract.<br/>- `1` Knight<br/>- `2` Assassin<br/>- `3` Archer<br/>- `4` Mage<br/>- `5` Priest |
| `classEquipmentId` | The equipment ID of the character class. Which is the `equip` parameter in the contract.                                                                                      |
| `grade`            | The grade of the equipment.<br/>- `1` Common<br/>- `2` Rare<br/>- `3` Epic<br/>- `4` Legendary<br/>- `5` Myth                                                                 |

##### Get a Token's Image with Base Stat

```
/assets/2/tokens/{equipmentId}/{grade}
/assets/2/tokens/{equipmentCode}/{grade}
/assets/2/tokens/{class}-{classEquipmentId}/{grade}
```

#### Talents Image Assets

##### Parameters

| Name         | Description                                                                                                |
|:-------------|:-----------------------------------------------------------------------------------------------------------|
| `talentId`   | The ID of talent generated by the NFTDS.                                                                   |
| `talentCode` | The code of the talent. Which is the `tp` parameter in the contract.                                       |
| `grade`      | The grade of the talent.<br/>- `1` Common<br/>- `2` Rare<br/>- `3` Epic<br/>- `4` Legendary<br/>- `5` Myth |

##### Get a Token's Image with Base Stat

```
/assets/7/tokens/{talentId}/{grade}
/assets/7/tokens/{talentCode}/{grade}
```

##### Get a Talent's Icon

```
/assets/7/talents/icons/{equipmentId}
/assets/7/talents/icons/{equipmentCode}
```

### Image Resizing

All resource URLs support image resizing, just simply add a string parameter list starts with the `@` symbol at the end of the resource URL.

#### Parameter Format

Concatenate the parameter value and name directly. For example, `200w` means specify the target width is `200px`, `100h` means specify the target height is `100px`.

#### Parameter List Format

Use the underscore `_` to concatenate all the parameters to be passed. For example, `200w_100h_1l_90q`.

#### Supported Parameters

| Name | Value Range               | Default Value | Description                                                                                                                                                                                                                                                                                                                                  |
|:-----|:--------------------------|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `w`  | `1` - `4096`              |               | Specify the target width.                                                                                                                                                                                                                                                                                                                    |
| `h`  | `1` - `4096`              |               | Specify the target height.                                                                                                                                                                                                                                                                                                                   |
| `m`  | `0` &#124; `1` &#124; `2` | `0`           | Specify the scaling mode.<br/>- `0` proportional scaling. It refers to the maximum image that is limited in the rectangle of the specified `w` and `h`.<br/>- `1` proportional scaling. It refers to the minimum image extending out of the rectangle of the specified `w` and `h`.<br/>- `2` fixed width and height, enforced scaling down. |
| `l`  | `0` &#124; `1`            | `1`           | Specify whether to process the target thumbnail when it is larger than the original image.<br/>- `1` indicates not to process<br/>- `0` indicates to process                                                                                                                                                                                 |
| `p`  | `1` - `1000`              | `100`         | Specify the percentage of proportional scaling. If it is less than 100, it means to scale down; if it is greater than 100, it means to scale up.                                                                                                                                                                                             |
| `q`  | `1` - `100`               | `80`          | Specify the percentage of the target quality.                                                                                                                                                                                                                                                                                                |
| `r`  | `0` &#124; `1`            | `0`           | Specify use the progressive JPEG.<br/>- `0` use non-progressive JPEG.<br/>- `1` use progressive JPEG.<br/>_This parameter only makes sense if the target is in JPEG format._                                                                                                                                                                 |

### Image Format Conversion

The resource URL does not use any extension to explicitly indicate the image format of the response. For static image resources, the default format is PNG, and for animation image resources, the default format is GIF. You can convert the format you want to use as needed, just add the extension at the end of the resource URL. If used with resizing, the extension must be at the end of the URL. For example, `.jpg`, `.webp`.

#### Supported Extensions

- `jpg`
- `jpeg`
- `png`
- `webp`

## Database Service

The database service provides queries for the game data such as characters, equipments, and skills. It is served through the graphql api, and you can read the documentation by visiting the links below.

### Links

#### Production

```
https://database.nft.xwg.games/
```

#### Development

```
https://database-dev.nft.xwg.games/
```
