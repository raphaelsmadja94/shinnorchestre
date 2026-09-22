# Skill : Spring

## Objectif
Conseiller et valider les pratiques Spring Boot modernes.

## Quand le charger
- Mission backend Spring Boot.
- Revue de controllers, services, repositories.
- Conception d’API REST ou WebFlux.

## Quand ne pas le charger
- Projet non Spring.
- Tâche purement frontend sans interface backend.

## Checklist
- Architecture en couches respectée.
- Validation des entrées.
- Gestion d’erreur cohérente.
- Configuration externalisée.
- Tests présents et non bloqués.
- Sécurité activée ou justifiée.
- Aucun secret en clair.

## Bonnes pratiques
- `@Valid` sur les DTOs entrants.
- Retour HTTP métier plutôt qu’exceptionnel en cas de demande invalide.
- Séparation controller/service/repository.
- Externaliser toute valeur sensible dans des variables d’environnement.
- Utiliser des profils Spring pour les environnements.

## Erreurs fréquentes
- Logique métier dans les controllers.
- Secrets codés en dur.
- Absence de validation des entrées.
- Désactivation globale de CSRF sans mesure compensatoire.
- WebFlux sans besoin réel.
- Retour d’exceptions techniques brutes au client.

## Critères de validation
- Compilation.
- Tests unitaires ou d’intégration.
- Revue de sécurité minimale.
- `application*.properties` sans secret.
- Contrats d’API documentés.

## Règles opérationnelles

### Compatibilité
- Respecter la version Java et Spring Boot du `pom.xml` parent.
- Dans ce projet : Java 21, Spring Boot 3.5.4.
- Ne pas introduire de dépendance incompatible sans validation du CTO.
- Vérifier la documentation officielle Spring Boot pour chaque starter ajouté.

### Architecture
- Respecter la séparation par sous-domaines :
  - `controller/` : REST endpoints, parsing HTTP, `@Valid`, pas de logique métier.
  - `service/` : logique métier, `@Transactional` uniquement ici si nécessaire.
  - `domain/` : entités JPA, enums, règles métier natives.
  - `repo/` : Spring Data JPA, queries optimisées, projections.
  - `dto/` : records, requests responses, mapping vers domaine.
  - `mappers/` : conversion entity <-> DTO.
  - `config/` : beans techniques, sécurité, CORS, stockage.
- Pas de dépendance cyclique : `controller -> service -> repo -> domain`.
- Les controllers ne doivent pas appeler directement un repository sans abstraction service.

### DTO entrants et sortants
- DTOs immuables préférés : `record`.
- DTOs entrants : `@NotNull`, `@NotBlank`, `@Size`, `@Email` selon le champ.
- DTOs sortants : ne jamais exposer d’entité JPA brute.
- Pas de champs techniques exposés au client (IDs internes inutiles, timestamps non métier).

### Validation Bean Validation
- Activer `spring-boot-starter-validation`.
- Ajouter `@Valid` sur chaque `@RequestBody`.
- Compléter les DTOs avec les contraintes métiers.
- Compléter les entités JPA uniquement si les contraintes sont intrinsèques au modèle.
- Ne pas valider les réponses : le contrat DTO suffit.

### Gestion centralisée des erreurs
- Utiliser `@RestControllerAdvice` pour :
  - mapper `MethodArgumentNotValidException` vers `400` avec liste de violations ;
  - mapper `ConstraintViolationException` vers `400` ;
  - mapper exceptions métier vers `4xx` avec code métier ;
  - mapper exceptions techniques vers `500` sans stacktrace en production.
- Retour JSON normalisé : `{ code, message, details, traceId? }`.
- Ne jamais renvoyer le message d’exception brute en production.

### Choix cohérents des statuts HTTP
- `200` : succès lecture ou mutation sans body explicite.
- `201` : création réussie, `Location` vers la ressource.
- `204` : suppression réussie.
- `400` : validation ou paramètre invalide.
- `401` : authentification manquante ou invalide.
- `403` : authentifié mais non autorisé.
- `404` : ressource introuvable.
- `409` : conflit métier.
- `422` : demande valide mais impossible à traiter.
- `429` : limite de débit atteinte.
- `500` : erreur serveur générique, log détaillé côté serveur uniquement.

### Transactions
- `@Transactional` sur les services, jamais sur les controllers.
- Lecture seule préférer `@Transactional(readOnly = true)`.
- Propagation et isolation par défaut sauf besoin explicite.
- Ne pas faire de transaction longue : découper les traitements batchs.
- Gérer les rollback sur exceptions runtime ; exceptions checked par `@Transactional(rollbackFor = ...)`.

### Spring Data JPA, pagination, projections et prévention N+1
- Préférer les interfaces `interface Projection { ... }` ou DTOs projetés quand le contrat est mappings explicites.
- Pagination systématique sur les listes : `Pageable`.
- Éviter `SELECT *` implicites : projections ou `@Query` ciblées.
- Anticiper le N+1 :
  - `@EntityGraph` ;
  - `JOIN FETCH` dans les `@Query` ;
  - `@BatchSize` pour les collections ;
  - éviter les boucles sur entités avec collections lazy.
- Ne jamais laisser Hibernate générer du SQL non maîtrisé sans vérifier le plan.

### Sécurité Spring Security, authentification, autorisation et CSRF
- Définir une `SecurityFilterChain` explicite par domaine.
- Authentification :
  - JWT signé pour API publique avec cookie ou bearer ;
  - session stateful seulement si besoin.
- Autorisation :
  - `requestMatchers(...).hasRole(...)` ou `hasAuthority(...)` ;
  - refus par défaut en production : tout ce qui n’est pas explicitement autorisé est interdit.
- CSRF :
  - activer pour les navigateurs ;
  - désactiver seulement pour les endpoints API publics consciemment ;
  - justifier toute exception.
- CORS :
  - origins explicites ;
  - `allowCredentials` seulement si nécessaire ;
  - ne jamais autoriser `*` avec credentials.
- Rate limiting :
  - sur les endpoints publics sensibles : formulaire de contact, authentification, upload.

### Configuration externalisée et profils
- Toute valeur dépendant de l’environnement doit être externalisée dans des variables d’environnement ou un serveur de configuration.
- Valeurs par défaut autorisées seulement pour les paramètres non sensibles.
- Profils Spring utilisés pour : dev, test, prod.
- `application.yml` ou `.properties` versionné sans aucun secret.
- `application-example.properties` ou README doivent documenter les variables obligatoires.

### Logs sans données sensibles
- Ne jamais logguer : mots de passe, tokens, secrets, données personnelles identifiables, cookies.
- Préférer logging métier : identifiants métiers, durée, statut.
- Ne pas logguer le body complet des requêtes entrantes sans masquage explicite.
- Masquer les tokens dans les logs HTTP.

### Actuator et observabilité
- Activer uniquement les endpoints nécessaires.
- Protéger les endpoints sensibles par `management.endpoints.web.exposure.include` et `management.endpoint.health.show-details=never` en prod.
- Activer les health indicators utiles : db, diskSpace.
- Ne pas exposer les env, config, beans en production sans justification.
- Ajouter des metrics clés : requêtes HTTP, erreurs 4xx/5xx, latence, pool datasource.
- Tracer les requêtes métier importantes.

### Tests
- `@WebMvcTest` : controllers isolés avec MockMvc.
- `@DataJpaTest` : repositories avec base embarquée ou Testcontainers.
- Tests unitaires : services avec Mockito, mocks externes.
- Tests d’intégration : `@SpringBootTest` avec profil `test` et conteneurs isolés.
- Testcontainers recommandé pour PostgreSQL, pas de base partagée.
- Nommage explicite : `should doX when Y`.
- Couverture bornée : privilégier les chemins métiers et sécurité.
- Vérifier les contrats HTTP sur les controllers.

### Spring MVC vs WebFlux
- Par défaut : Spring MVC (`spring-boot-starter-web`).
- WebFlux seulement si besoin réel de réactivité, SSE, WebSocket avancé ou flux streaming.
- Ne pas mélanger MVC et WebFlux dans le même service sans justification.
- Toute introduction de WebFlux doit être validée par le CTO et justifiée par un besoin fonctionnel mesuré.

### Documentation API
- Vérifier la documentation officielle Spring avant de proposer un comportement incertain.
- Ne pas inventer de comportement propriétaire sans confirmation docs.
- Documenter les endpoints avec OpenAPI si une UI est requise.

## Processus d’intervention

1. Lire la version Java et Spring Boot depuis le `pom.xml` parent.
2. Inspecter les conventions existantes du projet cible.
3. Identifier le périmètre minimal du changement.
4. Modifier sans casser l’architecture existante.
5. Compiler avec le Maven Wrapper du projet.
6. Tester les chemins impactés.
7. Vérifier sécurité, logs et configuration.
8. Produire un rapport court :
   - diagnostic ;
   - plan exécuté ;
   - fichiers modifiés ;
   - résultats des tests ;
   - risques ;
   - décision attendue.
