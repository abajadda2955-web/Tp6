# TP Verrouillage Optimiste (Optimistic Locking) avec JPA/Hibernate

Ce projet illustre le concept de **verrouillage optimiste** en Java Persistence API (JPA) à travers
une simulation de réservation concurrente de salles. Il montre comment gérer les conflits d'accès aux
données avec l'annotation "@Version" et traiter l'exception 'OptimisticLockException`.

---

## Objectifs du TP

- Comprendre le concept de verrouillage optimiste  
- Implémenter l'optimistic locking avec l'annotation `@Version`  
- Simuler un conflit de réservation concurrent  
- Gérer les exceptions `OptimisticLockException` avec et sans mécanisme de réessai (retry)

---



=====## Résultats attendus (captures d'écran)=====

### 1. Initialisation des données

<img width="616" height="580" alt="2" src="https://github.com/user-attachments/assets/4ca25dd0-44f5-4175-92bf-c5f19fd384b3" />

<img width="612" height="448" alt="1" src="https://github.com/user-attachments/assets/b3c595c6-8978-4f69-950d-9ab91c19f92a" />

<img width="616" height="585" alt="3" src="https://github.com/user-attachments/assets/60c3a2b2-6c82-41dc-b22e-2d4d49b452c3" />

<img width="619" height="391" alt="4" src="https://github.com/user-attachments/assets/46a8e4b2-6472-4a6c-9256-f42ce2fe2d40" />


---

### 2. Simulation d’un conflit sans mécanisme de réessai

<img width="622" height="346" alt="5" src="https://github.com/user-attachments/assets/7e3de228-c220-4c63-8a42-d08878bc7edc" />

<img width="614" height="466" alt="6" src="https://github.com/user-attachments/assets/a1ca5bae-b3ea-4800-a139-806af428651d" />

<img width="617" height="344" alt="7" src="https://github.com/user-attachments/assets/bc4e5e3f-a974-4298-9af1-fba066d090e8" />

<img width="614" height="475" alt="8" src="https://github.com/user-attachments/assets/2ed12f18-c98f-4db1-8981-3ee9152fdd29" />


*On observe :*
- Les deux threads récupèrent la même réservation avec la même version.
- Un thread réussit la mise à jour.
- L’autre thread échoue avec une `OptimisticLockException`.
- L’état final de la réservation après le conflit.

---

### 3. Simulation d’un conflit avec mécanisme de réessai (retry)


<img width="526" height="492" alt="11" src="https://github.com/user-attachments/assets/9c6d3f94-fae2-4541-b03f-cf2668b16f80" />

<img width="530" height="439" alt="12" src="https://github.com/user-attachments/assets/d933218c-3633-4e1c-986d-dad325969a7f" />

<img width="530" height="381" alt="13" src="https://github.com/user-attachments/assets/c2bb9212-16d5-4a82-ac5b-d86f9ea9a52f" />

<img width="541" height="352" alt="14" src="https://github.com/user-attachments/assets/a7795f6a-ff13-43d0-8133-5a7dd49e94f8" />

<img width="528" height="410" alt="15" src="https://github.com/user-attachments/assets/75e2e1cc-7a25-4fc4-896c-fd6f358c893c" />

*On observe :*
- Les threads tentent de modifier la réservation.
- En cas d’`OptimisticLockException`, le mécanisme de retry recharge l’entité et réapplique la modification.
- Après plusieurs tentatives, un thread finit par réussir.
- L’état final de la réservation est cohérent.

---

### 4. Vérification de la version après conflit

<img width="527" height="373" alt="16" src="https://github.com/user-attachments/assets/ebf65c4c-cc0b-425a-a0d6-fe8f7d140c1a" />


---

---

## Auteur

Projet réalisé dans le cadre d’un TP sur le verrouillage optimiste avec JPA/Hibernate.
