node("master") {

    stage('Preps') {
        stage('Checkout docker compose file') {
          git 'https://github.com/lajoshanko/jenkins-selenium/blob/master/docker-compose.yml'
        }
        stage('Run docker compose up') {
            sh 'docker-compose up -d'
        }
    }

    stage ('Run tests'){
        stage('Checkout the test repo') {
            git 'https://lajos.hanko@bitbucket.icellmobilsoft.hu/scm/nejp/nejp-frontend-test.git'
        }
        stage('Run the tests') {
            sh 'mvn -B clean test'
        }
    }

    stage ('Tear down') {
        sh 'docker-compose stop'
    }
}