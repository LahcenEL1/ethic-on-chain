## Solidity Patterns Decisions - design_pattern_decisions.md

Ce document liste tous les Patterns Solidity issus de https://fravoll.github.io/solidity-patterns et pour chacun indique
- si nous avons l'intention de l'utiliser
- quelques informations expliquant notre choix
- Si utilisé, exemple de class.function où le pattern peut être trouvé.

### Behavioral Patterns

#### Guard Check

- Utilisation : OUI
- L'utilisation des require() semble évidente pour tout développeur Solidity avec un minimum de connaissance Solidity voire une expérience similaire avec tout autre langage.
- Exemple d'utilisation : ...

#### State Machine

- Utilisation : OUI
- Nous avons besoin de réagir différemment suivant le statut du projet.
- Exemple d'utilisation : ...

#### Oracle

- Utilisation : PEUT-ETRE
- Si nous avons besoin - et le temps - d'utiliser un Oracle tel que Chainlink pour des conversions.
- Exemple d'utilisation : ...

#### Randomness

- Utilisation : NON
- Nous n'avons pas trouvé dans nos use cases de besoin d'utilisation d'un nombre aléatoire.

### Security Patterns

- Utilisation : OUI
- Nous avons besoin de gérer un concept de droit d'accès par utilisateur (RBAC - Role-Based Access Control), suivant les rôles (NPO, Donateur)
- Exemple d'utilisation : ...

#### Access Restriction

#### Checks Effects Interactions

- Utilisation : OUI
- Dès qu'une fonction offre une possibilité de transfert de tokens, nous devons nous assurer qu'il n'y a pas de risque de réentrance (re-entrancy exploit risk).
- Exemple d'utilisation : ...

#### Secure Ether Transfer

- Utilisation : OUI
- We will use it in the way we need to think which method (among send, transfer and call.value) is the most appropriate if we have to send tokens.
- nous devons réfléchir à la meilleure méthode / la plus appropriée en cas de transfert de tokens (parmi les méthodes send, transfer et call.value)
- Exemple d'utilisation : ...

#### Pull over Push

A REVOIR ENTRE TOUS LES MEMBRES DE L'EQUIPE !
- Utilisation : NON
- Dans notre modèle métier, il ne semble pas évident/facile de pouvoir demander aux intervenants de "réclamer" leur Tokens. Peut-être que dans le cas de la libération des tokens pour un projet cela peut-être utilisé.

#### Emergency Stop

- Utilisation : PEUT-ETRE
- Si nous avons le temps, il semble toujours préférable d'avoir une otpion qui permet de temporairement bloquer toute sortie/transfert de tokens en cas de découverte de bug avec risque de sécurité.
- Exemple d'utilisation : ...

### Upgradeability Patterns

#### Proxy Delegate

- Utilisation : NON, pas dans la v1.0
- Comme mentionné, l'utilisation de delegatecall est "more complex than most of the other patterns presented in this document".

#### Eternal Storage

- Utilisation : PEUT-ETRE si nous avons le temps
- Un tel pattern est vraiment très utile car il donne un moyen relativement simple de ne pas perdre les données stockées en cas de modifications fonctionnelles (si la structure / le stockage des données reste le même et que seules les fonctionalités / méthodes évoluent)

### Economic Patterns

#### String Equality Comparison

- Utilisation : PEUT-ETRE
- Dès qu'il y a besoin de comparer des chaines de caractères, cela vaut le coup de l'utiliser (simple copié/collé de l'exemple indiqué).

#### Tight Variable Packing

- Utilisation : PEUT-ETRE si nous avons le temps
- Considéré comme un "Could". Nous reverrions alors comment est écrit le contrat.

#### Memory Array Building

- Utilisation : PEUT-ETRE si nous avons le temps
- Nous vérifierons si de telles méthodes existent et appliquerons le pattern.