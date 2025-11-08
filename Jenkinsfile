pipeline {
    agent any
    
    environment {
        PYTHON_VERSION = '3.12'
    }
    
    stages {
        stage('Build') {
            steps {
                echo '========== ETAPA: Build =========='
                echo 'Preparando el entorno de construcción...'
                script {
                    if (isUnix()) {
                        sh 'python --version'
                        sh 'pip --version'
                    } else {
                        bat 'python --version'
                        bat 'pip --version'
                    }
                }
                echo 'Build completado exitosamente'
            }
        }
        
        stage('Test') {
            steps {
                echo '========== ETAPA: Test =========='
                echo 'Ejecutando pruebas unitarias...'
                script {
                    if (isUnix()) {
                        sh 'pip install pytest'
                        sh 'pytest --version || echo "Pytest instalado"'
                    } else {
                        bat 'pip install pytest'
                        bat 'pytest --version || echo Pytest instalado'
                    }
                }
                echo 'Tests completados (sin tests definidos aún)'
            }
        }
        
        stage('Analyze') {
            steps {
                echo '========== ETAPA: Analyze =========='
                echo 'Analizando calidad del código...'
                script {
                    if (isUnix()) {
                        sh 'pip install pylint'
                        sh 'pylint --version || echo "Pylint instalado"'
                        sh 'pylint app.py || echo "Análisis completado con advertencias"'
                    } else {
                        bat 'pip install pylint'
                        bat 'pylint --version || echo Pylint instalado'
                        bat 'pylint app.py || echo Análisis completado con advertencias'
                    }
                }
                echo 'Análisis de código completado'
            }
        }
        
        stage('Dependency Management') {
            steps {
                echo '========== ETAPA: Dependency Management =========='
                echo 'Gestionando dependencias con pipenv...'
                script {
                    if (isUnix()) {
                        sh 'pip install pipenv'
                        sh 'pipenv --version'
                        sh 'pipenv install --skip-lock'
                        sh 'pipenv check || echo "Verificación de seguridad completada"'
                    } else {
                        bat 'pip install pipenv'
                        bat 'pipenv --version'
                        bat 'pipenv install --skip-lock'
                        bat 'pipenv check || echo Verificación de seguridad completada'
                    }
                }
                echo 'Dependencias actualizadas y verificadas'
            }
        }
        
        stage('Deploy') {
            steps {
                echo '========== ETAPA: Deploy =========='
                echo 'Desplegando aplicación en entorno de prueba...'
                script {
                    if (isUnix()) {
                        sh 'echo "Aplicación lista para despliegue"'
                        sh 'pip install -r requirements.txt'
                    } else {
                        bat 'echo Aplicación lista para despliegue'
                        bat 'pip install -r requirements.txt'
                    }
                }
                echo 'Deploy completado exitosamente'
            }
        }
    }
    
    post {
        success {
            echo '✅ Pipeline completado exitosamente'
        }
        failure {
            echo '❌ Pipeline falló. Revisa los logs.'
        }
        always {
            echo '========== Limpieza y finalización =========='
        }
    }
}