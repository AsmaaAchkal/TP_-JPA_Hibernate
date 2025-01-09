# TP_-JPA_Hibernate

Ce TP a pour objectif de pratiquer JPA avec Hibernate et Maven sous Eclipse. Il consiste en  implémentation d’une application dans laquelle on utilise les annotations @OneToOne, @ManyToOne,  @OneToMany et @ManyToMany.

---

## Prérequis
  - **Java Development Kit (JDK)**:  version 8 ou supérieure.
  - **Maven**: pour la gestion des dépendances.
  - **Une base de données MySQL**
  - **Outil de gestion de base de données** (comme phpMyAdmin)

---

## Technologies Utilisées
  - **Java** : Langage principal du projet.  
  - **JPA (Java Persistence API)** : Gestion des entités et mapping objet-relationnel.  
  - **Hibernate** : Implémentation de JPA.  
  - **Maven** : Gestionnaire de dépendances et de construction du projet.  
  - **MySQL** : Base de données utilisée.  

---

## Structure du Projet

   ### Packages

   -	'com.mavenhibernate2.OneToOne' : Gère les relations 'OneToOne' entre **Personne** et **Professeur**.
   -	'com.mavenhibernate2.OneToMany_ManyToOne' : Gère les relations 'OneToMany' et 'ManyToOne' entre **Adresse** et **Departement**.
   -	'com.mavenhibernate2.ManyToMany' : Gère les relations 'ManyToMany' entre **Etudiant** et **Module**.

---

   ### Classes Principales

   - **Personne** : Représente une personne.  
   - **Professeur** : Représente un professeur, lié à une personne.  
   - **Adresse** : Représente une adresse pouvant avoir plusieurs départements.  
   - **Departement** : Représente un département associé à une adresse.  
   - **Etudiant** : Représente un étudiant inscrit dans plusieurs modules.  
   - **Module** : Représente un module suivi par plusieurs étudiants.

 ---

 ## Explications des Relations
  -	**OneToOne** : Relation entre **Personne** et **Professeur**.
      -	Une personne peut être associée à un professeur.
  - **OneToMany / ManyToOne** : Relation entre **Adresse** et **Departement**.
      -	Une adresse peut avoir plusieurs départements.
      -	Un département appartient à une seule adresse.
  -	**ManyToMany** : Relation entre **Etudiant** et **Module**.
      -	Un étudiant peut être inscrit dans plusieurs modules.
      -	Un module peut être suivi par plusieurs étudiants.

## Installation Exécution du Projet
   
   1. Clonez le projet:  Clonez le projet dans votre environnement local.
   2. Importez le projet dans votre IDE (comme IntelliJ IDEA ou Eclipse).
   3.Configurez la connexion à la base de données dans le fichier `persistence.xml` situé dans le dossier `src/main/resources/META-INF` :

    '''xml
    <persistence xmlns="http://xmlns.jcp.org/xml/ns/persistence"
             xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence
             http://xmlns.jcp.org/xml/ns/persistence/persistence_2_1.xsd"
             version="2.1">
    <persistence-unit name="tp5_jpa_hibernate2" transaction-type="RESOURCE_LOCAL">
    <provider>org.hibernate.jpa.HibernatePersistenceProvider</provider>
        <properties>
            <!-- Configuration de BDD -->
            <property name="javax.persistence.jdbc.driver" value="com.mysql.cj.jdbc.Driver"/>
            <property name="javax.persistence.jdbc.url" value="jdbc:mysql://localhost:3306/jpa_hibernate2"/> <!-- remplacer 'jpa_hibernate2' par votre DB-->
            <property name="javax.persistence.jdbc.user" value="root"/>
            <property name="javax.persistence.jdbc.password" value=""/>
            <!-- Configuration de hibernate -->
            <property name="hibernate.dialect" value="org.hibernate.dialect.MySQL8Dialect"/>
            <property name="hibernate.hbm2ddl.auto" value="update"/>
            <property name="hibernate.show_sql" value="true"/>
            <property name="hibernate.format_sql" value="true"/>
        </properties>
    </persistence-unit>
    </persistence>

   4. Utilisez Maven pour compiler le projet :
  
    '''bash
     mvn clean install
     
   6. Lancez le fichier Main correspondant à la relation que vous souhaitez tester 

   7. Vérifiez les données générées dans votre base de données : 
      - Tables : personne, professeur, adresse, departement, etudiant, module.
      - Relations créées automatiquement (ex. : etudiant_module pour ManyToMany).

## Résultats
Après exécution :
  - Les relations entre les entités sont correctement établies dans la base de données.
  - Les données persistées sont visibles via un outil de gestion de base de données.

