# HDF LABYRINTH 1.1.1

Jeu de labyrinthes de haies à la première personne de **F.S.M Game House**, construit sur le moteur 3D FSM3D de HDF WALL. Tout tient dans un seul fichier HTML autonome : `index.html`.

**Version 1.1.1** : correctif de la **roue des accessoires** du mode Horreur, qui ne permettait pas de choisir un accessoire.

- La roue est maintenant cliquable et tactile (elle était recouverte par une couche d'interface qui ignorait les touchers et les clics). Sur tablette, le toucher sur « Accessoire » ouvre la roue, puis un toucher sur Lampe, Lunettes NV ou Rien équipe l'accessoire.
- Manette : maintenir L1 et pousser le stick droit, ou utiliser ◀ ▶, puis relâcher L1. Un **appui bref** sur L1 passe à l'accessoire suivant.
- Clavier : maintenir X, puis touches 1 (lampe), 2 (lunettes), 3 (rien), ou un appui bref sur X pour passer au suivant.
- Souris : le survol sélectionne, le clic valide. Les lunettes non trouvées ne peuvent plus être visées par erreur.

**Version 1.1** : un **coéquipier** vous accompagne dans les deux modes (voir la section « Coéquipier »). Il fonctionne entièrement en local, sans réseau ; une couche IA facultative (OpenRouter, Claude Haiku 5.5 par défaut) peut le piloter si une clé est fournie. Les sauvegardes 1.0.x restent compatibles et la génération des labyrinthes est inchangée.

**Version 1.0.2** : son et confort audio, sans changement du jeu, des commandes ni du moteur.

- Le son s'active à la manette : chaque bouton relance le contexte audio. Les navigateurs (Chrome, Safari, iPad) refusent cependant de démarrer le son tant qu'il n'y a eu ni clic, ni toucher, ni touche du clavier. Tant que le son est suspendu, une invite discrète l'indique (« Appuie sur ✕ / un bouton pour activer le son », puis « touche l'écran ou clique une fois » si la manette seule ne suffit pas). Elle disparaît dès que le son joue.
- Le son reprend tout seul après un onglet en arrière-plan, une mise en veille ou une interruption iOS.
- Les menus ont leurs sons à la manette : déplacement à la croix, validation avec ✕, retour avec ○.
- Les sons ne se chevauchent plus :
  - un même son déclenché deux fois de suite (manette et clic, ou plusieurs appels dans la même image) ne joue qu'une fois ;
  - le nombre de voix est plafonné par catégorie (interface, pas, effets, musique) ;
  - la musique d'exploration s'efface en fondu à l'entrée du mode horreur.
- Affichage : sur les écrans bas (téléphone en paysage), seules les deux notifications les plus récentes restent visibles, pour ne plus recouvrir l'aide au centre de l'écran. L'invite du son se place dans le flux des menus et des notifications sans rien chevaucher.
- Moins de coupures :
  - la musique est programmée au fil de l'eau sur l'horloge audio, et non plus 170 notes d'un coup ;
  - les nœuds audio terminés sont libérés et les boucles inutilisées arrêtées ;
  - la musique d'horreur muette est débranchée ;
  - les percussions de poursuite sont calées sur l'horloge audio.

**Version 1.0.1** : corrections d'affichage de l'interface, sans changement du jeu, des commandes ni du moteur.

- Sur les petits écrans (800 × 500, iPhone en paysage, iPad), l'écran titre tient en entier : toutes les entrées du menu, dont « Aide », restent accessibles, et le pied de page ne recouvre plus le menu.
- Les notifications et les aides d'action ne recouvrent plus le cadre d'objectif.
- Le briefing, la pause, la fin de niveau et les pages longues (options, aide, carnet) défilent, y compris à la manette, et leurs boutons restent visibles.
- Les zones sûres de l'iPhone et de l'iPad sont respectées, et les libellés des boutons tactiles sont centrés.

**Version 1.0** : c'est la première version complète. Elle propose deux campagnes, **Exploration** et **Horreur**. Chaque labyrinthe est généré aléatoirement, comporte des objectifs à remplir et raconte un épisode d'une histoire suivie.

## Écran titre

- **Exploration** : reprend votre campagne Exploration, ou en commence une nouvelle s'il n'y en a pas.
- **Horreur** : fonctionne de la même façon pour la campagne Horreur.
- **Continuer** : reprend la dernière campagne jouée, au labyrinthe où vous vous êtes arrêté.
- **Nouvelle campagne** : choix du mode, avec une **graine** facultative. Une même graine redonne exactement les mêmes labyrinthes, objectifs et textes.
- **Records**, **Options**, **Aide**, **Réinitialiser** (efface les campagnes sauvegardées).

Tous les menus se pilotent à la manette PS4, au clavier ou au toucher. Chaque mode a sa propre sauvegarde et ses propres records : plus haut labyrinthe atteint, nombre de labyrinthes franchis, chapitres terminés et meilleurs temps.

## Déroulement d'un labyrinthe

1. **Briefing** : le chapitre, le titre de l'épisode, le récit et la liste des objectifs. La graine y est affichée. Le labyrinthe se construit pendant ce temps, par étapes, sans bloquer l'écran.
2. **Objectifs** : il faut les remplir avant de pouvoir sortir. Selon le niveau, on trouve :
   - des feuillets ou pages à lire (chacun révèle un morceau d'histoire et s'ajoute au carnet) ;
   - une relique à rapporter ;
   - des lanternes à allumer ;
   - des sceaux à activer **dans l'ordre** (I, II, III…) ;
   - un levier ;
   - des portes de bois qui s'ouvrent chacune avec sa clé (clé → porte → clé suivante…).
3. **Clairière centrale**, puis **sortie au nord**. La herse de la sortie ne se lève qu'une fois tous les objectifs remplis et la clairière atteinte.
4. **Fin du labyrinthe** : un temps, un record éventuel et la suite du récit. Vous pouvez alors passer au labyrinthe suivant, rejouer le même ou revenir au titre.

Chaque partie est garantie faisable : le générateur vérifie par parcours en largeur (BFS) que tout est atteignable, y compris la chaîne clés/portes. Le menu pause donne accès au **carnet**, qui rassemble l'objectif en cours, la progression et les pages déjà lues.

## Mode Exploration (de jour)

Ambiance sérieuse mais calme, sans monstres. La difficulté monte de niveau en niveau :

| Labyrinthe | Taille | Objectifs |
|---|---|---|
| 1 | 9 × 9 | 1 feuillet, 1 relique |
| 2 | 11 × 11 | 2 feuillets, 1 relique |
| 3 | 13 × 13 | 2 feuillets, 2 lanternes, 1 relique |
| 4 | 15 × 15 | 3 feuillets, 3 lanternes, 1 porte à clé |
| 5 | 17 × 17 | 3 feuillets, 3 sceaux ordonnés, 1 porte |
| 6 | 19 × 19 | 3 feuillets, 3 sceaux, levier, 1 porte, relique |
| 7 | 21 × 21 | 4 feuillets, 3 lanternes, 4 sceaux, levier, 2 portes + temps conseillé |
| 8 | 23 × 23 | idem + relique |
| 9 et + | 25 × 25 | 4 feuillets, 4 lanternes, 5 sceaux, levier, 3 portes, relique + temps conseillé qui se resserre |

À partir du labyrinthe 7, un **temps conseillé** est affiché. Il n'entraîne aucune pénalité : seul le record le prend en compte.

## Mode Horreur (de nuit)

Le mode reprend la même structure que l'Exploration, avec en plus tout le mode horreur de la v1.3 :
- nuit et brouillard ;
- gardien(s) ;
- clés et grilles ;
- haies mouvantes ;
- lampe, lunettes de vision nocturne et piles, avec la roue d'accessoires (L1) ;
- clôture, portail qui se referme et voiture de police ;
- musique dynamique.

| Labyrinthe | Taille | Grilles | Gardiens | Pages | Haies mouvantes |
|---|---|---|---|---|---|
| 1 | 11 × 11 | 1 | 1 (plus lent) | 1 | 6 |
| 3 | 15 × 15 | 2 | 1 | 2 | 10 |
| 5 | 19 × 19 | 3 | 1 | 2 | 16 |
| 6 | 21 × 21 | 3 | 2 | 3 | 18 |
| 8 et + | 25 × 25 | 4 | 2 (plus rapides, perception accrue) | 3 | 24 |

Au fil des niveaux, la lampe dure moins longtemps, les piles se font plus rares et les haies bougent plus souvent. Aucun flash ni effet stroboscopique : l'option « Effets réduits » est conservée.

## Récit

Les deux campagnes suivent le fil de *L'Atlas des haies*, l'œuvre inachevée d'une cartographe fictive. Le récit avance en arcs de 5 à 7 labyrinthes, chacun avec ses chapitres, ses temps forts et un épilogue. Douze prémisses sont prévues, six de jour et six de nuit. Les textes sont choisis de façon déterministe à partir de la graine, et les morceaux d'histoire ne se répètent pas avant de nombreux niveaux. Chaque briefing s'ouvre aussi sur une ligne d'ambiance (météo, lumière, bruits), tirée de la graine parmi douze par mode : deux campagnes ne commencent donc pas tout à fait de la même façon.

## Coéquipier

Un compagnon, dont le prénom et le caractère sont tirés de la graine, marche avec vous. Le jeu reste à la première personne : on le croise du regard, il ne gêne jamais.

- **Il suit** le joueur par le chemin le plus court (BFS sur le labyrinthe) et respecte les murs. Il n'a pas de collision : il ne bloque ni le joueur ni les portes. S'il se retrouve trop loin ou coincé, il réapparaît discrètement derrière vous, hors du champ de vision.
- **Il aide** : il signale ou ramasse les objets proches (ils vont toujours dans votre inventaire), et sur appel (**C**, **L2** ou le bouton tactile « Coéquipier ») il donne un indice sur un objectif **déjà découvert**. Il ne révèle jamais la sortie ni un objectif inconnu, et ne garde jamais une clé indispensable.
- **En Horreur**, il a peur : il se cache et n'attire jamais le gardien.
- Son état s'affiche dans le HUD et dans les Options : « Coéquipier : local », « IA » ou « hors ligne ».

### Options

Coéquipier (oui/non) · Cerveau (local ou IA) · Appels IA (toutes les 2, 3 ou 5 s, ou jamais) · Modèle IA (Claude Haiku 5.5 par défaut, GPT-6 Luna, Mercury 3) · champ « Clé perso » · Enregistrer la clé · Effacer la clé · Tester la connexion. Tout se règle aussi à la manette PS4.

### Couche IA facultative

- Sans clé, **aucune requête n'est envoyée** : le coéquipier reste local et le jeu marche hors ligne.
- Avec une clé, le jeu envoie au plus une petite requête à la fois (un état JSON compact, sans la position de la sortie), toutes les ~3 s, avec des plafonds de 30 par minute et 400 par partie, un délai de 4 s et une attente croissante après une erreur. La réponse doit être une action d'une liste fermée (suivre, aller_a, ramasser, ouvrir, activer_levier, attendre, avertir, se_cacher). Toute réponse invalide, interdite ou injoignable est ignorée, et le coéquipier repasse en local.
- **Où mettre la clé** :
  - soit dans le jeu, Options → « Clé perso » : elle est rangée dans le stockage local de l'appareil, n'est jamais réaffichée, et le bouton « Effacer la clé » la supprime ;
  - soit dans le code, constante `COEQ_CLE_API` en tête de la section `/* <<COÉQUIPIER 1.1>> */` de `index.html` (vide par défaut).
- ⚠️ Une clé écrite dans `index.html` publié sur GitHub Pages est **lisible par n'importe qui**. N'y mettez qu'une clé dédiée, à crédit plafonné, ou préférez le champ des Options.

## Commandes

| Action | Clavier / souris | Manette PS4 | Tactile |
|---|---|---|---|
| Avancer / reculer / pas de côté | ZQSD, WASD ou flèches | Stick gauche | Stick virtuel gauche |
| Regarder | Souris (clic pour capturer, Échap pour libérer) | Stick droit | Glisser le doigt |
| **Agir** (lire, prendre, allumer, activer, ouvrir) | E, Entrée ou Espace | ✕ (Croix) | Bouton Agir (ou toucher l'aide affichée) |
| Courir | Maj | R2 | Bouton Courir |
| Sprint | Ctrl | L3 (bascule) | — |
| Regard à l'horizon | R | R3 | — |
| Carte complète | M | R1 ou SHARE | Bouton Carte |
| Pause / carnet | Échap ou P | OPTIONS | Bouton ☰ |
| Horreur : lampe ou lunettes | F | □ | Bouton Lampe |
| Horreur : pile | T | △ | Bouton Pile |
| Horreur : roue d'accessoires | Maintenir X | Maintenir L1 | Bouton Accessoire |
| Appeler le coéquipier | C | L2 | Bouton Coéquipier |

Les commandes sont les mêmes que dans HDF WALL. Le jeu se joue uniquement à la première personne, sans mini-carte ; la carte complète reste disponible et montre les objectifs déjà aperçus, les portes et la herse.

## Technique

- Chaque niveau tire sa graine de la graine de campagne. Les labyrinthes vont de 9 × 9 à 25 × 25 et chacun est vérifié par BFS.
- La construction se fait par étapes derrière le briefing, donc sans gel sur iPad. Au plus grand niveau, on reste sous le budget iPad (moins de 150 Mo, environ 500 k triangles au maximum).
- Le correctif du moteur `G.roundBox` (r = 0) de la v1.3 est conservé.
- Les parties 1.x (v1.0 à v1.3) sont remplacées par les campagnes 1.0. Les options sont conservées.

![Aperçu](apercu.png)
