# <img src="https://raw.githubusercontent.com/IUTInfoAix-M2105/Syllabus/master/assets/logo.png" alt="class logo" class="logo"/> Bases de données avancées 

### IUT d’Aix-Marseille – Département Informatique Aix-en-Provence

* **Cours:** [M3106](http://cache.media.enseignementsup-recherche.gouv.fr/file/25/09/7/PPN_INFORMATIQUE_256097.pdf)
* **Responsable:** [Sébastien NEDJAR](mailto:sebastien.nedjar@univ-amu.fr)
* **Enseignants:** [Sébastien NEDJAR](mailto:sebastien.nedjar@univ-amu.fr)
* **Besoin d'aide ?**
    * La page [Piazza de ce cours](https://piazza.com/univ-amu.fr/fall2017/m3106/home).
    * Consulter et/ou créér des [issues](https://github.com/IUTInfoAix-M3106/TutoJdbc/issues).
    * [Email](mailto:sebastien.nedjar@univ-amu.fr) pour une question d'ordre privée, ou pour convenir d'un rendez-vous physique.

# Test JDBC 2015
Test de JDBC donné en 2015 aux étudiants de l'IUT d'Aix-Marseille

## Partie 2 (Sébastien NEDJAR)
### Document autorisé : Une feuille A4 manuscrite recto-verso


**Remarque :** *Les événements et les situations de ce sujet étant purement fictifs, toute ressemblance avec des événements et des situations existantes ou ayant existé ne saurait être que fortuite.*

Comme tous les étudiants informaticiens depuis plus d’une année, vous commencez à ne plus ressentir le besoin du contact social. Plutôt que de fréquenter des sites pour essayer de sortir et/ou rencontrer d’autres individus vaguement humains, vous décidez de développer une nouvelle plateforme : OnVaGeeker (abrégé en OVG).  Elle rassemblera toutes les personnes préférant s’adonner à leurs dévorantes passions plutôt que de développer des relations amicales.

Chaque geek, en plus de ses coordonnées, se voit attribuer une catégorie en fonction de sa passion principale (Dev, Cosplay, JdR, Manga, Jeux vidéo, Reblochon, ...). Une fois enregistré, il peut proposer des projets qu’il essayera tant bien que mal de réaliser sans l’aide d’aucun autre geek. Chaque projet sera classé en fonction de son thème (Concours, Convention, Hackathon, Tartiflette, ... ). L’application est constituée des tables suivantes : 

PROJET(*ID_P*, LIBELLE, DESCRIPTION_P, ID_T#, ID_G#)

THEME (*ID_T*, NOM_T, DESCRIPTION_T)

GEEK (*ID_G*, NOM_G, PRENOM, ADRESSE, CATEGORIE)


*Par convention, les clefs primaires sont en italique et les clefs étrangères sont postfixées par le symbole #.*


### Questions 

*Vous supposerez que vous disposez des classes d’entité associées à chaque relation de cette base de données. Chacune de ces classes respecte la convention Java Bean (constructeur par défaut, setter/getter, equals/hashcode, toString).*

1. Écrire la déclaration de la classe `DAOProjet` qui implémente l’interface `DAO<Projet>` (La définition de l’interface vous est donnée page suivante). Dans un premier temps, vous n’implémenterez aucune méthode de cette classe.
2. Implémenter la méthode `delete(Projet projet)` de la classe `DAOProjet`.
3. Implémenter la méthode `findAll()` de la classe `DAOProjet`. Pour cette question, ne chargez pas les associations hiérarchiques.
4. Implémenter la méthode `getById(int id)` de la classe `DAOProjet`. Pour cette question vous devez correctement gérer le chargement des objets matérialisant les associations hiérarchiques.

________________

```java
public interface DAO<T> {
    // Permet la suppression d'un tuple de la base
    public boolean delete(T obj);


    // Permet de récupérer tous les objets d'une table
    public List<T> findAll();


    // Permet de récupérer un objet via son ID
    public T getById(int id);


    // Permet de créer une entrée dans la base de données par rapport
    // à un objet
    public T insert(T obj);


    // Permet de mettre à jour un tuple dans la base à partir d'un
    // objet passé en paramètre
    public boolean update(T obj);
}
```
