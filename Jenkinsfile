node{
    stage("Git Clone"){
        git branch: 'main', credentialsId: 'GIT_HUB_CREDENTIALS', url: 'https://github.com/scott2srikanth1/MyFSDCCDemo'
    }
    stage("Docker Build"){

        sh 'docker build -t myfsdcc .'
        sh 'docker tag myfsdcc scott2srikanth/myfsdcc:latest'

    }

     withCredentials([string(credentialsId: 'dockerhub', variable: 'password')]){
         sh 'docker login -u scott2srikanth -p $password'
     }

    stage("Push image to Dockerhub"){
        sh 'docker push scott2srikanth/myfsdcc:latest'
    }
}