# Dividendes Degiro

Outil gratuit qui prépare la déclaration des **dividendes étrangers** (formulaire **2047**) à partir du relevé de compte du courtier **Degiro**.

## Vos données restent chez vous

Le relevé est lu et calculé **entièrement dans votre navigateur**. Il n'est envoyé nulle part :

- la page ne charge aucune ressource externe (ni police, ni bibliothèque, ni statistiques de visite) ;
- une règle de sécurité intégrée à la page (*Content-Security-Policy*) interdit au navigateur toute connexion sortante ;
- le code est public : chacun peut vérifier ce qu'il fait.

La page fonctionne aussi hors ligne : vous pouvez télécharger `index.html` et l'ouvrir depuis votre ordinateur.

## Utilisation

1. Sur le site Degiro, exportez votre **relevé de compte** (rubrique *Activité → Relevé de compte*) au format **.xlsx** ou **.csv**, en couvrant **tout l'historique depuis l'ouverture du compte** et jusqu'à mi-janvier de l'année suivant celle déclarée (certaines conversions de devises de fin décembre sont passées début janvier).
2. Ouvrez l'outil et choisissez le fichier, ou glissez-le sur la page.
3. Sélectionnez l'année à déclarer.

## Ce que fait l'outil

| Onglet | Contenu |
|---|---|
| **Par pays (2047)** | Brut, retenue à la source, net, frais et net encaissé en euros, par pays de source |
| **Par société** | Montants en devise et en euros, taux de retenue appliqué |
| **Suivi et formules** | Dividendes nets mois par mois, formules prêtes à coller dans un tableau de suivi (Google Sheets) |
| **À vérifier** | Cas particuliers repérés sur tout l'historique |
| **Détail des dividendes** | Chaque dividende avec son taux de change et ses frais théoriques |

### Règles de calcul

- **Conversion en euros** : chaque dividende est converti au taux de l'opération de change Degiro qui l'a **réellement** converti. Les conversions sont rapprochées par montant, dans l'ordre chronologique, y compris lorsque Degiro regroupe plusieurs dividendes dans une même conversion ou les convertit en plusieurs fois.
- **Retenue à la source** : rattachée à son dividende par recalcul du taux du pays (Japon 15,315 %, Canada 25 %, États-Unis 15 %), puis par ISIN, date et heure. Les régularisations ultérieures sont rattachées au dividende d'origine.
- **Frais Custody Degiro** : 1 € + 3 % du dividende net de retenue, plafonnés à 10 %. Ils sont rattachés par recalcul, y compris les frais prélevés en rattrapage plusieurs semaines après le dividende.
- **Opérations sur titres** (changement d'ISIN, fractionnement, modification d'instrument) : l'historique de l'ancien titre est rattaché au nouveau.
- **Pays** : celui de l'ISIN (2 premières lettres). Les ISIN « BMG » (sociétés des Bermudes cotées à Hong Kong) sont rattachés à Hong Kong.
- **Arrondis** : deux règles au choix, *brut, retenue et frais convertis séparément* ou *net converti en une fois* (comme le crédit en euros de Degiro). L'écart est de quelques centimes sur une année.

## Limites

- Seuls les **dividendes** sont traités pour l'instant. Les plus-values de cession (formulaire 2074, méthode du prix moyen pondéré) ne le sont pas encore.
- Seuls les relevés Degiro **en français** sont reconnus.
- Les **remboursements de capital** sont traités comme des dividendes et signalés dans l'onglet « À vérifier » : leur traitement fiscal est à vérifier au cas par cas.
- **Ce n'est pas un conseil fiscal.** L'outil est une aide au calcul : vérifiez les montants avant de les reporter sur votre déclaration.

## Signaler un problème

Ouvrez une *issue* sur ce dépôt en décrivant le cas. Si possible, joignez quelques lignes du relevé concerné, **anonymisées** (sans soldes, sans identifiants d'ordre, sans IBAN).

## Soutenir

Si cet outil vous a fait gagner du temps, vous pouvez m'offrir un café : https://ko-fi.com/vfxtdwiki ☕

## Auteur

Nicolas, ancien expert-comptable spécialisé en consolidation et reporting, aujourd'hui *technical director* Unreal Engine pour la télévision et le cinéma.

## Licence

© 2026 Nicolas. Code publié sous licence **GNU AGPL v3.0** ou ultérieure : voir le fichier [`LICENSE`](LICENSE).
Vous pouvez utiliser, étudier, modifier et redistribuer ce code. Toute version modifiée, y compris proposée comme service en ligne, doit être publiée sous la même licence, avec son code source.
