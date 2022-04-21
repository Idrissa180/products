node{

    stage("SCM Checkout"){
        git credentialsId: 'git-credential', url: 'https://github.com/enoch180/products.git'
    }

    stage("Build Docker Image"){
        sh "docker build -t enoch180/clientui:1.0 ."
    }

    stage("Push Docker Image"){
        withCredentials([string(credentialsId: 'docker-pwd', variable: 'pwd')]) {
            sh "docker login -u enoch180 -p ${pwd}"
        }
        sh "docker push enoch180/clientui:1.0"
    }
    stage("Deploying App to kubernetes"){
        kubernetesDeploy(configs: "Deployment.yaml", kubeconfigId: "kubernetes")
    }
    
}
