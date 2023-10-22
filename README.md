##  DevOps Jenkins CI

# Objectifs

Ce projet vise à vous guider dans la création et la configuration de deux types de projets Jenkins, à savoir un projet FreeStyle et un projet Pipeline. 

Ces étapes vous permettront de comprendre les principes de base de l'intégration continue et de l'automatisation des tâches de développement logiciel à l'aide de Jenkins.


# Partie 1 : Projet FreeStyle


  # Étape 1 : Configuration initiale de Jenkins



   Assurez-vous que Jenkins est installé et en cours d'exécution sur votre serveur.

    
  Ouvrez un navigateur web et accédez à l'interface Jenkins en utilisant l'URL  ==>  Http://localhost:8080.



  # Étape 2 : Création d'un projet FreeStyle
  

  Sur le tableau de bord Jenkins, cliquez sur "Nouvel élément" (ou "New Item").
  
  Dans la fenêtre qui s'ouvre :


 - Donnez un nom à votre projet FreeStyle, par exemple "MonProjetFreeStyle".

   
 - Choisissez "Projet de style libre" (ou "Freestyle project").

   
 - Cliquez sur "OK" pour créer le projet.
   

   ![Screenshot from 2023-10-22 21-39-01](https://github.com/AchourMaryem/Jenkins/assets/95104454/b2938b8f-f675-40de-af4e-f84b7eb71bd5)



  



# Étape 3 : Configuration du projet FreeStyle



  - Dans la page de configuration du projet FreeStyle, sous la section "Gestion de code source" (ou "Source Code Management"), assurez-vous d'avoir configuré correctement votre SCM  Git .

![Screenshot from 2023-10-22 21-54-53](https://github.com/AchourMaryem/Jenkins/assets/95104454/7b463629-b34f-4bbc-8be3-2ec747fbfe6f)

  
  - Sous la section "Build Triggers" (ou "Déclencheurs de construction"), cochez l'option "Poll SCM".
    
![image](https://github.com/AchourMaryem/Jenkins/assets/95104454/06726482-d92f-4e48-b992-51e2f6986662)

    
   - Dans le champ "Plan de déclenchement" (ou "Schedule"), entrez l'expression cron suivante pour déclencher la vérification SCM toutes les 5 minutes : */5 * * * *


![Screenshot from 2023-10-22 21-55-05](https://github.com/AchourMaryem/Jenkins/assets/95104454/3c9d480d-2358-4971-8a85-2d0958e336c1)


# Étape 4 : Exécution du projet FreeStyle

  - Cliquez sur "Enregistrer" pour sauvegarder la configuration du projet FreeStyle.
  
  - Cliquez sur "Construire maintenant" (ou "Build Now") pour exécuter le projet FreeStyle.


    ![Screenshot from 2023-10-22 21-54-37](https://github.com/AchourMaryem/Jenkins/assets/95104454/b98f110d-706a-4dae-b517-bbb9487f6eed)


- Vous pouvez suivre la progression de la construction en cliquant sur le projet et en consultant les journaux de build pour voir les messages affichés à chaque étape.





![Screenshot from 2023-10-22 21-54-07](https://github.com/AchourMaryem/Jenkins/assets/95104454/31925964-8c46-413c-9117-99a0455439b9)



# Partie 2 : Projet Pipeline

# Étape 1 : Création d'un projet Pipeline

  - Retournez sur le tableau de bord Jenkins.

    
- Cliquez sur "Nouvel élément" (ou "New Item").

  
- Dans la fenêtre qui s'ouvre :
  

    - Donnez un nom à votre projet Pipeline, par exemple "MonPipeline".

      - Choisissez "Pipeline" comme type de projet.
  
      - Cliquez sur "OK" pour créer le projet Pipeline.




![Screenshot from 2023-10-22 21-56-37](https://github.com/AchourMaryem/Jenkins/assets/95104454/7d0f3f04-26e9-465f-bb20-0258f0b57ec6)

# Étape 2 : Configuration du projet Pipeline

  - Dans la page de configuration du projet Pipeline, vous n'avez pas besoin de configurer de déclencheur "Poll SCM" car les pipelines ne fonctionnent généralement pas de cette manière. Au lieu de cela, vous pouvez intégrer la vérification SCM dans votre Jenkinsfile.

- Dans le Jenkinsfile, vous pouvez utiliser la fonction pollSCM pour déclencher la vérification SCM toutes les 5 minutes et utiliser echo pour afficher des messages à chaque étape. Voici un exemple :

  
      pipeline {
        agent any
        triggers {
            pollSCM('*/5 * * * *') // Planifier une vérification SCM toutes les 5 minutes
        }
        stages {
            stage('Checkout') {
                steps {
                    script {
                        echo "Étape 1: Récupération du code source depuis le référentiel"
                        checkout scm
                    }
                }
            }
            stage('Build') {
                steps {
                    echo "Étape 2: Installation des dépendances"
                    // Insérer ici les commandes réelles pour installer les dépendances
                    echo "Étape 3: Build du projet"
                    // Insérer ici les commandes réelles pour construire le projet
                    echo "Étape 4: Exécution des tests"
                    // Insérer ici les commandes réelles pour exécuter les tests
                }
            }
            stage('Deploy') {
                steps {
                    echo "Étape 5: Déploiement du projet"
                    // Insérer ici les commandes réelles pour le déploiement
                }
            }
        }
    }

    

![Screenshot from 2023-10-22 21-55-41](https://github.com/AchourMaryem/Jenkins/assets/95104454/041fc410-b0a7-4366-8cdc-11cdbbff4a31)


# Étape 3 : Exécution du projet Pipeline

  - Cliquez sur "Enregistrer" pour sauvegarder la configuration du projet Pipeline.

- Cliquez sur "Construire maintenant" (ou "Build Now") pour exécuter la pipeline.

  - Vous pouvez suivre la progression de la construction en cliquant sur le projet et en consultant les journaux de build pour voir les messages affichés à chaque étape.

  - Faites une modification dans le code dans votre repo et assurez-vous que la Pipeline est déclenchée.

![Screenshot from 2023-10-22 22-02-33](https://github.com/AchourMaryem/Jenkins/assets/95104454/a747e745-9545-4255-b59f-364664c203f9)


# Le resultat de les deux projet : 
 
![Screenshot from 2023-10-22 21-56-20](https://github.com/AchourMaryem/Jenkins/assets/95104454/31d53a47-fb09-46d3-aaa7-e48237e41b3d)
