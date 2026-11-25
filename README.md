# GSW Pro Android (base de compilation cloud)

Ce dépôt enveloppe la version HTML de GSW Pro dans une application Android WebView et compile un APK debug via GitHub Actions.

## Compilation sans ordinateur
1. Créer un dépôt GitHub vide (par exemple `GSWPro-Android`).
2. Depuis le téléphone, ouvrir le dépôt sur GitHub, choisir **Add file > Upload files** et téléverser tout le contenu de ce dossier (y compris `.github/workflows/android.yml`).
3. Valider avec **Commit changes**.
4. Ouvrir l'onglet **Actions**, sélectionner **Build GSW Pro APK**, puis lancer **Run workflow** si le workflow ne démarre pas automatiquement.
5. Ouvrir l'exécution terminée et télécharger l'artefact **GSW-Pro-APK**. Décompresser l'archive : `app-debug.apk` est le fichier à installer.

## Limites importantes de cette base
- C'est un APK Android de départ qui embarque les deux pages HTML et conserve le stockage local WebView.
- Le canal `BroadcastChannel` actuel ne synchronise pas plusieurs téléphones : il reste limité au contexte du navigateur/appareil. Le serveur LAN Android, la découverte des appareils, la réplication des données et le basculement automatique du serveur ne sont PAS encore implémentés.
- La compilation GitHub produit un APK debug non signé pour publication. Pour une diffusion publique, il faudra configurer une signature de release avec un keystore privé stocké dans les secrets GitHub.
- Le fonctionnement de toutes les fonctions de l'application doit être testé sur appareils Android réels avant usage en production.
