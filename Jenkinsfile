pipeline {
    agent any
    environment{
        DOCKERHUB_CREDS = credentials('dockerhubivan')
    }
    stages {
        stage('Clone Repo') {
            steps {
                checkout scm
                sh 'ls *'
            }
        }
        stage('Build Image') {
            steps {
                //Aquí debes poner tu repositorio de dockerhub
		sh 'docker build -t IvanJuBe/https://github.com/IvanJuBe/EjemploDockerHub_IvanJunquera.git . '
            }
        }
        stage('DockerHUB Login') {
            steps {
                
                sh 'echo $DOCKERHUB_CREDS_PSW | docker login -u $DOCKERHUB_CREDS_USR --password-stdin'                
                }
            }
        stage('Docker Push') {
            steps {
		//Aquí debes poner tu DockerHub
                sh 'docker push datoast/ejemplodockerhub'
                }
            }
        }
    post {
		always {
			sh 'docker logout'
		}
	 }
    }

