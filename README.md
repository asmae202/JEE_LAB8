
# Student Management API - Spring Boot

![Spring Boot](https://img.shields.io/badge/SpringBoot-6DB33F?style=flat\&logo=springboot\&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat\&logo=openjdk\&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat\&logo=mysql\&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=flat\&logo=swagger\&logoColor=black)
![Licence](https://img.shields.io/badge/License-MIT-green)

---

# 📖 Plan

[📝 Objectif](#-objectif)

[📚 Contexte](#-contexte)

[🛠 Technologies utilisées](#-technologies-utilisées)

[🏗 Structure du projet](#-structure-du-projet)

[⚙️ Configuration de la base de données](#️-configuration-de-la-base-de-données)

[💻 Explication des composants](#-explication-des-composants)

[🚀 Lancer l'application](#-lancer-lapplication)

[🌐 Endpoints REST](#-endpoints-rest)

[📄 Documentation API avec Swagger](#-documentation-api-avec-swagger)

[🧪 Tests des endpoints](#-tests-des-endpoints)

[💡 Concepts clés](#-concepts-clés)

---

# 📝 Objectif

Ce TP a pour objectif de développer une **API REST complète avec Spring Boot** permettant de gérer des étudiants.

Les objectifs pédagogiques sont :

* Comprendre la structure d’un **projet Spring Boot**
* Configurer **Spring Data JPA avec MySQL**
* Créer une **API REST**
* Implémenter les opérations **CRUD**
* Utiliser les **DTO avec Java Record**
* Implémenter un **mapper manuel**
* Gérer les **exceptions globales**
* Documenter et tester l’API avec **Swagger UI**

---

# 📚 Contexte

L'application **Student API** permet de gérer des étudiants dans une base de données MySQL.

Chaque étudiant possède les informations suivantes :

* id
* firstName
* lastName
* email
* major
* age

L’application est organisée selon une **architecture en couches** pour garantir un code propre et maintenable.

Architecture utilisée :

* **Entity** → représentation des tables en base
* **Repository** → accès aux données
* **Service** → logique métier
* **Controller** → endpoints REST
* **DTO** → objets d’échange API
* **Mapper** → transformation DTO ↔ Entity
* **Exception Handler** → gestion centralisée des erreurs

Cette structure est recommandée dans les applications backend modernes.

---

# 🛠 Technologies utilisées

Technologies principales utilisées dans ce projet :

* **Spring Boot**
* **Spring Web**
* **Spring Data JPA**
* **MySQL**
* **Hibernate**
* **Java 17**
* **Maven**
* **Swagger / OpenAPI**
* **Validation API**



---

# 🏗 Structure du projet

Structure principale du projet :

<img width="302" height="423" alt="Image" src="https://github.com/user-attachments/assets/681a9800-017f-4e8a-8a36-f0925b97f10c" />



---

# ⚙️ Configuration de la base de données

Création de la base MySQL :



Explication :

* **ddl-auto=update** → crée automatiquement les tables
* **show-sql=true** → affiche les requêtes SQL
* **MySQL8Dialect** → dialecte SQL utilisé par Hibernate

Documentation :
https://docs.spring.io/spring-boot/docs/current/reference/html/data.html

---

# 💻 Explication des composants

## Entity

La classe `Student` représente la table **students** dans la base de données.

Principales annotations :

```
@Entity
@Table(name="students")
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
```

---

## Repository

`StudentRepository` étend `JpaRepository`.

Cela permet d'utiliser directement :

* save()
* findAll()
* findById()
* delete()
* existsById()

Spring génère automatiquement l’implémentation.

---

## DTO

Les DTO servent à **contrôler les données envoyées et reçues par l’API**.

Deux DTO sont utilisés :

```
StudentRequestDTO
StudentResponseDTO
```

Ils sont définis avec **Java record**, ce qui réduit fortement le code.

Documentation Java Record :
https://docs.oracle.com/en/java/javase/17/language/records.html

---

## Mapper

Le mapper transforme :

```
DTO → Entity
Entity → DTO
```

Cela évite d'exposer directement les entités de base de données.

---

## Service

La couche service contient la **logique métier** :

* ajout d’un étudiant
* récupération de tous les étudiants
* recherche par id
* modification
* suppression

---

## Controller REST

Le contrôleur expose les endpoints :

```
/api/students
```

Principales annotations :

```
@RestController
@RequestMapping("/api/students")
@GetMapping
@PostMapping
@PutMapping
@DeleteMapping
```

Documentation Spring REST :
https://docs.spring.io/spring-framework/reference/web/webmvc.html

---

# 🚀 Lancer l'application

Étapes pour exécuter l'application :

1. Cloner le projet

```
git clone https://github.com/votre-repository/student-api
```

2. Ouvrir le projet dans **IntelliJ ou Eclipse**

3. Vérifier la configuration MySQL

4. Lancer l'application :

```
StudentApiApplication.java
```

Ou via Maven :

```
mvn spring-boot:run
```

Le serveur démarre sur :

```
http://localhost:8080
```

---

# 🌐 Endpoints REST

| Méthode | Endpoint           | Description                 |
| ------- | ------------------ | --------------------------- |
| POST    | /api/students      | ajouter un étudiant         |
| GET     | /api/students      | afficher tous les étudiants |
| GET     | /api/students/{id} | chercher un étudiant        |
| PUT     | /api/students/{id} | modifier un étudiant        |
| DELETE  | /api/students/{id} | supprimer un étudiant       |

---

# 📄 Documentation API avec Swagger

Swagger UI permet de **tester l’API directement dans le navigateur**.

Accès :

```
http://localhost:8080/swagger-ui/index.html
```

Swagger génère automatiquement :

* la documentation
* les endpoints
* les schémas JSON
* les tests interactifs

Documentation :
https://springdoc.org/

---

# 🧪 Tests des endpoints

## Test POST

Ajouter un étudiant :

```json
{
  "firstName": "Sara",
  "lastName": "El Amrani",
  "email": "sara.elamrani@example.com",
  "major": "Informatique",
  "age": 21
}
```

---

## Test GET

Afficher tous les étudiants :

```
GET /api/students
```

---

## Test GET BY ID

```
GET /api/students/1
```

---

## Test PUT

Modifier un étudiant :

```json
{
  "firstName": "Sara",
  "lastName": "El Amrani",
  "email": "sara.updated@example.com",
  "major": "Génie logiciel",
  "age": 22
}
```

---

## Test DELETE

```
DELETE /api/students/1
```

Réponse attendue :

```
204 No Content
```

---

# 💡 Concepts clés

À la fin de ce TP, les concepts suivants doivent être maîtrisés :

* Architecture backend en couches
* Spring Boot
* Spring Data JPA
* Hibernate
* DTO avec Java Record
* Mapper manuel
* Validation avec `@Valid`
* Gestion des exceptions
* API REST
* Swagger OpenAPI

---

# 📌 Résultat final

À la fin du TP, l’application offre :

✔ API REST complète
✔ connexion MySQL
✔ architecture propre
✔ validation des données
✔ gestion des exceptions
✔ documentation Swagger
✔ endpoints testables directement

---

# 📜 Licence

Projet pédagogique destiné à l’apprentissage de **Spring Boot et des API REST**.
