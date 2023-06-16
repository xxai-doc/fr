<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Il est recommandé d'installer d'abord nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) , puis `direnv allow` après être entré dans le répertoire ( [le .envrc](https://github.com/xxai-art/doc/blob/main/.envrc) sera exécuté automatiquement après être entré dans le répertoire).

La signification est la suivante : traduction du chinois vers le japonais, le coréen, l'anglais, la traduction de l'anglais vers toutes les autres langues. Si vous souhaitez uniquement prendre en charge le chinois et l'anglais, vous pouvez simplement écrire `zh: en` .

La signification est la suivante : traduction du chinois vers le japonais, le coréen, l'anglais, la traduction de l'anglais vers toutes les autres langues. Si vous souhaitez uniquement prendre en charge le chinois et l'anglais, vous pouvez simplement écrire `zh: en` .

* [code frontal](https://github.com/xxai-art/web)
* [Packs de langues pour le site dans son ensemble](https://github.com/xxai-art/web/tree/main/i18n)
* [Packs de langue pour les modules de connexion](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Site Web Documentation multilingue](https://github.com/xxai-doc)

Le langage de programmation frontal est [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , qui ajoute quelques fonctionnalités basées sur la syntaxe coffeescript, voir [./coffee_plus.md](./coffee_plus.md) .

## Internationalisation de sites Web et de documents

S'appuyer sur les 3 projets suivants

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Le suffixe est `.mdt` , vous pouvez utiliser la syntaxe similaire à `<+ ./coffee_plus/import.js>` pour faire référence à des fichiers externes et générer une démarque avec le suffixe `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  La traduction Markdown ne traduira pas les codes et les liens, et mettra en cache les phrases traduites. Si la traduction est modifiée mais que le texte original n'est pas modifié, l'exécuter à nouveau n'écrasera pas la modification de la traduction.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Fichiers de langue pour la traduction de sites Web générés par `yaml` .

### Instructions d'automatisation de la traduction de documents

Voir référentiel de code [xxai-art/doc](https://github.com/xxai-art/doc)

Il est recommandé d'installer d'abord nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) , puis `direnv allow` après être entré dans le répertoire ( [le .envrc](https://github.com/xxai-art/doc/blob/main/.envrc) sera exécuté automatiquement après être entré dans le répertoire).

Afin d'éviter la grande base de code traduite dans des centaines de langues, j'ai créé une base de code distincte pour chaque langue et créé une organisation pour stocker la base de code

La définition de la variable d'environnement `GITHUB_ACCESS_TOKEN` , puis l'exécution [de create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) créeront automatiquement le référentiel de code.

Bien sûr, vous pouvez également le mettre dans une base de code.

Référence du script de traduction [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Le code du script est interprété comme suit :

[bunx](https://bun.sh/docs/cli/bunx) remplace npx, qui est plus rapide. Bien sûr, si vous n'avez pas installé bun, vous pouvez utiliser `npx` à la place.

`bunx mdt zh` rend `.mdt` dans le répertoire zh en tant que `.md` , voir les 2 fichiers liés ci-dessous

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` est le code de base pour la traduction (si vous n'avez installé que `nodejs` , mais que `bun` et `direnv` ne sont pas installés, vous pouvez également exécuter `npx i18n` pour traduire).

Il analysera [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , la configuration de `i18n.yml` dans ce document est la suivante :

```
en:
zh: ja ko en
```

La signification est la suivante : traduction du chinois vers le japonais, le coréen, l'anglais, la traduction de l'anglais vers toutes les autres langues. Si vous souhaitez uniquement prendre en charge le chinois et l'anglais, vous pouvez simplement écrire `zh: en` .

Le dernier est [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , qui extrait le contenu entre le titre principal et le premier sous-titre `README.md` de chaque langue pour générer une entrée `README.md` . Le code est très simple, vous pouvez le regarder vous-même.

L'API Google est utilisée pour la traduction gratuite. Si vous ne pouvez pas accéder à Google, veuillez configurer et définir un proxy, tel que :

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Le script de traduction générera un cache traduit dans le répertoire `.i18n` , veuillez le vérifier avec `git status` et l'ajouter au référentiel de code pour éviter les traductions répétées.

Veuillez exécuter `bunx i18n` chaque fois que vous modifiez la traduction pour mettre à jour le cache.

Si le texte original et la traduction sont modifiés en même temps, le cache sera confus, donc si vous voulez en modifier, vous ne pouvez en modifier qu'un, puis exécutez `bunx i18n` pour mettre à jour le cache.
