pipeline {
    agent {
    label 'windows'
    }

    stages {
        stage('Checkout') {
            steps {
                // Étape de récupération du code source depuis un référentiel Git
                git 'https://github.com/mamadoucire/PHP.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Étape d'installation de Composer
                bat 'php --version'
                bat 'php -r "copy(\'https://getcomposer.org/installer\', \'composer-setup.php\');"'
                bat 'php composer-setup.php'
                bat 'php -r "unlink(\'composer-setup.php\');"'
                bat 'php composer.phar update'
                // Étape d'installation des dépendances via Composer
                bat 'php composer.phar install'
            }
        }

        stage('Build') {
            steps {
                // Étape de construction de votre projet PHP (par exemple, exécution de tests, génération de fichiers, etc.)
                bat 'php build.php'
            }
        }

      /*  stage('Deploy') {
            steps {
                // Étape de déploiement de votre projet PHP (par exemple, copie des fichiers sur un serveur distant)
                bat 'xcopy /E /I /Y src\ dist\'
                // ou utilisez d'autres commandes spécifiques à votre processus de déploiement
            }
        }*/
    }
}
