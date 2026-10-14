# Corridor à la maison · paquet Android

Enveloppe Android (Trusted Web Activity, générée par Bubblewrap) de l'application web https://corridor-maison.github.io/.
L'application elle-même vit dans le dépôt `corridor-maison.github.io` ; ce dépôt ne contient que l'emballage.

- `twa-manifest.json` : identifiant `io.github.corridormaison.app`, nom, couleurs, version.
- Le workflow « Construire le paquet Android » produit le bundle (`.aab`) et l'APK **non signés** sur GitHub Actions.
- La signature se fait hors de GitHub, avec la clé d'envoi du fondateur, qui ne quitte pas son poste :
  `zipalign`, `apksigner` pour l'APK, `jarsigner` pour le bundle.
- Le site publie `/.well-known/assetlinks.json` avec les empreintes des clés (envoi et signature Google Play).

Nouvelle version de l'application web : rien à faire ici, l'enveloppe ouvre toujours le site à jour.
Nouvelle version de l'enveloppe : changer `appVersionCode` et `appVersionName` dans `twa-manifest.json` et dans `app/build.gradle`, relancer le workflow, signer, envoyer sur Google Play.
