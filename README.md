# Farm Animals

Add farm animals using [Better Farm Animal Variety (BFAV)](https://github.com/paritee/Paritee.StardewValley.Frameworks/tree/master/BetterFarmAnimalVariety)

## Contents

- [Get Started](#get-started)
- [Animal Data](#animal-data)

## Get Started

### Install

See [Install a Content Pack](https://github.com/paritee/Paritee.StardewValley.Frameworks/tree/master/BetterFarmAnimalVariety#install-a-content-pack)

## Animal Data

### Harvest Types

The way you harvest produce from your animals is defined in its type's data value. For a `White Cow`, its data value looks like this:

`"1/5/184/186/cow/36/64/64/64/36/64/64/64/1/false/Barn/32/32/32/32/15/5/Milk Pail/639/1500/White Cow/Barn"`

There are a few key values to note in the string. Each value is delimited by a `/` and the index starts at `0` (see [Modding:Animal data](https://stardewvalleywiki.com/Modding:Animal_data#Basic_format) for more information on the other values).

| Index | Syntax | Description | White Cow Value |
| --- | --- | --- | --- |
| 13 | `<Harvest Type>` | The way in which produce is harvested from the animal. Accepts `0`, `1`, or `2`. The `Hog` type is the only animal which uses the value `2` and does not allow an animal with this harvest type to be named (will be referred to as "It") | `1` |
| 14 | `<Show Different Texture>` | Used for indicating an animal with a secondary texture (ex. `Sheep`) when ready for harvest. Accepts true/false. Animals that have this set to `true` must also have a `ShearedType` asset loaded. | `false` |
| 22 | `<Harvest Tool>` | The [tool](https://stardewvalleywiki.com/Tools) required to harvest from animals with the `tool` harvest type, `-1` for animals with the `none` harvest type and  `null` otherwise | `Milk Pail` |

#### Automatic

Animals with the `automatic` harvest type will spawn their produce inside of their animal homes each day.

| Index | Value |
| --- | --- |
| 13 | `0` |
| 14 | `false` |
| 22 | `null` |

#### Tool

Animals with the `tool` harvest type must be interacted with while holding the tool specified (ex. `Milk Pail`).

| Index | Value |
| --- | --- |
| 13 | `1` |
| 14 | `true` or `false` |
| 22 | `<Tool Name>` |

#### Find

Animals with the `find` harvest type will attempt to spawn produce while outside (ex. `Pigs`).

| Index | Value |
| --- | --- |
| 13 | `1` |
| 14 | `true` or `false` |
| 22 | `null` |

#### None

Animals with the `none` harvest type will never produce objects. This is a special BFAV-enabled harvest type and this syntax does not act the same without BFAV. To achieve without BFAV, you must set the default and deluxe produce to `-1`.

| Index | Value |
| --- | --- |
| 13 | `1` |
| 14 | `false` |
| 22 | `-1` |

### Tools

- [Generate Farm Animal Data](https://paritee.github.io/#generate-data-farmanimals-entry)
