
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

<img width="776" height="289" alt="Image" src="https://github.com/user-attachments/assets/22388f9f-0bfe-431d-9099-5196e9086cc0" />



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

---

# 🚀 Lancer l'application

<img width="743" height="414" alt="Image" src="https://github.com/user-attachments/assets/3dd1194f-9b68-4a67-9917-691f07b42c98" />


---


 ## Accé à l’interface Swagger:
 
<img width="901" height="470" alt="Image" src="https://github.com/user-attachments/assets/e76a261b-18fc-4b13-b6e7-de9c07e59f9c" />

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


---

# 🧪 Tests des endpoints

## Test POST

Ajouter un étudiant :

https://github.com/user-attachments/assets/446a3389-9cda-4b0a-9c65-3fe61c9b3e45

---

## Test Methode GET & GET BY ID:

https://github.com/user-attachments/assets/f11a2ecd-a784-4387-b903-f7fe0e009f15

---

## Test PUT

Modifier email de sara:

https://github.com/user-attachments/assets/53492bb9-a6ac-4d1e-818a-6590ed779aab

---

## Test DELETE

 Supprimer etudiant sara  id=1
 
https://github.com/user-attachments/assets/10d705ee-8eb3-41eb-9244-f248410a3dae

## Test GET apres suppression:

On veut verifier la suppression de sara avec methode get:

https://github.com/user-attachments/assets/57a243e1-64ce-49eb-bf95-4272c066c885
 
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


