node{
    stage("Git Clone"){
        git branch: 'main', credentialsId: 'GIT_HUB_CREDENTIALS', url: 'https://github.com/scott2srikanth1/MyFSDCCDemo'
    }
    stage("Docker Build"){
        sh 'docker version'
    }
}