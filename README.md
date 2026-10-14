# TP4 : Hibernate et Persistance des Données

## Objectif

Configurer une application Java avec Hibernate et MySQL pour gérer la persistance de deux entités, `Salle` et `Machine`, reliées par une association One-to-Many. Le projet suit une architecture en couches : entités, DAO, services, tests.

## Outils

- JDK 11 ou plus
- Maven
- Hibernate 5.6.15.Final
- MySQL (via XAMPP) et phpMyAdmin
- JUnit 5
- IntelliJ IDEA

## Structure du projet

<img width="286" height="526" alt="image" src="https://github.com/user-attachments/assets/cf9398f4-0d70-4912-a4c4-e29309e47fab" />


## Étapes réalisées

1. Ajout des dépendances Maven : `hibernate-core`, `mysql-connector-java` et JUnit 5.
2. Création de l'interface générique `IDao<T>` avec les méthodes `create`, `update`, `delete`, `getById` et `getAll`.
3. Création des entités `Salle` et `Machine`. Une salle contient plusieurs machines (`@OneToMany`), et chaque machine appartient à une salle (`@ManyToOne`).
4. Configuration de Hibernate dans `hibernate.cfg.xml` : connexion à la base `db_tp_hibernate`, dialecte MySQL 8, `hbm2ddl.auto=update` pour créer les tables automatiquement.
5. Création de `HibernateUtil` pour fournir une seule `SessionFactory` à toute l'application.
6. Implémentation de `SalleDao` et `MachineDao` avec les sessions Hibernate et la gestion des transactions (commit, rollback).
7. Création des services `SalleService` et `MachineService` qui s'appuient sur les DAO.
8. Écriture de `MainTest` pour insérer une salle et une machine.
9. Écriture du test JUnit `SalleServiceTest`.
10. Ajout de la requête HQL `findByMarque` dans `MachineDao`.

## Exécution

Avant de lancer le programme, démarrer MySQL dans XAMPP. La base `db_tp_hibernate` peut être créée dans phpMyAdmin, sinon Hibernate la crée grâce à l'option `createDatabaseIfNotExist=true` de l'URL de connexion.

Lancer ensuite la classe `MainTest`. Hibernate crée les tables `salles` et `machines`, puis insère les données.

### Console IntelliJ

<img width="1162" height="560" alt="image" src="https://github.com/user-attachments/assets/389c117c-f9f6-461e-ace0-ffa6b4c84a81" />

<img width="1115" height="495" alt="image" src="https://github.com/user-attachments/assets/85c7745d-bfc3-45ec-aa68-810053ce1988" />


### Tables créées dans phpMyAdmin

<img width="680" height="212" alt="image" src="https://github.com/user-attachments/assets/8d9b9b9c-c985-41ac-bb71-bb38c4dd5b9e" />


### Table salles

<img width="447" height="244" alt="image" src="https://github.com/user-attachments/assets/ce84bf4b-f556-435b-949e-d9062f38c3b5" />


### Table machines

<img width="453" height="246" alt="image" src="https://github.com/user-attachments/assets/849741b4-398f-4ada-aa76-d11bb6d915c3" />

