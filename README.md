# HDF LABYRINTH

Carte de labyrinthe de haies du jeu **HDF LABYRINTH** (F.S.M Game House), construite sur le moteur 3D FSM3D de HDF WALL. Un seul fichier HTML autonome : `index.html`.

- **Jeu à la première personne uniquement** : vue à hauteur des yeux (1,65 m), sans vue à la troisième personne ni zoom, le corps du joueur n'est pas affiché.
- Labyrinthe carré en haies, allées en terre, enceinte et route, clairière centrale, ruines et arches.
- Objectif : atteindre la clairière centrale. Carte complète (touche M, R1 ou Share sur la manette, bouton Carte en tactile), chrono, sans minimap.
- **Mode horreur** (nouveau en 1.2, bouton « Mode horreur » de l'écran titre) : nuit, brouillard et lampe torche ; un gardien rôde, il faut trouver 3 clés pour ouvrir 3 grilles et des haies se déplacent. Le mode classique reste identique.
- Version : HDF LABYRINTH v1.2

## Commandes

| Action | Clavier / souris | Manette PS4 | Tactile |
|---|---|---|---|
| Avancer / reculer / pas de côté | ZQSD, WASD ou flèches | Stick gauche | Stick virtuel gauche |
| Regarder | Souris (clic dans le jeu pour capturer la souris, Échap pour la libérer) | Stick droit | Glisser le doigt |
| Courir | Maj | R2 | Bouton Courir |
| Sprint | Ctrl | L3 (clic du stick gauche, bascule) | — |
| Regard à l'horizon | R | R3 (clic du stick droit) | — |
| Carte complète | M | R1 ou SHARE (ou pavé tactile) | Bouton Carte |
| Pause / menu | Échap ou P | OPTIONS | Bouton ☰ |

Le regard vertical est limité à ±80° et l'on avance dans la direction du regard. Un léger balancement de la marche peut être activé dans les options (désactivé par défaut sur iPad et tablette).

### Manette PS4 (mapping standard, mêmes contrôles que HDF WALL)

| Bouton | En jeu | Dans les menus |
|---|---|---|
| Stick gauche | Déplacement | Navigation haut / bas / gauche / droite |
| Stick droit | Regard (horizontal et vertical) | — |
| Carré (□) | Mode horreur : lampe torche | — |
| Croix directionnelle | — | Navigation (avec répétition) |
| Croix (X) | Mode horreur : ramasser une clé, ouvrir une grille | Valider |
| Rond (O) | — | Retour |
| R2 | Courir | — |
| L3 | Sprint (bascule) | — |
| R3 | Regard à l'horizon | — |
| R1 / SHARE | Carte complète | — |
| OPTIONS | Pause | Fermer le menu de pause |

L2 et les commandes de changement de vue ou de zoom de HDF WALL sont retirées : le jeu reste toujours à la première personne.

## Mode horreur (v1.2)

- **Ambiance** : nuit et brouillard, lampe torche à batterie (environ 5 minutes, elle se recharge lentement quand elle est éteinte), vent, battements de cœur, pas lourds et souffle. Pas de flash ni d'effet stroboscopique ; l'option « Effets réduits » coupe aussi la secousse de caméra et le vacillement de la lampe.
- **Musique angoissante dynamique** (synthétisée en direct, aucun fichier) avec trois états :
  - **calme** : une nappe sombre et discrète ;
  - **tension** (gardien proche, en vue ou qui fouille) : drone grave, cordes dissonantes en trémolo et battement qui accélère quand il approche ;
  - **poursuite** (gardien en chasse) : percussions rythmées et accords dissonants.

  On passe d'un état à l'autre en fondu (environ 1,5 s), et la musique revient au calme en fondu quand il perd votre trace. Un compresseur et un plafond de volume évitent tout son soudain fort. Les réglages Volume, Musique et muet sont respectés ; avec « Effets réduits », la musique est plus douce et les claquements de percussion sont retirés.
- **Le gardien** : une silhouette noire aux yeux rouges. Il patrouille et vous entend courir. Il vous voit dans un cône, si rien ne le cache. Il vous poursuit plus lentement que votre course et perd votre trace si vous disparaissez assez longtemps. S'il vous attrape, l'écran « Capturé » s'affiche : vous repartez de l'entrée en gardant vos clés. Vous avez 3 vies.
- **Endurance** : la course est limitée (environ 7 secondes, barre affichée), elle se recharge à la marche ou à l'arrêt.
- **Clés et grilles** : 3 clés cachées dans des impasses et 3 grilles verrouillées sur le chemin de la clairière. Chaque grille consomme une clé. La partie est toujours faisable (vérifiée par BFS).
- **Haies mouvantes** : toutes les 45 à 90 secondes, dans un grondement, quelques passages se ferment et d'autres s'ouvrent. Le chemin vers la clairière et la sortie n'est jamais coupé.

| Action (mode horreur) | Clavier | Manette PS4 | Tactile |
|---|---|---|---|
| Lampe torche (allumer / éteindre) | F | □ (Carré) | Bouton Lampe |
| Ramasser une clé / ouvrir une grille | E, Entrée ou Espace | ✕ (Croix) | Bouton Agir (ou toucher l'aide affichée) |
| Courir (limité par l'endurance) | Maj (Ctrl sprint) | R2 (L3 sprint) | Bouton Courir |

Les autres commandes sont les mêmes que dans le mode classique. La carte complète montre aussi les grilles et les haies déplacées ; il n'y a pas de mini-carte.

![Aperçu](apercu.png)
