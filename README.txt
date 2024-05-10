# Création d'une pipeline avec Jenkins et Ansible

Ce projet vise à automatiser le déploiement d'applications à l'aide d'une pipeline intégrant Jenkins et Ansible. La pipeline permettra de gérer les étapes de construction, de test et de déploiement d'une application de manière continue.
Prérequis

Avant de commencer, assurez-vous d'avoir les éléments suivants :

    Jenkins installé sur un serveur accessible. Vous pouvez trouver des instructions d'installation sur le site officiel de Jenkins.
    Ansible installé sur le même serveur que Jenkins ou sur un serveur accessible. Vous pouvez trouver des instructions d'installation sur le site officiel d'Ansible.
    Un environnement de développement pour l'application que vous souhaitez déployer, ainsi que les configurations nécessaires pour son déploiement avec Ansible.

# Utilisation
Configuration de Jenkins

    Accédez à l'interface Web de Jenkins et connectez-vous en utilisant vos identifiants.

    Créez un nouveau projet de type Pipeline dans Jenkins.

    Configurez le projet en spécifiant l'URL de votre référentiel Git et en ajoutant le fichier Jenkinsfile à la racine de votre projet. Ce fichier contiendra les étapes de la pipeline.

# Configuration d'Ansible

    Assurez-vous que votre inventaire Ansible contient les informations nécessaires sur les serveurs cibles où vous souhaitez déployer votre application.

    Créez vos playbooks Ansible avec les tâches de déploiement spécifiques à votre application.

Création du fichier Jenkinsfile

Voici un exemple de contenu pour un fichier Jenkinsfile :

```sh

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/votre-utilisateur/votre-projet.git'
            }
        }
        stage('Build') {
            steps {
                // Ajoutez les étapes de construction de votre application
            }
        }
        stage('Test') {
            steps {
                // Ajoutez les étapes de test de votre application
            }
        }
        stage('Deploy') {
            steps {
                sh 'ansible-playbook -i inventory playbook.yml'
            }
        }
    }

    post {
        always {
            // Ajoutez des étapes de nettoyage ou de notification si nécessaire
        }
    }
}

```
# Exécution de la pipeline

    Lorsque vous avez terminé de configurer votre projet Jenkins et votre fichier Jenkinsfile, déclenchez la pipeline en appuyant sur le bouton de construction dans l'interface Jenkins.

    Jenkins exécutera alors les étapes de la pipeline, y compris le déploiement de votre application avec Ansible.
