pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/tu-usuario/tu-repositorio.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                // Aquí puedes agregar comandos para compilar tu proyecto
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Aquí puedes agregar comandos para ejecutar pruebas
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the project...'
                // Aquí puedes agregar comandos para desplegar tu proyecto
            }
        }
    }
}
