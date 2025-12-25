# project-tower-ascension

## Objectif

Développement d’un jeu roguelike au tour par tour en Python dans le cadre d’un projet personnel. Le visuel et l’audio sont volontairement rudimentaires.

## Structure du jeu

1. Le Joueur et ses stats
2. Boucle principale
3. Système de combat

### 1) Le Joueur et ses stats

Un joueur possède les caractéristiques suivantes :
- Des Stats :
    * LVL (Level) : Points permettant d'augmenter qualitativement les autres stats du joueur.
    * HP (Health Points) : Ressource désignant la vie restante du joueur. À 0 ou moins, le joueur est vaincu.
    * SP (Stamina Points) : Ressource pouvant être consommée pour des actions. À 0 ou moins, le joueur subit 50 % de dégâts supplémentaires.
    * MP (Mystic Points) : Ressource pouvant être consommée pour des actions. À 0 ou moins, le joueur inflige 50 % de dégâts en moins.
- Une Classe : Détermine la répartition initiale des statistiques du joueur.
    * Warrior (Guerrier) : HP élevé, SP moyen et MP faible.
    * Mystic (Mystique) : MP élevé, HP moyen et SP faible.
    * Vagabond : SP élevé, MP moyen et HP faible.
- Un Équipement : 
    * Armor (Armure) : Ajoute des HP supplémentaire.
    * Weapon (Arme) : Ajoute de la puissance supplémentaire.
    * Artifact (Artifact) : Offre une variété de bonus différents.
- Un Inventaire : Permet de stocker, avec une capacité limitée, divers objets et équipements.

### 2) Boucle principale

La boucle principale du jeu s’articule autour des zones et des sections. Une partie se déroule en explorant 6 zones, chaque zone étant constituée de 5 sections. 
Une partie commence dans une sections aléatoire d'une zone aléatoire. Après complétion de la zone, le joueur doit ensuite choisir la prochaine section parmi 2 possibilités. Ce processus se répète jusqu’à la dernière section, où le joueur affronte un boss, un ennemi plus puissant. Après avoir vaincu le boss, le joueur doit choisir la prochaine zone parmi 2 possibilités (hormis la 6ème zone qui est spéciale).

Concernant les Zones et les Sections, voici des précisions.
- Les Zones : Elles ont un type, un rang et une météo
    * Le type désigne le thème général de la zone. Il détermine le visuel, les ennemi rencontrés et le type de butin obtenu.
    * Le rang désigne l'étage correspondant de la zone. Il dicte la difficulté des combats, la qualité des butins ainsi que le LVL du joueur.
    * La météo désigne un attribut spécifique de la zone. Il permet d'offrir de la variété dans l'exploration.
- Les Sections : Elles se déclinent en trois types différents
    1) Combat : Affronte un ennemi et collecte un butin
    2) Event (Évennement) : Fait un choix entre plusieurs possibilités pour obtenir une récompense ou un malus
    3) Supply (Ravitaillement) : Vends et/ou achète de objets grâce à l'or obtenu en butin

### 3) Système de combat

Les combats se déroulent au tour par tour. À chaque tour, le joueur choisit une action, puis l’ennemi agit à son tour. Ces actions permettent d’infliger des dégâts, de se défendre ou d’utiliser des objets. Les actions disponibles dépend de la classe, de l'équipement et du LVL.

Chaque attaque est définie par trois caractéristiques principales :
    1) Base Power (Puissance de base): Désigne la quantité de dégâts bruts infligés.
    2) Cost (Coût) : Désigne les (ou les) ressources devant être mées pour l'attaque.
    3) Condition : Désigne les restrictions pour savoir qui peut utiliser cette attaque. Souvent, elle dépend du LVL et/ou de le classe.

Voici également les formules de dégâts:

`dmg_dealt = (base_power + bonus_power) * crit_mult * low_mp`\
`dmg_taken = (dmg_dealt - dmg_mitigation) * low_sp`

- base_power : Vient des attaques
- bonus_power : Vient des artéfacts
- crit_mult : Vient des attaques et/ou des artéfacts (généralement vaut 2.5)
- low_mp : Vient du malus en cas de MP vide
- dmg_mitigation : Vient des artéfacts
- low_sp : Vient du malus en cas de SP vide

## Technologies utilisées

- Python 3.11
- PyGame
- JSON (sauvegarde)

## Auteur

- Raphaël Ducteil
- ENSSAT