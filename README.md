# LocoMobileExport
An exporter script for Localise.biz projects for iOS and Android projects

## How to use it?

1. Put ```loco_exporter.sh``` in your project folder.
2. Run script with the desired options


### Android example
Script placed in the app module, not the root folder.
```
# This imports the Swedish strings that are shared or android specific as app default language
shloco_exporter.sh android --key <loco-api-key> --map "values-sv=values" --tag "shared,android" --output "src/se/res"
# This imports the Swedish plural strings that are shared or android specific as app default language
sh loco_exporter.sh android --key <loco-api-key> --map "values-sv=values" --tag "plurals" --plurals true --output "src/se/res"
# This imports the English, Swedish and Norwegian (multilangual project) strings that are shared or android specific as app default language. English as default.
sh loco_exporter.sh android --key <loco-api-key> --map "values-en=values"  --map "values-sv=values-sv" --map "values-no=values-no" --tag "shared, android" --plurals true --output "src/se/res"
```

### iOS example
```
# This imports the Swedish strings that are shared or ios specific, --output (in this case viktklubbapp) is path to directory containing *.lproj relative to where import script is
sh loco_import.sh ios --key <loco-api-key> --map "sv=sv" --tag "shared,ios" --output "viktklubbapp"
# This imports the Swedish plural strings, --output (in this case viktklubbapp) is path to directory containing *.lproj relative to where import script is
sh loco_import.sh ios --key <loco-api-key> --map "sv=sv" --tag "plurals" --plurals true  --output "viktklubbapp"
# This imports the Swedish and Norwegian strings that are shared or ios specific, --output (in this case viktklubbapp) is path to directory containing *.lproj relative to where import script is
sh loco_import.sh ios --key <loco-api-key> --map "sv=sv" --map "no=nb" --tag "shared,ios" --output "viktklubbapp"
```

[Clipy](https://clipy-app.com/) is a great help for having a quick access to code snippets like this one.

## Options

Option | Explanation
------- | -------
{Platform} | `ios` or `android`
--key | API Key from localise.biz
--output | Path to the folder containing localization file. Relative to the script placement.
--map (iOS) | `en_US` on localise.biz exports, `en.lproj` in the xcode project, use `--map 'en_US=en'`, can map as many as you want to meet your project setup.
--map (Android) | use `--map 'values-sv=values'`, can map as many as you want to meet your project setup. If you support multiple languages use like `--map 'values-sv=values-sv' --map 'values-no=values-no'`. Right side is your project value folder. If you do  `--map 'values-sv=values'` you'll be getting Swedish as a default language.
--tags (optional) | Coma separated Loco tags
--plurals (optional) | `true` if resources should be exported as plural resource file


