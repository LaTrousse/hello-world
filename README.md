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

  **1/ Bitcoin**
    a/ Présentation
    Bitcoin est un protocole d'échange de valeurs de pair à pair, introduit en 2008 par Satoshi Nakamoto dans son whitepaper "Bitcoin : a peer-to-peer electronic cash system". Ce protocole est l'aboutissement du travail débuté dans les années 90 par les cypherpunks, groupe formé aux prémisses d'internet autour de la volonté de préserver la vie privée. Leur constat à l'époque était qu'internet allait  créer un monde de plus en plus connecté, où les données personelles seraient de plus en plus exposées. Il leur semblait alors primordial de créer des outils pour renforcer la confidentialité de ces données personelles et maintenir la vie privée des utilisateurs d'internet. Leurs efforts se sont ainsi concentrés sur la création d'une monnaie électronique, qui ne serait contrôlée par aucune entité et permettrait de s'échanger de la valeur sur internet sans compromettre les informations personnelles des utilisateurs. PLusieurs tentatives ont vu le jour entre 1990 et 2008, comme Hashcash ou Bit-Gold, mais ce n'est qu'en 2008 avec Bitcoin que cette problématique trouvait une réponse complète.
    Bitcoin repose sur plusieurs briques technologiques pour assurer la fiabilité et la sécurité de son système monétaire :
      - un réseau pair-à-pair qui diffuse et valide l'information ;
      - une chaîne de données horodatée qui assure la traçabilité de l'information ;
      - un algorithme de signature électronique (ECDSA) qui authentifie les transactions ;
      - un algorithme de consensus qui unifie l'état de chaque participant et l'inscrit dans la blackchain ;
      - une incitation économique qui aligne les intérêts des participants.

   **Réseau pair-à-pair**
      Le réseau pair-à-pair de Bitcoin est constitué de noeuds, des ordinateurs qui font tourner un des logiciels open-source qui implémente le protocole Bitcoin. Chaque noeud est connecté à un ensemble d'autres noeuds, mais pas nécessairement à tous. Ces noeuds peuvent, sans communiquer les uns avec les autres, rédiger un ensemble de transactions. Une fois ses transactions prêtes, chaque noeud les diffuse à l'ensemble du réseau. Il utilise pour cela la technique du *flooding* : le noeud envoie ses informations à ses voisins, ceux avec qui il a une connexion directe, qui relaient cette information à leurs propres voisins, et ainsi de suite jusqu'à ce que l'ensemble du réseau ait l'information.
      Une fois ces transactions reçues, chaque noeud a la responsabilité individuelle de vérifier leur validité. Il utilise pour cela la blockchain publique dont il a une copie - comme tous les autres noeds - et vérifie que les bitcoins dépensés par ces transactions ont bien été acquis en nombre suffisant par ceux qui les dépensent.

   **Chaîne horodatée**
      Les transactions validées par les noeuds du réseau sont assemblées dans des blocs par des noeuds particuliers, appelés "mineurs". Chaque bloc contient l'empreinte cryptographique, le hash, du bloc précédent ainsi que son horodatage. Les blocs sont ainsi reliés les uns aux autres, ce qui a initialement inspiré le terme de blockchain pour qualifier cette technologie. L'horodatage permet d'assurer à tous les noeuds du réseau que le nouveau bloc a bien été construit après le précédent, puisqu'il doit inclure son empreinte cryptographique et par conséquent son horodatage.
      Cette structuration des données en chaîne facilite la validation des transactions : pour vérifier qu'une transaction est légitime, il suffit au noeud de retracer l'historique des bitcoins dépensés par les transactions an parcourant la chaîne. Ils s'assurent ainsi que ces bitcoins ont bien été créés selon le protocole Bitcoin, et que l'utilisateur qui cherche à les dépenser les a bien en sa possession.

   **Signature électronique**
      Chaque utilisateur de Bitcoin est identifié sur le réseau par son adresse publique. Il s'agit d'un identifiant qui peut être communiqué sans risque à toute personne souhaitant envoyer des bitcoins à cet utilisateur, à l'image de l'IBAN d'un compte bancaire classique. La comparaison avec un compte bancaire s'arrête malheureusement ici. En effet, il n'y a pas de compte sur Bitcoin, ou de solde bancaire. Un utilisateur, identifié par son adresse publique, ne détient pas des bitcoins, contrairement à ce que laisse imaginer l'appellation *coin*.
      Bitcoin est un protocole transactionnel, les blocs qui consituent la chaîne ne contiennent que des transactions, soit schématiquement "A envoie X bitcoins à B", A et B étant ici des adresses publiques et pas des noms (ce qui qualifie Bitcoin de protocole pseudonymique). Ainsi un utilisateur ne détient pas de coins, mais un ensemble de transactions dont son adresse publique est receveuse. Pour envoyer une transaction, un utilisateur doit rassembler les transactions qu'il a reçues et qui se somment en une quantité de bitcoins supérieure à celle qu'il souhaite dépenser dans sa propre transaction. La dépense de bitcoins s'effectue en signant de façon électronique les transactions reçues ainsi rassemblées.
      Cette signature électronique repose sur l'algorithme ECDSA (*Elliptic Curve Digital Signature Algorithm*), et permet d'authentifier de façon certaine le détenteur de l'adresse publique dépensant les bitcoins. Le principe de cet algorithme repose sur la cryptographie asymétrique, ou cryptographie à clé publique. Dans ce système, chaque utilisateur détient une clé privée, qui doit absolument rester secrète, et une clé publique dont son adresse est dérivée. Un utilisateur peut ainsi communiquer sont adresse à tout le monde, et donc recevoir des transactions, mais seul lui est en mesure de les dépenser par la suite avec sa clé privée.
      La détention de bitcoins se résume ainsi à la possession d'une ou plusieurs clés privées.
