# HDF LABYRINTH

Carte de labyrinthe de haies du jeu **HDF LABYRINTH** (F.S.M Game House), construite sur le moteur 3D FSM3D de HDF WALL. Un seul fichier HTML autonome : `index.html`.

- **Jeu à la première personne uniquement** : vue à hauteur des yeux (1,65 m), sans vue à la troisième personne ni zoom, le corps du joueur n'est pas affiché.
- Labyrinthe carré en haies, allées en terre, enceinte et route, clairière centrale, ruines et arches.
- Objectif : atteindre la clairière centrale. Carte complète (touche M, R1 ou Share sur la manette, bouton Carte en tactile), chrono, sans minimap.
- **Mode horreur** (nouveau en 1.2, bouton « Mode horreur » de l'écran titre) : nuit, brouillard et lampe torche ; un gardien rôde, il faut trouver 3 clés pour ouvrir 3 grilles et des haies se déplacent. Le mode classique reste identique.
- **Nouveau en 1.3 (mode horreur)** : clôture grillagée de 3 m autour de la zone de départ, portail d'entrée qui se referme derrière vous, voiture de police abandonnée gyrophares allumés, lunettes de vision nocturne, piles et roue d'accessoires.
- Version : HDF LABYRINTH v1.3

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
| Carré (□) | Mode horreur : allumer / éteindre l'accessoire équipé (lampe ou lunettes) | — |
| Triangle (△) | Mode horreur : utiliser une pile | — |
| L1 (maintenu) | Mode horreur : roue d'accessoires (viser au stick droit, relâcher pour équiper) | — |
| Croix directionnelle | — | Navigation (avec répétition) |
| Croix (X) | Mode horreur : ramasser une clé, une pile ou les lunettes, ouvrir une grille | Valider |
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

## Mode horreur : nouveautés v1.3

- **Clôture** : un grillage de 3 m entoure la zone de départ dès l'apparition, et un second enclos entoure la sortie nord. On ne peut pas faire le tour du labyrinthe ni passer derrière. La collision est faite pour le rayon du joueur (0,35 m) et la caméra ne traverse jamais le grillage. C'est vérifié par un BFS de collision depuis le point d'apparition et par des milliers de sprints échantillonnés contre la clôture.
- **Portail d'entrée** : il se referme derrière vous dans un « clang » dès que vous êtes dans le labyrinthe, et il est solide. La seule issue est la sortie nord. Après une capture, vous réapparaissez à l'intérieur, devant le portail fermé. L'état du portail est sauvegardé.
- **Voiture de police** : garée devant l'entrée, sans personne autour. Elle est bleue et blanche, avec des vitres sombres et une rampe de gyrophares rouge et bleu.
  - Les feux alternent doucement à 1,5 Hz, sans jamais de blanc ni de flash.
  - Avec « Effets réduits », ils passent à 0,5 Hz et sont plus doux, et la radio de police est coupée.
  - La voiture a une collision.
- **Lunettes de vision nocturne** :
  - Elles sont cachées dans une impasse accessible sans clé (vérifié par BFS).
  - Elles donnent une vue verte amplifiée, avec moins de brouillard et un léger grain, sans flash.
  - Leur batterie dure environ 3 minutes, contre 5 pour la lampe. Éteintes, elles se rechargent très lentement (environ 15 minutes pour une charge complète, contre 7 pour la lampe).
  - Elles ne rendent pas plus discret : le gardien vous repère d'aussi loin qu'avec la lampe. En revanche, ses yeux rouges ressortent nettement.
- **Piles** : 5 piles sont réparties dans le labyrinthe et se ramassent avec le bouton d'action. Chaque pile recharge un accessoire de 50 %.
  - Une pile ramassée va dans la réserve (compteur « Piles » dans le HUD).
  - Si l'accessoire équipé est à 50 % ou moins au moment du ramassage, la pile est utilisée tout de suite.
  - T / △ / bouton « Pile » utilise une pile de la réserve sur l'accessoire équipé. Si vous n'avez rien d'équipé, elle va sur l'accessoire trouvé le plus déchargé. Elle est refusée si la batterie est déjà pleine.
- **Roue d'accessoires** : choix entre la lampe (disponible dès le départ), les lunettes (une fois trouvées) et « Rien ». Le jeu continue pendant que la roue est ouverte ; seule la vue est figée.
- **Sauvegarde** : elle conserve les accessoires trouvés, l'accessoire équipé, les deux batteries, la réserve de piles, les objets ramassés et l'état du portail.

| Action (mode horreur 1.3) | Clavier / souris | Manette PS4 | Tactile |
|---|---|---|---|
| Allumer / éteindre l'accessoire équipé | F | □ (Carré) | Bouton Lampe |
| Roue d'accessoires | Maintenir X, viser à la souris, relâcher | Maintenir L1, viser au stick droit, relâcher | Bouton Accessoire, puis toucher un secteur |
| Utiliser une pile | T | △ (Triangle) | Bouton Pile |
| Ramasser (clé, pile, lunettes) / ouvrir une grille | E, Entrée ou Espace | ✕ (Croix) | Bouton Agir |

## Corrections

- **v1.3, moteur FSM3D (`G.roundBox`)** : avec un rayon `r = 0`, les normales sortaient nulles (faces noires ou mal éclairées selon le GPU). Désormais, chaque sommet prend la normale de sa face, et en mode `unit` cette normale reste à ±1 sur son axe. Rien ne change pour `r > 0` : la sortie est identique octet par octet à la v1.2.

![Aperçu](apercu.png)
