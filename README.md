# project-tower-ascension

Jeu roguelike au tout par tour en Python dans le cadre d'un projet personnel.

## Structure du jeu

1. Le Joueur et ses stats
2. Boucle principale
3. Système de combat

### 1) Le Joueur et ses stats

Un Joueur possède 4 caractéristiques:
- Des stats :
    * HP (Health Points) : Ressource désignant la vie restant du joueur. A 0 ou moins, le joueur est vaincu.
    * SP (Stamina Points) : Ressource pouvant être consommé pour des actions. A 0 ou moins, prend 50% plus de dégâts.
    * MP (Mystic Points) : Ressource pouvant être consommé pour des actions. A 0 ou moins, délivre 50% moins de dégâts.
- Une classe : Décide de la répartition intiale des stats du Joueur. 
    * Warrior (Guerrier) : HP élevé, SP moyen et MP faible.
    * Mystic (Mystique) : MP élevé, HP moyen et SP faible.
    * Vagabond : SP élevé, MP moyen et HP faible.
- Un Equipement : 
    * Armor (Armure) : Ajoute des HP supplémentaire.
    * Weapon (Arme) : Ajoute de la puissance supplémentaire.
    * Artifact (Artifact) : Offre une variété de bonus différents.
- Un Inventaire : Permet de conserver, avec une place limité, divers items et équipements pour le joueur

### 2) Boucle principale

La boucle principale tourne autour des Zones et des Sections. Une partie se déroule en explorant 6 zones, chaque zone étant consituée de 5 sections. 
Une partie commance dans une sections aléatoire d'une zone aléatoire. Après complétion de la zone, le joueur doit ensuite choisir la prochaine section parmis 2 possibilité. Cela ce répéte jusqu'a la dernière section où il affronte un boss, un ennemie plus puissant. Après avoir vaincu le boss, le joueur doit chisir la prochaine zone parmis 2 possibilité (hormis la 6ème zone qui est spéciale).

Concernant les Zones et les Sections, voici des précisions.
- Les Zones : Elles ont un type, un rang et une météo
    * Le type désigne le thème générale de la zone. Il dicte le visuel, les enemies rencontré et le genre de butin à récolter.
    * Le rang désigne l'étage correspondant de la zone. Il dicte la difficulté des combats mais aussi de la qualité des butins
    * La météo  
## Technologies utilisées

- Python 3.11
- PyGame
- JSON (sauvegarde)

## Auteur

- Raphaël Ducteil
- ENSSAT