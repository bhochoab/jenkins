pipeline {
    agent any

    // Parámetro para seleccionar el ambiente
    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'qa', 'prod'], description: 'Selecciona el ambiente de despliegue')
    }

    stages {
        // Stage 1: Checkout del código
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/bhochoab/jenkins.git'
            }
        }

        // Stage 2: Compilación
        stage('Build') {
            steps {
                echo 'Compilando el proyecto...'
                sh 'mvn clean install'  // Ejemplo para Maven
            }
        }

        // Stage 3: Pruebas
        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
                sh 'mvn test'  // Ejemplo para Maven
            }
        }

        // Stage 4: Despliegue en el ambiente seleccionado
        stage('Deploy') {
            steps {
                script {
                    if (params.ENVIRONMENT == 'dev') {
                        echo 'Desplegando en Desarrollo...'
                        sh './deploy-dev.sh'  // Script para desarrollo
                    } else if (params.ENVIRONMENT == 'qa') {
                        echo 'Desplegando en QA...'
                        sh './deploy-qa.sh'  // Script para QA
                    } else if (params.ENVIRONMENT == 'prod') {
                        echo 'Desplegando en Producción...'
                        sh './deploy-prod.sh'  // Script para producción
                    }
                }
            }
        }
    }

    // Post-actions: Notificaciones
    post {
        success {
            echo "¡Despliegue en ${params.ENVIRONMENT} completado con éxito!"
        }
        failure {
            echo "Despliegue en ${params.ENVIRONMENT} falló. Revisa los logs para más detalles."
        }
    }
}
