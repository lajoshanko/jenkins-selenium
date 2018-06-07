node("master") {

    stage('Preps') {
        stage('Checkout docker compose file') {
          git 'https://github.com/lajoshanko/jenkins-selenium.git'
        }
        stage('Run docker compose up') {
            sh 'sudo dockerd &'
            sh 'sudo docker-compose up -d'
        }
    }

    stage ('Run tests'){
        stage('Checkout the test repo') {
            git branch: 'master', credentialsId: 'bitbucket', url: 'https://lajos.hanko@bitbucket.icellmobilsoft.hu/scm/nejp/nejp-frontend-test.git'
        }
        stage('Run the tests') {
            sh 'mvn -B clean test'
        }
    }

    stage ('Tear down') {
        sh 'sudo docker-compose stop'
        sh 'sudo pkill dockerd'
    }
}