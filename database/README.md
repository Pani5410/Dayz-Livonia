# DayZ Livonia object database

This folder is the working database for generating DayZ Editor/Object Spawner locations.

## Current state

`Classnames` is the raw source currently available in the repository. It contains a mixture of:

- placeable/world objects;
- inventory items;
- weapons and clothing;
- generic/base script classes;
- mod/base-game classes.

The first database file, `candidate_placeable_objects.json`, contains only candidates that are useful for location construction. They are **not yet marked as fully verified DayZ Editor objects**.

## Verification rule

A classname becomes `verified` when we can confirm it from one of these sources:

1. a DayZ Editor export JSON containing that `name`;
2. a relevant `CfgVehicles`/`config.cpp` definition;
3. another authoritative mod source that defines the object as a usable world entity.

This prevents us from inventing classnames when generating locations.

## Target structure

The database will eventually contain categories such as:

- buildings
- industrial
- military
- roads/urban props
- fences and barriers
- containers/storage
- generators/electrical
- furniture/interior
- vehicles/static objects
- vegetation/decoration
- signs
- mod-specific objects

Each verified object should eventually store its classname, source/mod, category, and notes relevant to DayZ Editor placement.

## Next input required

For a reliable Livonia placement library, add a DayZ Editor export JSON to the repository, for example:

`exports/livonia/sample_location.json`

Once such an export is available, the object `name` fields can be extracted automatically and used as the verified classname library for future generated locations.
