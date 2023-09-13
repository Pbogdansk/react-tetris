version: '3'


services:

 build:

  build:

   context: .

   dockerfile: Dockerfile_build

  volumes:

   - app-data:/usr/src/app

  ports:

   - "8081:8080"



 test:

  build:

   context: .

   dockerfile: Dockerfile_test

  volumes:

   - app-data:/usr/src/app


volumes:

 app-data:


https://chrisyeh96.github.io/2021/08/13/github-personal-access-tokens.html

token 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

<a href="url">link text</a>


pipeline {

  agent { docker { image 'node:18.17.1-alpine3.18' } }

  stages {

    stage('build') {

      steps {

        sh 'node --version'

      }

    }

  }

}


pipeline {

 agent any

 stages {

  stage('Build') {

   steps {

    sh 'yarn'

    sh 'yarn build'

   }

   post {

    success {

     echo 'Build is successful'

    }

    failure {

     echo 'Build errored'

    }

   }

  }

  stage('Test') {

   steps {

    sh 'yarn test'

   }

   post {

    success {

     echo 'Tests: passing'

     archiveArtifacts artifacts: 'tests.txt', followSymlinks: false

    }

    failure {

     echo 'Tests: failing'

    }

   }

  }

  stage('Deploy') {

   steps {

    sh 'docker-compose up -d'

   }

   post {

    success {

     echo 'Deployed!'

    }

    failure {

     echo 'Deployment failed'

    }

   }

  }

 }

}
