# Farm Animals

Adds farm animals as new entries to Data/FarmAnimals without overwriting existing farm animals.

## Contents

- [Get Started](#get-started)
- [Custom Spritesheets](#custom-spritesheets)
- [Tools](#tools)

## Get Started

### Using with BFAV

The following section explains how to add a new farm animal with the [Better Farm Animal Variety](https://www.nexusmods.com/stardewvalley/mods/3296) (BFAV) mod. In this example we will be using [Paritee's White Bull](https://www.nexusmods.com/stardewvalley/mods/3298) mod, but this can be done with any farm animal type that has been loaded into `Data/FarmAnimals`. See [Configure.FarmAnimals](https://github.com/paritee/Better-Farm-Animal-Variety/blob/master/README.md#farmanimals) for more information on the `Types` field.

1. Make sure you have [installed BFAV](https://github.com/paritee/Better-Farm-Animal-Variety/blob/master/README.md#install)
2. Unzip the [Paritee's White Bull](https://www.nexusmods.com/stardewvalley/mods/3298) folder into `Stardew Valley/Mods`
3. Add "White Bull" to the `Cows.Types` array inside BFAV's `config.json`
4. Run the game using SMAPI

Your `Cows` section of the `config.json` should now look like the following:

```json
"Cows": {
  "Name": "default",
  "Description": "default",
  "ShopIcon": "default",
  "Types": [
    "White Cow",
    "Brown Cow",
    "White Bull"
  ]
},
```

### Using with Content Patcher

You cannot add a new farm animal without BFAV, but you can override and existing farm animal with a few modifications. Here is a method for overriding the `White Cow` with [Paritee's White Bull](https://www.nexusmods.com/stardewvalley/mods/3298). To do this, you need to change the following inside the farm animal mod's `content.json`:

1. Change the `Data/FarmAnimals` `Entries` key to `White Cow`

```json
{
  "Action": "EditData",
  "Target": "Data/FarmAnimals",
  "Entries": {
    "White Cow": ..,
  }
},
```

2. Change the sprite `Target` paths to `White Cow`

```json
{
  "Action": "Load",
  "Target": "Animals/White Cow",
  ..
},
{
  "Action": "Load",
  "Target": "Animals/BabyWhite Cow",
  ..
},
```

3. Change the localization `Data/FarmAnimals` `Field` keys to `White Cow` for each language

```json
{
  "Action": "EditData",
  "Target": "Data/FarmAnimals",
  "Fields": {
    "White Cow": ..,
  },
  "When": { "Language": "de" },
},
```

## Custom Spritesheets

It is possible to override the default spritesheets for the BFAV farm animals so that you can use your favourite packs. You need to do the following two steps within your Content Patcher skin mod.

### Example

I'll be using [Elle's New Barn] Animals(https://www.nexusmods.com/stardewvalley/mods/3167) as the Content Patcher skin mod and [Paritee's White Bulls](https://www.nexusmods.com/stardewvalley/mods/3298) mod as the BFAV farm animal in the example.

1. Add your target BFAV farm animal's mod `UniqueID` (found in `manifest.json`) as a required dependency in your Content Patcher skin mod's `manifest.json`.

```json
{
   "Name": "Elle's New White Cow",
   ..
   "ContentPackFor": {
      "UniqueID": "Pathoschild.ContentPatcher"
   },
   "Dependencies": [
      {
         "UniqueID": "Paritee.WhiteBulls",
         "IsRequired": true
      }
   ]
}
```

2. In your Content Patcher skin mod's `content.json` replace all `"Action": "Load"` to `"Action": "EditImage"` and change all instances of `Target` to the same that's in your BFAV farm animal's `content.json`. Below is what your Content Patcher skin mod's `content.json` should look like.

```json
{
  "Format": "1.3",
  "Changes": [
       {
          "Action": "EditImage",
          "Target": "Animals/White Bull",
          ..
       },
       {
          "Action": "EditImage",
          "Target": "Animals/BabyWhite Bull",
          ..
       },
    ]
}
```

## Tools

- [Generate Farm Animal Data](https://paritee.github.io/#generate-data-farmanimals-entry)
