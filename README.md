# DRAFT Blockchain et crypto-actifs
Objectif : rédiger un article introductif à la Blockchain, aux crypto-actifs et à l'impact de ces technologies sur un business.

Plan v1
  Introduction
  1/ Bitcoin
    a/ Présentation
    b/ Avantages et inconvénients
    c/ Développements
  2/ Généralisation
    a/ Cryptoactifs
    b/ Blockchains et DLT
    c/ Fonctions que peuvent remplir ces technologies
  3/ Cas d'usage
    a/ Grille de lecture --> dans quel cas une blockchain est-elle intéressante ?
    b/ Exemples de mise en oeuvre (Ripple (protocole, pas le token), Quorum, Hyperledger, Carrefour/Walmart, Banque de France, etc.)
    c/ Applications décentralisées
  4/ Perspectives
    a/ Difficultés (scalabilité, réglementation (pas aboutie, RGPD, etc.), gouvernance/consensus, ...)
    b/ Propositions et expérimentations
  Conclusion

  **1/ Bitcoin**\\
    a/ Présentation\\
    Bitcoin est un protocole d'échange de valeurs de pair à pair, introduit en 2008 par Satoshi Nakamoto dans son whitepaper "Bitcoin : a peer-to-peer electronic cash system". Ce protocole est l'aboutissement du travail débuté dans les années 90 par les cypherpunks, groupe formé aux prémisses d'internet autour de la volonté de préserver la vie privée. Leur constat à l'époque était qu'internet allait  créer un monde de plus en plus connecté, où les données personelles seraient de plus en plus exposées. Il leur semblait alors primordial de créer des outils pour renforcer la confidentialité de ces données personelles et maintenir la vie privée des utilisateurs d'internet. Leurs efforts se sont ainsi concentrés sur la création d'une monnaie électronique, qui ne serait contrôlée par aucune entité et permettrait de s'échanger de la valeur sur internet sans compromettre les informations personnelles des utilisateurs. PLusieurs tentatives ont vu le jour entre 1990 et 2008, comme Hashcash ou Bit-Gold, mais ce n'est qu'en 2008 avec Bitcoin que cette problématique trouvait une réponse complète.\\
    Bitcoin repose sur plusieurs briques technologiques pour assurer la fiabilité et la sécurité de son système monétaire :\\
      - un réseau pair-à-pair qui diffuse et valide l'information ;\\
      - une chaîne de données horodatée qui assure la traçabilité de l'information ;\\
      - un algorithme de signature électronique (ECDSA) qui authentifie les transactions ;\\
      - un algorithme de consensus qui unifie l'état de chaque participant et l'inscrit dans la blockchain ;\\
      - une incitation économique qui aligne les intérêts des participants.\\

   **Réseau pair-à-pair**\\
      Le réseau pair-à-pair de Bitcoin est constitué de noeuds, des ordinateurs qui font tourner un des logiciels open-source qui implémente le protocole Bitcoin. Chaque noeud est connecté à un ensemble d'autres noeuds, mais pas nécessairement à tous. Ces noeuds peuvent, sans communiquer les uns avec les autres, rédiger un ensemble de transactions. Une fois ses transactions prêtes, chaque noeud les diffuse à l'ensemble du réseau. Il utilise pour cela la technique du *flooding* : le noeud envoie ses informations à ses voisins, ceux avec qui il a une connexion directe, qui relaient cette information à leurs propres voisins, et ainsi de suite jusqu'à ce que l'ensemble du réseau ait l'information.\\
      Une fois ces transactions reçues, chaque noeud a la responsabilité individuelle de vérifier leur validité. Il utilise pour cela la blockchain publique dont il a une copie - comme tous les autres noeds - et vérifie que les bitcoins dépensés par ces transactions ont bien été acquis en nombre suffisant par ceux qui les dépensent.

   **Chaîne horodatée**\\
      Les transactions validées par les noeuds du réseau sont assemblées dans des blocs par des noeuds particuliers, appelés "mineurs". Chaque bloc contient l'empreinte cryptographique, le hash, du bloc précédent ainsi que son horodatage. Les blocs sont ainsi reliés les uns aux autres, ce qui a initialement inspiré le terme de blockchain pour qualifier cette technologie. L'horodatage permet d'assurer à tous les noeuds du réseau que le nouveau bloc a bien été construit après le précédent, puisqu'il doit inclure son empreinte cryptographique et par conséquent son horodatage.\\
      Cette structuration des données en chaîne facilite la validation des transactions : pour vérifier qu'une transaction est légitime, il suffit au noeud de retracer l'historique des bitcoins dépensés par les transactions an parcourant la chaîne. Ils s'assurent ainsi que ces bitcoins ont bien été créés selon le protocole Bitcoin, et que l'utilisateur qui cherche à les dépenser les a bien en sa possession.

   **Signature électronique**\\
      Chaque utilisateur de Bitcoin est identifié sur le réseau par son adresse publique. Il s'agit d'un identifiant qui peut être communiqué sans risque à toute personne souhaitant envoyer des bitcoins à cet utilisateur, à l'image de l'IBAN d'un compte bancaire classique. La comparaison avec un compte bancaire s'arrête malheureusement ici. En effet, il n'y a pas de compte sur Bitcoin, ou de solde bancaire. Un utilisateur, identifié par son adresse publique, ne détient pas des bitcoins, contrairement à ce que laisse imaginer l'appellation *coin*.
      Bitcoin est un protocole transactionnel, les blocs qui consituent la chaîne ne contiennent que des transactions, soit schématiquement "A envoie X bitcoins à B", A et B étant ici des adresses publiques et pas des noms (ce qui qualifie Bitcoin de protocole pseudonymique). Ainsi un utilisateur ne détient pas de coins, mais un ensemble de transactions dont son adresse publique est receveuse. Pour envoyer une transaction, un utilisateur doit rassembler les transactions qu'il a reçues et qui se somment en une quantité de bitcoins supérieure à celle qu'il souhaite dépenser dans sa propre transaction. La dépense de bitcoins s'effectue en signant de façon électronique les transactions reçues ainsi rassemblées. \\
      Cette signature électronique repose sur l'algorithme ECDSA (*Elliptic Curve Digital Signature Algorithm*), et permet d'authentifier de façon certaine le détenteur de l'adresse publique dépensant les bitcoins. Le principe de cet algorithme repose sur la cryptographie asymétrique, ou cryptographie à clé publique. Dans ce système, chaque utilisateur détient une clé privée, qui doit absolument rester secrète, et une clé publique dont son adresse est dérivée. Un utilisateur peut ainsi communiquer sont adresse à tout le monde, et donc recevoir des transactions, mais seul lui est en mesure de les dépenser par la suite avec sa clé privée.\\
      La détention de bitcoins se résume ainsi à la possession d'une ou plusieurs clés privées.

   **Consensus**\\
      Le cheminement d'une transaction dans Bitcoin peut se résumer à ce stade de la façon suivante : \\
      - un utilisateur rassemble les transactions qu'il précédemment reçues et qu'il souhaite dépenser ; \\
      - il les signe à l'aide de sa clé privée, et forme ainsi une nouvelle transaction ; \\
      - il diffuse cette nouvelle transaction à tous ses noeuds voisins dans le réseau, qui en vérifient la validité ; \\
      - si la transaction est considérée valide par certains de ces noeuds, elle se propage dans tout le réseau ; \\
      - les mineurs qui la reçoivent l'ajoutent dans un bloc aux côtés d'autres transactions. \\
      Il reste donc à déterminer comment un bloc est ajouté à la blockchain, et comment le choix du mineur qui réalisera cet ajout se fait. Le protocole Bitcoin étant par construction décentralisé, il n'y pas d'organe de décision en mesure d'imposer le nouveau bloc au réseau. Le choix du mineur ajoutant le nouveau bloc se fait de manière aléatoire, et ce nouveau bloc doit obtenir consensus de la majorité du réseau. \\
      Comme expliqué plus haut, la blockchain est une chaîne horodatée, dont les blocs sont liés par une empreinte cryptographique : chaque bloc contient l'empreinte du bloc précédent. Pour ajouter un bloc à la chaîne, un mineur doit donc calculer inscrire l'empreinte du bloc précédent dans son bloc, puis calculer l'empreinte de son propre bloc pour qu'il puisse être ajouté au bloc suivant, et ainsi de suite. Bitcoin introduit alors dans le calcul du nouveau hash (la nouvelle empreinte) une preuve de travail. Cette preuve se compose de deux éléments : \\
      - un nombre aléatoire inscrit dans le bloc ; \\
      - une cible de difficulté, c'est-à-dire une valeur de hash fixée que le nouveau hash ne doit pas dépasser. En pratique dans Bitcoin, ce hash est un nombre composé de 256 bits, et la cible détermine le nombre de zéros par lequel le nouveau hash doit commencer. \\
      Tous les mineurs doivent donc trouver un nombre aléatoire à inscrire dans leur bloc, tel que le hash de leur bloc soit bien inférieur à la cible. Pour se faire, ils sont obligés d'essayer tous les nombres possibles et de calculer à chaque fois le hash de leur bloc, jusqu'à en trouver un qui fonctionne. En effet, la fonction de hash utilisé dans Bitcoin (SHA-256) est dite cryptographique, et satisfait entre autres la popriété de ne pas pouvoir être inversée. Il est donc très facile connaissant un bloc de calculer son hash, mais extrêmement difficile connaissant un hash de retrouver la donnée correspondante. Tous les mineurs essaient donc de trouver le bon nombre aléatoire qui donnera un hash suffisament faible pour satisfaire la cible fixée. Le premier à trouver un tel nombre diffuse son bloc au réseau, de la même façon que les transactions sont diffusées, et chaque noeud peut alors vérifier que le hash de ce bloc satisfait bien la cible de difficulté. Si les mineurs acceptent ce nouveau, ils incluront son hash en tant qu'empreinte du bloc précédent, sinon ils continuent leur travail en ignorant ce nouveau bloc. \\
      La diffusion dans le réseau présente toutefois l'inconvénient que tous les noeuds ne reçoivent pas l'information au même moment, en fonction de la distance qui les sépare et de la qualité de leur connexion. Il est donc totu à fait possible que deux mineurs distincts trouvent un nouveau bloc à ajouter au même moment et commencent à le diffuser à leurs voisins respectifs. Dans un premier temps, si les mineurs sont à très éloignés, leurs voisins ne verront qu'un seul de ces deux blocs concurrents, l'ajouteront à la chaîne et continueront à construire par-dessus ce nouveau bloc, jusqu'à recevoir le bloc concurrent, sur lequel d'autres blocs auront peut-être commencé à se rattacher. Certains mineurs se retrouvent alors avec deux chaînes à partir desquelles ils peuvent miner leur nouveau bloc, il a donc fallu inclure dans Bitcoin une règle de sélection de la chaîne principale. A l'origine, dans le whitepaper de Satoshi Nakamoto en 2008, cette règle était de toujours miner la chaîne la plus longue. Elle a rapidement été remplacée par la règle de miner la chaîne qui dispose de la plus grande puissance de calcul des empreintes, ou puissance de hashage. En effet, par construction de la preuve de travail, la chaîne qui a la plus grande puissance de hashage a une plus grande probabilité de trouver le nombre aléatoire adéquat pour ajouter un bloc, et de fait de nouveaux blocs seront ajoutés plus rapidement à cette chaîne qu'à une chaîne disposant de moins de puissance.\\
      La preuve de travail permet donc de sélectionner aléatoirement le mineur qui ajoutera le nouveau bloc à la chaîne, et de ne retenir que la chaîne principale lorsque des blocs concurrents sont diffusés au même moment sur le réseau. Couplée au système d'incentives introduit par Nakamote, cette preuve de travail permet également de s'assurer que le réseau est fiable est sécurisée.

  **Incentives**
