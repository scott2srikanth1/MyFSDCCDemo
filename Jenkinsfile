node{
    stage("Git Clone"){
        git branch: 'main', credentialsId: 'GIT_HUB_CREDENTIALS', url: 'https://github.com/scott2srikanth1/MyFSDCCDemo'
    }
    stage("Docker Build"){

        sh 'docker build -t myfsdcc_pipeline .'
        sh 'docker tag myfsdcc_pipeline scott2srikanth/myfsdcc_pipeline:latest'

    }

     withCredentials([string(credentialsId: 'dockerhub', variable: 'password')]){
         sh 'docker login -u scott2srikanth -p $password'
     }

    stage("Push image to Dockerhub"){
        sh 'docker push scott2srikanth/myfsdcc_pipeline:latest'
    }

     stage("Spin-up Kubernetes"){
        sh 'kubectl apply -f mykube.yaml'
    }
}