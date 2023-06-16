<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Une partie du code du site est open source, bienvenue pour aider à optimiser la traduction.

## code frontal

* [code frontal](https://github.com/xxai-art/web)
* [Packs de langues pour le site dans son ensemble](https://github.com/xxai-art/web/tree/main/i18n)
* [Packs de langue pour les modules de connexion](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Site Web Documentation multilingue](https://github.com/xxai-doc)

Le langage de programmation frontal est [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , qui ajoute quelques fonctionnalités basées sur la syntaxe coffeescript, voir [./coffee_plus.md](./coffee_plus.md) .

## Internationalisation de sites Web et de documents

S'appuyer sur les 3 projets suivants

### [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

Le modèle de démarquage, avec le suffixe `.mdt` , peut faire référence à des fichiers externes avec une syntaxe similaire à `<+ ./coffee_plus/import.js>` .

[@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

La traduction Markdown ne traduira pas les codes et les liens, et mettra en cache les phrases traduites. Si la traduction est modifiée mais que le texte original n'est pas modifié, l'exécuter à nouveau n'écrasera pas la modification de la traduction.

[@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

Fichiers de langue pour la traduction de sites Web générés par `yaml` .
